# Reading Path

This path is for engineers who want to understand sim2real learning as a deployment discipline, not as a loose collection of RL papers.

## 0. Separate substrate from learning

Use the two-repo boundary:

```text
Real2Sim Robotics → build simulator-executable assets/environments/digital twins
Sim2Real Learning → train/evaluate/deploy behavior using simulation
```

If the contribution is mainly environment construction, place it in `awesome-real2sim`. If it changes how policies learn, adapt, evaluate, or deploy, place it here.

## 1. Start with the classic reality-gap tools

Read:

- Domain Randomization
- Dynamics Randomization
- Automatic Domain Randomization
- SimOpt
- Sim-to-Sim / RCAN

Ask:

- What is randomized?
- Is the randomization distribution fixed, adapted, or inferred from real rollouts?
- Does the policy learn invariance, adaptation, or domain-conditioned behavior?

## 2. Study locomotion transfer

Read:

- RMA
- Sim-to-real biped locomotion
- Humanoid-Gym
- H2O

Ask:

- What observations and action spaces survive deployment?
- Are hidden physical parameters inferred online?
- How are actuator delay, command rate, torque limits, and safety handled?

## 3. Study manipulation transfer

Read:

- RialTo
- TRANSIC
- Human2Sim2Robot
- SIM1

Ask:

- Is transfer zero-shot, few-shot, corrected, or fine-tuned?
- What real data is required?
- Are contact, friction, object pose, and controller gaps explicitly addressed?

## 4. Study synthetic data and co-training

Read:

- MimicGen
- ReBot
- Sim-and-Real Co-Training
- A Mechanistic Analysis of Sim-and-Real Co-Training in Generative Robot Policies
- ComSim

Ask:

- Does sim data replace real data, augment it, or fill coverage holes?
- What mixing ratio is used?
- Which gaps matter most for the task: visual, physical, task distribution, or action distribution?

## 5. Study robot foundation model transfer

Read:

- MolmoBot
- Scaling Sim-to-Real RL for Robot VLAs
- TwinRL-VLA
- Sim2Real-VLA

Ask:

- Is simulation used for pretraining, post-training, RL fine-tuning, or evaluation?
- Does diversity preserve generality, or does RL overfit the VLA to one scene?
- Are digital twins used for exploration, failure mining, or real rollout targeting?

## 6. Study world models as simulators

Read:

- Interactive World Simulator
- World4RL
- Real-is-Sim

Ask:

- Can the world model run long-horizon closed-loop interaction?
- Does policy ranking in the world model correlate with real robot performance?
- Can policies exploit model artifacts?

## 7. Evaluate like a deployment engineer

Read:

- RoboLab

A strong sim2real result should report:

- real robot trials, not only videos;
- transfer mode: zero-shot, few-shot, online correction, fine-tuning;
- controller/action interface;
- safety constraints;
- failure modes;
- ablations over sim diversity, real data amount, randomization, and calibration;
- sim-real policy ranking or evaluation correlation.
