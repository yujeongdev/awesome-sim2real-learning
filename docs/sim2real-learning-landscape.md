# Sim2Real Learning Landscape

This note tracks the major method families for learning robot behavior in simulation and deploying it in the real world.

## System view

```text
simulation/data source
  → task abstraction
  → policy learning
  → gap strategy
  → deployment interface
  → real-world evidence
  → feedback loop
```

The hard part is not just learning a high reward policy in simulation. The hard part is deciding which parts of the simulator should be accurate, which should be randomized, which should be adapted online, and which should be bypassed by better observations/actions.

## Method families

| Family | Main lever | Typical risk |
| --- | --- | --- |
| Domain randomization | broaden training distribution | ranges become arbitrary or too broad |
| System ID / adaptive randomization | fit or adapt sim parameters from real evidence | real rollout budget and task specificity |
| Online adaptation | infer hidden physical state at runtime | adaptation may fail under new failure modes |
| Real2Sim2Real policy learning | train/evaluate in target digital twins | twin construction and synchronization cost |
| Sim-and-real co-training | combine synthetic and real demos | poor mixing can cause negative transfer |
| Human correction / residuals | learn missing gap from real interventions | human supervision and safety complexity |
| VLA synthetic scaling | use sim/generated worlds for foundation-policy post-training | synthetic diversity may not cover real contact failures |
| Learned world simulators | train/evaluate policies in neural environments | model exploitation and long-horizon drift |

## 2026 snapshot

The 2026 frontier is moving from “train an RL policy in a hand-built simulator” toward:

- sim-only or sim-primary robot data scaling;
- VLA/RFM post-training in generated or procedural worlds;
- digital twins used for exploration and failure mining;
- learned world simulators for policy evaluation;
- deformable manipulation becoming a serious sim2real test case;
- co-training studies that quantify when sim data helps or hurts.

## Practical engineering questions

For every paper, ask:

1. What exactly is learned in simulation?
2. What is the real robot deployment interface?
3. What real data is used: none, demos, rollouts, corrections, scans, logs?
4. Which gap is targeted: visual, physics, controller, embodiment, task distribution, or policy distribution?
5. Does simulation improve success, robustness, data efficiency, safety, or evaluation fidelity?
6. Is the result reproducible with released code/data, or mainly a systems demonstration?

## Representative reading clusters

### Transfer by broader distributions

- Domain Randomization
- Dynamics Randomization
- Automatic Domain Randomization
- SimOpt

### Transfer by adaptation

- RMA
- Humanoid-Gym and humanoid locomotion recipes
- Sim-to-real biped locomotion

### Transfer by target digital twins

- RialTo
- TwinRL-VLA
- Real-is-Sim

### Transfer by real feedback

- TRANSIC
- i-Sim2Real-style iterative real feedback
- human-in-the-loop residual learning

### Transfer by synthetic data scaling

- MimicGen
- ReBot
- Sim-and-Real Co-Training
- ComSim
- SIM1
- MolmoBot

### Transfer by learned simulators

- Interactive World Simulator
- World4RL
- Robotic World Model

## What belongs in `awesome-real2sim` instead?

If a resource mainly constructs assets, scenes, digital twins, or sensor/physics models, it belongs in the Real2Sim repo. It belongs here only when the learning loop or deployment evidence is central.
