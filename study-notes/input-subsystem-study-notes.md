# Linux Input 子系统学习笔记

> 来源：i.MX6ULL 嵌入式Linux驱动课程 · 魏老师（海归博士 dr.wei）
> 整理日期：2026-07-13

---

## 一、前情回顾：一切皆文件

在学 input 子系统之前，先回顾 LED 和蜂鸣器的驱动方式：

| 设备 | 操作 | 关键文件 |
|------|------|---------|
| LED | `write` → brightness | `/sys/class/leds/xxx/brightness` |
| 蜂鸣器 (beep) | `write` → 同上 | `/sys/class/beep/xxx/` |

**核心思想：** Linux 下一切皆文件，控制设备就是读写对应的设备文件。

- 往 `brightness` 写 `1` → 亮/响
- 往 `brightness` 写 `0` → 灭/静

> 💡 **控制变量法：** 魏老师先用简单硬件（LED/蜂鸣器）让你聚焦"Linux 如何驱动设备"——流程一样，硬件复杂度可逐步增加。

---

## 二、什么是 Input 子系统

### 2.1 解决的问题

输入设备种类繁多，差异巨大：

| 设备 | 特点 |
|------|------|
| 按键 | 简单高低电平 |
| 键盘 | 几十个键，每个产生扫描码 |
| 鼠标 | 相对位移 |
| 触摸屏 | 多点 + 滑动，坐标数据 |
| 传感器 | 各种类型 |

**核心目标：屏蔽硬件差异，统一管理。**

### 2.2 工作原理

```
输入设备 → 驱动层 → input 子系统 → 设备节点 (/dev/input/eventX) → 应用程序 read()
```

- 输入设备注册后，在 `/dev/input/` 下生成设备节点——`eventX`
- 应用程序通过 `open()` 打开，`read()` 读取事件数据
- **输入设备用 `read`**（区别于 LED 等输出设备用 `write`）

### 2.3 设备节点示例

| 设备 | 节点（举例） |
|------|-------------|
| 按键 (GPIO) | `/dev/input/event2` |
| 触摸屏 | `/dev/input/event1` |
| 键盘 | `/dev/input/event3` |

> 具体对应关系可通过 `/proc/bus/input/devices` 查看。

---

## 三、核心数据结构：`struct input_event`

应用程序通过 `read()` 读取到的数据存放在这个结构体中：

```c
struct input_event {
    struct timeval time;  // 时间戳（可暂不关注）
    unsigned short type;  // 事件类型（16位，无符号）
    unsigned short code;  // 事件编码（16位，无符号）
    int value;            // 事件值（32位，有符号）
};
```

**核心三要素：`type`、`code`、`value`**

---

## 四、Type — 事件类型

`type` 决定了这是什么类型的事件。

| 宏定义 | 值 | 含义 | 适用设备 |
|--------|:--:|------|---------|
| `EV_KEY` | 1 | 按键类事件 | 按键、键盘 |
| `EV_REL` | 2 | 相对位移 | 鼠标 |
| `EV_ABS` | 3 | 绝对坐标 | 触摸屏 |
| `EV_SYN` | 0 | 同步事件 | 数据同步收尾 |

> 头文件中有宏定义，直接使用宏名即可，不需要记数值。

---

## 五、Code — 事件编码

`code` 的含义**取决于 `type`**。

### 5.1 当 type = EV_KEY（按键事件）

`code` 表示具体哪个按键：

| 宏定义 | 值 | 含义 |
|--------|:--:|------|
| `KEY_ENTER` | 28 | 回车键 |
| `KEY_1` | 2 | 数字键 1 |
| `KEY_A` | 21 | A 键 |
| `KEY_B` | 22 | B 键 |
| `KEY_POWER` | 29 | 电源键 |
| ... | ... | ... |

所有按键的 `code` 都在 Linux 头文件中预定义好了。

### 5.2 当 type = EV_REL（相对位移）

`code` 表示移动方向：
- `REL_X` — X 轴方向
- `REL_Y` — Y 轴方向

### 5.3 当 type = EV_ABS（绝对坐标）

`code` 表示坐标轴：
- `ABS_X` — X 轴坐标
- `ABS_Y` — Y 轴坐标

---

## 六、Value — 事件值

`value` 的含义同样**取决于 `type`**。

### 6.1 按键事件（EV_KEY）

| value | 含义 |
|:-----:|------|
| 0 | 松开 (release) |
| 1 | 按下 (press) |
| 2 | 长按 (repeat/long press) |

### 6.2 坐标事件（EV_ABS / EV_REL）

