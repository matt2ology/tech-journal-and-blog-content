---
authors:
  - Matt2ology
categories:
  - blog
  - raspberry-pi
  - how-to
date: 2025-02-23T21:08:39-08:00
draft: false
notes: blog
related-notes:
tags:
title: How to setup a USB thermal printer using ESC/POS commands with a Raspberry Pi
---

## How to setup a USB thermal printer using ESC/POS commands with a Raspberry Pi

<!-- [Propose edits or changes on GitHub](link to GitHub repo of file) -->

Inspired from [IEEE Spectrum short video: Here's how to build the perfect cryptographic machine](https://youtube.com/shorts/Nyf0d2rZQV0?si=GaLDK8N-HZI4nOhX), and full guide by [IEEE Spectrum's Director of Special Projects - Stephen Cass](https://spectrum.ieee.org/diy-one-time-pad-machine), compelled me to buy on Amazon a [Rongta RP332 POS Printer, 80mm Direct Thermal Receipt Printer with Auto Cutter, USB Serial Ethernet Interface](https://a.co/d/1DgqVRx).

This "how-to" details the commands and steps I've executed to get started and have text
printed to the thermal printer.

### Setup the Raspberry Pi & Printer

Update your Raspberry Pi

```sh
sudo apt-get update
sudo apt-get install python3-pip
```

#### **Check if the Printer is Recognized**

Connect the USB thermal printer to your Raspberry Pi and run:

```bash
lsusb
```

This will list connected USB devices. Your printer should appear in the list.

With some plugging-and-unplugging... I've found that the Rongta's Thermal Receipt Printer
when connected via USB populated as:

> `Bus 001 Device 003: ID 0fe6:811e ICS Advent Parallel Adapter`

Without any options, it provides a concise list of connected USB devices basic output
typically shows:

- **Bus Number:** \[`001`\] The USB bus the device is connected to.  
- **Device Number:** \[`003`\] The device's unique number on that bus.  
- **ID:** \[`0fe6:811e`\] The vendor and product IDs (in hexadecimal format).
  - **Vender ID:** `0fe6`: This is the vendor ID, identifying ICS Advent.
  - **Product ID:** `811e`: This is the product ID, specifically for their parallel adapter.
- **Device Description:** \[`ICS Advent Parallel Adapter`\] A brief description of the device.

I can find out more detailed information by using the following command format

```bash
lsusb -v -s Bus_Number:Device_Number
```

Next, find the printer’s device path:

```bash
ls /dev/usb/lp*
```

If a device like `/dev/usb/lp0` appears, your printer is recognized.

### Test Printing from Command Line

Try printing a test message:

```bash
echo -e 'Hello, Thermal Printer!\n' | sudo tee /dev/usb/lp0
```

- **`-e` flag**: This enables interpretation of escape sequences (like `\n` for a newline). Without `-e`, the escape sequences would be printed literally
- **`tee`**: This command reads from standard input and writes the input to both standard output (your terminal) and to the file specified—in this case, `/dev/usb/lp0`
- **`/dev/usb/lp0`**: This is the device file for the USB thermal printer. Writing data to this file sends it directly to the printer.

### Test Script

This Python script is designed to send formatted text to a thermal receipt printer using
[ESC/POS (Escape Sequence for Point of Sale) commands](https://escpos.readthedocs.io/en/latest/index.html).

```python
import os

# Define the printer device path (adjust as needed)
PRINTER_DEVICE = "/dev/usb/lp0"

# ESC/POS Commands
ESC_INIT = b'\x1B\x40'                # Initialize printer
ESC_BOLD_ON = b'\x1B\x45\x01'         # Bold text ON
ESC_BOLD_OFF = b'\x1B\x45\x00'        # Bold text OFF
ESC_UNDERLINE_ON = b'\x1B\x2D\x01'    # Underline ON
ESC_UNDERLINE_OFF = b'\x1B\x2D\x00'   # Underline OFF
ESC_DOUBLE_HEIGHT = b'\x1D\x21\x01'   # Double height
ESC_DOUBLE_WIDTH = b'\x1D\x21\x10'    # Double width
ESC_NORMAL = b'\x1D\x21\x00'          # Normal text formatting
ESC_REVERSE_ON = b'\x1D\x42\x01'      # Reverse (inverted) text ON
ESC_REVERSE_OFF = b'\x1D\x42\x00'     # Reverse text OFF
ESC_FEED_LINES = b'\x1B\x64\x03'      # Feed 3 lines
ESC_CUT_PAPER = b'\x1B\x6D\x00'       # Cut paper (Full Cut)

# Test text demonstrating various formatting and style
TEST_TEXT = (
    ESC_INIT +
    # Header: Double width, double height, bold
    ESC_DOUBLE_WIDTH + ESC_DOUBLE_HEIGHT + ESC_BOLD_ON + b"TEST PRINT - FORMATTING\n" +
    ESC_NORMAL + ESC_BOLD_OFF +
    b"---------------------------------------\n\n" +

    # Bold Text
    ESC_BOLD_ON + b"Bold Text Example\n" + ESC_BOLD_OFF +

    # Underlined Text
    ESC_UNDERLINE_ON + b"Underlined Text Example\n" + ESC_UNDERLINE_OFF +

    # Reversed (Inverted) Text
    ESC_REVERSE_ON + b"Reversed (Inverted) Text Example\n" + ESC_REVERSE_OFF +

    # Double Width Text
    ESC_DOUBLE_WIDTH + b"Double Width Text Example\n" + ESC_NORMAL +

    # Double Height Text
    ESC_DOUBLE_HEIGHT + b"Double Height Text Example\n" + ESC_NORMAL +

    # Mixed Formatting
    b"Mixing Styles: " +
    ESC_BOLD_ON + b"Bold " + ESC_BOLD_OFF +
    ESC_UNDERLINE_ON + b"Underlined " + ESC_UNDERLINE_OFF +
    ESC_DOUBLE_WIDTH + b"Double Width " + ESC_NORMAL +
    ESC_DOUBLE_HEIGHT + b"Double Height" + ESC_NORMAL + b"\n\n" +

    # Normal text with Lorem Ipsum sample
    b"Lorem ipsum dolor sit amet, consectetur adipiscing elit. " +
    b"Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.\n" +
    b"Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.\n\n" +

    ESC_FEED_LINES +
    ESC_CUT_PAPER
)

try:
    # Open the printer device and send data
    with open(PRINTER_DEVICE, "wb") as printer:
        printer.write(TEST_TEXT)
    print("Test print with various formatting completed successfully!")
except PermissionError:
    print("Permission denied. Try running with sudo or check device permissions.")
except FileNotFoundError:
    print(f"Printer device {PRINTER_DEVICE} not found. Check your connection.")
except Exception as e:
    print(f"Error: {e}")
```

<!-- ## Related blogs -->

<!-- [Related blog post]({{< ref "/post/blog/path_to_file.md" >}}) -->
