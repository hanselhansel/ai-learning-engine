# Day 3 Session: Key Terminology Decoder Ring

**Date:** 2026-03-18 (Generated post-session)
**Phase:** 1 - Foundations | **Week:** 1 | **Day:** 3
**Core Question:** What do insiders actually mean when they say these words?
**Status:** PREPARED (Learner to review before live session)

> Read this before your next live session. Then say "let's learn" to start the interactive review.

---

## A. Flags from Day 2

1. **"Spatial AI" not "Special AI"**: 3rd time flagged. This keeps appearing in your founder summaries. Say it out loud 10 times before reading further. Spatial. Spatial. Spatial.

2. **"Unitree" not "Unity"**: You said "Unity robot" in your Day 2 founder summary. Unitree = Chinese robotics company (G1 humanoid, $13,500). Unity = game engine (Unity Technologies). Different companies, different industries.

3. **Cosmos = 20M hours, not 200M**: You inflated the number 10x in your Day 2 summary. In interviews, wrong numbers kill credibility even when direction is right.

4. **DoF still weak (6/10)**: Quick drill right now:
   - How many DoF in a human arm? **7**
   - How many DoF in a human hand? **20+**
   - How many DoF in a typical factory robot arm? **6**
   - What does more DoF mean? **More flexible, but exponentially harder to control**

5. **Perception = sensing ONLY**: You keep blending it with planning. Drill: Perception answers "what's around me?" Planning answers "what should I do?" Control answers "how do I move?" Three separate layers.

6. **Take positions, don't hedge**: You said "it's a mix of all three" on the ImageNet question. Practice: pick one answer, defend it with data, then add nuance after.

7. **Community check-in deferred**: Did you browse r/robotics and LeRobot Discord yet? Note observations below:
   - Observation: _______________
   - Interesting person/thread: _______________

8. **LeCun paper**: Did you read "A Path Towards Autonomous Machine Intelligence"? Key takeaways: _______________

---

## B. Review Quiz: Day 1 + Day 2 Combined (10 Terms)

Mix of Day 1 and Day 2 terms. Cover the answer column. Explain each to a non-technical founder in one sentence.

| # | Term | Your Answer | Reference Answer |
|---|------|-------------|-----------------|
| 1 | **Degrees of Freedom (DoF)** | | Number of independent axes a joint can move. Human arm = 7. More DoF = more flexible but harder to control |
| 2 | **Perception** | | Sensing and understanding the environment via cameras/lidar. The robot's eyes and ears. Input only, not decisions |
| 3 | **CLIP** | | OpenAI model (2021) trained on 400M image-text pairs, first to connect vision and language at internet scale. Bridge to VLAs |
| 4 | **Transformer** | | Neural network architecture using attention to process all input simultaneously. Powers ChatGPT, ViT, and now robot VLAs. Key: parallelizable, scales with data/compute |
| 5 | **Manipulation** | | Grasping, moving, assembling physical objects. Hardest unsolved problem in robotics because objects vary in shape, weight, texture, fragility |
| 6 | **AlexNet** | | CNN that won ImageNet 2012 by 10+ points, triggering the deep learning revolution. Step-function improvement, not incremental |
| 7 | **World Model** | | AI that predicts what happens next in a physical environment. Like an LLM predicting the next token, but for physics/video |
| 8 | **SLAM** | | Simultaneous Localization and Mapping. How robots figure out where they are while navigating unknown environments. 1990s invention, still used today |
| 9 | **Sim-to-Real** | | Training methodology: train in simulation, deploy on real robot. Solves the data scarcity problem. 95% sim + 5% real fine-tuning is current best practice |
| 10 | **VLA** | | Vision-Language-Action model. Sees the world, understands language instructions, outputs motor commands. "LLM + eyes + hands" |

**Target: 7+/10.** Priority: DoF, Perception, Manipulation, World Model (all below 7/10 in Day 2 quiz).

---

## C. Today's Lesson: The Full Terminology Decoder Ring

### Why This Matters

In interviews, networking, and due diligence conversations, vocabulary is your entry ticket. If you say "the robot uses reinforcement learning to perceive its environment," that's wrong (RL is for learning, not perception) and it signals you don't know the field. Today locks in the complete vocabulary.

### Section 1: Tier 2 Terms (New Today)

These are terms you need to know by end of Week 2. Each one includes a definition, an analogy to your LLM/business experience, and a "latest update" from web research (as of March 2026).

---

#### 1. NeRF (Neural Radiance Field)

