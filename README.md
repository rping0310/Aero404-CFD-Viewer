================================================================================
                          AERO404 CFD VIEWER v1.0
================================================================================

A lightweight CFD (Computational Fluid Dynamics) result visualization tool
for viewing and comparing simulation cases with slice images and 3D STL models.

Author: Lin Ping
Contributors: Claude (Anthropic AI Assistant)
Release Date: November 3, 2025
License: Non-Commercial Use Only

================================================================================
TABLE OF CONTENTS
================================================================================

1. Overview
2. Key Features
3. System Requirements
4. Dependencies
5. Installation
6. Usage Guide
7. Keyboard Shortcuts
8. File Structure Requirements
9. Known Issues
10. License
11. Contact Information

================================================================================
1. OVERVIEW
================================================================================

Aero404 CFD Viewer is designed for aerodynamics engineers and researchers to
efficiently review CFD simulation results. It provides intuitive interfaces for:

- Browsing multiple simulation cases
- Viewing velocity/pressure slice images with playback controls
- Examining 3D flow structures (Q-criterion isosurfaces)
- Comparing two cases side-by-side
- Synchronizing views between cases

================================================================================
2. KEY FEATURES
================================================================================

[Case Management]
- Load and browse multiple CFD cases from a directory
- Sort cases by name or aerodynamic coefficients (CL, CD, etc.)
- Display case parameters and simulation results in organized tables

[Slice Viewer]
- View velocity/pressure slice images across different planes
- Playback controls: forward, reverse, frame-by-frame navigation
- Variable playback speed (0.2x to 2.0x)
- Zoom and pan for detailed inspection (mouse wheel + drag)
- Image caching for smooth playback

[3D STL Viewer]
- Load and render Q-criterion isosurface STL files
- Interactive 3D rotation, zoom, and pan
- Wireframe display mode
- Camera reset to default view

[Case Comparison]
- Load main and sub cases simultaneously
- Side-by-side view with synchronized controls
- Sync options: slice type, slice position, zoom level, 3D camera

[User Interface]
- Tab-based layout: Cases / Slices / 3D / About
- Responsive design supporting 720p and higher resolutions
- Dark theme for reduced eye strain

================================================================================
3. SYSTEM REQUIREMENTS
================================================================================

[Minimum Requirements]
- CPU: Dual-core processor, 2.0 GHz or higher
- RAM: 4 GB
- GPU: OpenGL 3.2 compatible graphics card
- Display: 1280x720 (720p) or higher
- Storage: 100 MB for application + space for CFD data

[Recommended Specifications]
- CPU: Quad-core processor, 3.0 GHz or higher
- RAM: 8 GB or more
- GPU: Dedicated graphics card with OpenGL 4.6 support
- Display: 1920x1080 (1080p) or higher
- Storage: SSD recommended for faster data loading

[Operating System Compatibility]

HIGHLY RECOMMENDED:
- Ubuntu 22.04 LTS (Jammy Jellyfish)
  * Mesa 23.x series
  * Most stable and tested platform
  * Best OpenGL compatibility

COMPATIBLE (with potential issues):
- Ubuntu 24.04 LTS (Noble Numbat)
  * Mesa 25.x series
  * May require recompilation or Python execution
  * AMD integrated graphics may have compatibility issues

- Ubuntu 20.04 LTS (Focal Fossa)
  * Mesa 21.x series
  * Older but stable

OTHER DISTRIBUTIONS:
- Debian 11/12
- Fedora 38+
- openSUSE Leap 15.5+

NOTE: The application is most stable on Ubuntu 22.04 with Mesa 23.x.
      Newer Mesa versions (25.x) in Ubuntu 24.04 may cause VTK/OpenGL
      compatibility issues with certain GPU configurations.

================================================================================
4. DEPENDENCIES
================================================================================

[Python Version]
- Python 3.8 or higher (Python 3.10+ recommended)

