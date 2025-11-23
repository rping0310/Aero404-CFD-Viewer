# Aero404 CFD Viewer V2.0
## Cross-Platform Edition

A lightweight CFD (Computational Fluid Dynamics) result visualization tool for viewing and comparing simulation cases with slice images and 3D STL models.

**Author:** Lin Ping  
**Release Date:** November 23, 2025  
**License:** Non-Commercial Use Only

**Supported Platforms:** ✅ Windows 10/11 | ✅ Linux (Ubuntu 20.04+) | ✅ macOS

---

## 📋 Table of Contents

1. [Overview](#overview)
2. [Key Features](#key-features)
3. [System Requirements](#system-requirements)
4. [Installation](#installation)
   - [Windows 10/11](#windows-1011-installation)
   - [Linux](#linux-installation)
5. [Network Setup (SMB/CIFS)](#network-setup-smbcifs)
6. [Usage Guide](#usage-guide)
7. [Keyboard Shortcuts](#keyboard-shortcuts)
8. [File Structure Requirements](#file-structure-requirements)
9. [Troubleshooting](#troubleshooting)
10. [License](#license)
11. [Contact](#contact-information)

---

## Overview

Aero404 CFD Viewer is designed for **Formula Student aerodynamics teams** and motorsport engineers to efficiently review CFD simulation results without expensive commercial software.

### Core Capabilities
- Browse and compare multiple simulation cases
- View velocity/pressure slice images with playback controls
- Examine 3D flow structures (Q-criterion isosurfaces)
- Side-by-side case comparison with synchronized views
- Network folder support (SMB/CIFS) for team collaboration

---

## Key Features

### 📁 Case Management
- Load multiple CFD cases from local or network directories
- Sort by name or aerodynamic coefficients (CL, CD, DF, etc.)
- Display case parameters and results in organized tables
  <img width="1918" height="1045" alt="image" src="https://github.com/user-attachments/assets/43c58451-5527-488b-929c-394369a4bf8c" />


### 🖼️ Slice Viewer
- View velocity/pressure/temperature slice images
- Playback controls: forward, reverse, variable speed (0.2x-2.0x)
- Zoom (100%-500%) and pan with mouse wheel + drag
- Frame-by-frame navigation with keyboard shortcuts (J/L)
- Image caching for smooth playback
  <img width="1918" height="1045" alt="image" src="https://github.com/user-attachments/assets/33fd7df9-b7cc-404f-b441-4d3cd9f1b72e" />


### 🎨 3D STL Viewer
- Load and render Q-criterion isosurface STL files
- Interactive 3D rotation, zoom, and pan
- Wireframe/surface display modes
- Camera reset to default view
  <img width="1918" height="1045" alt="image" src="https://github.com/user-attachments/assets/374307f2-f241-4552-a125-6c1c4ac47b15" />


### 🔄 Case Comparison
- Load main and sub cases simultaneously
- Side-by-side synchronized views
- Sync options: slice type, position, zoom, 3D camera

### 💻 User Interface
- Tab-based layout: Cases / Slices / 3D / About
- Responsive design (720p to 4K)
- Dark theme for reduced eye strain
- Cross-platform consistent experience

---

## System Requirements

### Minimum Requirements
- **CPU:** Dual-core 2.0 GHz
- **RAM:** 4 GB
- **GPU:** OpenGL 3.2 compatible (or Mesa3D software rendering)
- **Display:** 1280x720 (720p)
- **Storage:** 100 MB + CFD data space
- **Network:** 100 Mbps (for network access)

### Recommended Specifications
- **CPU:** Quad-core 3.0 GHz or higher
- **RAM:** 8 GB or more
- **GPU:** Dedicated graphics card with OpenGL 4.6
- **Display:** 1920x1080 (1080p) or higher
- **Storage:** SSD
- **Network:** 1 Gbps (for network access)

---

## Installation

## Windows 10/11 Installation

### Step 1: Install Python

**Method A (Recommended): Microsoft Store**
1. Press `Windows Key`
2. Search "Microsoft Store"
3. Search "Python 3.12"
4. Click "Install"

**Method B: Python.org**
1. Visit: https://www.python.org/downloads/
2. Download Python 3.12.x for Windows
3. Run installer
4. ✅ **CHECK "Add Python to PATH"**
5. Click "Install Now"

**Verify Installation:**
```cmd
python --version
```
You should see: `Python 3.12.x`

### Step 2: Install Dependencies

Open Command Prompt and run:

```cmd
python -m pip install --upgrade pip
pip install PyQt6 vtk numpy
```

⏰ Wait 5-10 minutes (VTK is ~100 MB)

**Verify Installation:**
```cmd
python -c "import PyQt6, vtk, numpy; print('All packages OK!')"
```

### Step 3: Download CFD Viewer

1. Download `cfd_viewer_cross_platform.py`
2. Save to: `C:\CFD_Viewer\cfd_viewer_cross_platform.py`

### Step 4: Run the Application

**Method 1: Command Prompt**
```cmd
cd C:\CFD_Viewer
python cfd_viewer_cross_platform.py
```

**Method 2: Create Desktop Shortcut**
- Right-click Desktop → New → Shortcut
- Location: `python "C:\CFD_Viewer\cfd_viewer_cross_platform.py"`
- Name: CFD Viewer

**Method 3: Batch File (run_cfd.bat)**
```batch
@echo off
cd C:\CFD_Viewer
python cfd_viewer_cross_platform.py
pause
```

### Step 5: Fix OpenGL Issues (If 3D View Doesn't Work)

If you see OpenGL errors, install Mesa3D:

1. Download: https://github.com/pal1000/mesa-dist-win/releases
2. Download latest `mesa3d-XX.X.X-release-msvc.7z`
3. Extract (requires 7-Zip)
4. Run: `systemwidedeploy.cmd`
5. Select: `[1] Desktop OpenGL`
6. Restart CFD Viewer

**Alternative:** Update graphics drivers
- **Intel:** https://www.intel.com/content/www/us/en/support/detect.html
- **NVIDIA:** https://www.nvidia.com/drivers
- **AMD:** https://www.amd.com/support

---

## Linux Installation

### Ubuntu 20.04 / 22.04 / 24.04

**Step 1: Install System Dependencies**
```bash
sudo apt update
sudo apt install -y python3 python3-pip
sudo apt install -y libgl1-mesa-dri libegl1-mesa libglx-mesa0
sudo apt install -y mesa-vulkan-drivers libosmesa6
```

**For Ubuntu 24.04, also install XCB libraries:**
```bash
sudo apt install -y libxcb-cursor0 libxcb-icccm4 libxcb-image0 \
                    libxcb-keysyms1 libxcb-randr0 libxcb-render-util0
```

**Step 2: Install Python Packages**
```bash
pip3 install PyQt6 vtk numpy --break-system-packages
```

**Step 3: Run the Application**
```bash
python3 cfd_viewer_cross_platform.py
```

**For Ubuntu 24.04 with Wayland:**
```bash
QT_QPA_PLATFORM=xcb python3 cfd_viewer_cross_platform.py
```

**Create a launcher script (optional):**
```bash
cat > run_cfd.sh << 'EOF'
#!/bin/bash
export QT_QPA_PLATFORM=xcb
python3 cfd_viewer_cross_platform.py
EOF
chmod +x run_cfd.sh
./run_cfd.sh
```
---

## Usage Guide

### Initial Setup

1. Launch CFD Viewer
2. Click Browse (📁) button
3. Select your CFD results directory (local or network)
4. Application scans for available cases

### Viewing a Single Case

1. Go to "Cases" tab
2. Check checkbox next to a case
3. Click "Load as Main"
4. Switch to "Slices" or "3D" tab

### Comparing Two Cases

1. In "Cases" tab, check first case
2. Click "Load as Main"
3. Check another case
4. Click "Load as Sub"
5. Both cases appear side-by-side

### Slice Viewer Controls

**Navigation Buttons:**
- ⏮ **First** - Jump to first slice
- ◄ **Prev** - Previous slice
- ◄◄ **Reverse** - Reverse playback
- ▶ **Play** - Forward playback
- ► **Next** - Next slice
- ⏭ **Last** - Jump to last slice

**Zoom/Pan:**
- **Mouse Wheel** - Zoom in/out (100%-500%)
- **Left Click + Drag** - Pan image (when zoomed)
- **🔍 100% Button** - Reset zoom and pan

**Synchronization (when comparing):**
- ☑ **Sync Slice Type** - Both cases show same slice type
- ☑ **Sync Slice Position** - Both cases at same frame
- ☑ **Sync Zoom** - Both cases have same zoom/pan

### 3D Viewer Controls

**Mouse Interaction:**
- **Left Click + Drag** - Rotate view
- **Middle Click + Drag** - Pan view
- **Mouse Wheel** - Zoom in/out
- **🔄 Reset View** - Return to default camera

**Display Options:**
- ☑ **Wireframe** - Toggle wireframe/surface mode

**Synchronization:**
- ☑ **Sync Camera View** - Both cases have same 3D viewpoint

---

## Keyboard Shortcuts

### Slice Viewer

> **Note:** Click on image area first to activate shortcuts

| Key | Action |
|-----|--------|
| `L` | Play forward |
| `J` | Play reverse |
| `→` | Next frame |
| `←` | Previous frame |

---

## File Structure Requirements

### Directory Structure

```
base_directory/
├── Case_001/
│   ├── q-criterion.stl           # 3D flow structure
│   ├── Result.dat                # Simulation results
│   ├── case_parameter.dat        # Case parameters
│   ├── x_direction_velocity/     # Slice images
│   │   ├── slice_001.png
│   │   ├── slice_002.png
│   │   └── ...
│   ├── y_direction_velocity/
│   └── z_direction_pressure/
├── Case_002/
│   └── ...
```

### Result.dat Format

Key-value pairs with `=` or `:` separator:

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

### Slice Directory Naming

Must contain **"direction"** (case-insensitive):
- `x_direction_velocity`
- `y_direction_pressure`
- `z_direction_temperature`
- etc.

### File Encoding

Supported: **UTF-8, CP1252, GBK, Latin-1** (Automatically detected)

---

## Troubleshooting

### Windows

**Problem:** `'python' is not recognized`  
**Solution:** Reinstall Python, check "Add to PATH" | Or restart computer after installation

**Problem:** `No module named 'PyQt6'`  
**Solution:** `pip install PyQt6 vtk numpy`

**Problem:** 3D view doesn't work (OpenGL errors)  
**Solution:** Install Mesa3D or update graphics drivers (See Installation Step 5)

**Problem:** Cannot access network drive  
**Solution:** 
1. Test: `ping server_ip`
2. Map network drive in File Explorer first
3. Check server Samba is running
4. Verify firewall allows SMB (port 445)

**Problem:** Slow performance over network  
**Solution:** Use wired connection | Copy case to local drive for faster viewing

### Linux

**Problem:** `Could not find a decent visual`  
**Solution:** Ubuntu 24.04 Wayland issue  
```bash
QT_QPA_PLATFORM=xcb python3 cfd_viewer_cross_platform.py
```

**Problem:** `libxcb-cursor0 not found`  
**Solution:**
```bash
sudo apt install libxcb-cursor0 libxcb-icccm4 libxcb-image0
```

**Problem:** VTK OpenGL errors  
**Solution:**
```bash
sudo apt install libgl1-mesa-dri libegl1-mesa mesa-vulkan-drivers
```

### Cross-Platform

**Problem:** Large STL files load slowly  
**Solution:** Normal behavior for >500 MB files (up to 60 seconds) | Files >5M faces are automatically simplified

**Problem:** Slice playback lag with >1000 images  
**Solution:** Reduce playback speed | Images are cached automatically (20 frame buffer)

**Problem:** Text encoding errors in Result.dat  
**Solution:** Application auto-detects UTF-8, CP1252, GBK, Latin-1 | Ensure files use one of these encodings

---

## License

### Non-Commercial Use License

**Copyright (c) 2025 Lin Ping**

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to use the Software for **NON-COMMERCIAL purposes only**.

### ✅ Permitted Uses
- Academic research
- Educational purposes
- Personal projects
- Non-profit organizations
- Formula Student teams

### ❌ Prohibited Uses
- Commercial products or services
- For-profit organizations
- Selling or licensing this software
- Generating revenue directly or indirectly

### 📤 Distribution
- You may distribute unmodified copies
- Modified versions must clearly indicate changes
- This license must be included with all distributions

### 🏷️ Attribution
- Credit must be given to Lin Ping
- Include link to official repository when redistributing

### ⚠️ Warranty Disclaimer

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.

**For commercial licensing inquiries:** rpingrider@gmail.com

---

## Contact Information

**Author:** Lin Ping  
**Email:** rpingrider@gmail.com  
**GitHub:** https://github.com/rping0310  
**Organization:** Aero404

### Bug Reports
Report via GitHub Issues or email with:
- Operating system and version
- Python version (`python --version`)
- Error messages or screenshots
- Steps to reproduce

### Feature Requests
Submit via email or GitHub Issues

---

**Thank you for using Aero404 CFD Viewer!**

*Designed for Formula Student aerodynamics teams worldwide.*

For updates and documentation: https://github.com/rping0310

---
