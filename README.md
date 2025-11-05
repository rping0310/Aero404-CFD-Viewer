# AERO404 CFD VIEWER v1.0

A lightweight CFD (Computational Fluid Dynamics) result visualization tool for viewing and comparing simulation cases with slice images and 3D STL models.

**Author:** Lin Ping  
**Release Date:** November 3, 2025  
**License:** Non-Commercial Use Only

---

## Table of Contents

1. [Overview](#overview)
2. [Key Features](#key-features)
3. [System Requirements](#system-requirements)
4. [Dependencies](#dependencies)
5. [Installation](#installation)
6. [Usage Guide](#usage-guide)
7. [Keyboard Shortcuts](#keyboard-shortcuts)
8. [File Structure Requirements](#file-structure-requirements)
9. [Known Issues](#known-issues)
10. [License](#license)
11. [Contact Information](#contact-information)

---

## Overview

Aero404 CFD Viewer is designed for aerodynamics engineers and researchers, particularly in Formula Student racing teams, to efficiently review CFD simulation results without expensive commercial software. 

### Primary Use Cases
- Formula Student aerodynamics development
- Wing configuration comparison
- Downforce distribution analysis
- Flow structure visualization
- Academic research and education

### Core Capabilities
- Browse multiple simulation cases
- View velocity/pressure slice images with playback controls
- Examine 3D flow structures (Q-criterion isosurfaces)
- Compare two cases side-by-side
- Synchronize views between cases

---

## Key Features

### 📁 Case Management
- Load and browse multiple CFD cases from a directory
- Sort cases by name or aerodynamic coefficients (CL, CD, etc.)
- Display case parameters and simulation results in organized tables
<img width="1847" height="1050" alt="image" src="https://github.com/user-attachments/assets/60daea49-219d-40b6-9126-4383298fb055" />


### 🖼️ Slice Viewer
- View velocity/pressure slice images across different planes
- Playback controls: forward, reverse, frame-by-frame navigation
- Variable playback speed (0.2x to 2.0x)
- Zoom and pan for detailed inspection (mouse wheel + drag)
- Image caching for smooth playback
<img width="1847" height="1049" alt="image" src="https://github.com/user-attachments/assets/13120648-f713-4a9b-97e2-1fce9e1e581b" />


### 🎨 3D STL Viewer
- Load and render Q-criterion isosurface STL files
- Interactive 3D rotation, zoom, and pan
- Wireframe display mode
- Camera reset to default view
<img width="1849" height="1049" alt="image" src="https://github.com/user-attachments/assets/47dc8fa7-5d07-4c28-b3ae-4f07274c5e76" />


### 🔄 Case Comparison
- Load main and sub cases simultaneously
- Side-by-side view with synchronized controls
- Sync options: slice type, slice position, zoom level, 3D camera

### 💻 User Interface
- Tab-based layout: Cases / Slices / 3D / About
- Responsive design supporting 720p and higher resolutions
- Dark theme for reduced eye strain

---

## System Requirements

### Minimum Requirements
- **CPU:** Dual-core processor, 2.0 GHz or higher
- **RAM:** 4 GB
- **GPU:** OpenGL 3.2 compatible graphics card
- **Display:** 1280x720 (720p) or higher
- **Storage:** 100 MB for application + space for CFD data

### Recommended Specifications
- **CPU:** Quad-core processor, 3.0 GHz or higher
- **RAM:** 8 GB or more
- **GPU:** Dedicated graphics card with OpenGL 4.6 support
- **Display:** 1920x1080 (1080p) or higher
- **Storage:** SSD recommended for faster data loading

### Operating System Compatibility

#### ✅ Highly Recommended
- **Ubuntu 22.04 LTS (Jammy Jellyfish)**
  - Mesa 23.x series
  - Most stable and tested platform
  - Best OpenGL compatibility

#### ⚠️ Compatible (with potential issues)
- **Ubuntu 24.04 LTS (Noble Numbat)**
  - Mesa 25.x series
  - May require recompilation or Python execution
  - AMD integrated graphics may have compatibility issues

- **Ubuntu 20.04 LTS (Focal Fossa)**
  - Mesa 21.x series
  - Older but stable

#### 📝 Other Distributions
- Debian 11/12
- Fedora 38+
- openSUSE Leap 15.5+

> **Note:** The application is most stable on Ubuntu 22.04 with Mesa 23.x. Newer Mesa versions (25.x) in Ubuntu 24.04 may cause VTK/OpenGL compatibility issues with certain GPU configurations.

---

## Dependencies

### Python Version
- Python 3.8 or higher (Python 3.10+ recommended)

### Required Python Packages

| Package | Version | Purpose |
|---------|---------|---------|
| PyQt6 | >= 6.0.0 | GUI framework |
| vtk | >= 9.0.0 | 3D visualization |
| numpy | >= 1.20.0 | Numerical operations |

### System Libraries

| Library | Package Name (Ubuntu/Debian) |
|---------|------------------------------|
| OpenGL | `libgl1-mesa-dri` |
| EGL | `libegl1-mesa` |
| GLX | `libglx-mesa0` |
| OSMesa (optional) | `libosmesa6` |
| Mesa Vulkan (optional) | `mesa-vulkan-drivers` |

### Graphics Driver Requirements
- OpenGL 3.2 or higher support
- **For AMD GPUs:** `mesa-vulkan-drivers`, `libglapi-mesa`
- **For NVIDIA GPUs:** `nvidia-driver-XXX` (latest proprietary driver)
- **For Intel GPUs:** `intel-media-va-driver`

---

## Installation

### Option A: Running from Python (Recommended)

1. **Install system dependencies:**
   ```bash
   sudo apt update
   sudo apt install -y python3 python3-pip
   sudo apt install -y libgl1-mesa-dri libegl1-mesa libglx-mesa0
   sudo apt install -y mesa-vulkan-drivers libosmesa6
   ```

2. **Install Python packages:**
   ```bash
   pip3 install PyQt6 vtk numpy --break-system-packages
   ```

3. **Run the application:**
   ```bash
   python3 cfd_viewer_v2.3_final.py
   ```

### Option B: Using Pre-built Executable

1. Download `CFDViewer_v1.0` executable

2. Make it executable:
   ```bash
   chmod +x CFDViewer_v1.0
   ```

3. Run:
   ```bash
   ./CFDViewer_v1.0
   ```

> **Note:** Pre-built executables may have OpenGL compatibility issues on Ubuntu 24.04 or with AMD integrated graphics. If you encounter errors, use Option A (Python execution).

### Troubleshooting OpenGL Issues

If you see "Could not find a decent visual" or "vtkOpenGLRenderWindow" errors:

1. **Verify OpenGL is working:**
   ```bash
   glxinfo | grep "OpenGL version"
   ```

2. **If glxinfo is not installed:**
   ```bash
   sudo apt install mesa-utils
   ```

3. **Install missing libraries:**
   ```bash
   sudo apt install -y libgl1-mesa-dri libegl1-mesa libglx-mesa0 \
                       libosmesa6 mesa-vulkan-drivers
   ```

4. **For AMD Radeon users on Ubuntu 24.04:**  
   Use Python execution method (Option A) instead of the executable.

---

## Usage Guide

### Initial Setup

1. Launch the application
2. Click **Browse...** (📁) button
3. Select your CFD results directory
4. The application will scan for available cases

### Viewing a Single Case

1. In the **Cases** tab, check the checkbox next to a case
2. Click **Load as Main** button
3. Switch to **Slices** or **3D** tab to view results

### Comparing Two Cases

1. In the **Cases** tab, check the first case
2. Click **Load as Main**
3. Check another case
4. Click **Load as Sub**
5. Both cases will appear side-by-side

### Slice Viewer Controls

#### Navigation
- **⏮ First:** Jump to first slice
- **◄ Prev:** Previous slice
- **◄◄ Reverse:** Reverse playback
- **▶ Play:** Forward playback
- **► Next:** Next slice
- **⏭ Last:** Jump to last slice

#### Zoom/Pan
- **Mouse Wheel:** Zoom in/out (100% to 500%)
- **Left Click + Drag:** Pan image when zoomed
- **🔍 100% Button:** Reset zoom and pan

#### Synchronization (when comparing)
- ☑️ **Sync Slice Type:** Both cases show same slice type
- ☑️ **Sync Slice Position:** Both cases show same slice index
- ☑️ **Sync Zoom:** Both cases have same zoom/pan settings

### 3D Viewer Controls

#### Mouse Interaction
- **Left Click + Drag:** Rotate view
- **Middle Click + Drag:** Pan view
- **Mouse Wheel:** Zoom in/out
- **🔄 Reset View:** Return to default camera position

#### Display Options
- **Wireframe:** Toggle between surface and wireframe mode

#### Synchronization (when comparing)
- ☑️ **Sync Camera View:** Both cases have same 3D viewpoint

---

## Keyboard Shortcuts

### Slice Viewer Shortcuts

> **Note:** You must click on the slice image area first to activate shortcuts.

| Key | Action |
|-----|--------|
| `L` | Toggle forward playback |
| `J` | Toggle reverse playback |
| `→` (Right Arrow) | Next slice |
| `←` (Left Arrow) | Previous slice |

---

## File Structure Requirements

The application expects the following directory structure:

```
base_directory/
├── Case_001/
│   ├── q-criterion.stl              # 3D flow structure
│   ├── Result.dat                   # Simulation results
│   ├── case_parameter.dat           # Case parameters
│   ├── x_direction_velocity/        # Slice images
│   │   ├── slice_001.png
│   │   ├── slice_002.png
│   │   └── ...
│   ├── y_direction_velocity/
│   │   └── ...
│   └── z_direction_velocity/
│       └── ...
├── Case_002/
│   └── ...
```

### Result.dat Format

The `Result.dat` file should contain key-value pairs:

```
CLA = 0.5234
FW DF = 125.67
SW DF = 45.32
RW DF = 234.56
UT DF = 67.89
W DF = 473.44
W Drag = 89.12
Aero balance z = 0.0023
```

Supported separators: `=` or `:`

### Slice Directory Naming

Slice directories must contain **"direction"** (case-insensitive) in their names:
- `x_direction_velocity`
- `y_direction_pressure`
- `z_direction_temperature`
- etc.

---

## Known Issues

### Performance
- Large STL files (>500 MB) may take up to 60 seconds to load
- Slice playback with >1000 images may experience lag

### Compatibility
- **Ubuntu 24.04 with Mesa 25.x + AMD Radeon integrated graphics:**  
  Pre-built executables may fail to initialize OpenGL. Use Python execution.
  
- **AppImage format:**  
  May not detect system OpenGL libraries correctly on certain configurations.

### Workarounds
- **For STL loading issues:** Ensure files are in binary STL format
- **For OpenGL errors:** Run from Python instead of executable
- **For missing dependencies:** See [Installation](#installation) section

---

## License

### Non-Commercial Use License

Copyright (c) 2025 Lin Ping

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to use the Software for **NON-COMMERCIAL purposes only**, subject to the following conditions:

#### ✅ Permitted Uses
- Academic research
- Educational purposes
- Personal projects
- Non-profit organizations

#### ❌ Prohibited Uses
The following uses are **STRICTLY PROHIBITED** without explicit written permission:
- Use in commercial products or services
- Use by for-profit organizations
- Selling or licensing this software
- Using this software to generate revenue directly or indirectly

#### 📤 Distribution
- You may distribute unmodified copies of this software
- Modified versions must clearly indicate changes made
- This license must be included with all distributions

#### 🏷️ Attribution
- Credit must be given to the original author (Lin Ping)
- Include a link to the official repository when redistributing

#### ⚠️ Warranty Disclaimer
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

**For commercial licensing inquiries, please contact:** rpingrider@gmail.com

---

## Contact Information

- **Author:** Lin Ping
- **Email:** rpingrider@gmail.com
- **GitHub:** https://github.com/rping0310
- **Organization:** NTHURacing

### Bug Reports
Please report bugs via GitHub Issues or email with:
- Operating system and version
- Python version
- Error messages or screenshots
- Steps to reproduce the issue

### Feature Requests
Feature suggestions are welcome via email or GitHub Issues.

### Donations
This is a free, open-source project. Donations are not accepted at this time.

---

**Thank you for using Aero404 CFD Viewer!**

For the latest updates and documentation, visit: https://github.com/rping0310
