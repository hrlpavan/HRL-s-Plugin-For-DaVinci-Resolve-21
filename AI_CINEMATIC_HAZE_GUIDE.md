# ✦ AI Cinematic Haze — Complete User & Technical Guide

> **AI-Powered Volumetric Atmospheric Haze, Neural Depth Estimation, Light Rays & Halos for DaVinci Resolve (Free & Studio) and Standalone Video Studio.**

---

## 📌 Table of Contents
1. [Overview](#-overview)
2. [Key Features](#-key-features)
3. [DaVinci Resolve Free vs Studio Compatibility](#-davinci-resolve-free-vs-studio-compatibility)
4. [Inspector Parameter Reference (7 Complete Modules)](#-inspector-parameter-reference-7-complete-modules)
5. [Standalone Video Studio Application](#-standalone-video-studio-application)
6. [Installation & Setup](#-installation--setup)
7. [Technical Architecture](#-technical-architecture)
8. [Workflow Tutorial](#-workflow-tutorial)

---

## 🌟 Overview

**AI Cinematic Haze** is an advanced optical atmospheric engine designed for filmmakers, colorists, and VFX artists. It creates physically accurate volumetric fog, depth-aware atmospheric scattering, volumetric god rays, anamorphic halos, and turbulence without requiring paid Studio-only features or external rendering packages.

It is delivered as:
1. **Standalone Video Studio Application**: A hardware-accelerated video grading and rendering application with real-time AI neural depth estimation, timeline scrubbing, and high-fidelity video export.
2. **DaVinci Resolve Free Native Fuse (`.fuse`)**: 100% watermark-free node for the Free version of DaVinci Resolve (and Studio).
3. **OpenFX Plugin (`.ofx.bundle`)**: C++ / Metal / CUDA GPU-accelerated OpenFX plugin for color grading suites.

---

## ⚡ Key Features

- **Dense Monocular AI Depth Estimation**: Generates continuous, contour-accurate depth maps (isolating actors, hair, jewelry, foreground limbs, and distant background geometry) without studio watermarks.
- **Koschmieder & Henyey-Greenstein Scattering**: Physically accurate optical simulation of sunlight passing through atmospheric particulates.
- **Volumetric God Rays & Light Halos**: Directional, radial, and omnidirectional volumetric rays that interact with depth planes.
- **3D Atmospheric Turbulence**: Fluid-dynamic seething and flowing air disturbance.
- **Cross-Platform & Zero Dependencies**: Runs locally on macOS (Apple Silicon M1/M2/M3/M4 & Intel) and Windows/Linux.

---

## 🛡️ DaVinci Resolve Free vs Studio Compatibility

| Capability | DaVinci Resolve Free | DaVinci Resolve Studio | Standalone Video Studio |
| :--- | :---: | :---: | :---: |
| **Volumetric Haze & Scattering** | ✅ 100% Free | ✅ 100% Supported | ✅ Native 60 FPS |
| **Neural Depth Slicing** | ✅ Free (via AI Fuse) | ✅ Supported | ✅ Built-in Neural AI |
| **No Watermarks** | ✅ Zero Watermarks | ✅ Zero Watermarks | ✅ Zero Watermarks |
| **Video Import / Export** | ✅ Supported | ✅ Supported | ✅ Direct WebM / MP4 |
| **GPU Acceleration** | ✅ OpenCL / Metal | ✅ Metal / CUDA | ✅ WebGL / Canvas2D |

---

## 🎛️ Inspector Parameter Reference (7 Complete Modules)

The inspector strictly follows professional color-grading layout guidelines:

```
🔴 AI Cinematic Haze (Master Switch & Reset)
├── 1. Color Space Overrides
├── 2. Depth Map
├── 3. Atmospheric Scattering
├── 4. Light Halos
├── 5. Light Rays
├── 6. Air Disturbance
└── 7. Global Blend
```

### 1. Color Space Overrides
- **Input Color Space**: Select from `Use timeline`, `Rec.709`, `DaVinci Wide Gamut`, `ACEScg`, `sRGB`, `P3-D65`.
- **Input Gamma**: Select from `Use timeline`, `Rec.709`, `DaVinci Intermediate`, `Linear`, `Gamma 2.4`, `Gamma 2.2`.

### 2. Depth Map
- **Depth Map Preview** *(Checkbox)*: Displays the grayscale depth map directly on the viewer.
- **Depth Map Source** *(Dropdown)*: `Internal (Depth Anything V2)` or `External / Auxiliary`.
- **Quality** *(Dropdown)*: `Fast` (real-time preview), `Better` (balanced), `Ultra` (production render).
- **Invert** *(Checkbox)*: Inverts depth polarity (black near / white far).
- **Adjust Map Levels** *(Checkbox)*: Enables custom near/far clipping boundaries.
- **Far Limit** *(Slider `0.000 – 1.000`)*: Sets the distant horizon clipping threshold.
- **Near Limit** *(Slider `0.000 – 1.000`)*: Sets the camera-lens proximity clipping threshold.
- **Gamma** *(Slider `0.100 – 3.000`)*: Non-linear depth distribution curve.
- **Advanced Depth Controls** *(Checkbox)*: Unlocks bilateral edge smoothing and temporal anti-flicker filters.

### 3. Atmospheric Scattering
- **Airlight** *(Slider `0.000 – 1.000`)*: Ambient luminance scattered by air particulates.
- **Density** *(Slider `0.000 – 1.000`)*: Volumetric density of fog and haze.
- **Resolution Loss** *(Slider `0.000 – 1.000`)*: High-frequency optical blur over distance.
- **Colorize** *(Color Swatch & Eyedropper)*: Tint the scattered particulate airlight.

### 4. Light Halos (Bloom)
- **Halo Threshold** *(Slider `0.000 – 1.000`)*: Luminance threshold where highlights bleed into haze.
- **Size** *(Slider `0.100 – 3.000`)*: Optical spread radius of the halation bloom.
- **Brightness** *(Slider `0.000 – 2.000`)*: Intensity of the glow around light sources.
- **Saturation** *(Slider `0.000 – 2.000`)*: Chromatic richness of the halation bloom.
- **Colorize** *(Color Swatch & Eyedropper)*: Custom tint for highlight glow.

### 5. Light Rays (God Rays)
- **Enable Light Rays** *(Checkbox)*: Master toggle for directional volumetric god rays.
- **Preview Threshold** *(Checkbox)*: View the binary light emitter mask.
- **Source Threshold** *(Slider `0.000 – 1.000`)*: Minimum brightness required to cast rays.
- **Ray Directions** *(Dropdown)*: `At An Angle`, `Radial / Point`, `Omnidirectional`.
- **Angle** *(Slider `-180.0° – 180.0°`)*: Directional trajectory of incoming sunlight.
- **Length** *(Slider `0.000 – 2.000`)*: Projection distance of light shafts.
- **Soften** *(Slider `0.000 – 1.000`)*: Diffusion and feathering across ray boundaries.
- **Brightness** *(Slider `0.000 – 2.000`)*: Intensity multiplier for rays.
- **Saturation** *(Slider `0.000 – 2.000`)*: Color saturation of light rays.

### 6. Air Disturbance (Turbulence)
- **Enable Disturbance** *(Checkbox)*: Enables 3D Simplex noise modulation.
- **Preview Influence** *(Checkbox)*: Visualizes air vector eddies and currents.
- **Intensity** *(Slider `0.000 – 1.000`)*: Amplitude of air density variations.
- **Brightness** *(Slider `0.000 – 2.000`)*: Micro-contrast in fog clusters.
- **Scale** *(Slider `0.100 – 10.000`)*: Spatial scale of fog turbulence patches.
- **Detail** *(Slider `1.00 – 10.00`)*: Fractal Brownian Motion (FBM) octaves.
- **Follow FX Tracker** *(Checkbox)*: Links air turbulence drift to camera motion tracking.
- **Flow Direction** *(Slider `-180.0° – 180.0°`)*: Wind drift angle.
- **Flow Speed** *(Slider `0.000 – 5.000`)*: Wind velocity.
- **Seethe Rate** *(Slider `0.000 – 1.000`)*: Internal convective boiling rate of fog.
- **Start Frame & Randomize** *(Button)*: Random seed generator for unique air patterns.

### 7. Global Blend
- **Blend** *(Slider `0.000 – 1.000`)*: Master wet/dry opacity mix.

---

## 🖥️ Standalone Video Studio Application

If you are not using DaVinci Resolve or prefer a dedicated standalone environment:

### Launching the Studio:
Run the local launcher in terminal:
```bash
python3 /Users/pavankumars/.gemini/antigravity/scratch/ai-cinematic-haze-ofx/app/web_studio/server.py
```
*(The studio automatically binds to the first open port and opens your browser).*

### Studio Capabilities:
- **Video Import**: Drag & drop any `.mov`, `.mp4`, ProRes, or `.mkv` clip.
- **Timeline Transport**: Play/Pause (`Space`), frame stepping (`⏮`/`⏭`), timecode display (`HH:MM:SS:FF`), and responsive scrubber.
- **Dedicated View Tabs**:
  - `🎬 Final Haze` (Full composite)
  - `🗺️ Depth Map` (Neural AI depth map)
  - `☀️ Light Rays` (Threshold extraction)
  - `⭕ Light Halos` (Bloom isolation)
  - `💨 Air Disturbance` (Turbulence vectors)
- **Export**: Click **`🚀 Render & Export Video`** to generate the final processed video.

---

## 📦 Installation & Setup

### Option 1: macOS Disk Image (.dmg) Installer
1. Open the generated DMG installer:
   ```bash
   open /Users/pavankumars/.gemini/antigravity/scratch/ai-cinematic-haze-ofx/build/AICinematicHaze_v1.0.dmg
   ```
2. Double-click **`1-Click_Install_For_DaVinci_Resolve.command`** to auto-install the Fuse into DaVinci Resolve.
3. Drag **`AI Cinematic Haze.app`** to your Applications folder.

### Option 2: Direct DaVinci Resolve Fuse Installation
Copy the Fuse file to DaVinci Resolve's user Fuses directory:
```bash
mkdir -p "$HOME/Library/Application Support/Blackmagic Design/DaVinci Resolve/Support/Fusion/Fuses"
cp /Users/pavankumars/.gemini/antigravity/scratch/ai-cinematic-haze-ofx/fuses/AICinematicHaze.fuse "$HOME/Library/Application Support/Blackmagic Design/DaVinci Resolve/Support/Fusion/Fuses/"
```
Restart DaVinci Resolve → Open the **Fusion** page → Press `Shift + Space` → Search for `AI Cinematic Haze`.

---

## 🏗️ Technical Architecture

```
ai-cinematic-haze-ofx/
├── AI_CINEMATIC_HAZE_GUIDE.md        # This Documentation
├── fuses/
│   └── AICinematicHaze.fuse          # Native DaVinci Resolve Free Fuse
├── app/
│   ├── web_studio/
│   │   ├── index.html                # Studio UI & Neural Depth Engine
│   │   └── server.py                 # Auto-rebinding local server
│   └── ai_haze_gui.py                # Desktop GUI Fallback
├── src/
│   ├── AIDepthEngine.cpp             # C++ AI Depth Estimation & Temporal Filter
│   ├── AtmosphericModel.cpp          # Koschmieder Scattering & FBM Noise
│   ├── HazePlugin.cpp                # OpenFX 1.4 Entry Points & Parameters
│   ├── metal/HazeShaders.metal       # Apple Metal Compute Shaders
│   └── cuda/HazeShaders.cu           # NVIDIA CUDA GPU Kernel
├── include/                          # OpenFX 1.4 API Headers
├── scripts/
│   ├── create_macos_dmg.sh           # DMG & ZIP Packaging Pipeline
│   └── build_and_test.sh             # C++ Unit & Integration Test Suite
└── build/
    ├── AICinematicHaze_v1.0.dmg      # Mountable macOS Installer
    └── AICinematicHaze_v1.0_macOS.zip# Portable Archive
```

---

## 🎬 Workflow Tutorial: Adding Cinematic Haze to Video

1. **Import Footage**: Open the Video Studio or DaVinci Resolve and load your scene.
2. **Inspect the Depth Map**:
   - Switch to **`🗺️ Depth Map`**.
   - Adjust **`Far Limit`** and **`Near Limit`** so the background is bright white and the foreground actor is deep dark.
3. **Add Atmospheric Haze**:
   - Switch to **`🎬 Final Haze`**.
   - Increase **`Density`** to `0.150` and **`Airlight`** to `0.450`.
   - The haze will naturally wrap behind the actor based on the 3D depth map!
4. **Enable Volumetric God Rays**:
   - Expand **`Light Rays`** → Check **`Enable Light Rays`**.
   - Adjust **`Angle`** to align with the sun/practical light source in your shot.
5. **Add Atmospheric Turbulence**:
   - Expand **`Air Disturbance`** → Check **`Enable Disturbance`**.
   - Set **`Intensity`** to `0.200` and **`Flow Speed`** to `0.400` to give the air subtle organic movement.
6. **Export**: Click **`🚀 Render & Export Video`** to save your graded video.
