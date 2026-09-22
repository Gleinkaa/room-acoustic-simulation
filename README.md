# Studio Acoustic Simulation

[![Platform: Web](https://img.shields.io/badge/Platform-Web%20Browser-blue.svg)](roomacousticsimulation.html)
[![Zero Dependencies](https://img.shields.io/badge/Dependencies-None%20(Pure%20Vanilla%20JS)-green.svg)](roomacousticsimulation.html)
[![License: MIT](https://img.shields.io/badge/License-MIT-purple.svg)](LICENSE)

An interactive, physics-based studio acoustics and room mode simulator designed for rectangular control rooms, nearfield monitoring setups (featuring the **ADAM Audio A7V**), and low-end critical electronic/psytrance music production.

Built as a **single, self-contained HTML5 file** (`roomacousticsimulation.html`) with zero external dependencies, no build steps, and instant local execution in any modern web browser.

---

## Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Quick Start](#quick-start)
- [Interactive Interface Tour](#interactive-interface-tour)
  - [1. Room Plan View](#1-room-plan-view)
  - [2. Standing Waves & Modes Calculator](#2-standing-waves--modes-calculator)
  - [3. Treatment Plan & First Reflection Points](#3-treatment-plan--first-reflection-points)
  - [4. Panel Specs & DIY Materials Cost](#4-panel-specs--diy-materials-cost)
  - [5. Live Metrics Sidebar](#5-live-metrics-sidebar)
- [Acoustic Science & Simulation Model](#acoustic-science--simulation-model)
  - [Modal Sound Field (Green's Function Expansion)](#modal-sound-field-greens-function-expansion)
  - [Dual Coherent Speaker Excitation](#dual-coherent-speaker-excitation)
  - [Damping & RT60 Estimation](#damping--rt60-estimation)
  - [Schroeder Frequency](#schroeder-frequency)
  - [Specular First Reflection Ray-Tracing](#specular-first-reflection-ray-tracing)
- [Practical Studio Setup Guidelines](#practical-studio-setup-guidelines)
  - [The 38% Rule](#the-38-rule)
  - [The Equilateral Listening Triangle](#the-equilateral-listening-triangle)
  - [Combating Narrow Room Modes](#combating-narrow-room-modes)
- [ADAM A7V Monitor Optimization](#adam-a7v-monitor-optimization)
- [DIY Acoustic Treatment Specifications](#diy-acoustic-treatment-specifications)
- [Assumptions & Model Boundaries](#assumptions--model-boundaries)
- [User Manual](#user-manual)

---

## Overview

Achieving accurate low-frequency reproduction in small-to-medium rectangular rooms is one of the most challenging aspects of studio design. In bass-heavy genres such as psytrance, techno, and drum & bass, room modes create massive frequency peaks and deep cancellations (nulls) below 300 Hz that compromise mix translation.

This simulator bridges the gap between theoretical acoustics and practical DIY studio setup. It calculates room modes, standing waves, specular reflection points, and steady-state 2D pressure fields in real time, giving audio engineers and producers an intuitive, visual platform to optimize:

1. **Room Geometry & Desk Placement**
2. **Speaker Position (Front Wall Standoff & Stereo Spread)**
3. **Listening Sweet Spot (Chair Position along the Length Axis)**
4. **Targeted Acoustic Treatment (Bass Traps, Broadband Absorbers, Ceiling Cloud, Diffusers)**
5. **Hardware Monitor Boundary EQ Tuning**

---

## Key Features

- **Single-File Zero-Dependency Architecture:** Open `roomacousticsimulation.html` directly in any modern browser (`file://`). No `npm`, no bundlers, no server, and no internet connection required.
- **Interactive 2D Acoustic Heatmap:** 3 cm spatial grid resolution calculating the steady-state acoustic pressure distribution across the room floor plan for any frequency between 20 Hz and 400 Hz.
- **Dual-View Visualization:** Top-down room plan paired with a front elevation view showing monitor height, ear height (1.20 m seated reference), ceiling cloud depth, and stereo spread.
- **Listener Modal Frequency Response (20–300 Hz):** Live frequency response transfer function computed at the listener's exact ear location, comparing **Treated** vs. **Untreated** acoustic conditions side by side.
- **Interactive Crosshairs & Heatmap Sync:** Hover over the frequency response chart or 1D standing wave plot for instant dB/amplitude tooltips; click any point on the response curve to jump the 2D room heatmap directly to that frequency.
- **Direct Drag Interactions:** Real-time mouse/touch drag handles on the canvas for:
  - **Listening Position:** Slide listener forward/backward along the room centerline.
  - **Speaker Wall Distance:** Move speakers closer to or further from the front boundary.
  - **Speaker Spread:** Adjust stereo width interactively on the canvas or via slider.
- **1D Standing Wave Visualizer:** Real-time pressure waveform plotting along Length ($L$), Width ($W$), or Height ($H$) showing nodal pressure dips, antinodes, and exact pressure percentage at the listener.
- **Automated Mode Classification:** Complete room mode calculation below 400 Hz categorized by dimension, harmonic order, resonance frequency, severity rating (**Critical**, **High**, **Moderate**, **Low**), and tailored acoustic remedy.
- **Early Reflection Ray Tracing:** Automated mirror-image ray tracing calculating exact early reflection zones on left/right side walls and the ceiling cloud.
- **DIY Acoustic Specs & Cost Estimation:** Detailed recipes, dimensions, gas-flow resistivity/density guidance, and budget breakdowns for DIY Rockwool panels and superchunk corner traps.
- **Automatic State Persistence:** Automatically caches room dimensions, desk sizes, and placement coordinates in browser `localStorage` across page reloads.

---

## Quick Start

### Running the Simulator

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Gleinkaa/simulation.git
   cd simulation
   ```
2. **Open in browser:**
   Double-click `roomacousticsimulation.html` or open it from the terminal:
   ```bash
   # On Linux
   xdg-open roomacousticsimulation.html

   # On macOS
   open roomacousticsimulation.html

   # On Windows
   start roomacousticsimulation.html
   ```

### 3-Minute Quick Setup Workflow

1. **Enter Dimensions:** Under the **Room plan** tab, enter your room's Length, Width, and Height (in cm), along with your desk dimensions.
2. **Check the Sweet Spot:** Look at the **38% rule target** in the sidebar. Drag the circular listening position node on the top-down canvas until it aligns closely with the target (around 38% of room length from the front wall).
3. **Position Your Monitors:** Drag the speaker icons to set their front-wall distance (recommended: 95–110 cm) and adjust speaker spacing to form an equilateral triangle with your listening chair.
4. **Identify Problem Frequencies:** Inspect the **Modal frequency response** chart. Look for sharp peaks or deep nulls. Click on any peak or dip to see how the sound pressure distributes across your room in the 2D heatmap.
5. **Review Treatment & Specs:** Switch to the **Treatment plan** and **Panel specs** tabs to view the exact positions for side wall absorbers, ceiling clouds, and corner bass traps.

---

## Interactive Interface Tour

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  Studio Acoustic Simulation               5.30 m × 2.77 m × 2.50 m  [Badge] │
├────────────────────────────────────────────────────────┬────────────────────┤
│  [Room plan]  [Standing waves]  [Treatment]  [Specs]   │  Room Dimensions   │
├────────────────────────────────────────────────────────┤  Key Placements    │
│  Live Heatmap Freq: [====•===] 62 Hz                   │  Axial Mode Sum.   │
│  Speaker Spacing:   [======•=] 119 cm                  │  Quick Wins        │
│  Room: L [530] W [277] H [250] | Desk: W [160] D [70]  │                    │
│ ┌───────────────────────────┐ ┌──────────────────────┐ │                    │
│ │ Top-Down Room Plan Canvas │ │ Front View Canvas    │ │                    │
│ │ (Draggable speakers &     │ │ (Height × Width,     │ │                    │
│ │  listener, 2D Heatmap)    │ │  A7V elevation)      │ │                    │
│ └───────────────────────────┘ └──────────────────────┘ │                    │
│ ┌────────────────────────────────────────────────────┐ │                    │
│ │ Modal Frequency Response Canvas (20 Hz - 300 Hz)   │ │                    │
│ └────────────────────────────────────────────────────┘ │                    │
│  [With treatment] [No treatment] [Heatmap] [Reflect]   │                    │
└────────────────────────────────────────────────────────┴────────────────────┘
```

### 1. Room Plan View

The main simulation hub consists of:

- **Top-Down Canvas:**
  - **Monitors:** Marked with dark rectangular icons representing the ADAM A7Vs, showing membrane orientation and stereo toe-in angles.
  - **Listener Position:** Concentric circle target. Drag forward/backward to adjust listening distance.
  - **Ray Tracing Lines:** Dashed projection lines demonstrating direct paths and first reflections bouncing off side walls into the listener's ears.
  - **Acoustic Treatment Overlays:** Blue-tinted boundary panels showing front wall broadband absorbers, side wall first-reflection panels, flutter echo absorbers, rear wall absorbers/diffusers, and triangular corner bass traps.
  - **Acoustic Heatmap Overlay:** High-resolution 2D sound pressure level visualization. High pressure zones (antinodes) appear bright; low pressure zones (nodes/nulls) appear dark.
- **Front View Canvas:**
  - Displays room Width $\times$ Height in exact proportional scale.
  - Renders the seated ear height reference line ($1.20\text{ m}$), ceiling cloud suspension zone, and ADAM A7V front baffles (showing woofer and ribbon tweeter placement).
- **Modal Frequency Response Canvas:**
  - Solid curve: active treatment mode.
  - Dashed curve: alternative state (untreated baseline).
  - Vertical dashed marker: current heatmap inspection frequency.
  - Axial mode tick marks ($L_1, W_1, H_1, L_2, \dots$).
  - Crosshair cursor with high-precision tooltip.
- **Control Bar:**
  - `With treatment` / `No treatment`: Toggles broadband absorption damping in the modal equation and RT60 estimation.
  - `Heatmap`: Toggles 2D pressure field rendering on/off.
  - `Reflections`: Toggles early reflection ray-tracing lines.
  - `Reset positions`: Restores default optimal geometry.

### 2. Standing Waves & Modes Calculator

- **1D Standing Wave Simulator:**
  - Frequency slider ($20\text{ Hz} - 400\text{ Hz}$).
  - Dimension selection buttons: Length ($L$), Width ($W$), and Height ($H$).
  - Visual standing wave plot displaying pressure nodes and antinodes.
  - Real-time indicator showing listener position along that axis and whether the listener is sitting in a pressure peak or null (colored green for balanced, amber for moderate, red for extreme null/peak).
- **Room Modes Table (< 400 Hz):**
  - Displays all axial modes up to the 4th harmonic.
  - Interactive clickable frequency chips: clicking a chip instantly tunes the wave canvas and frequency response marker to that mode.
  - Lists severity, resonant dimension, and target acoustic remedy.

### 3. Treatment Plan & First Reflection Points

- **Live Speaker & Geometry Metrics:**
  - Distance from front wall and side walls.
  - Actual speaker spacing vs. equilateral triangle side length.
  - Precise toe-in angle (calculated via $\arctan(\text{offset} / \text{distance})$).
- **Treatment Priority Order (1–6):**
  1. *Corner Bass Traps (Superchunk / Floor-to-ceiling):* Tames dominant width and length fundamentals.
  2. *Side Wall First Reflection Points:* Cleans up early reflections, preserving stereo imaging and transient clarity.
  3. *Ceiling Cloud:* Eliminates floor-ceiling bounce and mix position comb filtering.
  4. *Front Wall Broadband:* Reduces speaker boundary interference response (SBIR) and mid-bass clutter.
  5. *Rear Wall Absorption/Diffusion:* Eliminates flutter echo and long-axis slap-back.
  6. *Rear Corner Soffit Traps:* Provides deep low-end damping for sub-bass length modes.
- **Calculated Reflection Points:**
  - Left & Right side wall reflection coordinates (distance from front wall).
  - Ceiling cloud center point coordinate.
- **Bill of Materials (BOM) Panel Count Table:**
  - Pre-calculated quantities and standard dimensions for broadband absorbers, corner traps, and diffusers.

### 4. Panel Specs & DIY Materials Cost

- **Panel Build Specifications:**
  - Core insulation materials: Rockwool RWA45, Safe'n'Sound, Knauf Earthwool, Owens Corning 703.
  - Density recommendations: $45\text{–}60\text{ kg/m}^3$ for broadband panels; $60\text{–}80\text{ kg/m}^3$ for corner bass traps.
  - Thickness: $10\text{ cm}$ (effective down to $200\text{ Hz}$) or $15\text{ cm}$ (effective down to $125\text{ Hz}$).
  - Air gap rule: $5\text{–}10\text{ cm}$ wall spacing to double low-frequency efficiency without extra insulation.
- **ADAM A7V Specific Calibration:**
  - Boundary EQ shelving trim guide.
  - Wide-dispersion X-ART ribbon tweeter acoustic implications.
- **DIY Cost Estimator:**
  - Approximate cost breakdown for insulation, timber framing, breathable acoustic fabric, mounting brackets, and diffusers.

### 5. Live Metrics Sidebar

The right sidebar provides real-time mathematical validation of your room:

- **Room Geometry:** Length, Width, Height, Volume ($\text{m}^3$), Aspect Ratio ($L:W$ with warnings if $> 1.8$ or $< 1.2$), and Schroeder Frequency ($f_s$).
- **Key Placements:** Distance to front wall, listening position, deviation from the 38% rule target (with color alerts), distance to rear wall, and toe-in angle.
- **Live Axial Mode Summary:** Evaluates the prominent axial modes at the listener's exact seat, classifying each as a **peak** ($+\text{dB}$) or **null** ($-\text{dB}$) relative to median room energy, with dynamic bar meters.
- **Quick Wins:** Context-sensitive tips prioritized for your specific room proportions.

---

## Acoustic Science & Simulation Model

### Modal Sound Field (Green's Function Expansion)

In an enclosed rectangular room with rigid boundaries, sound pressure $p(\mathbf{r}, \omega)$ at observation position $\mathbf{r} = (x, y, z)$ driven by an acoustic source at $\mathbf{r}_0 = (x_0, y_0, z_0)$ is governed by the Helmholtz equation. Using eigenmode expansion, the steady-state complex acoustic pressure is modeled as:

$$p(\mathbf{r}, \omega) = \rho c^2 \sum_{\mathbf{n}} \frac{\epsilon_{\mathbf{n}} \, \psi_{\mathbf{n}}(\mathbf{r}) \, \psi_{\mathbf{n}}(\mathbf{r}_0)}{\omega_{\mathbf{n}}^2 - \omega^2 + 2 j \delta_{\mathbf{n}} \omega}$$

Where:
- $\mathbf{n} = (n_x, n_y, n_z)$ are the mode integers.
- $\psi_{\mathbf{n}}(\mathbf{r}) = \cos\left(\frac{n_x \pi x}{L}\right) \cos\left(\frac{n_y \pi y}{W}\right) \cos\left(\frac{n_z \pi z}{H}\right)$ are the orthogonal room eigenfunctions.
- $\epsilon_{\mathbf{n}} = \epsilon(n_x)\epsilon(n_y)\epsilon(n_z)$ is the Neumann factor ($\epsilon(0) = 1$, $\epsilon(n \ge 1) = 2$).
- $\omega_{\mathbf{n}} = 2 \pi f_{\mathbf{n}}$ is the eigenmode angular resonance frequency, with:
  $$f_{\mathbf{n}} = \frac{c}{2} \sqrt{\left(\frac{n_x}{L}\right)^2 + \left(\frac{n_y}{W}\right)^2 + \left(\frac{n_z}{H}\right)^2}$$
  ($c = 343\text{ m/s} = 34,300\text{ cm/s}$).
- $\delta_{\mathbf{n}}$ is the modal damping coefficient.

### Dual Coherent Speaker Excitation

Unlike basic calculators that assume a single point source at a room corner, this simulator calculates the coherent sum of **both stereo monitors** operating at their true physical coordinates:

$$\psi_{\mathbf{n}}(\text{sources}) = \psi_{\mathbf{n}}(\mathbf{r}_{\text{left}}) + \psi_{\mathbf{n}}(\mathbf{r}_{\text{right}})$$

**Physical Consequence:** Because the left and right speakers are placed symmetrically around the width center line ($y = W/2$), their source sum for odd width modes ($n_y = 1, 3, 5\dots$) equals zero:

$$\cos\left(\frac{n_y \pi (W/2 - \Delta y)}{W}\right) + \cos\left(\frac{n_y \pi (W/2 + \Delta y)}{W}\right) = 0 \quad (\text{for odd } n_y)$$

This accurately reproduces the real-world acoustic phenomenon where centered symmetric speakers **cannot excite odd-order lateral room modes** in a symmetrical rectangular enclosure.

### Damping & RT60 Estimation

Modal damping is directly tied to the room's reverberation decay time ($\text{RT}_{60}$):

$$\delta_{\mathbf{n}} = \frac{3 \ln(10)}{\text{RT}_{60}(f)} \approx \frac{6.91}{\text{RT}_{60}(f)}$$

The simulator models frequency-dependent $\text{RT}_{60}$ for untreated and treated conditions:
- **Untreated Room:** $\text{RT}_{60}(f) = \max(0.50, \, 0.95 - 0.001 f)\text{ seconds}$ (long decay times, narrow high-$Q$ resonances, sharp peaks and nulls).
- **Treated Room:** $\text{RT}_{60}(f) = \max(0.22, \, 0.34 - 0.0003 f)\text{ seconds}$ (controlled decay, broader low-$Q$ resonances, flattened response curve).

### Schroeder Frequency

The Schroeder frequency ($f_s$) marks the transition boundary between discrete, isolated resonant room modes and statistical high-frequency reverberant behavior:

$$f_s \approx 2000 \sqrt{\frac{\text{RT}_{60}}{V}}$$

- Below $f_s$: Wave acoustics dominate; sound quality depends heavily on speaker and listener positioning and bass trapping.
- Above $f_s$: Geometric and ray acoustics dominate; sound quality depends on specular reflection management and diffusion.

### Specular First Reflection Ray-Tracing

Early reflections are determined using the classic **mirror-image acoustic source method**. For a speaker at $(x_s, y_s)$ and listener at $(x_l, y_l)$, the specular reflection contact point on the side wall ($y = 0$) occurs at:

$$x_{\text{reflection}} = x_s + (x_l - x_s) \cdot \frac{y_s}{y_s + y_l}$$

Placing broadband porous absorption panels centered at this coordinate intercepts the reflection before it arrives at the mixing position, preventing destructive comb filtering.

---

## Practical Studio Setup Guidelines

### The 38% Rule

In rectangular rooms, the longitudinal axial modes ($L_1, L_2, L_3, \dots$) create standing waves with pressure antinodes (maximum bass buildup) at the front and back walls, and a massive pressure null (zero bass) directly in the center of the room ($50\%$ of length).

Sitting at **38% of the room length** (measured from either the front or rear wall) places the engineer in the most statistically uniform modal pressure zone:
- Avoids the center null of $L_1$.
- Avoids the boundary buildup of the rear wall.
- Balances positive and negative excursions across $L_1$ through $L_4$.

The simulator displays your exact deviation from the 38% target in real time.

### The Equilateral Listening Triangle

Accurate stereo phantom center imaging and depth perception require an equilateral triangle between the acoustic centers of the monitors and the engineer's ears:

1. Speaker-to-speaker distance equals speaker-to-listener distance.
2. Toe-in angle should be approximately **$30^\circ$**, directing the high-frequency acoustic axis directly at (or slightly behind) the listener's head.
3. Keep tweeters at ear level ($1.20\text{ m}$ seated standard).

### Combating Narrow Room Modes

In narrow rooms (e.g., width $< 3\text{ m}$), the fundamental width mode ($W_1 = c / (2W)$) typically falls between $50\text{ Hz}$ and $70\text{ Hz}$—directly in the sub-bass kick/bass fundamentals for electronic music.

- **The Problem:** Even with symmetric speaker placement suppressing $W_1$ excitation, lateral movement or room asymmetry causes massive bass unevenness.
- **The Solution:** Floor-to-ceiling corner bass traps ($20\text{–}30\text{ cm}$ thick) in all four vertical corners. Corners are the convergence zones where all three axial modes (length, width, height) exhibit simultaneous pressure maxima.

---

## ADAM A7V Monitor Optimization

The simulator is pre-configured with the acoustic profile of the **ADAM Audio A7V** active nearfield studio monitor:

- **X-ART Ribbon Tweeter:** Offers fast transient response and wide horizontal dispersion ($120^\circ$). Because horizontal dispersion is broad, untreated side wall reflections are particularly energetic. High-absorption side panels are mandatory.
- **Bass Reflex Porting:** Front-firing bass ports minimize immediate turbulent coupling with the front wall compared to rear-ported monitors. However, front wall standoff should still remain $\ge 95\text{ cm}$ to mitigate low-mid boundary phase cancellation.
- **Built-in Boundary EQ Switches:**
  - **Bass (LF Shelf):** Set to `-2 dB` or `-4 dB` when positioned within $1\text{ m}$ of the front wall to offset boundary half-space loading ($+3\text{ dB}$ to $+6\text{ dB}$ low-end boost).
  - **Desk (Low-Mid Notch):** Set to `-2 dB` to tame reflections off the mixing console or desk surface.
  - **Treble (HF Shelf):** Leave flat (`0 dB`) in properly treated rooms, or `-1.5 dB` if high frequencies feel fatigued in reflective environments.

---

## DIY Acoustic Treatment Specifications

| Treatment Type | Location | Target Acoustic Problem | Minimum Thickness | Recommended Core Material | Air Gap |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Corner Bass Traps** | All 4 vertical corners (floor-to-ceiling) | Low-frequency modal buildup ($40\text{–}150\text{ Hz}$) | $20\text{–}30\text{ cm}$ (face) | Rockwool RWA45 or Safe'n'Sound ($60\text{–}80\text{ kg/m}^3$) | Fill triangular corner solid |
| **Side Wall Panels** | Left & right 1st reflection points | Early specular reflections ($200\text{ Hz}\text{–}10\text{ kHz}$) | $10\text{ cm}$ | Rockwool RWA45 or OC 703 ($45\text{–}60\text{ kg/m}^3$) | $5\text{–}10\text{ cm}$ |
| **Ceiling Cloud** | Suspended above desk & listening chair | Floor-ceiling bounce & comb filtering | $10\text{ cm}$ | Rockwool RWA45 ($45\text{–}60\text{ kg/m}^3$) | $10\text{ cm}$ air space |
| **Front Wall Absorber** | Behind monitor baffles | Low-mid SBIR buildup & boundary loading | $10\text{–}15\text{ cm}$ | Rockwool RWA45 ($45\text{–}60\text{ kg/m}^3$) | $5\text{ cm}$ |
| **Rear Wall Absorption** | Lower half of back wall | Axial length reflections ($L_1, L_2$) | $15\text{ cm}$ | Dense Rockwool ($60\text{ kg/m}^3$) | $10\text{ cm}$ |
| **Rear Wall Diffusers** | Upper half of back wall | Flutter echo while retaining room air & liveliness | $10\text{–}15\text{ cm}$ | 1D QRD or stepped timber diffusors | Flush mount |

---

## Assumptions & Model Boundaries

1. **Rigid Enclosure Boundaries:** The modal expansion assumes infinitely rigid, non-yielding wall, ceiling, and floor boundaries. Lightweight drywall, floating floors, and partition walls flex at low frequencies, providing natural bass absorption and slightly shifting modal frequencies downward.
2. **Shoebox Geometry:** Calculations strictly model rectangular prism (shoebox) rooms. Irregular rooms, alcoves, slanted ceilings, or L-shaped layouts require boundary element method (BEM) or finite element method (FEM) solvers.
3. **Modal Expansion Cutoff:** Modal calculation focuses on frequencies below $300\text{–}400\text{ Hz}$ where discrete room modes dominate. Above the Schroeder frequency, statistical room acoustics take over.
4. **Planning vs. Measurement:** This tool is designed for **pre-construction planning, setup optimization, and diagnostic insight**. Always verify final room acoustic response using a calibrated omnidirectional measurement microphone (e.g., miniDSP UMIK-1) and Room EQ Wizard (REW).

---

## User Manual

For an in-depth walkthrough, step-by-step room optimization recipes, DIY panel construction instructions, and troubleshooting tips, consult the complete manual:

👉 **[Read the Full User Manual (USER_MANUAL.md)](USER_MANUAL.md)**

---

## Contributing & License

- **License:** MIT License. Free to use, adapt, and build upon.
- **Contributions:** Pull requests and suggestions for acoustic models, UI refinements, or additional monitor profiles are warmly welcomed.
