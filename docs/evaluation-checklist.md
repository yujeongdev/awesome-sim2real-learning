# Sim2Real Learning Evaluation Checklist

Use this checklist before treating a sim2real learning result as deployment-relevant.

## 1. Task and robot scope

- [ ] Real robot hardware is named.
- [ ] Task distribution is described, not only one demo scene.
- [ ] Number of real trials and success definition are reported.
- [ ] Failure modes are shown or discussed.

## 2. Transfer mode

- [ ] Zero-shot transfer is separated from few-shot adaptation.
- [ ] Real-world fine-tuning, online correction, or human intervention is disclosed.
- [ ] Training data sources are separated: sim, real demos, real rollouts, synthetic video, world model rollouts.
- [ ] Any real2sim or digital twin construction cost is included.

## 3. Observation and action interface

- [ ] Observation modality is clear: RGB, RGB-D, point cloud, proprioception, tactile, force, language.
- [ ] Real and simulated camera/sensor calibration assumptions are stated.
- [ ] Action space is clear: joint position, velocity, torque, OSC, end-effector delta, high-level primitive.
- [ ] Controller frequency, latency, saturation, and safety constraints are considered.

## 4. Domain-gap strategy

- [ ] Visual randomization/adaptation is described.
- [ ] Physics randomization/adaptation is described.
- [ ] Task/object/scene distribution randomization is described.
- [ ] Domain randomization ranges are motivated by real variation or failure modes.
- [ ] System identification or adaptation modules are validated separately when used.

## 5. Learning evidence

- [ ] Baselines include real-only, sim-only, and sim+real where relevant.
- [ ] Ablations isolate reward/curriculum/randomization/calibration/data-scale effects.
- [ ] Policy ranking in simulation is compared with real-world ranking when possible.
- [ ] Robustness is evaluated under pose, object, visual, disturbance, and environment shifts.

## 6. Deployment evidence

- [ ] Real-world videos are paired with quantitative trials.
- [ ] Safety intervention policy is described.
- [ ] Runtime constraints are realistic for the robot.
- [ ] The policy does not rely on privileged simulator-only information at deployment.

## Red flags

- “Sim2real” means only visual transfer, with no real robot trials.
- The simulator uses privileged state at train time and the deployment observation stack is unclear.
- The paper reports only curated videos or one-off demos.
- Real-world fine-tuning is used but described as zero-shot transfer.
- The learned policy could be exploiting simulator artifacts or world-model hallucinations.