[Required Python Packages]
The following packages must be installed:

  Package         Version      Purpose
  -------         -------      -------
  PyQt6           >= 6.0.0     GUI framework
  vtk             >= 9.0.0     3D visualization
  numpy           >= 1.20.0    Numerical operations

[System Libraries]
The following system libraries are required for OpenGL rendering:

  Library                  Package Name (Ubuntu/Debian)
  -------                  ----------------------------
  OpenGL                   libgl1-mesa-dri
  EGL                      libegl1-mesa
  GLX                      libglx-mesa0
  OSMesa (optional)        libosmesa6
  Mesa Vulkan (optional)   mesa-vulkan-drivers

[Graphics Driver Requirements]
- OpenGL 3.2 or higher support
- For AMD GPUs: mesa-vulkan-drivers, libglapi-mesa
- For NVIDIA GPUs: nvidia-driver-XXX (latest proprietary driver)
- For Intel GPUs: intel-media-va-driver

================================================================================
5. INSTALLATION
================================================================================

[Option A: Running from Python (Recommended)]

1. Install system dependencies:
   
   sudo apt update
   sudo apt install -y python3 python3-pip
   sudo apt install -y libgl1-mesa-dri libegl1-mesa libglx-mesa0
   sudo apt install -y mesa-vulkan-drivers libosmesa6

2. Install Python packages:
   
   pip3 install PyQt6 vtk numpy --break-system-packages

3. Run the application:
   
   python3 cfd_viewer_v2.3_final.py

[Option B: Using Pre-built Executable]

1. Download CFDViewer_v1.0 executable

2. Make it executable:
   
   chmod +x CFDViewer_v1.0

3. Run:
   
   ./CFDViewer_v1.0

NOTE: Pre-built executables may have OpenGL compatibility issues on
      Ubuntu 24.04 or with AMD integrated graphics. If you encounter
      errors, use Option A (Python execution).

[Troubleshooting OpenGL Issues]

If you see "Could not find a decent visual" or "vtkOpenGLRenderWindow" errors:

1. Verify OpenGL is working:
   
   glxinfo | grep "OpenGL version"

2. If glxinfo is not installed:
   
   sudo apt install mesa-utils

3. Install missing libraries:
   
   sudo apt install -y libgl1-mesa-dri libegl1-mesa libglx-mesa0 \
                       libosmesa6 mesa-vulkan-drivers

4. For AMD Radeon users on Ubuntu 24.04:
   Use Python execution method (Option A) instead of the executable.

================================================================================
6. USAGE GUIDE
================================================================================

[Initial Setup]

1. Launch the application
2. Click "Browse..." (📁) button
3. Select your CFD results directory
4. The application will scan for available cases

[Viewing a Single Case]

1. In the "Cases" tab, check the checkbox next to a case
2. Click "Load as Main" button
3. Switch to "Slices" or "3D" tab to view results

[Comparing Two Cases]

1. In the "Cases" tab, check the first case
2. Click "Load as Main"
3. Check another case
4. Click "Load as Sub"
5. Both cases will appear side-by-side

[Slice Viewer Controls]

Navigation:
  - ⏮ First: Jump to first slice
  - ◄ Prev: Previous slice
  - ◄◄ Reverse: Reverse playback
  - ▶ Play: Forward playback
  - ► Next: Next slice
  - ⏭ Last: Jump to last slice

Zoom/Pan:
  - Mouse Wheel: Zoom in/out (100% to 500%)
  - Left Click + Drag: Pan image when zoomed
  - 🔍 100% Button: Reset zoom and pan

Synchronization (when comparing):
  - Sync Slice Type: Both cases show same slice type
  - Sync Slice Position: Both cases show same slice index
  - Sync Zoom: Both cases have same zoom/pan settings

[3D Viewer Controls]

Mouse Interaction:
  - Left Click + Drag: Rotate view
  - Middle Click + Drag: Pan view
  - Mouse Wheel: Zoom in/out
  - 🔄 Reset View: Return to default camera position

Display Options:
  - Wireframe: Toggle between surface and wireframe mode