| Aspect | Detail |
|--------|--------|
| **What** | AI technique that reconstructs 3D scenes from a collection of 2D photos. Take 50 photos of a room from different angles, NeRF creates a full 3D model you can explore from any viewpoint |
| **Invented** | 2020 (UC Berkeley) |
| **How it works** | A neural network learns the color and density at every point in 3D space. Given a new camera angle, it renders what you'd see from that position |
| **LLM analogy** | Like how an LLM can generate text it's never seen by learning language patterns, NeRF generates views it's never seen by learning 3D structure from photos |
| **Limitation** | Slow: training takes hours, rendering takes seconds per frame |
| **Current status (2026)** | Largely superseded by Gaussian Splatting for practical applications, but still used in research. Hybrid NeRF+GS methods are emerging (ICCV 2025) |

---

#### 2. Gaussian Splatting (3DGS)

| Aspect | Detail |
|--------|--------|
| **What** | Faster alternative to NeRFs. Instead of a neural network, it represents scenes as millions of tiny 3D "splats" (Gaussian blobs) that are rendered in real-time |
| **Invented** | 2023 (INRIA, France) |
| **Speed advantage** | 100+ FPS rendering vs. ~5 FPS for NeRFs. Training in minutes vs. hours |
| **Why it matters for robotics** | Robots need real-time 3D understanding. You can't wait hours to reconstruct a scene. Gaussian Splatting makes 3D perception practical |
| **LLM analogy** | NeRF is like running a huge LLM for every query (slow but thorough). Gaussian Splatting is like a distilled/quantized model (fast, good enough, deployable) |
| **Current status (2026)** | Now the standard for production 3D reconstruction. Used in robotics navigation, AR, and factory digital twins. Active research on hybrid NeRF+GS methods for combining speed with quality |

**Key comparison for interviews:**

| Factor | NeRF | Gaussian Splatting |
|--------|------|-------------------|
| Rendering speed | ~5 FPS | 100+ FPS |
| Training time | Hours | Minutes |
| Visual quality | Excellent | Equal or better |
| Real-time capable? | No | Yes |
| Production use | Rare | Standard |
| Year introduced | 2020 | 2023 |

---

#### 3. Reinforcement Learning (RL) / Deep RL

| Aspect | Detail |
|--------|--------|
| **What** | Learning by trial and error with rewards. Agent takes actions in an environment, gets positive/negative rewards, learns to maximize reward over time |
| **How it works** | Robot tries random actions → gets reward signal (e.g., +1 if cup grasped, -1 if dropped) → learns which actions lead to rewards → improves over millions of tries |
| **Why "Deep" RL** | Uses deep neural networks to handle complex observations (images, sensor data) instead of simple state tables |
| **Key success** | OpenAI's Dexterous Hand solving Rubik's Cube (2018): trained entirely in simulation via RL, then transferred to real robot |
| **Limitation** | Needs millions of trials. Impractical on real robots (too slow, too expensive, too dangerous). That's why sim-to-real matters |
| **LLM analogy** | RLHF (Reinforcement Learning from Human Feedback) that makes Claude helpful is the same RL concept, just with different rewards (human preference instead of physics success) |
| **Current status (2026)** | Still used for locomotion and some manipulation tasks, but increasingly being replaced by imitation learning and VLA models for general tasks |

---

#### 4. Imitation Learning

| Aspect | Detail |
|--------|--------|
| **What** | Learning by watching demonstrations. A human shows the robot how to do a task, the robot learns to replicate it |
| **Two main approaches** | (1) **Behavioral Cloning**: directly copy the demonstrated actions. Simple but brittle. (2) **DAgger**: human corrects the robot as it practices, iterating toward competence |
| **Why it's hot right now** | Foundation models (pi-0, Helix) are trained primarily on imitation learning data, not RL. It's more data-efficient and produces more natural behavior |
| **LLM analogy** | Imitation learning is like fine-tuning an LLM on curated examples. RL is like RLHF. Most modern systems use imitation learning first, then polish with RL |
| **Current status (2026)** | Dominant training paradigm for VLA models. Diffusion-based imitation learning (learning to generate smooth action sequences) is the latest technique. Chef Robotics using it for food handling. Isaac Lab 2.3 added enhanced teleoperation support (Meta Quest VR, Manus gloves) to accelerate demo data collection |

**Key comparison:**

