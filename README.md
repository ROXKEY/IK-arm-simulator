# Fun Projects

A collection of small interactive builds — games, simulations, and robotics/AI
demos. Each one lives in its own folder, is entirely self-contained (open
`index.html`, no install or build step), and has its own README with details.

## Projects

| Project | Description |
|---|---|
| [`ik-arm-simulator/`](./ik-arm-simulator) | Interactive 2-link robot arm — drag a target point and watch the analytic inverse-kinematics solver compute the joint angles in real time. |
| [`tower-of-hanoi/`](./tower-of-hanoi) | Classic Tower of Hanoi puzzle with 3–8 disks, a move counter, and an auto-solve animation. |

More to come as I build them.

## Running any project

Each folder is self-contained:

```bash
git clone https://github.com/ROXKEY/IK-arm-simulator.git
cd IK-arm-simulator/<project-folder>
open index.html      # macOS — or just double-click it, or use VS Code Live Server
```

## About

I'm a robotics student building small projects to explore algorithms, controls,
and interactive simulation as I go.
