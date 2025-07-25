# Polygyatt QMK/Vial Setup

This README provides instructions for setting up the Polygyatt keyboard with QMK firmware and Vial support.

## Prerequisites

Before starting, make sure you have the following installed:
- Git
- Python 3.7 or higher
- QMK CLI tools

## Setup Instructions

### 1. Clone the QMK Vial Repository

First, clone the QMK Vial repository from GitHub:

```bash
git clone https://github.com/vial-kb/vial-qmk.git
cd vial-qmk
```

### 2. Complete QMK Setup

Set up the QMK environment by running the setup command:

```bash
qmk setup
```

This will install the necessary dependencies and configure your QMK environment.

### 3. Copy Keyboard Configuration

Copy the `splittinkeebs` folder from this directory to the `keyboards` folder in your QMK installation:

```bash
cp -r /path/to/your/polygyatt/QMK/splittinkeebs ./keyboards/
```

Replace `/path/to/your/polygyatt/QMK/` with the actual path to this directory.

Alternatively, you can create a symbolic link (recommended for development):

```bash
ln -s /path/to/your/polygyatt/QMK/splittinkeebs ./keyboards/splittinkeebs
```

### 4. Compile the Firmware

Compile the Vial-compatible firmware for the Polygyatt keyboard:

```bash
qmk compile -kb splittinkeebs/polygyatt -km vial
```

### 5. Flash the Firmware

After successful compilation, you'll find the firmware file (`.uf2` or `.hex`) in the QMK build directory. To flash it to your Polygyatt keyboard:

#### For RP2040-based boards (UF2 method):
1. Hold the BOOTSEL button on your Polygyatt keyboard while connecting it to your computer
2. The keyboard should appear as a USB mass storage device
3. Copy the generated `.uf2` file to the mounted device
4. The keyboard will automatically reboot with the new firmware

#### Alternative flashing method:
```bash
qmk flash -kb splittinkeebs/polygyatt -km vial
```

## Using Vial

Once the firmware is flashed:

1. Download and install [Vial](https://get.vial.today/)
2. Connect your Polygyatt keyboard
3. Open Vial - it should automatically detect your keyboard
4. Customize your keymap, rotary encoders, and other features in real-time

## Available Keymaps

- `default` - Basic keymap configuration
- `vial` - Vial-compatible keymap with real-time customization support

## Troubleshooting

- If you encounter build errors, ensure QMK is properly set up with `qmk doctor`
- Make sure the `splittinkeebs` folder is correctly placed in the `keyboards` directory
- Verify that the compile command uses the correct keyboard path: `splittinkeebs/polygyatt`
- If Vial doesn't detect your keyboard, ensure you flashed the `vial` keymap, not the `default` one

## Additional Resources

- [QMK Documentation](https://docs.qmk.fm/)
- [Vial Documentation](https://get.vial.today/docs/)
- [QMK Vial Repository](https://github.com/vial-kb/vial-qmk)

For more information about QMK configuration and advanced features, visit the official QMK documentation.