| Factor | Reinforcement Learning | Imitation Learning |
|--------|----------------------|-------------------|
| Data source | Self-generated (trial & error) | Human demonstrations |
| Data efficiency | Low (millions of trials) | High (hundreds to thousands of demos) |
| Behavior quality | Can find surprising solutions | More natural, human-like |
| Failure mode | Reward hacking (finds loopholes) | Distribution shift (fails on unseen situations) |
| Current trend | Declining for general tasks | Dominant for VLA training |

---

#### 5. Teleoperation

| Aspect | Detail |
|--------|--------|
| **What** | Human remotely controlling a robot. The human wears sensors/uses controllers, the robot mirrors their movements in real-time |
| **Why it matters** | THE primary data collection method for robot foundation models. Physical Intelligence, Figure, 1X all use teleoperation to generate training data |
| **Hardware** | VR headsets (Meta Quest), haptic gloves (Manus), leader-follower arms, motion capture suits |
| **Scale challenge** | One human can only generate data on one robot at a time. Companies need fleets of teleoperators. 1X reportedly has 100+ teleoperation stations |
| **LLM analogy** | Teleoperation is like the human labelers who create instruction-following data for Claude. Expensive per-hour, but generates the highest-quality data |
| **Current status (2026)** | NVIDIA Isaac Lab 2.3 expanded teleoperation device support. TeleOpBench (2025) introduced standardized benchmarks for teleoperation quality. Leader-Follower setups (operator controls leader arm, robot mirrors) becoming standard |
| **Business opportunity** | Teleoperation-as-a-Service could be a business. Companies need demo data but don't want to build teleoperation infrastructure. Think: "AWS for robot training data" |

---

#### 6. End Effector

| Aspect | Detail |
|--------|--------|
| **What** | The tool at the end of a robot arm. Could be a gripper (parallel jaw, suction cup, dexterous hand), a welding torch, a screwdriver, a camera |
| **Why it matters** | The end effector determines what tasks a robot can do. A suction cup gripper can pick up flat boxes but not round objects. A dexterous hand can do both but costs 10x more and is harder to control |
| **Types** | Parallel jaw (simple, cheap), suction/vacuum (fast for flat objects), dexterous hand (flexible, expensive), soft gripper (for fragile items) |
| **LLM analogy** | Think of it as the "output interface." An LLM's end effector is text. A VLA's end effector is whatever tool is attached to the robot arm |
| **Key trade-off** | Generality vs. performance. A simple gripper is fast and reliable for one task. A dexterous hand can do many tasks but is slower and less reliable at each |

---

#### 7. Sim-to-Real Gap

| Aspect | Detail |
|--------|--------|
| **What** | The performance drop when transferring a policy trained in simulation to a real robot. A robot that succeeds 95% in simulation might only succeed 60% in reality |
| **Why it exists** | Simulation approximates physics: friction, deformation, lighting, sensor noise are never perfectly accurate |
| **How it's addressed** | Domain randomization (random messiness forces robustness), sim-to-real fine-tuning (train 95% sim + 5% real), digital twins (high-fidelity simulation of specific real environments) |
| **LLM analogy** | Like the gap between benchmark performance and real-world user satisfaction. A model that scores 90% on MMLU might still give bad answers to your specific client's questions |
| **Current status (2026)** | Partially solved for rigid object manipulation. Still significant for soft objects (fabrics, food), contact-rich tasks (assembly), and highly variable environments (outdoor, homes) |

---

#### 8. Digital Twin

| Aspect | Detail |
|--------|--------|
| **What** | A virtual replica of a physical system (factory, warehouse, robot, city). Updated in real-time with sensor data from the real system |
| **Why it matters for robotics** | Test robot behavior in the digital twin before deploying on the real factory floor. Reduce downtime, catch errors virtually |
| **Key player** | NVIDIA Omniverse is the dominant platform. "Mega" blueprint (2025) enables factory-scale digital twins for robot fleet testing |
| **Adoption (2026)** | Foxconn using Omniverse for its 242K sq ft Houston facility. Caterpillar for predictive maintenance. TSMC for semiconductor fab optimization. PepsiCo deploying Siemens Digital Twin Composer (mid-2026) |
| **Market** | $1.2 trillion in US manufacturing investment announced in 2025, much of it incorporating digital twin technology |
| **LLM analogy** | Like a staging/test environment for your code. You don't deploy to production without testing. Digital twins are the staging environment for physical robots |
| **Your bridge** | your business could eventually use digital twins for warehouse layout optimization. The concept scales from robot testing to full supply chain simulation |

---

