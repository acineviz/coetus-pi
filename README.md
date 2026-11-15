# 🎮 Coetus-Pi

**A lightweight, bare-metal-feel gaming console OS and launcher for Raspberry Pi.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform](https://img.shields.io/badge/Platform-Raspberry%20Pi%204%20%7C%205-C51A4A?logo=raspberry-pi)](https://www.raspberrypi.com/)
[![Graphics](https://img.shields.io/badge/Graphics-KMS%2FDRM%20%7C%20OpenGL%20ES-blue)](#architecture)
[![Status](https://img.shields.io/badge/Status-Early%20Development-orange)](#roadmap)

Coetus-Pi transforms a standard Raspberry Pi into a dedicated gaming console. By bypassing heavy desktop environments (X11/Wayland) and rendering directly to the hardware via **KMS/DRM**, it delivers near-zero input latency, fast boot times, and maximum system resource allocation for games.

---

## ✨ Key Features

*   **Zero Desktop Overhead:** Runs directly on Linux Framebuffer / KMS/DRM without X11 or Wayland.
*   **Fast Boot Experience:** Stripped-down background services allow the console UI to launch within seconds of powering on.
*   **Controller-First UI:** Designed from the ground up for seamless gamepad navigation (Xbox, PlayStation, and generic HID controllers).
*   **Hardware Accelerated:** Powered by Broadcom VideoCore GPU drivers (Mesa/V3D) with OpenGL ES / Vulkan support.
*   **Modular Game Execution:** Supports native Raspberry Pi binaries (SDL2, Raylib, Godot) as well as Libretro-based emulators.

---

## 🏗️ Architecture

    +-------------------------------------------------------+ 
    |                Coetus-Pi Console UI                   |
    |        (C++ / SDL2 / OpenGL ES - Hardware Accel)      |
    +-------------------------------------------------------+
    |              Input (evdev) & Audio (ALSA)             |
    +-------------------------------------------------------+
    |           Linux Kernel + KMS/DRM + Mesa V3D           |
    +-------------------------------------------------------+
    |             Raspberry Pi Hardware (ARM64)             |
    +-------------------------------------------------------+


🛠️ Prerequisites & Hardware Support
Supported Hardware: Raspberry Pi 4 Model B, Raspberry Pi 5 (Raspberry Pi 3B+ supported with reduced visual effects).

Base OS: Raspberry Pi OS Lite (64-bit / Bookworm or newer).

Controllers: Any Linux evdev compatible USB or Bluetooth gamepad.

🚀 Building from Source
1. Install Dependencies
Boot into your Raspberry Pi OS Lite installation and install the required build tools and graphics libraries:

sudo apt update
sudo apt install -y build-essential cmake git libsdl2-dev libgles2-mesa-dev libdrm-dev libgbm-dev

2. Clone & Compile
git clone [https://github.com/YOUR_USERNAME/coetus-pi.git](https://github.com/YOUR_USERNAME/coetus-pi.git)
cd coetus-pi
mkdir build && cd build
cmake ..
make -j$(nproc)

3. Run
Make sure no display manager is occupying the DRM device, then launch directly from the TTY console:
sudo nano /etc/systemd/system/coetus-pi.service


🗺️ Roadmap
[x] Core KMS/DRM rendering pipeline setup
[x] Basic gamepad (evdev) navigation
[ ] Grid-based game library UI & cover art loader
[ ] On-screen virtual keyboard & Wi-Fi manager
[ ] Integrated audio mixer & volume OSD
[ ] Pre-built .img release for direct SD card flashing

🤝 Contributing
Contributions, bug reports, and feature requests are welcome! Feel free to check the issues page or submit a Pull Request.
Fork the Project
Create your Feature Branch (git checkout -b feature/AmazingFeature)
Commit your Changes (git commit -m 'Add some AmazingFeature')
Push to the Branch (git push origin feature/AmazingFeature)
Open a Pull Request

📄 License
Distributed under the MIT License. See LICENSE for more information.



