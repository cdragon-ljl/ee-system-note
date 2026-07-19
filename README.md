# 嵌入式软件知识体系 · 深度技术文章

一个专注于嵌入式软件开发的深度技术文章合集，从 C 语言核心到 RTOS、ARM 底层、工具链等全方位覆盖。

## 📚 文章列表

| # | 标题 | 文件 | 状态 |
|---|------|:----:|:----:|
| 01 | C语言核心关键字深度解析（volatile / const / static / extern） | [`articles/01-c-volatile-const-static-extern.md`](articles/01-c-volatile-const-static-extern.md) | ✅ |
| 02 | 函数指针与回调机制：嵌入式状态机的灵魂 | [`articles/02-c-function-pointer-callback-state-machine.md`](articles/02-c-function-pointer-callback-state-machine.md) | ✅ |
| 03 | 结构体位域与内存对齐：省内存也要讲效率 | [`articles/03-bit-field-memory-alignment.md`](articles/03-bit-field-memory-alignment.md) | ✅ |
| 04 | `__attribute__` 妙用：编译器扩展让 C 更强大 | [`articles/04-c-attribute-extensions.md`](articles/04-c-attribute-extensions.md) | ✅ |
| 05 | 宏的高级写法：从 `do{}while(0)` 到 `##` 拼接 | [`articles/05-c-macro-advanced-do-while-pp-join.md`](articles/05-c-macro-advanced-do-while-pp-join.md) | ✅ |
| 06 | C++ 智能指针与 RAII：嵌入式也能用 | [`articles/06-cpp-smart-pointer-raii-embedded.md`](articles/06-cpp-smart-pointer-raii-embedded.md) | ✅ |
| 07 | C++ 移动语义与模板元编程实战 | [`articles/07-cpp-move-semantics-template-meta.md`](articles/07-cpp-move-semantics-template-meta.md) | ✅ |
| 08 | 现代 C++ 嵌入式开发最佳实践 | [`articles/08-cpp-modern-embedded-practice.md`](articles/08-cpp-modern-embedded-practice.md) | ✅ |
| 09 | Rust 嵌入式 no_std 入门 | [`articles/09-rust-embedded-no-std-baremetal.md`](articles/09-rust-embedded-no-std-baremetal.md) | ✅ |
| 10 | MicroPython 在嵌入式测试与自动化中的应用 | [`articles/10-micropython-embedded-test-automation.md`](articles/10-micropython-embedded-test-automation.md) | ✅ |
| 11 | Makefile 与 CMake：嵌入式构建系统精讲 | [`articles/11-makefile-cmake-embedded-build.md`](articles/11-makefile-cmake-embedded-build.md) | ✅ |
| 12 | 链接脚本深入解析 | [`articles/12-linker-script-deep-dive.md`](articles/12-linker-script-deep-dive.md) | ✅ |
| 13 | ARM 汇编与 AAPCS 调用规范 | [`articles/13-arm-assembly-thumb-aapcs.md`](articles/13-arm-assembly-thumb-aapcs.md) | ✅ |
| 14 | STM32 时钟树从 HSE 到 SysClk | [`articles/14-stm32-clock-tree-hse-sysclk.md`](articles/14-stm32-clock-tree-hse-sysclk.md) | ✅ |
| 15 | NVIC 中断优先级：抢占与子优先级 | [`articles/15-nvic-interrupt-priority-preempt-sub.md`](articles/15-nvic-interrupt-priority-preempt-sub.md) | ✅ |
| 16 | STM32 DMA 双缓冲乒乓实战 | [`articles/16-stm32-dma-double-buffer-ping-pong.md`](articles/16-stm32-dma-double-buffer-ping-pong.md) | ✅ |
| 17 | HAL 与 LL 库选型决策指南 | [`articles/17-hal-vs-ll-library-choice.md`](articles/17-hal-vs-ll-library-choice.md) | ✅ |
| 18 | 启动文件分析：从 Reset 到 main | [`articles/18-startup-file-reset-to-main.md`](articles/18-startup-file-reset-to-main.md) | ✅ |
| 19 | ESP32 双核 FreeRTOS SMP 实战 | [`articles/19-esp32-dual-core-freertos-smp.md`](articles/19-esp32-dual-core-freertos-smp.md) | ✅ |
| 20 | ESP32 WiFi + BLE 共存机制 | [`articles/20-esp32-wifi-ble-coexistence.md`](articles/20-esp32-wifi-ble-coexistence.md) | ✅ |
| 21 | OTA 与分区表设计：嵌入式设备的生命线 | [`articles/21-ota-partition-design.md`](articles/21-ota-partition-design.md) | ✅ |
| 22 | ESP-IDF 构建系统：从 menuconfig 到 idf.py | [`articles/22-esp-idf-build-system.md`](articles/22-esp-idf-build-system.md) | ✅ |
| 23 | Nordic nRF52 BLE 开发：SoftDevice 架构深入 | [`articles/23-nrf52-softdevice-ble.md`](articles/23-nrf52-softdevice-ble.md) | ✅ |
| 24 | GD32 / NXP / TI 与 STM32 的差异对比 | [`articles/24-gd32-nxp-ti-comparison.md`](articles/24-gd32-nxp-ti-comparison.md) | ✅ |
| 25 | 低功耗设计实战：STOP / STANDBY 模式与唤醒策略 | [`articles/25-low-power-sleep-wakeup.md`](articles/25-low-power-sleep-wakeup.md) | ✅ |
| 26 | Cortex-M 中断向量表与 VTOR：灵活的中断管理 | [`articles/26-cortex-m-vtor-vector-table.md`](articles/26-cortex-m-vtor-vector-table.md) | ✅ |
| 27 | 特权级与 MPU：给你的嵌入式系统加一道防火墙 | [`articles/27-privilege-mpu-memory-protection.md`](articles/27-privilege-mpu-memory-protection.md) | ✅ |
| 28 | SysTick 的妙用：不止是 RTOS 的心跳 | [`articles/28-systick-timer-usage.md`](articles/28-systick-timer-usage.md) | ✅ |
| 29 | bit-band 操作：Cortex-M 的原子位操作黑科技 | [`articles/29-bit-band-atomic-operation.md`](articles/29-bit-band-atomic-operation.md) | ✅ |
| 30 | HardFault 排查三板斧：SP→PC→LR→addr2line | [`articles/30-hardfault-debug-sp-pc-lr-addr2line.md`](articles/30-hardfault-debug-sp-pc-lr-addr2line.md) | ✅ |
| 31 | Cortex-M 异常入栈/出栈完整流程 | [`articles/31-cortex-m-exception-stack-unstack.md`](articles/31-cortex-m-exception-stack-unstack.md) | ✅ |
| 32 | Cortex-A 的 MMU 与虚拟内存：从页表到 TLB | [`articles/32-cortex-a-mmu-virtual-memory.md`](articles/32-cortex-a-mmu-virtual-memory.md) | ✅ |
| 33 | L1 / L2 Cache 一致性问题：flush 与 invalidate 的艺术 | [`articles/33-cache-coherency-flush-invalidate.md`](articles/33-cache-coherency-flush-invalidate.md) | ✅ |
| 34 | TrustZone 与异常等级 EL0-EL3 | [`articles/34-trustzone-exception-level-el0-el3.md`](articles/34-trustzone-exception-level-el0-el3.md) | ✅ |
| 35 | RISC-V 与 ARM 的核心差异：CSR 寄存器与中断模型 | [`articles/35-riscv-arm-csr-interrupt-diff.md`](articles/35-riscv-arm-csr-interrupt-diff.md) | ✅ |
| 36 | UART 深入：波特率容限、FIFO 与硬流控 | [`articles/36-uart-baudrate-fifo-flow-control.md`](articles/36-uart-baudrate-fifo-flow-control.md) | ✅ |
| 37 | RS485 与 Modbus RTU：工业通信的黄金搭档 | [`articles/37-rs485-modbus-rtu-industrial.md`](articles/37-rs485-modbus-rtu-industrial.md) | ✅ |
| 38 | I²C 多主仲裁与时钟拉伸：从机不听话怎么办 | [`articles/38-i2c-multi-master-arbitration-clock-stretch.md`](articles/38-i2c-multi-master-arbitration-clock-stretch.md) | ✅ |
| 39 | SPI 的四种模式与时序图速记法 | [`articles/39-spi-four-modes-timing-diagram.md`](articles/39-spi-four-modes-timing-diagram.md) | ✅ |
| 40 | EtherCAT 从站控制器：工业以太网的飞读飞写 | [`articles/40-ethercat-esc-slave-controller.md`](articles/40-ethercat-esc-slave-controller.md) | ✅ |

## 🎯 定位

每篇文章专注一个核心主题，深入底层原理 + 代码实战，适合：

- 嵌入式软件开发工程师
- 从单片机转向 Linux/RTOS 开发的工程师
- 想系统性巩固嵌入式软件功底的开发者

## 📖 阅读建议

按编号顺序阅读效果最佳，每篇文章约 1500–2000 字，可在公众号「学嵌入式的长路」上查看排版版本。

## 🤝 许可

仅供学习和参考。