#### 9. RaaS (Robots-as-a-Service)

| Aspect | Detail |
|--------|--------|
| **What** | Business model where customers pay monthly/per-use for robots instead of buying them outright. The vendor owns, maintains, and upgrades the robots |
| **Market size** | ~$2.1-2.4B in 2025, growing at 16-21% CAGR. Projected $10-15B by 2034 |
| **Why it matters** | Removes the CAPEX barrier. A warehouse doesn't need $500K upfront for robots. They pay $2-5K/month per robot and scale up/down |
| **LLM analogy** | This is the SaaS model applied to physical robots. Same as how you pay monthly for Claude API instead of building your own LLM. Same economics: vendor bears R&D cost, customer gets predictable OpEx |
| **Key players** | Amazon Robotics (internal), Locus Robotics, Bear Robotics (hospitality), Agility (warehouse) |
| **Your bridge** | Your agency operates on a service model (monthly retainer, not project-based). RaaS is the same concept for hardware. Apply your understanding of MRR, churn, unit economics |
| **Investment lens** | RaaS companies have SaaS-like metrics: recurring revenue, net dollar retention, usage-based expansion. Evaluate them with the same frameworks you use for software companies |

---

#### 10. Embodiment Gap

| Aspect | Detail |
|--------|--------|
| **What** | A policy (behavior model) trained on one robot body may not work on a different robot body, even for the same task. An arm with 6 DoF moves differently than one with 7 DoF |
| **Why it matters** | If every robot needs its own training, the economics don't scale. The dream is one model that works on any robot body |
| **Current state (2026)** | Active research area. Cross-embodiment transfer improving rapidly. OXE-AugE (Dec 2025) generated 4.44M trajectories across 9 robot types, showing 24-45% improvement in cross-robot transfer. UniSkill achieves 0.87 success rate in zero-shot human-to-robot transfer. ET-VLA uses synthetic data to warm up models for new embodiments without real demos |
| **LLM analogy** | Like fine-tuning one LLM to work across different API formats and tool schemas. The underlying intelligence is the same, but the "interface" (robot body) changes |
| **Key question** | Will there be one universal robot model (like GPT for text), or will each robot type need its own model? Current evidence: trending toward universal, but not there yet |

---

#### 11. Morphology

| Aspect | Detail |
|--------|--------|
| **What** | The physical form/shape of a robot. Humanoid, quadruped, wheeled, snake-like, flying. Each morphology has different capabilities and constraints |
| **Why it matters** | Morphology determines what tasks a robot can do, what environments it can operate in, and how hard it is to control. Humanoid morphology is the most general-purpose but also the hardest |
| **Types** | Humanoid (general-purpose, expensive), quadruped (stable, good for rough terrain, e.g., Spot), wheeled (fast on flat surfaces, cheap), aerial (drones), snake/soft (can navigate tight spaces) |
| **LLM analogy** | Morphology is like choosing a model architecture. GPT-style (decoder-only) vs. BERT-style (encoder-only) vs. T5 (encoder-decoder). Each has trade-offs for different use cases |

---

### Section 2: Bonus Terms (Surfaced from Web Research, March 2026)

| Term | Definition | Why You Should Know It |
|------|-----------|----------------------|
| **Diffusion Policy** | Using diffusion models (like image generators) to generate smooth robot action sequences. Now standard in VLA training | Used by pi-0, Chef Robotics. The "next-gen" approach to imitation learning |
| **Dual-System Architecture** | VLA design with System 2 (slow, high-level reasoning via VLM) + System 1 (fast, low-level motor control). Used by Helix and GR00T N1 | This is the emerging standard for humanoid VLAs. Know this for interviews |
| **Cross-Embodiment Transfer** | Training one model on data from multiple robot types so it generalizes across bodies. OXE-AugE generated 4.44M trajectories across 9 robot types | The key to making robot foundation models economically viable |
| **Isaac Lab 2.3** | NVIDIA's latest robot simulation/training platform. Added whole-body control, enhanced teleoperation (Meta Quest, Manus gloves) | The standard tool for robot training. Know what it does |
| **Omniverse Mega Blueprint** | NVIDIA's framework for building factory-scale digital twins. Siemens, Foxconn, FANUC first adopters | The infrastructure layer for industrial digital twins |

---

## D. Drill Exercise: Term Categorization

Organize all terms you've learned (Day 1 + Day 2 + Day 3) into the robot stack. This tests whether you understand how the pieces fit together.

**Fill in this table with the terms that belong at each layer:**

