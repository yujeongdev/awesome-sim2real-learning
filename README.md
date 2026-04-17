# Awesome Sim2Real Learning [![Awesome](https://awesome.re/badge.svg)](https://awesome.re) ![Status](https://img.shields.io/badge/status-seed-blue) ![Focus](https://img.shields.io/badge/focus-policy%20transfer-8A2BE2) ![License](https://img.shields.io/badge/license-CC--BY--4.0-green)

**Curated papers, systems, benchmarks, and engineering recipes for learning robot behavior in simulation and transferring it to the real world.**

---

## Sibling Projects

- [Awesome Sim-Ready 3D Asset Generation](https://github.com/yujeongdev/awesome-sim-ready) — object-level assets: geometry, articulation, physical properties, simulator formats, and asset validation.
- [Awesome Sim2Real Environments](https://github.com/yujeongdev/awesome-sim2real-environments) — environment-level systems: scenes, digital twins, sensors, physics, calibration, and validation.
- [Awesome Sim2Real Learning](https://github.com/yujeongdev/awesome-sim2real-learning) — policy-level transfer: RL/IL, domain randomization, curricula, policy evaluation, and deployment case studies.

## Aim of the Project

This repository focuses on the **learning layer** of sim-to-real robotics: how policies, perception modules, controllers, and robot foundation models trained or evaluated in simulation survive deployment on physical robots.

It is intentionally separate from environment construction. A simulator may be realistic, but a learning pipeline still needs the right observations, action spaces, reward/curriculum design, randomization, evaluation, deployment interface, and real-world feedback loop.

## What is Sim2Real Learning?

```text
sim2real learning
≈ simulated experience + task abstraction + policy learning
  + domain-gap strategy + deployment interface + real-world feedback
```

The central question is not only “does the simulator look realistic?” but:

> Does behavior learned in simulation transfer robustly to real robots?

## Legend

Capability tags:

- `[RL]` Reinforcement learning
- `[IL]` Imitation learning / behavior cloning / diffusion policy
- `[VLA]` Vision-language-action or robot foundation model transfer
- `[DR]` Domain randomization / automatic domain randomization
- `[DA]` Domain adaptation / representation alignment
- `[CUR]` Curriculum / task generation
- `[CTRL]` Control / locomotion / manipulation policy
- `[PER]` Perception policy or visual transfer
- `[DEP]` Real robot deployment interface
- `[EVAL]` Evaluation / benchmark / policy ranking
- `[V]` Real-world validation

Availability labels:

- ⭐ representative / must-read
- 🧪 real-robot validation
- 🧰 code available
- 📦 data / checkpoints / tasks available
- ⚠️ caveat: limited robot coverage, fragile setup, weak real validation, or simulator-specific assumption

## Selection Criteria

A strong entry should contribute to at least one of:

- policy learning in simulation with real-world robot evidence;
- domain randomization, dynamics randomization, or automatic domain randomization;
- sim-to-real imitation learning or diffusion-policy transfer;
- curriculum or task generation for robust transfer;
- policy evaluation metrics that correlate with real-world success;
- deployment recipes connecting simulation-trained policies to real robot stacks.

Usually out of scope:

- generic RL papers with no real robot transfer;
- simulator-only benchmark results without sim-to-real analysis;
- pure digital twin or reconstruction work with no learning/deployment component;
- robot policy papers where simulation is incidental and not reusable or analyzed.

## Must Read First

- ⭐ **[2017] Sim-to-real transfer of robotic control with dynamics randomization** `[RL][DR][CTRL][V]` — classic dynamics randomization baseline for control transfer. Links: [OpenAI](https://openai.com/index/sim-to-real-transfer-of-robotic-control-with-dynamics-randomization)
- ⭐ **[2019] Solving Rubik's Cube with a Robot Hand** `[RL][DR][CTRL][V]` — automatic domain randomization for dexterous manipulation. Links: [paper](https://arxiv.org/abs/1910.07113)
- ⭐ **[2019] Sim-to-Real Transfer for Biped Locomotion** `[RL][CTRL][DEP][V]` — system identification and policy transfer for biped locomotion. Links: [project](https://faculty.cc.gatech.edu/~turk/paper_pages/2019_sim_to_real_biped/index.html)

## Core Sections

- Foundations of Sim2Real Transfer
- Reinforcement Learning Sim2Real
- Imitation Learning and Diffusion Policy Transfer
- Domain Randomization and Adaptation
- Curriculum and Task Generation
- Locomotion Transfer
- Manipulation Transfer
- Visuotactile and Sensor-Based Transfer
- Policy Evaluation and Real-World Validation
- Deployment Recipes

## Contributing

Contributions are welcome when they clarify what was learned in simulation, what transferred to real robots, what domain-gap strategy was used, and what validation evidence exists. Prefer concise engineering summaries over copied abstracts.

## License

This curated list and documentation are released under [CC BY 4.0](LICENSE), unless a linked project states otherwise. Linked papers, code, datasets, assets, and checkpoints retain their own licenses.
