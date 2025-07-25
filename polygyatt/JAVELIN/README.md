# Polygyatt Javelin Steno Setup

This README provides instructions for setting up the Polygyatt keyboard with Javelin steno firmware.

## Prerequisites

Before starting, make sure you have the following installed:
- Git
- CMake (version 3.12 or higher)
- GCC ARM toolchain
- Python 3

## Setup Instructions

### 1. Clone the Javelin Steno Pico Repository

First, clone the javelin-steno-pico repository from GitHub and complete the setup mentioned there:

```bash
git clone https://github.com/jthlim/javelin-steno-pico.git
cd javelin-steno-pico
```

### 2. Copy Board Configuration

Copy the `polygyatt.h` file from this directory to the `config` folder of the javelin-steno-pico repository:

```bash
cp /path/to/your/polygyatt/JAVELIN/polygyatt.h ./config/
```

Replace `/path/to/your/polygyatt/JAVELIN/` with the actual path to this directory.

### 3. Build the Firmware

Create a build directory and compile the firmware:

```bash
mkdir build
cd build
cmake .. -DJAVELIN_BOARD=polygyatt
make
```

### 4. Flash the Firmware

After successful compilation, you'll find the firmware file (`polygyatt.uf2`) in the build directory. To flash it to your Polygyatt keyboard:

1. Hold the BOOTSEL button on your RP2040-based Polygyatt keyboard while connecting it to your computer
2. The keyboard should appear as a USB mass storage device
3. Copy the `polygyatt.uf2` file to the mounted device
4. The keyboard will automatically reboot with the new firmware

## Troubleshooting

- If you encounter build errors, ensure all prerequisites are properly installed
- Make sure the `polygyatt.h` file is correctly placed in the `config` directory
- Verify that the CMake command includes the correct board specification: `-DJAVELIN_BOARD=polygyatt`

## Additional Resources

- [Javelin Steno Pico Repository](https://github.com/jthlim/javelin-steno-pico)
- [Plover Steno Software](https://www.openstenoproject.org/plover/)

For more information about stenography and the Javelin firmware, visit the main repository documentation.