- `EV_ABS`（触摸屏）：value = 坐标值（如 `130` 表示 X=130）
- `EV_REL`（鼠标）：value = 偏移量（如 `+50` 表示向上50个单位）

---

## 七、编程步骤

### 7.1 完整流程

```c
#include <stdio.h>
#include <fcntl.h>
#include <linux/input.h>

int main() {
    // 1. 打开设备节点（输入设备只读打开）
    int fd = open("/dev/input/event2", O_RDONLY);
    if (fd < 0) {
        perror("open");
        return -1;
    }

    // 2. 声明 input_event 结构体
    struct input_event ev;

    // 3. 读取事件（阻塞模式：没事件时休眠）
    while (1) {
        read(fd, &ev, sizeof(ev));

        // 4. 分析 type
        if (ev.type == EV_KEY) {
            // 这是一个按键事件

            // 5. 分析 code — 哪个按键
            if (ev.code == KEY_ENTER) {
                // 回车键

                // 6. 分析 value — 按下/松开/长按
                if (ev.value == 1) {
                    printf("回车键按下了！\n");
                } else if (ev.value == 0) {
                    printf("回车键松开了！\n");
                } else if (ev.value == 2) {
                    printf("回车键长按中...\n");
                }
            }
        }
    }

    close(fd);
    return 0;
}
```

### 7.2 判断逻辑总结

```
读事件 → 判断 type
           ├── EV_KEY (1) → 判断 code（哪个按键）→ 判断 value（按下/松开/长按）
           ├── EV_REL (2) → 判断 code（X/Y轴）→ value 是偏移量
           ├── EV_ABS (3) → 判断 code（X/Y轴）→ value 是坐标值
           └── EV_SYN (0) → 同步信号，忽略
```

---

## 八、调试方法：查看设备映射

### 8.1 查看所有输入设备

```bash
cat /proc/bus/input/devices
```

输出示例：

```
I: Bus=... Vendor=... Product=... Version=...
N: Name="gpio-keys"
P: Phys=gpio-keys/input0
H: Handlers=sysrq kbd event2
B: EV=3
B: KEY=100000 0 0 0
```

关键信息：
- **Handlers** 字段显示 `event2` → 该设备对应 `/dev/input/event2`
- **Name** 字段显示设备名

### 8.2 查看设备节点

```bash
ls -l /dev/input/
```

典型输出：
```
crw-rw---- 1 root input 13, 64 ... event0    # power key（电源键）
crw-rw---- 1 root input 13, 65 ... event1    # touch screen（触摸屏）
crw-rw---- 1 root input 13, 66 ... event2    # gpio keys（用户按键）
```

---

## 九、实践：i.MX6ULL 按键实验

### 硬件信息

- 红色按键（左边）→ **Reset**（重启，不用于用户程序）
- 黄色按键（右边）→ **用户按键** → GPIO → 对应 `event2`

### 实验步骤

1. 连接开发板（MobaXterm / Serial: COM4, 115200, None）
2. 查看设备映射：
   ```bash
   cat /proc/bus/input/devices
   ```
3. 找到 GPIO 按键对应的 event（本例中为 `event2`）
4. 编写程序，打开 `/dev/input/event2`
5. `read()` 读取事件，解析 `type/code/value`
6. 验证：按下黄色按键 → 输出相应信息

---

## 十、知识要点总结

### 10.1 与裸机（单片机）的关键区别

| 对比项 | 裸机（51/STM32） | Linux Input 子系统 |
|--------|-----------------|-------------------|
| 按键扫描 | 轮询或外部中断 | 应用层 read() 阻塞等待 |
| 事件处理 | 手动判断引脚电平 | read 获取结构体，分析 type/code/value |
| 多设备管理 | 各自为政 | 统一接口，统一框架 |
| 扩展性 | 每加一个设备重新写 | 驱动注册即可，应用代码不变 |

### 10.2 一句话总结

> Linux input 子系统通过统一的 `type` + `code` + `value` 三要素，屏蔽了所有输入设备的硬件差异，应用程序只需要 `open → read → 解析` 三步即可处理按键、鼠标、触摸屏等任何输入设备。

### 10.3 下一步学习方向

- 触摸屏驱动：`EV_ABS` 类型，多点触摸协议
- 编写 input 子系统驱动（内核层）
- 使用 `select/poll/epoll` 同时管理多个输入设备
- 输入子系统与设备树的配合

---

> 🏷️ `#Linux驱动` `#Input子系统` `#嵌入式Linux` `#i.MX6ULL` `#设备驱动` `#EV_KEY` `#学习笔记`
