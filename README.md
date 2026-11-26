# SenseHub

Hobby C++ firmware for the **STM32F746G-DISCO** board (STM32F746NGH6, Cortex-M7).

- Base project generated with STM32CubeMX (`sensehub.ioc`, STM32Cube FW_F7 V1.17.4)
- FreeRTOS (CMSIS-RTOS), FatFs on SD card, USB Host
- Build system: CMake + Ninja, GNU Arm toolchain

## Requirements

- [STM32CubeCLT](https://www.st.com/en/development-tools/stm32cubeclt.html) (GNU Arm toolchain, STM32CubeProgrammer, ST-LINK udev rules)
- CMake ≥ 3.22, Ninja

Toolchain and programmer must be on `PATH`, e.g. in `~/.bashrc`:

```bash
export STM32CLT_PATH=/opt/st/stm32cubeclt_1.23.0
export PATH="$STM32CLT_PATH/GNU-tools-for-STM32/bin:$STM32CLT_PATH/STM32CubeProgrammer/bin:$PATH"
```

## Build & flash

```bash
cmake --preset Debug                          # configure (once)
cmake --build --preset Debug                  # build
cmake --build --preset Debug --target flash   # build + flash via ST-LINK
```

Use the `Release` preset for an optimized build. Output: `build/<preset>/sensehub.elf`.

The board is connected through the on-board ST-LINK (USB connector **CN14**).
