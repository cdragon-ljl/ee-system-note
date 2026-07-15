# 嵌入式软件技术深度笔记 📓

> 公众号「学嵌入式的长路」的知识体系文章仓库

系统化整理嵌入式软件开发所需的**编程语言**、**MCU平台**、**RTOS**、**Linux驱动**、**AI边缘计算**、**PCB硬件**、**项目工程化**、**求职面试**等全栈知识。

---

## 📂 仓库结构

| 目录 | 说明 |
|------|------|
| `articles/` | 主文章系列 #01~#20（编程语言 → MCU 基础知识） |
| `frameworks/` | 系列框架文档、标题列表、JD拆解框架 |
| `study-notes/` | B站视频学习笔记、Linux子系统、RV1126 笔记 |
| `learning-roadmaps/` | i.MX6ULL、RV1126 AI视觉 学习路线图 |
| `jd-decode/` | 嵌入式岗位 JD 拆解系列 |

---

## 📝 主文章系列（已发布 & 待发布）

### 一、编程语言（#01~#13）

| # | 标题 | 状态 |
|:-:|------|:----:|
| 01 | C语言核心关键字深度解析（volatile / const / static / extern） | ✅ |
| 02 | 函数指针与回调机制：嵌入式状态机的灵魂 | ✅ |
| 03 | 结构体位域与内存对齐：省内存也要讲效率 | ✅ |
| 04 | `__attribute__` 妙用：编译器扩展让 C 更强大 | ✅ |
| 05 | 宏的高级写法：从 `do{}while(0)` 到 `##` 拼接 | ✅ |
| 06 | C++ 智能指针：嵌入式中的 RAII 与所有权管理 | ✅ |
| 07 | C++ 移动语义与模板元编程入门 | ✅ |
| 08 | C++11/14/17/20 在嵌入式中的落地实践 | ✅ |
| 09 | Rust 嵌入式编程：no_std 裸机开发实战 | ✅ |
| 10 | MicroPython 与嵌入式测试自动化 | ✅ |
| 11 | Makefile 进阶与 CMake 实战 | ✅ |
| 12 | 链接脚本逐行解读：从编译到运行的最后一步 | ✅ |
| 13 | ARM 汇编基础：Thumb / Thumb-2 与 AAPCS 调用约定 | ✅ |

### 二、MCU 平台（#14~#25）

| # | 标题 | 状态 |
|:-:|------|:----:|
| 14 | STM32 时钟树完全解析：从 HSE 到 SYSCLK | ✅ |
| 15 | NVIC 中断优先级：抢占优先级与子优先级的博弈 | ✅ |
| 16 | STM32 DMA 双缓冲：让数据传输飞起来 | ✅ |
| 17 | HAL 库 vs LL 库：选择、混合与抽象层设计 | ✅ |
| 18 | 启动文件逐行拆解：从 Reset 到 main | ✅ |
| 19 | ESP32 双核 FreeRTOS：SMP 调度深度解析 | ✅ |
| 20 | ESP32 Wi-Fi + BLE 共存：协议栈与内存布局 | ✅ |

> 完整 97 篇文章规划详见 [`frameworks/embedded-knowledge-series-framework.md`](frameworks/embedded-knowledge-series-framework.md)

---

## 🧠 学习笔记

| 文件 | 来源 | 说明 |
|------|------|------|
| `i.MX6ULL 驱动开发笔记` | B站视频 | 从ARM芯片到操作系统，基于正点原子 i.MX6ULL |
| `Linux Input 子系统` | B站视频 | 输入子系统框架、驱动层级、事件处理 |
| `RV1126 AI视觉入门` | 学习笔记 | 从 ARM 到 AI 芯片，第一篇入门笔记 |
| `B站嵌入式笔记` | B站视频 | 嵌入式 Linux 学习笔记汇总 |

---

## 💼 JD拆解系列

看真实的嵌入式岗位 JD → 分析技能画像 → 出面试题 + 标准回答

- [JD拆解框架](frameworks/jd-decode-framework.md)
- [#001 具身机器人嵌入式开发](jd-decode/jd-decode-001-embodied-robot-embedded-v4.md)

---

## 🛣️ 学习路线图

- [i.MX6ULL 嵌入式 Linux 学习路线](learning-roadmaps/i.MX6ULL-learning-roadmap.md)
- [RV1126 AI 视觉学习路线](learning-roadmaps/RV1126-AI-vision-learning-roadmap.md)

---

## 📅 发布节奏

所有主文章发布于 **周二 / 周四 / 周日 21:00**

> 公众号：**学嵌入式的长路**

---

## ⚖️ License

本仓库内容仅供学习交流使用。
