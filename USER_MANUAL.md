# Studio Acoustic Simulation: User Manual & Room Tuning Guide

A practical, step-by-step field manual for music producers, audio engineers, and studio builders using the **Studio Acoustic Simulation** suite.

---

## Table of Contents

1. [Quick Navigation & Interface Map](#1-quick-navigation--interface-map)
2. [Step-by-Step Room Optimization Workflow](#2-step-by-step-room-optimization-workflow)
   - [Phase 1: Room & Furniture Dimensioning](#phase-1-room--furniture-dimensioning)
   - [Phase 2: Establishing the 38% Listening Sweet Spot](#phase-2-establishing-the-38-listening-sweet-spot)
   - [Phase 3: Positioning the Monitors & Setting the Triangle](#phase-3-positioning-the-monitors--setting-the-triangle)
   - [Phase 4: Modal Analysis & Identifying Standing Waves](#phase-4-modal-analysis--identifying-standing-waves)
   - [Phase 5: Mapping Acoustic Treatment](#phase-5-mapping-acoustic-treatment)
   - [Phase 6: Calibrating Monitor Boundary EQ](#phase-6-calibrating-monitor-boundary-eq)
3. [Electronic & Psytrance Mix Translation Guide](#3-electronic--psytrance-mix-translation-guide)
4. [DIY Acoustic Treatment Construction Guide](#4-diy-acoustic-treatment-construction-guide)
   - [Broadband Absorber Panels (10 cm & 15 cm)](#broadband-absorber-panels-10-cm--15-cm)
   - [Floor-to-Ceiling Superchunk Corner Bass Traps](#floor-to-ceiling-superchunk-corner-bass-traps)
   - [Ceiling Cloud Installation](#ceiling-cloud-installation)
   - [The Physical Mirror Test](#the-physical-mirror-test)
5. [Interface Controls & Interaction Reference](#5-interface-controls--interaction-reference)
6. [Acoustic Troubleshooting & FAQ](#6-acoustic-troubleshooting--faq)

---

## 1. Quick Navigation & Interface Map

The simulator divides studio analysis into four primary tabs and a live telemetry sidebar:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ TAB BAR                                                                     │
│ [Room plan]         [Standing waves]      [Treatment plan]   [Panel specs]  │
├─────────────────────────────────────────────────────────────────────────────┤
│ PRIMARY WORKSPACE                                        │ SIDEBAR          │
│ • Live frequency slider & speaker width slider           │ • Room metrics   │
│ • Dimension number input fields (L, W, H, Desk W, Desk D)│ • Key placements │
│ • Interactive Top-Down Plan (with 2D pressure heatmap)   │ • Axial mode sum.│
│ • Front Elevation View (Monitors & Cloud height)         │ • Quick wins     │
│ • Modal Frequency Response (20 Hz - 300 Hz transfer fx)  │                  │
│ • Global Action Bar (Treatment on/off, Heatmap, Reset)   │                  │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Canvas Interaction Basics

- **Drag Listener:** Click and hold the circular listening position node on the Room Plan canvas to slide it forward or backward along the room's centerline.
- **Drag Speaker Wall Distance:** Click and drag the horizontal speaker crossbar to move both monitors closer to or further from the front wall.
- **Drag Speaker Spread:** Click and drag either the left or right monitor icon sideways to expand or contract the stereo spread.
- **Hover Crosshairs:** Hover over the Frequency Response chart or 1D Standing Wave chart to view exact decibel and amplitude figures.
- **Click to Inspect Frequency:** Click anywhere along the Modal Frequency Response curve to immediately set the 2D room heatmap and standing wave visualizer to that specific frequency.

---

## 2. Step-by-Step Room Optimization Workflow

Follow this six-phase methodology to tune your room from an empty space into an accurate acoustic listening environment.

### Phase 1: Room & Furniture Dimensioning

1. Measure your room's internal boundaries with a tape measure or laser distance meter:
   - **Length ($L$):** Distance from front wall (behind speakers) to rear wall (behind listener).
   - **Width ($W$):** Distance between left and right side walls.
   - **Height ($H$):** Distance from finished floor to ceiling slab.
2. In the **Room plan** tab, enter these dimensions into the `Room length`, `Room width`, and `Room height` fields (values in centimeters).
3. Measure your production desk's width and depth and input them into `Desk width` and `Desk depth`.
4. **Check the Aspect Ratio:** Review the sidebar under **Room dimensions**:
   - Ideal ratios distribute room modes evenly across the spectrum.
   - If your Length-to-Width ratio exceeds $1.80:1$, the simulator highlights it with an amber warning: your room is relatively long and narrow, making width modes concentrated in narrow frequency bands.

### Phase 2: Establishing the 38% Listening Sweet Spot

The longitudinal length axis of any rectangular room exhibits strong standing waves. Placing your head at $50\%$ of the room length puts you inside the deepest cancellation null of the fundamental length mode ($L_1$), where bass notes disappear almost entirely.

1. Check the sidebar metric labeled **38% rule target** (calculated as $0.38 \times \text{Length}$).
2. Drag the circular **Listening position** icon on the top-down canvas until your seat is positioned at or near this distance from the front wall.
3. Observe the **Deviation from 38%** warning:
   - **Green:** Within $\pm 15\text{ cm}$ of optimum.
   - **Amber:** $15\text{–}35\text{ cm}$ deviation (compromised modal balance).
   - **Red:** $> 35\text{ cm}$ deviation (risk of severe low-end dips or boomy buildup).

> [!TIP]
> If desk depth or room layout prevents sitting at 38% from the front wall, the second-best theoretical position is **38% from the rear wall** (i.e., at $62\%$ of room length).

### Phase 3: Positioning the Monitors & Setting the Triangle

1. **Front Wall Standoff:**
   - Drag the speaker pair so that the front baffle sits **$95\text{–}110\text{ cm}$** from the front wall.
   - *Why?* Placing speakers too close to the front wall creates strong half-space boundary loading ($+3\text{ dB}$ to $+6\text{ dB}$ bass boost). Placing them too far ($1.5\text{–}2.2\text{ m}$) shifts Speaker Boundary Interference Response (SBIR) cancellations right into the critical $50\text{–}80\text{ Hz}$ kick drum punch zone.
2. **Stereo Spread & Equilateral Triangle:**
   - Adjust the **Speaker spacing** slider until the distance between tweeters matches the distance from each tweeter to the listening position.
   - Look at the sidebar metrics: **Speaker spacing** and **Listening triangle**. When both numbers match closely (typically $115\text{–}140\text{ cm}$ for nearfields), your stereo phantom center and soundstage width are geometrically locked.
3. **Toe-In Alignment:**
   - The simulator calculates your exact required **Toe-in angle** (typically $28^\circ\text{–}32^\circ$).
   - Physically rotate the monitors inward so the acoustic axis of each ribbon tweeter points directly at your ears, crossing approximately $15\text{–}30\text{ cm}$ behind your head.
4. **Elevation (Front View):**
   - Switch to the front view canvas: the acoustic axis (center of the ADAM A7V ribbon tweeter) should sit exactly at seated ear height ($120\text{ cm}$ above finished floor). Use sturdy, decoupled speaker stands.

### Phase 4: Modal Analysis & Identifying Standing Waves

1. Open the **Standing waves** tab.
2. Click through the dimension selectors (`Length`, `Width`, `Height`):
   - Notice the blue standing wave pressure curve.
   - Observe where the vertical dashed marker (**Listener**) intersects the wave.
   - The indicator in the top right displays the **Pressure at listener** percentage.
3. Look at the **Room modes below 400 Hz** table:
   - Modes flagged as **CRITICAL** (red) represent high-energy fundamental resonances where room dimensions are small.
   - Click any frequency chip (e.g. `62 Hz` or `32 Hz`).
4. Return to the **Room plan** tab with the **Heatmap** active:
   - High-pressure zones (antinodes) appear illuminated; null zones appear dark.
   - If the listener circle falls in a dark pocket at that frequency, mixes will suffer from overcompensated, boomy bass on other systems.
   - If the listener circle falls in a bright zone, bass will sound artificially loud in the room, leading to thin, bass-starved exports.

### Phase 5: Mapping Acoustic Treatment

Switch to the **Treatment plan** tab and review the numbered priority hierarchy:

1. **Priority 1 (All 4 Vertical Corners):**
   - Install floor-to-ceiling porous absorber bass traps ($20\text{–}30\text{ cm}$ triangular superchunks).
   - This single intervention provides the highest reduction in modal decay time across all three room axes.
2. **Priority 2 (Side Wall First Reflections):**
   - Note the calculated coordinates: `Left side wall, from front wall` and `Right side wall, from front wall`.
   - Place $10\text{ cm}$ thick broadband panels centered at these coordinates at ear height.
3. **Priority 3 (Ceiling Cloud):**
   - Note the `Ceiling, from front wall` coordinate.
   - Suspend a $100 \times 120\text{ cm}$ panel directly above the desk and listening chair with a $5\text{–}10\text{ cm}$ air gap.
4. **Priority 4 & 5 (Front & Rear Walls):**
   - Front wall: Broadband panels directly behind the monitor cabinets to tame SBIR.
   - Rear wall: Thick absorbers on the lower half (to absorb length reflections) and 1D diffusers on the upper half (to scatter reflections and retain air).

### Phase 6: Calibrating Monitor Boundary EQ

When your physical layout matches the simulation, apply the hardware boundary EQ filters on the rear panel of your ADAM A7V monitors:

- **Distance to front wall $\ge 95\text{ cm}$:** Set `Bass` (LF shelf) to `-2 dB`.
- **Distance to front wall $< 95\text{ cm}$:** Set `Bass` (LF shelf) to `-4 dB`.
- **Desk reflection:** If the desk surface causes a hollow boxiness in vocals or snares, set the `Desk` EQ switch to `-2 dB` (cuts around $160\text{ Hz}$).
- **Highs:** Keep `Treble` at `0 dB`. If the room has untreated glass windows or bare plaster, set to `-1.5 dB` temporarily until side panels are installed.

---

## 3. Electronic & Psytrance Mix Translation Guide

Electronic genres (psytrance, techno, d&b, bass music) place extreme demands on low-frequency accuracy. Unlike acoustic jazz or rock, electronic tracks feature sustained synthesized basslines and full-scale sub-bass tones between $35\text{ Hz}$ and $100\text{ Hz}$.

### The Kick-Bass Phase Relationship

In psytrance production, the kick drum fundamental usually sits between $50\text{ Hz}$ and $65\text{ Hz}$, while the rolling 16th-note bassline occupies the exact same octave.

- **The Problem:** In an untreated room, a room mode at $62\text{ Hz}$ has an $\text{RT}_{60}$ decay time of $> 0.8\text{ seconds}$. The tail of the kick drum rings out so long that it masks the transient attack of the subsequent bass notes.
- **The Diagnostic:** Click `No treatment` in the simulator. Notice the sharp modal spike on the frequency response curve. Click `With treatment`: the resonance bandwidth widens ($Q$ drops), and the amplitude peak drops by $6\text{–}12\text{ dB}$, representing a dry, punchy low end that translates onto club sound systems.

### Width Modes in Typical Rooms

Most home studio bedrooms are between $2.5\text{ m}$ and $3.2\text{ m}$ wide. This creates a fundamental width mode ($W_1$) between $53\text{ Hz}$ and $68\text{ Hz}$.

- Even with centered speakers, moving your head just $15\text{–}20\text{ cm}$ left or right changes the perceived sub-bass level by up to $10\text{ dB}$.
- **Remedy:** Dense corner bass trapping and substantial side panels are essential so you hear the actual synthesizer envelope rather than room resonance.

---

## 4. DIY Acoustic Treatment Construction Guide

Professional studio acoustics do not require thousands of euros in commercial products. Building your own panels using dense mineral wool provides identical or superior acoustic performance.

### Broadband Absorber Panels (10 cm & 15 cm)

Broadband absorber panels target first reflection points, flutter echo, and low-mid reverberation ($150\text{ Hz}\text{–}10\text{ kHz}$).

#### Materials List (Per $120 \times 60\text{ cm}$ Panel)
- **Insulation:** 1 slab of Rockwool RWA45 or Owens Corning 703 ($120 \times 60\text{ cm}$, $10\text{ cm}$ thick; density $45\text{–}60\text{ kg/m}^3$).
- **Timber:** 1x4 pine or spruce battens ($20 \times 95\text{ mm}$ finished dimension).
- **Fabric:** Acoustically transparent fabric (Guilford of Maine, unbleached burlap/jute, or breathable speaker cloth).
- **Backing:** Thin breathable scrim, weed control membrane, or muslin cloth.
- **Hardware:** Wood glue, 40 mm wood screws, L-brackets, heavy-duty staple gun, and flush heavy-duty picture hanging cleats (French cleats).

#### Step-by-Step Construction

```
  ┌──────────────────────────────────────────────┐
  │                 Top Rail                     │
  │  ┌────────────────────────────────────────┐  │
  │  │                                        │  │
  │  │                                        │  │
  │  │         Rockwool Core Slab             │  │
  │  │         (45 - 60 kg/m³ density)        │  │
  │  │         120 cm × 60 cm × 10 cm         │  │
  │  │                                        │  │
  │  │                                        │  │
  │  └────────────────────────────────────────┘  │
  │                Bottom Rail                   │
  └──────────────────────────────────────────────┘
```

1. **Cut the Timber Frame:**
   - 2 pieces at $120.0\text{ cm}$ (sides).
   - 2 pieces at $60.0\text{ cm} - (2 \times \text{timber thickness})$ (top & bottom).
2. **Assemble the Box:** Glue and screw the frame corners square. Ensure internal dimensions snugly match your insulation slab ($120 \times 60\text{ cm}$).
3. **Insert Insulation:** Wear protective gloves, long sleeves, and an FFP2 mask. Press the Rockwool slab into the wooden frame. It should fit with slight friction.
4. **Rear Scrim:** Staple thin breathable fabric across the back of the frame to contain fibers.
5. **Front Acoustic Fabric:**
   - Lay your acoustic fabric face down on a clean work surface.
   - Center the framed panel face-down onto the fabric.
   - Pull the fabric taut over one side and staple every 5 cm along the back edge.
   - Repeat on the opposite side, working from center outwards while maintaining uniform tension.
   - Fold neat hospital corners on the top and bottom before stapling.
6. **Mounting with an Air Gap:**
   - Mount using wood spacers or offset French cleats to create a **$5\text{–}10\text{ cm}$ air gap** between the back of the panel and the drywall.
   - *Why?* Sound passes through the panel, hits the wall, and passes back through the panel. An air gap equal to panel thickness extends absorption down a full octave without purchasing extra insulation.

---

### Floor-to-Ceiling Superchunk Corner Bass Traps

Corners represent maximum acoustic impedance where all three room dimensions meet. Standard thin foam placed in corners has zero effect below 200 Hz. Superchunk traps fill the corner completely with dense porous absorber material.

```
       Wall A
       ┌───────────────────────────────┐
       │▲                             │
       ││\                            │
       ││ \                           │
       ││  \                          │
Wall B ││   \   Porous Insulation      │
       ││    \  (Rockwool Triangles)   │
       ││     \                        │
       │▼      \                       │
       └───────────────────────────────┘
               ◄── 40 - 60 cm Face ──►
```

#### Step-by-Step Construction

1. **Cut Triangular Slabs:**
   - Cut standard $120 \times 60\text{ cm}$ Rockwool slabs into right-angled triangles.
   - Cutting diagonally twice yields triangles with two $42\text{ cm}$ sides and a $60\text{ cm}$ front hypotenuse face.
2. **Build a Lightweight Retaining Frame:**
   - Fasten two thin vertical wooden battens along each wall $42\text{ cm}$ out from the corner.
3. **Stack Floor to Ceiling:**
   - Stack the insulation triangles tightly inside the corner from finished floor to ceiling slab with no air gaps.
   - Every 80 cm, install a thin horizontal wooden or wire support shelf to prevent the bottom layers from compressing under the weight.
4. **Finish with Fabric:**
   - Stretch acoustic fabric across the front face and staple into the side battens. Finish edges with decorative wooden trim molding.

---

### Ceiling Cloud Installation

Floor-to-ceiling reflections cause severe comb filtering that degrades vocal clarity, transient snap, and high-frequency balance.

1. Build a $10\text{ cm}$ panel sized $100 \times 120\text{ cm}$ using the broadband absorber method.
2. Drill four heavy-duty heavy-gauge eye-bolts into the corners of the panel frame.
3. Locate solid ceiling joists or use heavy-duty toggle bolts in drywall. Install corresponding ceiling hooks directly above the mix position (centered on the coordinate given in the **Treatment plan** tab).
4. Hang the cloud using sturdy steel picture wire or small-link steel chain.
5. Level the cloud horizontally at **$10\text{–}15\text{ cm}$ below the ceiling**. Ensure all hanging hardware is securely rated for at least $4\times$ the panel weight.

---

### The Physical Mirror Test

To confirm that your side wall panels cover the exact specular reflection zones calculated by the simulator:

1. Sit in your calibrated listening chair at normal mix posture.
2. Have a friend hold a flat handheld mirror against the left side wall at ear height and walk slowly from front wall to back wall.
3. When you can see the **left monitor's ribbon tweeter** in the mirror, mark the wall.
4. Continue sliding the mirror until you can see the **right monitor's ribbon tweeter**. Mark the wall.
5. Your side wall acoustic panel must span both marks with at least $15\text{ cm}$ of margin on either side.
6. Repeat the process for the right side wall and the ceiling.

---

## 5. Interface Controls & Interaction Reference

| Control Element | Location | Function / Description |
| :--- | :--- | :--- |
| **`Room length (cm)`** | Room plan tab | Sets longitudinal room dimension ($L$). Automatically recalculates all length modes and the 38% rule target. |
| **`Room width (cm)`** | Room plan tab | Sets lateral room dimension ($W$). Recomputes fundamental width mode and speaker standoff metrics. |
| **`Room height (cm)`** | Room plan tab | Sets vertical room dimension ($H$). Recomputes height modes and front elevation ceiling cloud placement. |
| **`Desk width / depth`** | Room plan tab | Updates desk outline on the plan; checks physical clearance with monitors and listener. |
| **`Live heatmap freq`** | Room plan tab | Continuously varies the 2D Green's function modal sound field frequency ($20\text{–}400\text{ Hz}$). |
| **`Speaker spacing`** | Room plan tab | Adjusts stereo width between monitors ($40\text{–}250\text{ cm}$); updates toe-in and triangle metrics. |
| **`With treatment`** | Action bar | Activates treated room RT60 decay profile ($\sim 0.25\text{ s}$), damping modal response. |
| **`No treatment`** | Action bar | Reverts to bare reflective room RT60 profile ($\sim 0.8\text{ s}$), showing raw resonant peaks. |
| **`Heatmap`** | Action bar | Toggles 2D sound pressure level rendering on top-down canvas. |
| **`Reflections`** | Action bar | Toggles dashed mirror-image ray-tracing paths from speakers to listener. |
| **`Reset positions`** | Action bar | Resets listener to 38% mark and speakers to 100 cm standoff with 119 cm spread. |
| **Frequency Response Click** | Bottom canvas | Clicking any point on the modal curve immediately tunes the heatmap and wave slider to that frequency. |
| **Frequency Response Hover** | Bottom canvas | Displays precision crosshair tooltip showing frequency, treated dB, and untreated dB. |
| **Mode Frequency Chips** | Standing waves tab | Quick-selection buttons that jump directly to known resonant eigenfrequencies. |

---

## 6. Acoustic Troubleshooting & FAQ

### Q: Why does sub-bass sound thin at my desk, but boomy when I stand near the back wall?
**A:** You are experiencing the classic symptom of longitudinal standing waves. The back wall is a rigid acoustic termination where air velocity drops to zero and sound pressure reaches maximum (an antinode). The center of the room is a pressure node (velocity maximum) where cancellation occurs. Follow the **38% rule** to move your seat out of the central null, and install dense bass traps in the rear corners to absorb the boundary energy.

### Q: Why do odd-order width modes disappear in the simulation?
**A:** This is accurate acoustic physics. When two monitors are placed symmetrically at equal distances from the room centerline, they drive the room with equal phase. Odd-order width modes ($W_1, W_3, W_5$) have anti-symmetric pressure distributions (positive pressure on the left, negative on the right). Identical in-phase sources cannot excite anti-symmetric modes. If your real room exhibits $W_1$ ringing, it indicates either asymmetrical speaker placement, asymmetrical furniture, or off-center listening.

### Q: Should I put foam wedges on my walls?
**A:** Standard polyurethane foam wedges ($2\text{–}5\text{ cm}$) only absorb high frequencies above $1\text{ kHz}$. Using foam without low-frequency bass trapping removes air and brightness while leaving modal bass booming unchecked, resulting in a dark, muffled, and boomy room. Always prioritize **dense mineral wool (Rockwool)** bass trapping and $10\text{ cm}$ broadband panels before addressing high-frequency flutter.

### Q: Can DSP room correction software (e.g., Sonarworks SoundID, Dirac Live) replace physical treatment?
**A:** No. DSP can cut narrow modal peaks at a single listening point, but it cannot fix phase cancellations (nulls). Boosting an acoustic null simply pumps more amplifier power into a destructive cancellation, burning headroom and stressing speaker drivers. Furthermore, DSP cannot reduce reverberant decay time ($\text{RT}_{60}$). Physical bass traps are required to absorb energy and stop room ringing; DSP should only be used for final fine-tuning after physical acoustic treatment is installed.

### Q: How do I clear saved settings and restore original defaults?
**A:** The simulator stores your configuration in browser `localStorage`. To completely reset:
1. Open your browser Developer Tools (`F12` or `Ctrl+Shift+I` / `Cmd+Opt+I`).
2. Navigate to the **Console** tab.
3. Type `localStorage.removeItem('acoustic_sim_settings'); location.reload();` and press Enter.