| Stack Layer | Description | Terms That Belong Here |
|-------------|------------|----------------------|
| **Hardware** | Physical robot body, sensors, actuators | _(fill in)_ |
| **Perception** | Sensing and understanding the environment | _(fill in)_ |
| **World Understanding** | 3D scene representation, prediction | _(fill in)_ |
| **Planning** | Deciding what to do | _(fill in)_ |
| **Control** | Executing motor commands | _(fill in)_ |
| **Learning/Training** | How the robot acquires skills | _(fill in)_ |
| **Infrastructure** | Simulation, data, compute | _(fill in)_ |
| **Business Model** | How companies monetize | _(fill in)_ |

**Example answers (reveal after attempting):**
- Hardware: DoF, End Effector, Morphology, Locomotion
- Perception: SLAM, Perception, NeRF, Gaussian Splatting
- World Understanding: World Model, Spatial Intelligence, Digital Twin
- Planning: Planning, VLA (spans planning + control)
- Control: Control, Manipulation
- Learning/Training: RL, Imitation Learning, Sim-to-Real, Teleoperation, Foundation Model, Embodiment Gap
- Infrastructure: ImageNet, NVIDIA Cosmos/Isaac/Omniverse, Gaussian Splatting (also perception)
- Business Model: RaaS

---

## E. Community Check-In

Lurk mode. Fill in after browsing today:

| Question | Your Notes |
|----------|-----------|
| Most interesting post on r/robotics this week? | |
| Any LeRobot Discord projects that caught your eye? | |
| Who posted something insightful? (Username) | |
| Did you see any of today's terms used "in the wild"? | |

---

## F. Reflect: "Explain It to a Founder" Summary

Today's prompt: **"What's the tech stack inside a modern robot?"**

Write 2-3 sentences using today's terminology. Draft here, refine in live session:

> _Your summary:_ _______________________________________________

**Suggested framing:** "A modern robot runs on a layered stack. Perception (cameras, lidar) tells it what's around it. A VLA model combines that visual understanding with language instructions to plan actions. Control executes precise motor commands through the robot's joints and end effector. The whole thing is trained using imitation learning in simulation, then fine-tuned with real-world data to close the sim-to-real gap."

---

## G. New Terms Introduced Today

| Term | Definition | Status |
|------|-----------|--------|
| NeRF | Neural Radiance Field: reconstructs 3D scenes from 2D photos. Slow but high quality | New |
| Gaussian Splatting | Faster alternative to NeRFs for real-time 3D reconstruction (100+ FPS vs 5 FPS) | New |
| Reinforcement Learning (RL) | Learning by trial and error with rewards. Needs millions of trials | New |
| Imitation Learning | Learning by watching human demonstrations. More data-efficient than RL | New |
| Teleoperation | Human remotely controlling a robot. Primary data collection method for VLA training | New |
| End Effector | The tool at the end of a robot arm (gripper, hand, welding torch) | New |
| Sim-to-Real Gap | Performance drop when moving from simulation to real robot | New |
| Digital Twin | Virtual replica of a physical system, updated in real-time | New |
| RaaS | Robots-as-a-Service: subscription model for robot access | New |
| Embodiment Gap | Policy trained on one robot body may not transfer to another | New |
| Morphology | Physical form/shape of a robot (humanoid, quadruped, wheeled) | New |
| Diffusion Policy | Using diffusion models to generate smooth robot action sequences | Bonus |
| Dual-System Architecture | VLA design: System 2 (slow reasoning) + System 1 (fast motor control) | Bonus |
| Cross-Embodiment Transfer | Training one model on multiple robot types for generalization | Bonus |

---

## H. Suggested Follow-Up Questions

1. **"If I were evaluating a robot company's tech stack, what questions would I ask the CTO?"** Practice asking: What's your perception pipeline? How do you collect training data? What's your sim-to-real transfer rate? What end effectors do you support? How many DoF?

2. **"Which Tier 2 term represents the biggest unsolved problem and therefore the biggest investment opportunity?"** Hint: sim-to-real gap, embodiment gap, and manipulation are all billion-dollar problems.

3. **"How does RaaS unit economics compare to traditional SaaS?"** Apply your Rule-of-40 framework. What's the gross margin on a RaaS robot? What's the churn rate? How does hardware maintenance affect LTV/CAC?

---

*Session generated: 2026-03-18 (post-live-session). Web research current as of March 2026. Learner: read this before your next live session, then launch /learn.*
