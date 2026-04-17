# Contributing to Awesome Sim2Real Learning

Thanks for helping keep this list useful.

## Quality Bar

A good entry should explain:

- what was learned in simulation;
- what real robot or real data was used for validation;
- what domain-gap strategy was used;
- what deployment interface was used;
- what caveats or failure modes matter in practice.

## Entry Format

```markdown
- ⭐ **[YEAR] Resource Name — Short Title** `[RL][IL][DR][DEP][V]` 🧰 🧪
  One-line summary focused on the learning/transfer contribution. Links: paper · project · code · data
  *Why engineers care:* concrete utility for learning, evaluating, or deploying sim-trained policies.
  *Caveat:* known limitation, weak real validation, robot/task lock-in, or fragile setup.
```

## Scope

Usually belongs here:

- simulation-trained policies deployed on real robots;
- RL/IL/VLA policy transfer;
- domain randomization or adaptation for policies;
- sim-and-real co-training;
- synthetic-data scaling for policy learning;
- learned/world-model simulators used for policy training or evaluation;
- real-world validation and deployment recipes.

Usually belongs in [Awesome Real2Sim Robotics](https://github.com/yujeongdev/awesome-real2sim):

- asset generation;
- simulator-ready object/environment construction;
- digital twin reconstruction without a policy-learning contribution;
- sensor/physics calibration as infrastructure rather than policy training.

## Style

- Prefer official links.
- Do not copy abstracts wholesale.
- Avoid hype unless backed by evidence.
- Include caveats when validation is weak or simulator assumptions are narrow.
