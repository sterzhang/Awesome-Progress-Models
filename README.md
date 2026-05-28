<div align="center">
    <h1 style="display: inline-flex; align-items: center;">
        Progress Reward Models for Robotic Learning
    </h1>
</div>

This repository collects papers cited by the survey **Progress Reward Model for Robotic Learning: A Comprehensive Survey**. The list is organized around the survey's central view:

\[
y = f_\theta(x, g)
\]

where \(x\) is the available evidence, \(g\) is the task goal, and \(y\) is a progress-related signal such as a scalar progress score, local progress delta, preference, success probability, or executable reward function.

The curation rule is intentionally strict: **papers are included here only if they are cited in the survey**.

## News

- Survey citation: TBD
- Current README coverage: **44 survey-cited papers**

## Overview

- [Scope](#scope)
- [Taxonomy](#taxonomy)
- [Reading Map](#reading-map)
- [Benchmark Lens](#benchmark-lens)
- [Coverage Audit](#coverage-audit)
- [Citation](#citation)
- [Contributing](#contributing)

## Scope

Progress is not treated as an intrinsic property of an image or a video frame. It is a task-conditioned judgment: the same observation can indicate progress, no progress, or regression depending on the instruction and expected procedure.

This README therefore avoids a flat "reward model" list. Instead, papers are grouped by the role they play in progress modeling:

- **Interface**: what evidence is observed, how the goal is specified, and what the model outputs.
- **Construction mechanism**: how the progress signal is obtained, such as frozen foundation-model scoring, temporal structure, preferences, process supervision, stage decomposition, or reward code generation.
- **Supervision and evaluation**: what assumption turns data into progress labels, and what claim a benchmark actually supports.

## Taxonomy

### Interface

| Question | Common choices | Why it matters |
|---|---|---|
| What is the evidence \(x\)? | single observation, temporal window, before-after pair, full trajectory, simulator state, structured feedback | Determines whether the model can resolve temporal ambiguity and non-monotonic behavior. |
| How is the goal \(g\) specified? | language, goal image, demonstration, symbolic predicate, executable task description | Defines what counts as progress. |
| What is the output \(y\)? | progress score, progress delta, success probability, preference/ranking, reward code | Determines whether the signal is useful for monitoring, reranking, planning, or RL. |

### Method Families

| Family | Core assumption | Typical use |
|---|---|---|
| Frozen foundation-model scoring | pretrained semantic priors can score task relevance or completion | zero-shot rewards, success detection, instruction grounding |
| Temporal and representation learning | temporal order, goal proximity, or video dynamics imply reward geometry | dense rewards from demonstrations, passive video, or value-like representations |
| Preference and contrastive learning | relative comparisons can recover useful reward structure | ranking rollouts, pairwise feedback, failure-aware reward learning |
| Fine-tuned process reward models | progress can be directly supervised or reasoned about over task execution | calibrated progress, process scoring, long-horizon monitoring |
| Structured and programmatic rewards | task logic can be decomposed into stages, predicates, or executable code | long-horizon reward design, simulator/API-based reward synthesis |

## Reading Map

### Fine-Tuned Progress and Process Reward Models

These works directly model progress, process quality, stage structure, or progress-aware policy learning.

| Date | Paper | Main role in the survey | Links |
|---|---|---|---|
| 2026/04 | [ARM: Advantage Reward Modeling for Long-Horizon Manipulation](https://arxiv.org/abs/2604.03037) | local forward/static/backward progress and completion estimation | - |
| 2026/04 | [Generalizable Dense Reward for Long-Horizon Robotic Tasks](https://arxiv.org/abs/2604.00055) | dense long-horizon reward through subgoal and progress decomposition | - |
| 2026/03 | [Robometer: Scaling General-Purpose Robotic Reward Models via Trajectory Comparisons](https://arxiv.org/abs/2603.02115) | progress, success, and preference heads from robot trajectory comparisons | [GitHub](https://github.com/robometer/robometer) |
| 2026/03 | [ProgressVLA: Progress-Guided Diffusion Policy for Vision-Language Robotic Manipulation](https://arxiv.org/abs/2603.27670) | progress-conditioned policy learning and initial-current progress comparison | - |
| 2026/03 | [Recurrent Reasoning with Vision-Language Models for Estimating Long-Horizon Embodied Task Progress](https://arxiv.org/abs/2603.17312) | recurrent VLM reasoning for long-horizon task progress and answerability | - |
| 2026/01 | [PROGRESSLM: Towards Progress Reasoning in Vision-Language Models](https://arxiv.org/abs/2601.15224) | explicit progress reasoning and calibrated progress prediction | [GitHub](https://github.com/ProgressLM/ProgressLM) |
| 2026/01 | [RoboReward: General-Purpose Vision-Language Reward Models for Robotics](https://arxiv.org/abs/2601.00675) | rubric-based VLM reward modeling over robot rollouts | [Project](https://crfm.stanford.edu/helm/robo-reward-bench/) |
| 2025/12 | [Robo-Dopamine: General Process Reward Modeling for High-Precision Robotic Manipulation](https://arxiv.org/abs/2512.23703) | keyframe-anchored hop progress and process reward modeling | [GitHub](https://github.com/FlagOpen/Robo-Dopamine) |
| 2025/09 | [SARM: Stage-Aware Reward Modeling for Long Horizon Robot Manipulation](https://arxiv.org/abs/2509.25358) | stage identity plus within-stage progress | [GitHub](https://github.com/xdofai/opensarm) |
| 2025/09 | [A Vision-Language-Action-Critic Model for Robotic Real-World Reinforcement Learning](https://arxiv.org/abs/2509.15937) | signed before-after progress deltas for real-world robot RL | [GitHub](https://github.com/InternRobotics/VLAC) |
| 2025/05 | [ReWiND: Language-Guided Rewards Teach Robot Policies without New Demonstrations](https://arxiv.org/abs/2505.10911) | language-guided reward construction with rewound and mismatched examples | [GitHub](https://github.com/rewind-reward/ReWiND) |
| 2025/02 | [Subtask-Aware Visual Reward Learning from Segmented Demonstrations](https://openreview.net/forum?id=mqKVe6F3Up) | segmented demonstrations and subtask-aware visual rewards | [GitHub](https://github.com/csmile-1006/REDS_agent) |
| 2024/05 | [VICtoR: Learning Hierarchical Vision-Instruction Correlation Rewards for Long-horizon Manipulation](https://arxiv.org/abs/2405.16545) | hierarchical visual-instruction reward modeling | [GitHub](https://github.com/cmlab-victor/victor-code) |

### Foundation-Model Scoring and Success Criticism

These works use frozen or lightly adapted foundation models as reward scorers, success detectors, critics, or value-like estimators.

| Date | Paper | Main role in the survey | Links |
|---|---|---|---|
| 2026/02 | [TOPReward: Token Probabilities as Hidden Zero-Shot Rewards for Robotics](https://arxiv.org/abs/2602.19313) | token probabilities as zero-shot progress-like rewards | [GitHub](https://github.com/TOPReward/TOPReward) |
| 2025/09 | [OpenGVL -- Benchmarking Visual Temporal Progress for Data Curation](https://arxiv.org/abs/2509.17321) | visual temporal progress benchmark and data curation signal | [GitHub](https://github.com/budzianowski/opengvl) |
| 2024/11 | [Vision Language Models are In-Context Value Learners](https://arxiv.org/abs/2411.04549) | in-context VLM value/progress estimation | - |
| 2024/02 | ["Task Success" Is Not Enough: Investigating the Use of Video-Language Models as Behavior Critics for Catching Undesirable Agent Behaviors](https://arxiv.org/abs/2402.04210) | VLM behavior criticism beyond binary task success | [GitHub](https://github.com/GuanSuns/VLMs-Behavior-Critic) |
| 2023/12 | [Vision-Language Models as a Source of Rewards](https://arxiv.org/abs/2312.09187) | VLM-derived rewards from pretrained semantic models | - |
| 2023/10 | [Vision-Language Models are Zero-Shot Reward Models for Reinforcement Learning](https://arxiv.org/abs/2310.12921) | zero-shot VLM reward scoring for RL | [GitHub](https://github.com/AlignmentResearch/vlmrm) |
| 2023/03 | [Vision-Language Models as Success Detectors](https://arxiv.org/abs/2303.07280) | VLM success detection and endpoint supervision | - |
| 2022/07 | [Zero-Shot Reward Specification via Grounded Natural Language](https://proceedings.mlr.press/v162/mahmoudieh22a.html) | grounded language as zero-shot reward specification | - |
| 2022/04 | [Can Foundation Models Perform Zero-Shot Task Specification for Robot Manipulation?](https://arxiv.org/abs/2204.11134) | foundation-model task specification and visual goal grounding | [Project](https://sites.google.com/view/zestproject) |

### Temporal, Video, and Representation-Based Rewards

These works build reward-like signals from temporal order, passive video, value-like representations, goal proximity, or learned visual features.

| Date | Paper | Main role in the survey | Links |
|---|---|---|---|
| 2024/05 | [Video-Language Critic: Transferable Reward Functions for Language-Conditioned Robotics](https://arxiv.org/abs/2405.19988) | transferable video-language scalar rewards | [GitHub](https://github.com/minttusofia/video_language_critic) |
| 2024/04 | [Rank2Reward: Learning Shaped Reward Functions from Passive Video](https://arxiv.org/abs/2404.14735) | passive-video ranking converted to shaped rewards | [GitHub](https://github.com/dxyang/rank2reward) |
| 2023/12 | [Video Prediction Models as Rewards for Reinforcement Learning](https://papers.nips.cc/paper_files/paper/2023/hash/d9042abf40782fbce28901c1c9c0e8d8-Abstract-Conference.html) | video prediction model rewards | [GitHub](https://github.com/Alescontrela/viper_rl) |
| 2023/09 | [Robotic Offline RL from Internet Videos via Value-Function Pre-Training](https://arxiv.org/abs/2309.13041) | value-function pretraining from internet videos | - |
| 2023/07 | [LIV: Language-Image Representations and Rewards for Robotic Control](https://proceedings.mlr.press/v202/ma23b.html) | language-image representations as robotic rewards | [GitHub](https://github.com/penn-pal-lab/LIV) |
| 2022/10 | [VIP: Towards Universal Visual Reward and Representation via Value-Implicit Pre-Training](https://arxiv.org/abs/2210.00030) | value-implicit pretraining for visual reward and representation | [GitHub](https://github.com/facebookresearch/vip) |
| 2022/03 | [R3M: A Universal Visual Representation for Robot Manipulation](https://proceedings.mlr.press/v205/nair23a.html) | universal video-trained representation for robot manipulation | [GitHub](https://github.com/facebookresearch/r3m) |
| 2021/12 | [Generalizable Imitation Learning from Observation via Inferring Goal Proximity](https://papers.nips.cc/paper/2021/hash/868b7df964b1af24c8c0a9e43a330c6a-Abstract.html) | goal proximity as a progress-like signal | [GitHub](https://github.com/clvrai/goal_prox_il) |
| 2021/09 | [Learning Language-Conditioned Robot Behavior from Offline Data and Crowd-Sourced Annotation](https://arxiv.org/abs/2109.01115) | language-conditioned offline data and crowd annotations | [Project](https://sites.google.com/view/robotlorel) |
| 2021/03 | [Learning Generalizable Robotic Reward Functions from "In-The-Wild" Human Videos](https://arxiv.org/abs/2103.16817) | reward learning from in-the-wild human videos | [GitHub](https://github.com/anniesch/dvd) |
| 2016/12 | [Unsupervised Perceptual Rewards for Imitation Learning](https://arxiv.org/abs/1612.06699) | perceptual rewards from unsupervised representation learning | [Project](https://sermanet.github.io/rewards/) |

### Preference, Contrastive, and Human-Feedback Rewards

These works emphasize relative judgments, contrastive supervision, endpoint labels, or human feedback as the source of reward information.

| Date | Paper | Main role in the survey | Links |
|---|---|---|---|
| 2024/10 | [On-Robot Reinforcement Learning with Goal-Contrastive Rewards](https://arxiv.org/abs/2410.19989) | goal-contrastive rewards for on-robot RL | - |
| 2024/02 | [RL-VLM-F: Reinforcement Learning from Vision Language Foundation Model Feedback](https://arxiv.org/abs/2402.03681) | pairwise VLM feedback for RL | [GitHub](https://github.com/yufeiwang63/RL-VLM-F) |
| 2023/10 | [Robot Fine-Tuning Made Easy: Pre-Training Rewards and Policies for Autonomous Real-World Reinforcement Learning](https://arxiv.org/abs/2310.15145) | pretrained rewards and policies for autonomous real-world RL | [Project](https://robofume.github.io) |
| 2023/06 | [PEARL: Zero-Shot Cross-Task Preference Alignment and Robust Reward Learning for Robotic Manipulation](https://arxiv.org/abs/2306.03615) | cross-task preference alignment and robust reward learning | [Project](https://sites.google.com/view/pearl-preference) |
| 2019/09 | [Scaling Data-Driven Robotics with Reward Sketching and Batch Reinforcement Learning](https://arxiv.org/abs/1909.12200) | human reward sketches over trajectories | [Project](https://sites.google.com/view/data-driven-robotics/) |
| 2019/04 | [End-to-End Robotic Reinforcement Learning without Reward Engineering](https://arxiv.org/abs/1904.07854) | learned success/reward classifiers for robotic RL | [GitHub](https://github.com/avisingh599/reward-learning-rl) |

### Structured and Programmatic Reward Construction

These works construct rewards through task decomposition, symbolic state, generated reward functions, or executable visual reward logic.

| Date | Paper | Main role in the survey | Links |
|---|---|---|---|
| 2024/11 | [ELEMENTAL: Interactive Learning from Demonstrations and Vision-Language Models for Reward Design in Robotics](https://arxiv.org/abs/2411.18825) | VLM-generated features plus inverse reinforcement learning | - |
| 2024/02 | [Code as Reward: Empowering Reinforcement Learning with VLMs](https://arxiv.org/abs/2402.04764) | executable visual reward logic generated with VLMs | [GitHub](https://github.com/dvVenuto/vlm-car) |
| 2023/10 | [Eureka: Human-Level Reward Design via Coding Large Language Models](https://arxiv.org/abs/2310.12931) | LLM-generated reward code refined through policy feedback | [GitHub](https://github.com/eureka-research/Eureka) |
| 2023/09 | [Text2Reward: Reward Shaping with Language Models for Reinforcement Learning](https://arxiv.org/abs/2309.11489) | reward shaping through LLM-generated reward functions | [GitHub](https://github.com/xlang-ai/text2reward) |
| 2023/06 | [Language to Rewards for Robotic Skill Synthesis](https://proceedings.mlr.press/v229/yu23a.html) | natural language to dense reward functions for robot skills | [GitHub](https://github.com/google-deepmind/language_to_reward_2023) |

## Benchmark Lens

Different evaluations support different claims about progress modeling:

| Benchmark claim | What it tests | Representative papers |
|---|---|---|
| Scalar progress accuracy | Whether outputs match calibrated progress labels, hop values, or stage progress | ProgressLM, RoboReward, SARM, ARM, Robo-Dopamine |
| Temporal consistency | Whether scores recover monotonic or ordered progress in demonstrations | GVL, OpenGVL, TOPReward, ReWiND, VLAC, Robo-Dopamine |
| Preference and ranking | Whether the model ranks states, clips, or trajectories correctly | Robometer, Rank2Reward, RL-VLM-F, PEARL |
| Instruction grounding | Whether progress depends on the intended task rather than generic motion | RoboReward, ReWiND, VLAC, GVL |
| Answerability and uncertainty | Whether the model recognizes insufficient evidence or ambiguous progress | ProgressLM, Recurrent Reasoning VLM |
| Downstream utility | Whether the signal improves RL, planning, filtering, or policy learning | RoboReward, Robometer, ReWiND, VLAC, Text2Reward, Eureka, Code as Reward |

## Coverage Audit

This README was aligned with the survey citations.

| Check | Result |
|---|---|
| Papers cited in survey | 44 |
| Papers previously missing from README | R3M; ProgressVLA; Recurrent Reasoning with Vision-Language Models |
| README papers not cited by survey | None found |
| Papers removed for being uncited | None |

## Citation

If you find this survey helpful, a citation to our paper would be appreciated:

```bibtex
TBD
```

## Contributing

Contributions are welcome through pull requests. Please follow [CONTRIBUTING.md](CONTRIBUTING.md).

To keep this repository consistent with the survey, new README entries should either be cited in the survey or be proposed together with the corresponding survey citation update.
