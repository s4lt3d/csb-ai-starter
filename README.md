# Coders Strike Back AI Starter

> High-performance C++ bot for Coders Strike Back: a competitive racing game with collision physics and search-based AI achieving 250k+ simulations per turn.

---

## Challenge Overview

[Coders Strike Back](https://www.codingame.com/multiplayer/bot-programming/coders-strike-back) is a real-time multiplayer bot racing challenge where:
- 2-4 players compete on a race track
- Each player controls a racing pod
- Goal: Complete laps, navigate checkpoints, reach the finish line
- Challenge: Optimize speed while avoiding collisions and handling physics

---

## Project Overview

A production-ready starter bot featuring:
- **Fully-functional simulation engine** with collision physics
- **Mutation-based search algorithm** exploring thrust and angle parameters
- **Depth-6 search tree** evaluating future states
- **Competitive baseline** suitable for Gold/Legend leagues
- **Copy-paste ready** — Can be submitted directly to CodinGame

---

## Architecture

### Core Components

**Physics Simulation**
- `Point` — 2D position with distance calculations
- `Unit` — Base class for entities (pods, checkpoints)
- `Pod` — Racing pod with position, velocity, angle, thrust
- `Checkpoint` — Track waypoints pods must navigate
- `Collision` — Collision detection and response system

**Game State**
- Up to 4 pods (2 players, 2 pods each)
- Up to 10 checkpoints per lap
- Full physics state replication for predictions

**Search Algorithm**
- **Mutation-based approach:** Generate solutions by varying thrust (0-100) and angle values
- **Depth 6:** Plan 6 turns ahead for each pod
- **250k-300k simulations per turn:** Explore thousands of action combinations
- **Evaluation function:** Score based on checkpoint progress, speed, position

### Optimization

- GCC compiler pragmas: `-Ofast`, inline, unroll loops
- Custom `fastrand()` for quick random number generation
- Minimal memory allocation during search
- Collision detection with early termination

---

## Features

- **High-Performance Simulation** — 250k-300k simulations/turn at competitive speeds
- **Mutation-Based Search** — Randomly explore thrust/angle combinations
- **Collision Physics** — Realistic pod-to-pod and pod-to-checkpoint interactions
- **Extensible Evaluation** — Easy to adjust scoring parameters
- **Production-Ready** — Tested on Gold/Legend league levels
- **Well-Documented References** — Built on proven strategies

---

## Usage

### Setup

1. Copy `main.cpp` to CodinGame CSB challenge
2. Use Gold or Legend league input format
3. Submit directly

### Input Format (Gold/Legend)

```
<pod1_x> <pod1_y> <pod1_vx> <pod1_vy> <pod1_angle> <pod1_thrust> <pod1_shield>
<pod2_x> <pod2_y> <pod2_vx> <pod2_vy> <pod2_angle> <pod2_thrust> <pod2_shield>
[pod3 and pod4 if present]
<checkpoint_count>
<checkpoint1_x> <checkpoint1_y>
...
```

### Output

```
<thrust> <angle>
```

---

## Performance

**Out of the box:**
- Performs adequately for Silver/Gold
- Simple tweaks → Top 100 Legend
- Parameter tuning → Top 50 Legend
- Heavily-modified variant (in this repo): **Rank 6 Legend**

---

## Improvement Roadmap

**Easy** (quick wins):
1. Adjust evaluation function parameters
2. Weight checkpoint distance vs speed
3. Add penalty for collisions

**Medium** (moderate effort):
4. Add multiple bot variants with different parameters
5. Cache expensive math operations
6. Fine-tune search depth/mutation strategies

**Hard** (most impact):
7. **Replace with Genetic Algorithm** — Evolve optimal parameters
8. Rewrite with reinforcement learning
9. Hybrid approach: GA + search

---

## License

[MIT License](LICENSE)

---

## References & Credits

- [Magus post-mortem](http://files.magusgeek.com/csb/csb_en.html) — Original simulation API and collision physics
- [pb4 post-mortem](https://www.codingame.com/blog/coders-strike-back-pb4608s-ai-rank-3rd/) — Strategy insights (Rank 3)
- [Jeff06 post-mortem](https://www.codingame.com/blog/genetic-algorithms-coders-strike-back-game/) — Genetic algorithm approach
- [sethorizer's sim engine tester](https://github.com/sethorizer/csb) — Physics validation