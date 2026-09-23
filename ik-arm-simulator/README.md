# 2-Link Planar Arm — Inverse Kinematics Simulator

An interactive browser demo of analytic inverse kinematics for a 2-degree-of-freedom
planar robot arm. Click or drag anywhere in the workspace and the solver computes
the shoulder and elbow joint angles needed to place the end-effector at that point.

[Live demo](#) — open `index.html` in any browser, no build step required.

## What it demonstrates

- **Forward vs. inverse kinematics**: the arm's pose is driven entirely by solving
  for joint angles from a desired end-effector position, not the other way around.
- **Analytic IK via the law of cosines**: given link lengths `L1`, `L2` and a target
  `(x, y)`, the elbow angle is solved from the triangle formed by the two links and
  the line to the target, then the shoulder angle follows from the target's polar
  angle minus the offset introduced by the elbow bend.
- **Workspace limits**: points beyond `L1 + L2` (or inside `|L1 - L2|` for a two-link
  arm with overlapping range) are unreachable; the demo clamps to the nearest
  reachable point and flags it, rather than failing silently.
- **Elbow-up / elbow-down configurations**: for any reachable target (other than at
  the workspace boundary) there are generally two valid solutions. A toggle lets you
  switch between them, which is a useful illustration of IK's non-uniqueness.

## The math

For link lengths `L1`, `L2` and target `(x, y)` at distance `d = sqrt(x² + y²)`:

```
cos(θ2) = (d² - L1² - L2²) / (2 · L1 · L2)
θ2      = ±acos(cos(θ2))        (sign selects elbow-up / elbow-down)

θ1      = atan2(y, x) − atan2(L2·sin(θ2), L1 + L2·cos(θ2))
```

This is the standard closed-form solution for a 2R planar manipulator — no
iteration or numerical solver needed, which is part of why 2-link arms are a
common first example in robotics courses before moving to Jacobian-based or
optimization-based IK for higher-DOF arms.

## Project structure

```
ik-arm-sim/
├── index.html   # self-contained: markup, styles, and IK logic in one file
└── README.md
```

Everything lives in a single HTML file on purpose, so it's easy to read top-to-bottom
and easy to fork into a starting point for a 3-link arm, a Jacobian-based solver, or
a version that drives a real servo setup over serial/WebUSB.

## Running it

No dependencies, no build tooling:

```bash
git clone <your-repo-url>
cd ik-arm-sim
open index.html      # macOS
# or just double-click index.html / use the VS Code Live Server extension
```

## Possible extensions

- Add a 3rd link and switch to a numerical (Jacobian pseudo-inverse or CCD) solver
- Animate a path (e.g. draw a shape) by feeding a sequence of targets
- Add joint limits and visualize when a target is reachable only outside those limits
- Export joint angle sequences as a CSV/JSON trajectory for a real servo-driven arm

## Background

- [Inverse kinematics — Wikipedia](https://en.wikipedia.org/wiki/Inverse_kinematics)
