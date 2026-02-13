# NTHURacing CFD Viewer V2.1
## Real-time Monitoring Edition

A lightweight CFD visualization tool for Formula Student teams to review simulation results with slice images, 3D models, and convergence monitoring.

**Author:** Lin Ping  
**Release Date:** February 12, 2026  
**License:** Non-Commercial Use Only

**Platforms:** ✅ Windows 10/11 | ✅ Linux (Ubuntu 20.04+)

---

## 📋 Table of Contents

1. [What's New in V2.1](#whats-new-in-v21)
2. [Key Features](#key-features)
3. [System Requirements](#system-requirements)
4. [Installation](#installation)
5. [Quick Start](#quick-start)
6. [File Structure](#file-structure)
7. [Troubleshooting](#troubleshooting)
8. [License](#license)

---

## What's New in V2.1

### 📊 Plots Page - Real-time Convergence Monitoring

**Monitor simulation convergence in real-time with interactive plots.**

#### Features:
- **Auto-detect CSV files** (Residuals, Forces, Coefficients)
- **Smart Y-axis scaling:**
  - Residuals: Log scale (1e-6 to 1.0)
  - Forces/Coefficients: Linear scale (0 to max)
- **Interactive controls:**
  - Mouse zoom/pan
  - Crosshair with exact values
  - Toggle series visibility
  - Refresh during running simulations
- **Side-by-side comparison** of Main/Sub cases

#### Supported Data:
- **Residuals:** Continuity, X/Y/Z-momentum, Tke, Sdr
- **Forces:** FW_DF, RW_DF, SW_DF, UT_DF, W_DF
- **Coefficients:** Cl, Cd, Cla, Cl/Cd

#### CSV Format:
```csv
"Iteration","Continuity: Residual","X-momentum: Residual",...
1.0,0.114,0.038,...
2.0,0.092,0.031,...
```
- First row: Headers (auto-cleaned)
- First column: Iteration number
- Auto-detects Residual vs Force files by filename

---

## Key Features

### 📋 Case Management
- Load multiple cases from local/network folders
- Sort by aerodynamic coefficients
- Display parameters and results in tables

### 🖼️ Slice Viewer
- View velocity/pressure/temperature slices
- Playback controls (forward/reverse, variable speed)
- Zoom (100%-500%) and pan
- Keyboard shortcuts (J/L for play)

### 📊 Plots (NEW in V2.1)
- Real-time CSV monitoring
- Residuals with log scale
- Forces with linear scale
- Interactive data inspection

### 🎨 3D STL Viewer
- Q-criterion isosurface visualization
- Interactive rotation/zoom/pan
- Wireframe/surface modes

### 🔄 Case Comparison
- Side-by-side Main/Sub cases
- Synchronized views (slice type, position, zoom, camera)

---

## System Requirements

**Minimum:**
- CPU: Dual-core 2.0 GHz
- RAM: 4 GB
- GPU: OpenGL 3.2+ (or Mesa3D)
- Display: 1280x720

**Recommended:**
- CPU: Quad-core 3.0 GHz+
- RAM: 8 GB+
- GPU: Dedicated card with OpenGL 4.6
- Display: 1920x1080+

---

## Installation

### Linux (Ubuntu 22.04)

**Quick Install:**
```bash
sudo apt update
sudo apt install -y python3-pyqt6 python3-vtk9 python3-numpy python3-pyqtgraph
```

**Run:**
```bash
python3 cfd_viewer_V2_1_en.py
```

**Ubuntu 24.04 (Wayland):**
```bash
QT_QPA_PLATFORM=xcb python3 cfd_viewer_V2_1_en.py
```

### Dependencies
| Package    | Purpose              |
|------------|----------------------|
| PyQt6      | GUI framework        |
| VTK        | 3D visualization     |
| NumPy      | Data processing      |
| PyQtGraph  | Plotting (NEW)       |

---

## Quick Start

### 1. Load Cases
1. Click **📁 Browse** button
2. Select CFD results directory
3. Cases appear in table

### 2. View Single Case
1. Check a case
2. Click **Load as Main**
3. Switch to **Slices**, **Plots**, or **3D** tab

### 3. Compare Cases
1. Load first case as Main
2. Load second case as Sub
3. Both appear side-by-side

### 4. Monitor Convergence (NEW)
1. Go to **Plots** tab
2. Select CSV file (e.g., `Residuals_0000_000.csv`)
3. Use checkboxes to show/hide series
4. Click **Refresh** during simulation

### Controls

**Slice Viewer:**
- Mouse Wheel: Zoom
- Left Drag: Pan
- J/L: Play reverse/forward

**Plots:**
- Mouse Wheel: Zoom
- Left Drag: Pan
- Hover: Show data values
- Reset View: Return to default

**3D Viewer:**
- Left Drag: Rotate
- Middle Drag: Pan
- Mouse Wheel: Zoom

---

## File Structure

```
base_directory/
├── Case_001/
│   ├── q-criterion.stl           # 3D model
│   ├── Result.dat                # Results
│   ├── case_parameter.dat        # Parameters
│   ├── Residuals_0000_000.csv    # Convergence data (NEW)
│   ├── DF_0000_000.csv           # Force data (NEW)
│   ├── x_direction_velocity/     # Slices
│   │   ├── slice_001.png
│   │   └── ...
│   └── ...
└── Case_002/
    └── ...
```

### Result.dat Format

Updated format for V2.1:

```
mean_Cl/Cd = 1.135077
mean_Cla = 9.335337
mean_FW_DF = 51.465307
mean_RW_DF = 365.918952
mean_SW_DF = 253.503996
mean_UT_DF = 62.427584
mean_W_DF = 863.518670
Aero_balance_x = 0.874921
Aero_balance_z = 0.321509
```

Display mapping:
- `mean_Cla` → `Cla`
- `mean_RW_DF` → `RW`
- `Aero_balance_x` → `x balance`

### CSV Files (NEW)

**Residuals CSV:**
```csv
"Iteration","Continuity: Residual","X-momentum: Residual",...
1.0,0.114,0.038,...
```

**Force CSV:**
```csv
"mean_SW_DF Monitor: Iteration","mean_SW_DF Monitor: mean_SW_DF Monitor (N)",...
1.0,253.50,...
```

---

## Troubleshooting

### Linux

**Wayland visual error:**
```bash
QT_QPA_PLATFORM=xcb python3 cfd_viewer_V2_1_en.py
```

**Missing PyQtGraph:**
```bash
sudo apt install python3-pyqtgraph
```

**Missing XCB libraries (Ubuntu 24.04):**
```bash
sudo apt install libxcb-cursor0 libxcb-icccm4 libxcb-image0
```

### Plots Page

**"PyQtGraph not available":**
```bash
sudo apt install python3-pyqtgraph
# or
pip install pyqtgraph --break-system-packages
```

**CSV not loading:**
- Check CSV is in case folder root
- First row must be headers
- First column must be iteration numbers

**Wrong Y-axis range:**
- Residual files must contain "residual" or "resid" in filename
- Use Reset View button to recalculate range

---

## License

**Copyright (c) 2026 Lin Ping**

**Non-Commercial Use Only**

✅ Permitted: Academic research, education, Formula Student teams  
❌ Prohibited: Commercial products, for-profit use

**Warranty:** None. Provided "AS IS".

For commercial licensing: rpingrider@gmail.com

---

## Contact

**Author:** Lin Ping  
**Email:** rpingrider@gmail.com  
**GitHub:** https://github.com/rping0310

**Bug Reports:** Include OS, Python version, error messages, and steps to reproduce.

---

**Thank you for using NTHURacing CFD Viewer V2.1!**

*Designed for Formula Student aerodynamics teams worldwide.*