Synchronization (when comparing):
  - Sync Camera View: Both cases have same 3D viewpoint

================================================================================
7. KEYBOARD SHORTCUTS
================================================================================

[Slice Viewer Shortcuts]

When the Slice Viewer has focus (click on the image area):

  Key         Action
  ---         ------
  L           Toggle forward playback
  J           Toggle reverse playback
  → (Right)   Next slice
  ← (Left)    Previous slice

NOTE: You must click on the slice image area first to activate shortcuts.

================================================================================
8. FILE STRUCTURE REQUIREMENTS
================================================================================

The application expects the following directory structure:

base_directory/
├── Case_001/
│   ├── q-criterion.stl              (3D flow structure)
│   ├── Result.dat                   (simulation results)
│   ├── case_parameter.dat           (case parameters)
│   ├── x_direction_velocity/        (slice images)
│   │   ├── slice_001.png
│   │   ├── slice_002.png
│   │   └── ...
│   ├── y_direction_velocity/
│   │   └── ...
│   └── z_direction_velocity/
│       └── ...
├── Case_002/
│   └── ...

[Result.dat Format]

The Result.dat file should contain key-value pairs in the format:

CLA = 0.5234
FW DF = 125.67
SW DF = 45.32
RW DF = 234.56
UT DF = 67.89
W DF = 473.44
W Drag = 89.12
Aero balance z = 0.0023

Supported separators: "=" or ":"

[Slice Directory Naming]

Slice directories must contain "direction" (case-insensitive) in their names:
- x_direction_velocity
- y_direction_pressure
- z_direction_temperature
- etc.

================================================================================
9. KNOWN ISSUES
================================================================================

[Performance]
- Large STL files (>500 MB) may take up to 60 seconds to load
- Slice playback with >1000 images may experience lag

[Compatibility]
- Ubuntu 24.04 with Mesa 25.x + AMD Radeon integrated graphics:
  Pre-built executables may fail to initialize OpenGL. Use Python execution.
  
- AppImage format:
  May not detect system OpenGL libraries correctly on certain configurations.

[Workarounds]
- For STL loading issues: Ensure files are in binary STL format
- For OpenGL errors: Run from Python instead of executable
- For missing dependencies: See Installation section

================================================================================
10. LICENSE
================================================================================

NON-COMMERCIAL USE LICENSE

Copyright (c) 2025 Lin Ping & Claude (Anthropic)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to use
the Software for NON-COMMERCIAL purposes only, subject to the following
conditions:

NON-COMMERCIAL USE ONLY:
This software may only be used for:
  - Academic research
  - Educational purposes
  - Personal projects
  - Non-profit organizations

COMMERCIAL USE PROHIBITED:
The following uses are STRICTLY PROHIBITED without explicit written permission:
  - Use in commercial products or services
  - Use by for-profit organizations
  - Selling or licensing this software
  - Using this software to generate revenue directly or indirectly

DISTRIBUTION:
  - You may distribute unmodified copies of this software
  - Modified versions must clearly indicate changes made
  - This license must be included with all distributions

ATTRIBUTION:
  - Credit must be given to the original authors (Lin Ping & Claude)
  - Include a link to the official repository when redistributing

WARRANTY DISCLAIMER:
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

For commercial licensing inquiries, please contact: rpingrider@gmail.com

================================================================================
11. CONTACT INFORMATION
================================================================================

Author:       Lin Ping
Email:        rpingrider@gmail.com
GitHub:       https://github.com/rping0310
Organization: Aero404

Contributors:
- Claude (Anthropic AI Assistant) - Software architecture and implementation

Bug Reports:
Please report bugs via GitHub Issues or email with:
  - Operating system and version
  - Python version
  - Error messages or screenshots
  - Steps to reproduce the issue

Feature Requests:
Feature suggestions are welcome via email or GitHub.

Donations:
This is a free, open-source project. Donations are not accepted at this time.

================================================================================

Thank you for using Aero404 CFD Viewer!

For the latest updates and documentation, visit:
https://github.com/rping0310

================================================================================
