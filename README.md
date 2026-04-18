<div align="center">

# 🧠 Awesome Sim2Real Learning

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
![Status](https://img.shields.io/badge/status-curated%20MVP-blue)
![Focus](https://img.shields.io/badge/focus-sim2real%20learning-8A2BE2)
![License](https://img.shields.io/badge/license-CC--BY--4.0-green)

**Curated papers, systems, benchmarks, and engineering recipes for learning robot behavior in simulation and transferring it to the real world.**

</div>

---

## 🔗 Sibling Project

- [Awesome Real2Sim Robotics](https://github.com/yujeongdev/awesome-real2sim) — simulation substrate: sim-ready assets, environments, digital twins, calibration, and validation.
- [Awesome Sim2Real Learning](https://github.com/yujeongdev/awesome-sim2real-learning) — policy-level transfer: RL/IL/VLA, domain randomization, curricula, policy evaluation, and deployment.

## 🚩 News & Updates

- **2026-04** — Expanded into a curated MVP covering classical RL transfer, locomotion, manipulation, VLA/synthetic-data scaling, world models, co-training, online correction, and evaluation.

## 📋 Contents

| | Section | What it answers |
| --- | --- | --- |
| 🎯 | [Aim of the Project](#aim) | Why sim2real learning is not just training in a simulator |
| 🧠 | [What is Sim2Real Learning?](#definition) | What must transfer from sim to robot behavior |
| 🏷️ | [Legend](#legend) | How to read capability and availability tags |
| 🎚️ | [Selection Criteria](#selection-criteria) | What belongs here and what does not |
| 🔥 | [Must Read First](#must-read) | A practical reading order |
| 🧱 | [Foundations: Randomization, Adaptation, and Gap Closure](#foundations) | Core ideas for bridging the reality gap |
| 🦿 | [Locomotion and Whole-Body Control](#locomotion) | Sim-trained policies for legged/humanoid robots |
| 🦾 | [Manipulation and Contact-Rich Transfer](#manipulation) | Sim-trained manipulation policies that survive real contact |
| 🎥 | [Imitation, Synthetic Data, and Co-Training](#imitation-synthetic) | Mixing sim and real demonstrations for policy learning |
| 🤖 | [VLA and Robot Foundation Model Transfer](#vla) | Synthetic/digital-twin training for VLA policies |
| 🌐 | [World Models and Learned Simulators](#world-models) | Learned environments for policy training/evaluation |
| ✅ | [Evaluation and Deployment](#evaluation) | What proves a policy actually transferred |

<a id="aim"></a>

## 🎯 Aim of the Project

This repository focuses on the **learning layer** of sim-to-real robotics: how policies, perception modules, controllers, and robot foundation models trained or evaluated in simulation survive deployment on physical robots.

It is intentionally separate from Real2Sim construction. A simulator or digital twin may be realistic, but a learning pipeline still needs the right observations, action space, reward/curriculum, domain-gap strategy, evaluation, deployment interface, safety checks, and real-world feedback loop.

<a id="definition"></a>

## 🧠 What is Sim2Real Learning?

```text
sim2real learning
≈ simulated experience + task abstraction + policy learning
  + domain-gap strategy + deployment interface + real-world feedback
```

The central question is not only “does the simulator look realistic?” but:

> Does behavior learned or evaluated in simulation transfer robustly to real robots?

A strong sim2real learning paper should tell us at least one of:

- what was learned in simulation;
- what real robot or real data was used for validation;
- which gaps were targeted: visual, physics, controller, embodiment, task distribution, or data distribution;
- whether simulation improves real success, robustness, data efficiency, safety, or policy selection.

<a id="legend"></a>

## 🏷️ Legend

Capability tags:

- `[RL]` Reinforcement learning
- `[IL]` Imitation learning / behavior cloning / diffusion policy
- `[VLA]` Vision-language-action or robot foundation model transfer
- `[WM]` World model / learned simulator
- `[DR]` Domain randomization / automatic domain randomization
- `[DA]` Domain adaptation / representation alignment
- `[CUR]` Curriculum / task generation / reward generation
- `[CTRL]` Control / locomotion / whole-body policy
- `[MAN]` Manipulation / contact-rich policy
- `[PER]` Perception policy or visual transfer
- `[TACT]` Tactile / force / visuotactile transfer
- `[DEP]` Real robot deployment interface
- `[EVAL]` Evaluation / benchmark / policy ranking
- `[V]` Real-world validation

Availability labels:

- ⭐ representative / must-read
- 🧪 real-robot validation
- 🧰 code available
- 📦 data / checkpoints / tasks available
- ⚠️ caveat: limited robot coverage, fragile setup, weak real validation, or simulator-specific assumption

<a id="selection-criteria"></a>

## 🎚️ Selection Criteria

A strong entry should contribute to at least one of:

- policy learning in simulation with real-world robot evidence;
- reinforcement learning, imitation learning, diffusion-policy, or VLA transfer;
- domain randomization, dynamics randomization, automatic domain randomization, or adaptation;
- curriculum, reward, task, or synthetic data generation for robust transfer;
- sim-and-real co-training or real2sim2real policy improvement;
- policy evaluation metrics that correlate with real-world success;
- deployment recipes connecting simulation-trained policies to real robot stacks.

Usually out of scope:

- generic RL papers with no real robot transfer;
- simulator-only benchmark results without sim-to-real analysis;
- pure digital twin / environment construction work better placed in [Awesome Real2Sim Robotics](https://github.com/yujeongdev/awesome-real2sim);
- robot policy papers where simulation is incidental and not reusable or analyzed.

<a id="must-read"></a>

## 🔥 Must Read First

1. **[2017] Dynamics Randomization / Domain Randomization** — the classic “make sim broad enough” baseline.
2. **[2019] SimOpt / Automatic Domain Randomization** — close the loop with real evidence or adaptive distributions.
3. **[2021] RMA and locomotion transfer** — learn adaptation mechanisms for hidden physical parameters.
4. **[2024] RialTo / TRANSIC** — use digital twins or human correction to robustify manipulation policies.
5. **[2025] ReBot / Sim-and-Real Co-Training** — synthetic video or sim+real demonstrations for VLA/diffusion policies.
6. **[2026] Interactive World Simulator / World4RL** — learned simulators as training/evaluation environments.
7. **[2026] MolmoBot / Scaling VLA RL** — simulation as the primary scaling substrate for robot foundation policies.

See also: [docs/reading-path.md](docs/reading-path.md), [docs/sim2real-learning-landscape.md](docs/sim2real-learning-landscape.md), and [docs/evaluation-checklist.md](docs/evaluation-checklist.md).

<a id="foundations"></a>

## 🧱 Foundations: Randomization, Adaptation, and Gap Closure

- ⭐ **[2017] Sim-to-real transfer of robotic control with dynamics randomization** `[RL][DR][CTRL][V]` 🧪
  Trains control policies under randomized simulator dynamics and deploys them on a real robot. Links: [OpenAI](https://openai.com/index/sim-to-real-transfer-of-robotic-control-with-dynamics-randomization)
  *Why engineers care:* classic baseline for covering actuator/contact/model mismatch with randomized training distributions.
  *Caveat:* randomization ranges are engineering choices; too broad can hide root causes and slow learning.

- ⭐ **[2017] Domain Randomization for Transferring Deep Neural Networks from Simulation to the Real World** `[PER][DR][V]` 🧪
  Randomizes simulated visual appearance so policies/perception models generalize to real images. Links: [paper](https://arxiv.org/abs/1703.06907)
  *Why engineers care:* foundational visual-transfer idea for synthetic data and vision-based policies.
  *Caveat:* visual randomization does not solve contact, actuator, or controller mismatch.

- ⭐ **[2019] Solving Rubik's Cube with a Robot Hand** `[RL][DR][CTRL][MAN][V]` 🧪
  Uses automatic domain randomization for dexterous manipulation transfer. Links: [paper](https://arxiv.org/abs/1910.07113)
  *Why engineers care:* representative of adaptive randomization for high-dimensional dexterous control.
  *Caveat:* strong compute, simulator, and hardware assumptions; not a lightweight recipe.

- ⭐ **[2019] SimOpt — Closing the Sim-to-Real Loop by Adapting Simulation Randomization** `[RL][DR][DA][EVAL][V]` 🧪
  Interleaves real rollouts and policy training to adapt simulation parameter distributions. Links: [project](https://sites.google.com/view/simopt/home) · [paper](https://arxiv.org/abs/1810.05687)
  *Why engineers care:* turns randomization into a real-evidence feedback loop instead of static hand-tuned ranges.
  *Caveat:* task-specific real rollouts remain necessary.

- **[2018] Sim-to-Real via Sim-to-Sim — Randomized-to-Canonical Adaptation Networks** `[RL][DA][PER][MAN][V]` 🧪
  Learns to translate randomized simulation observations to a canonical representation for grasping transfer. Links: [paper](https://arxiv.org/abs/1812.07252)
  *Why engineers care:* useful early example of using sim-to-sim adaptation to improve real transfer.
  *Caveat:* representation alignment can fail when physics/contact mismatch dominates.

<a id="locomotion"></a>

## 🦿 Locomotion and Whole-Body Control

- ⭐ **[2021] RMA — Rapid Motor Adaptation for Legged Robots** `[RL][DA][CTRL][DEP][V]` 🧪
  Learns policies with online adaptation to latent physical/environmental parameters. Links: [project](https://ashish-kmr.github.io/rma-legged-robots/) · [paper](https://arxiv.org/abs/2107.04034)
  *Why engineers care:* canonical example of adaptation modules making sim-trained locomotion robust to real terrain/dynamics.
  *Caveat:* mostly locomotion; adaptation assumptions may not transfer directly to manipulation.

- ⭐ **[2019] Sim-to-Real Transfer for Biped Locomotion** `[RL][CTRL][DEP][V]` 🧪
  Uses system identification and policy transfer for biped locomotion. Links: [project](https://faculty.cc.gatech.edu/~turk/paper_pages/2019_sim_to_real_biped/index.html)
  *Why engineers care:* practical reminder that dynamics identification and policy learning are coupled.
  *Caveat:* hardware-specific; reward and dynamics details matter.

- **[2024] Humanoid-Gym — Reinforcement Learning for Humanoid Robot with Zero-Shot Sim2Real Transfer** `[RL][CTRL][DEP][V]` 🧰 🧪
  Isaac Gym-based humanoid locomotion framework with sim-to-sim checks and real humanoid deployment. Links: [paper](https://arxiv.org/abs/2404.05695) · [code](https://github.com/roboterax/humanoid-gym)
  *Why engineers care:* useful open recipe for training humanoid locomotion policies with zero-shot transfer claims.
  *Caveat:* zero-shot success depends strongly on robot model, reward, actuator assumptions, and safety interface.

- **[2024] H2O — Learning Human-to-Humanoid Real-Time Whole-Body Teleoperation** `[RL][CTRL][IL][DEP][V]` 🧪
  Filters human motion through simulation and trains a humanoid motion imitator that transfers to real hardware. Links: [paper](https://arxiv.org/abs/2403.04436)
  *Why engineers care:* sim-to-data filtering plus RL imitation is a useful pattern for whole-body humanoid skills.
  *Caveat:* teleoperation and retargeting choices are tightly coupled to morphology.

<a id="manipulation"></a>

## 🦾 Manipulation and Contact-Rich Transfer

- ⭐ **[2024] RialTo — Real-to-Sim-to-Real for Robust Manipulation** `[RL][IL][MAN][DEP][V]` 🧰 🧪
  Builds digital twins from small real data, transfers demonstrations to simulation, and fine-tunes robust policies with RL. Links: [project](https://real-to-sim-to-real.github.io/RialTo/) · [paper](https://arxiv.org/abs/2403.03949)
  *Why engineers care:* strong template for real2sim2real manipulation: scan environment, construct twin, fine-tune, distill, deploy.
  *Caveat:* still needs target-environment setup and demonstrations.

- ⭐ **[2024] TRANSIC — Sim-to-Real Policy Transfer by Learning from Online Correction** `[RL][IL][MAN][DEP][V]` 🧰 📦 🧪
  Deploys sim-trained policies with human online correction, then learns residual policies for contact-rich assembly. Links: [project](https://transic-robot.github.io/) · [paper](https://arxiv.org/abs/2410.10315)
  *Why engineers care:* treats human correction as a direct signal for unmodeled sim2real gaps instead of trying to pre-enumerate them.
  *Caveat:* requires careful human-in-the-loop deployment and correction collection.

- **[2025] Human2Sim2Robot — Sim-to-Real RL using One Human Demonstration** `[RL][IL][MAN][DEP][V]` 🧰 🧪
  Converts one RGB-D human video into object-centric rewards and exploration initialization for dexterous manipulation RL in simulation. Links: [project](https://human2sim2robot.github.io/) · [paper](https://arxiv.org/abs/2504.12609)
  *Why engineers care:* good example of using human videos to specify task objectives without collecting robot teleoperation at scale.
  *Caveat:* task-specific extraction quality and embodiment gap handling are critical.

- **[2026] SIM1 — Physics-Aligned Simulator as Zero-Shot Data Scaler in Deformable Worlds** `[IL][MAN][DR][V]` 🧰 📦 🧪
  Uses high-fidelity cloth simulation and synthetic trajectory generation for zero-shot deformable manipulation transfer. Links: [project](https://internrobotics.github.io/sim1.github.io/) · [paper](https://arxiv.org/abs/2604.08544)
  *Why engineers care:* 2026 signal that simulation-only data can become competitive when deformable physics, action structure, and visual randomization are aligned.
  *Caveat:* deformable simulation quality and task-specific setup are still the bottleneck.

<a id="imitation-synthetic"></a>

## 🎥 Imitation, Synthetic Data, and Co-Training

- ⭐ **[2025] ReBot — Scaling Robot Learning with Real-to-Sim-to-Real Robotic Video Synthesis** `[IL][VLA][DA][MAN][V]` 🧰 🧪
  Replays real robot trajectories in simulation with new objects and blends simulated motion into real backgrounds for synthetic videos. Links: [project](https://yuffish.github.io/rebot/) · [paper](https://arxiv.org/abs/2503.14526)
  *Why engineers care:* practical VLA adaptation recipe: keep real trajectory structure, diversify objects in sim, synthesize temporally consistent robot videos.
  *Caveat:* video realism and physical consistency must both be checked.

- ⭐ **[2025] Empirical Analysis of Sim-and-Real Cotraining for Diffusion Policies** `[IL][DA][MAN][EVAL][V]` 🧰 🧪
  Studies how simulated and real demonstrations should be mixed for diffusion-policy manipulation. Links: [project](https://sim-and-real-cotraining.github.io/) · [paper](https://arxiv.org/abs/2509.14042)
  *Why engineers care:* turns “add sim data” into measured design rules around physics gap, visual gap, and mixing ratios.
  *Caveat:* focused on planar pushing; generalization to other manipulation types requires care.

- **[2023] MimicGen — Data Generation System for Scalable Robot Learning using Human Demonstrations** `[IL][MAN][V]` 🧰 📦
  Generates large-scale simulation demonstrations from a small number of human demonstrations. Links: [project](https://mimicgen.github.io/) · [paper](https://arxiv.org/abs/2310.17596)
  *Why engineers care:* useful data multiplier once a valid simulation task exists.
  *Caveat:* does not by itself solve environment fidelity or sim2real validation.

- **[2026] ComSim — Building Scalable Real-World Robot Data Generation via Compositional Simulation** `[IL][VLA][DA][V]` 🧪
  Combines classical simulation and neural simulation to generate action-video pairs with real-world consistency. Links: [project](https://faceong.github.io/ComSim/) · [paper](https://arxiv.org/abs/2604.11386)
  *Why engineers care:* highlights a hybrid recipe: keep simulator control/action consistency while reducing appearance gap with neural simulation.
  *Caveat:* watch whether the policy gains come from behavior-relevant realism or mainly visual translation.

<a id="vla"></a>

## 🤖 VLA and Robot Foundation Model Transfer

- ⭐ **[2026] MolmoBot — Training robot manipulation entirely in simulation** `[IL][VLA][DR][MAN][V]` 🧰 📦 🧪
  Open manipulation policy suite trained entirely on procedurally generated simulation data across two platforms. Links: [blog](https://allenai.org/blog/molmobot-robot-manipulation) · [technical site](https://allenai.github.io/molmobot/)
  *Why engineers care:* major 2026 example of sim-only scaling with released data, engine, training/eval code, and real robot zero-shot evaluation.
  *Caveat:* simulation scale and procedural diversity are core to the claim; small private sims may not reproduce the result.

- ⭐ **[2026] Scaling Sim-to-Real Reinforcement Learning for Robot VLAs with Generative 3D Worlds** `[RL][VLA][CUR][DR][V]` 🧪
  Uses generative 3D worlds and language-driven scene design for parallel VLA RL fine-tuning and sim2real transfer. Links: [paper](https://arxiv.org/abs/2603.18532)
  *Why engineers care:* important 2026 direction: preserve broad VLA generality by scaling scene/object diversity in simulation rather than overfitting in real-world RL.
  *Caveat:* depends on quality of generated interactive worlds and digital twins.

- **[2026] TwinRL-VLA — Digital Twin-Driven Reinforcement Learning for Real-World Robotic Manipulation** `[RL][VLA][DEP][EVAL][V]` 🧪
  Uses smartphone-captured digital twins to expand VLA exploration support and guide targeted human-in-the-loop real rollouts. Links: [paper](https://arxiv.org/abs/2602.09023)
  *Why engineers care:* shows digital twins as active exploration/failure-sampling tools, not only offline evaluation scenes.
  *Caveat:* overlaps strongly with Real2Sim; include here for the policy learning loop.

- **[2026] Sim2Real-VLA — Zero-Shot Generalization of Synthesized Skills to Realistic Manipulation** `[VLA][IL][DR][MAN][V]` 🧪
  Synthetic-data VLA framework for zero-shot manipulation transfer. Links: [paper](https://openreview.net/pdf/a4174c2964dc0df03c26c311b73e0a2e43de2929.pdf)
  *Why engineers care:* representative of synthetic-skill training for VLA-style manipulation policies.
  *Caveat:* verify released code/data and benchmark comparability before treating as a reproducible recipe.

- **[2026] Sim2Real-AD — Modular Sim-to-Real for VLM-Guided RL in Autonomous Driving** `[RL][VLA][PER][DEP][V]` 🧪
  Transfers CARLA-trained VLM-guided RL policies to a full-scale vehicle through observation/action bridges and deployment pipeline. Links: [paper](https://arxiv.org/abs/2604.03497) · [project](https://zilin-huang.github.io/Sim2Real-AD-website/)
  *Why engineers care:* good modular transfer pattern: observation bridge, action mapping, progressive training, real-time deployment.
  *Caveat:* autonomous driving domain; lessons need translation to manipulation/locomotion.

<a id="world-models"></a>

## 🌐 World Models and Learned Simulators

- ⭐ **[2026] Interactive World Simulator for Robot Policy Training and Evaluation** `[WM][IL][EVAL][MAN][V]` 🧪
  Builds action-conditioned world models from robot interaction data for policy training and evaluation. Links: [project](https://www.yixuanwang.me/interactive_world_sim/) · [paper](https://arxiv.org/abs/2603.08546)
  *Why engineers care:* claims stable long-horizon interaction simulation and real-world correlation for policy evaluation.
  *Caveat:* learned simulators must be stress-tested for compounding errors and exploitable artifacts.

- **[2025] World4RL — Diffusion World Models for Policy Refinement with Reinforcement Learning** `[WM][RL][MAN][V]` 🧰 🧪
  Refines pretrained manipulation policies entirely inside frozen diffusion world models. Links: [project](https://world4rl.github.io/) · [paper](https://arxiv.org/abs/2509.19080)
  *Why engineers care:* shifts world models from planning demos to policy optimization substrates.
  *Caveat:* reward modeling and action-conditioned dynamics fidelity are critical.

- **[2025] Real-is-Sim — Dynamic Digital Twin for Policy Evaluation** `[WM][IL][EVAL][DEP][V]` 🧪
  Uses a synchronized dynamic digital twin as the policy execution/evaluation medium. Links: [paper](https://arxiv.org/abs/2504.03597)
  *Why engineers care:* reframes deployment as real hardware tracking a synchronized sim, moving the gap into twin synchronization.
  *Caveat:* depends on reliable real-time state estimation and twin correction.

<a id="evaluation"></a>

## ✅ Evaluation and Deployment

- **[2026] RoboLab — A High-Fidelity Simulation Benchmark for Analysis of Task Generalist Policies** `[VLA][MAN][EVAL]` 🧰 📦 ⚠️
  Robot- and policy-agnostic Isaac Lab benchmark with 120 manipulation tasks for evaluating real-world-data-trained task-generalist policies under controlled visual, relational, and procedural axes. Links: [project](https://research.nvidia.com/labs/srl/projects/robolab/) · [paper](https://arxiv.org/abs/2604.09860) · [code](https://github.com/NVLabs/RoboLab)
  *Why engineers care:* gives a reproducible simulation harness for stress-testing VLA/generalist policies, language specificity, object confusion, and sensitivity to environment parameters before real deployment.
  *Caveat:* primarily simulation-side evaluation; treat real-world transfer claims as hypotheses unless paired with robot trials or sim-real correlation.

See [docs/evaluation-checklist.md](docs/evaluation-checklist.md).

A sim2real learning result is stronger when it reports:

- real robot model, task, and number of trials;
- whether transfer is zero-shot, few-shot, online-corrected, or fine-tuned;
- domain gaps explicitly targeted by the method;
- safety/deployment interface: action rate, controller type, latency, saturation, emergency stops;
- policy ranking correlation between sim and real;
- failure modes, not only success rates;
- ablations for randomization, calibration, real data amount, and simulator diversity.

## 🤝 Contributing

Contributions are welcome when they clarify what was learned in simulation, what transferred to real robots, what domain-gap strategy was used, and what validation evidence exists. Prefer concise engineering summaries over copied abstracts.

## 📚 Citation

If this list helps your work, cite the repository URL for now:

```bibtex
@misc{awesome_sim2real_learning,
  title        = {Awesome Sim2Real Learning},
  howpublished = {\url{https://github.com/yujeongdev/awesome-sim2real-learning}},
  year         = {2026}
}
```

## 📄 License

This curated list and documentation are released under [CC BY 4.0](LICENSE), unless a linked project states otherwise. Linked papers, code, datasets, assets, and checkpoints retain their own licenses.
