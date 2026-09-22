# Studio acoustic simulation

A single-file simulator for a rectangular studio production room, built around
an ADAM A7V nearfield setup and psytrance and electronic production. It is one
self-contained HTML file that opens straight in a browser, with no build step
and no dependencies.

## How to use it

Open `roomacousticsimulation.html`, then:

- Set the room and desk dimensions in the number fields.
- Drag the listening position, the speaker wall distance, or the speaker spread
  on the room plan.
- Read the four tabs: Room plan, Standing waves, Treatment plan and Panel specs.

The room plan is schematic. The panel count table on the Treatment plan tab
carries the product sizes.

## What the model does

The model is a steady-state modal expansion over rigid rectangular walls,
driven coherently by both speakers at their actual positions. Absorption enters
only as an RT60 estimate that changes with the treatment toggle, so the treated
and untreated curves come from the same geometry and differ in damping alone.

This is an estimate for planning where to put treatment, not a substitute for
measuring the room.

## Assumptions

- Ear and acoustic-centre height 1.2 m.
- Rigid walls.
- A 38% rule target for the listening position.
- Default room of 5.30 m x 2.77 m x 2.50 m.

## Design

The interface follows the house design system in `docs/BRAND.md`
(tailnet-dashboard).
