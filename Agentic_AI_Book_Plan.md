# Building Agentic AI
## From Goals to Autonomous Systems

**Series:** Hands-On AI Science
**Authors:** Alexander Apartsin & Yehudit Aperstein
**Edition:** First Edition, 2026

---

# Series Positioning

The Hands-On AI Science series develops AI from perception to action to innovation:

1. Building Language AI: From Tokens to Agents
2. Building Vision AI: From Pixels to Generative Models
3. Building Temporal AI
4. Building Scalable AI
5. Building Embodied AI
6. **Building Agentic AI: From Goals to Autonomous Systems**
7. Building Discovery AI

## Role of This Book

Language AI teaches models to communicate. Vision AI teaches models to perceive. Agentic AI teaches models to pursue goals.

The central question: how can an AI system perceive, reason, plan, decide, act, collaborate, learn, and improve while pursuing long-term objectives?

---

# Book Description

Building Agentic AI is a practitioner's guide to autonomous intelligent systems in 39 chapters across four parts: foundations of agency, learning agents, LLM-powered agents, and multi-agent and deployed systems. Every core idea is built from first principles and then shown with the modern library that turns it into practical code.

The book unifies classical AI planning and decision theory, reinforcement learning, LLM-based agent frameworks, multi-agent systems, and production deployment. It serves two audiences simultaneously: graduate students and researchers (formal theory, complexity analysis, benchmark reproduction, open-problem pointers) and software engineers (working Python recipes, canonical stack, AI-assisted extension patterns).

A recurring narrative runs through all four parts: concepts introduced in classical form return in learned form. The utility function (Ch 3) becomes the reward signal (Ch 7); the search tree (Ch 4) becomes Monte Carlo Tree Search and then chain-of-thought reasoning (Ch 18); the knowledge base (Ch 5) becomes the retrieval-augmented memory (Ch 20); tool use in classical planners (Ch 4) returns in LLM function calling (Ch 19) and then in software engineering agents (Ch 31). Readers are invited to follow these arcs through the text.

## Target Audience

Software engineers and graduate students with Python experience and basic probability and linear algebra. Prior knowledge of deep learning (at the level of Building Language AI or Building Vision AI) is assumed for Parts III and IV; the appendices cover any remaining prerequisites.

## Canonical Software Stack

Every implementation recipe uses this stack. Alternative libraries are shown where instructive.

| Layer | Primary | Alternatives shown |
|---|---|---|
| LLM API | Anthropic Claude (claude-opus-4-8) | OpenAI, Gemini |
| Agent framework | LangGraph | AutoGen, CrewAI, smolagents |
| Tool use / MCP | Anthropic MCP SDK | OpenAI function calling |
| Memory | mem0, Qdrant, Chroma | Pinecone, Weaviate |
| Reinforcement learning | Stable-Baselines3, CleanRL | RLlib |
| Robotics simulation | Isaac Lab, MuJoCo, Gymnasium | PyBullet |
| Evaluation | AgentBench, GAIA, SWE-bench | BrowserGym, WebArena |
| Observability | LangSmith | W&B Weave, Phoenix Arize |
| Orchestration | Modal, Prefect | Ray, Celery |

## The Right Tool Principle

Every section that teaches a concept from scratch includes a **Library Shortcut** callout showing the same task solved in a few lines with a modern library. The line-count reduction is stated explicitly and names what the library handles internally.

## Vibe Coding Contract

Every recipe ends with an `# EXTEND:` block describing next steps in natural language. The companion GitHub repository contains one folder per chapter with a runnable `main.py` and `AGENT_PROMPT.md` — the prompt you would give Claude Code to extend it. Chapter 31 (Software Engineering Agents) uses the book's own codebase as its working example.

## Per-Chapter Template

Every chapter follows a five-beat structure:

1. **Theory** — formal definitions, key theorems, derivations
2. **Models** — architecture diagrams, pseudocode, complexity analysis
3. **Implementation** — working Python recipe (~50-100 lines) using the canonical stack
4. **Benchmarks** — standard evaluation datasets, published SOTA numbers in a table, reproduction steps
5. **Frontier** — 3-5 open problems with paper pointers

---

# The Four-Part Arc

| Part | Chapters | Focus |
|---|---|---|
| I: Foundations of Agency | Ch 0-6 | What agents are, how they are built, how they reason classically |
| II: Learning Agents | Ch 7-15 | MDPs, reinforcement learning, memory, lifelong and meta-learning |
| III: LLM-Powered Agents | Ch 16-26 | LLM agents, reasoning, tools, memory, RAG, autonomous tasks, computer use |
| IV: Multi-Agent and Deployed Systems | Ch 27-38 | Multi-agent systems, swarms, robotics, software engineering, safety, frontier |

---

# Part I: Foundations of Agency

## Chapter 0: The Agent Development Stack

Setup and tooling: Python environment, Gymnasium, Anthropic SDK, LangGraph, MCP SDK, Qdrant, Stable-Baselines3, LangSmith. A minimal agent loop end-to-end by the end of the chapter. Directory structure and conventions used throughout the book.

`module-00-agent-development-stack`

## Chapter 1: What Is an Agent?

**Theory**: PEAS framework (Performance, Environment, Actuators, Sensors), agent-environment loop, rationality, task environment taxonomy (fully/partially observable, deterministic/stochastic, episodic/sequential, static/dynamic, discrete/continuous, single/multi-agent). Formal definition: A = (S, A, T, R, O, Ω, γ). **Models**: reflex agent, model-based agent, goal-based agent, utility-based agent, learning agent. **Implementation**: five agent types on a grid world (Gymnasium). **Benchmarks**: BabyAI, MiniGrid. **Frontier**: general agent formalization, open-endedness.

`module-01-what-is-an-agent`

## Chapter 2: Agent Architectures

**Theory**: reactive architectures, deliberative architectures, hybrid architectures, BDI (Belief-Desire-Intention) model, sense-plan-act loop, subsumption architecture, three-layer architectures. **Models**: BDI cycle diagram, subsumption hierarchy. **Implementation**: BDI agent with belief and intention queues. **Benchmarks**: NetLogo agent-based models. **Frontier**: neurosymbolic hybrid architectures.

`module-02-agent-architectures`

## Chapter 3: Utility and Decision Theory

**Theory**: expected utility, von Neumann-Morgenstern axioms, risk attitudes, prospect theory, multi-attribute utility, preferences under uncertainty. **Models**: decision trees, influence diagrams. **Implementation**: decision-theoretic agent for resource allocation. **Benchmarks**: sequential investment tasks. **Frontier**: bounded rationality, satisficing agents. _The utility function introduced here becomes the reward signal in Chapter 7._

`module-03-utility-decision-theory`

## Chapter 4: Planning as Goal Pursuit

**Theory**: classical planning (STRIPS, PDDL), state-space search, heuristic planning (A\*, relaxation heuristics), partial-order planning, temporal planning, hierarchical task networks (HTN). **Models**: forward/backward search, task decomposition tree. **Implementation**: PDDL planner with unified-planning library. **Benchmarks**: IPC competition domains. **Frontier**: learned heuristics, neural planning. _The search tree returns as MCTS in Chapter 8 and chain-of-thought in Chapter 18._

`module-04-planning-goal-pursuit`

## Chapter 5: Knowledge and Reasoning in Agents

**Theory**: propositional and first-order logic, knowledge bases, inference (resolution, forward/backward chaining), ontologies, uncertainty reasoning (Bayesian networks, Dempster-Shafer theory). **Models**: knowledge graph + inference engine. **Implementation**: agent with OWL ontology and SPARQL reasoning. **Benchmarks**: OpenBookQA, ARC. **Frontier**: neurosymbolic reasoning, knowledge-grounded LLMs. _The knowledge base returns as agentic RAG in Chapter 20._

`module-05-knowledge-reasoning`

## Chapter 6: Tools of the Trade: Classical Agent Stack

Comparative guide to classical agent libraries: unified-planning, py-pddl, owlready2, pgmpy, networkx, Mesa. Installation, hello-world for each, decision guide. When to reach for classical planning versus learned approaches. Code templates carried forward through the book.

`module-06-tools-classical-agent-stack`

---

# Part II: Learning Agents

## Chapter 7: Markov Decision Processes

**Theory**: MDP formalism (S, A, T, R, γ), Bellman equations, value functions V\* and Q\*, policy evaluation, policy iteration, value iteration, POMDP extension. Convergence proofs. **Models**: tabular MDP, POMDP belief-state formulation. **Implementation**: policy iteration on FrozenLake (Gymnasium). **Benchmarks**: classic control suite, MiniGrid. **Frontier**: constrained MDPs, risk-sensitive MDPs. _The reward function is the operationalization of the utility function from Chapter 3._

`module-07-markov-decision-processes`

## Chapter 8: Reinforcement Learning Foundations

**Theory**: exploration-exploitation tradeoff, multi-armed bandits (UCB, Thompson sampling), Monte Carlo methods, temporal-difference learning (TD(0), TD(λ)), Q-learning, SARSA, convergence guarantees. **Models**: tabular Q-table, TD update diagram. **Implementation**: Q-learning on Taxi-v3. **Benchmarks**: Atari-57 (tabular baselines). **Frontier**: reward learning, inverse RL, preference-based RL.

`module-08-reinforcement-learning-foundations`

## Chapter 9: Deep Reinforcement Learning

**Theory**: DQN and extensions (Double DQN, Dueling, Prioritized Experience Replay), policy gradient theorem, REINFORCE, actor-critic, PPO, SAC, TD3. Stability and convergence in deep RL. **Models**: deep Q-network architecture, actor-critic network. **Implementation**: PPO agent on LunarLander (CleanRL). **Benchmarks**: Atari-57, MuJoCo continuous control. **Frontier**: offline RL, decision transformers, RL from human feedback.

`module-09-deep-reinforcement-learning`

## Chapter 10: Model-Based Agents

**Theory**: world models, Dyna architecture, MBPO, Dreamer, latent dynamics models, planning in latent space, imagination rollouts. **Models**: RSSM (Recurrent State-Space Model), trajectory optimization. **Implementation**: Dreamer-v3 on DMControl suite. **Benchmarks**: DMControl, PlaNet benchmark. **Frontier**: foundation world models, generative simulators.

`module-10-model-based-agents`

## Chapter 11: Hierarchical Agents

**Theory**: options framework, semi-MDPs, feudal RL, goal-conditioned RL, temporal abstraction, subgoal discovery, HIRO, HAC. **Models**: option-critic architecture, feudal hierarchy diagram. **Implementation**: HIRO on AntMaze (Gymnasium-Robotics). **Benchmarks**: AntMaze, BabyAI BossLevel. **Frontier**: automatic hierarchy discovery, language-conditioned hierarchies.

`module-11-hierarchical-agents`

## Chapter 12: Agent Memory Systems

**Theory**: taxonomy of agent memory (sensory, working, episodic, semantic, procedural), memory consolidation, indexing and retrieval (sparse, dense, hybrid), forgetting and interference, the complementary learning systems hypothesis. **Models**: external memory store with retrieval-augmented generation. **Implementation**: episodic memory agent with Qdrant and mem0. **Benchmarks**: MemGPT eval, LongMemEval. **Frontier**: continual memory without catastrophic forgetting. _Memory returns as agentic RAG in Chapter 20._

`module-12-agent-memory-systems`

## Chapter 13: Lifelong and Meta-Learning Agents

**Theory**: catastrophic forgetting, continual learning methods (EWC, PackNet, progressive networks, replay), task-incremental vs. class-incremental learning. Meta-learning: MAML, Reptile, few-shot learning, in-context learning as meta-learning. **Models**: EWC-regularized network, MAML inner/outer loop. **Implementation**: continual RL agent (Avalanche); MAML on few-shot RL (learn2learn). **Benchmarks**: Continual World, Meta-Dataset. **Frontier**: in-context RL, foundation model fine-tuning without forgetting.

`module-13-lifelong-meta-learning`

## Chapter 14: Self-Reflective Agents

**Theory**: metacognition in agents, introspective monitoring, uncertainty estimation, calibration, hallucination detection, self-assessment loops, Reflexion architecture. **Models**: self-critique and revision loop. **Implementation**: Reflexion agent on HotpotQA (LangGraph). **Benchmarks**: HotpotQA, FEVER. **Frontier**: calibrated self-knowledge in LLMs, process reward models.

`module-14-self-reflective-agents`

## Chapter 15: Tools of the Trade: Learning Agent Stack

Comparative guide: Gymnasium, Stable-Baselines3, CleanRL, RLlib, Avalanche, learn2learn, Dreamer-v3. Training loop templates, experiment tracking with W&B, hyperparameter tuning. When to use model-free vs. model-based vs. hierarchical approaches.

`module-15-tools-learning-agent-stack`

---

# Part III: LLM-Powered Agents

## Chapter 16: Foundations of LLM Agents

**Theory**: emergent capabilities of LLMs, in-context learning, instruction following, LLM as policy, tokenization and context windows, system prompt architecture. Formal view: LLM agent as a conditional distribution over actions. **Models**: transformer review, attention patterns for reasoning. **Implementation**: minimal agent loop with Anthropic SDK. **Benchmarks**: MMLU, HellaSwag, BIG-Bench Hard. **Frontier**: long-context agents (1M+ tokens), multimodal foundations.

`module-16-foundations-llm-agents`

## Chapter 17: Prompt Engineering for Agents

**Theory**: zero-shot and few-shot prompting, chain-of-thought (CoT), scratchpad reasoning, ReAct (Reason + Act), Tree of Thoughts (ToT), Reflexion, self-consistency, program-of-thought, automatic prompt optimization (DSPy, TextGrad). Formal analysis of why CoT improves reasoning. **Models**: ToT search tree, ReAct action-observation loop. **Implementation**: ReAct agent on HotpotQA; ToT on 24-game puzzle. **Benchmarks**: GSM8K, ARC-Challenge. **Frontier**: DSPy-style learned prompts, TextGrad differentiable prompt optimization.

`module-17-prompt-engineering-agents`

## Chapter 18: Reasoning Agents

**Theory**: deductive, inductive, abductive reasoning in LLMs; process reward models vs. outcome reward models; test-time compute scaling (o1/o3-style extended thinking); formal verification of reasoning chains; MCTS over reasoning steps. **Models**: internal chain-of-thought, process reward model, MCTS reasoning tree. **Implementation**: extended-thinking reasoning agent (Claude API) on MATH. **Benchmarks**: MATH, GPQA, ARC-Challenge, OlympiadBench. **Frontier**: verified generation, neurosymbolic reasoning, superposition of reasoning chains.

`module-18-reasoning-agents`

## Chapter 19: Tool-Using Agents

**Theory**: tool use as grounding, tool selection policies, API calling, function calling protocols, Model Context Protocol (MCP) architecture, parallel tool use, error recovery in tool loops, tool invention. **Models**: tool-call/tool-response loop, MCP server-client diagram. **Implementation**: multi-tool agent with MCP server (web search + code execution + file I/O). **Benchmarks**: ToolBench, API-Bank, ToolAlpaca. **Frontier**: self-extending toolsets, tool synthesis. _Tool use introduced in planning (Ch 4) returns here at LLM scale._

`module-19-tool-using-agents`

## Chapter 20: Memory-Augmented Agents and Agentic RAG

**Theory**: retrieval-augmented generation (RAG), dense vs. sparse retrieval, hybrid search. Agentic RAG: query rewriting, iterative retrieval, multi-hop reasoning, confidence-gated termination, retriever-as-policy. Knowledge graph augmentation. **Models**: RAG pipeline, multi-hop retrieval loop, subquery decomposition tree. **Implementation**: multi-hop agentic RAG (LangGraph + Qdrant + BGE embeddings) on 2WikiMultiHopQA. **Benchmarks**: BEIR, RGB, FRAMES, 2WikiMultiHopQA. **Frontier**: multi-modal RAG, learned retrieval policies. _The knowledge base from Chapter 5 and memory systems from Chapter 12 converge here._

`module-20-memory-augmented-agentic-rag`

## Chapter 21: Autonomous Task Agents

**Theory**: task decomposition, plan-and-execute architectures, ReAct vs. plan-and-solve, long-horizon task completion, failure recovery, agent scratchpads, open-ended task formulation. **Models**: outer planner + inner executor loop. **Implementation**: autonomous research agent (web search + summarization + structured report). **Benchmarks**: GAIA, AgentBench, τ-bench. **Frontier**: open-ended long-horizon benchmarks, persistent agents.

`module-21-autonomous-task-agents`

## Chapter 22: Computer-Use and GUI Agents

**Theory**: pixel-level observation spaces, OS-level action spaces (clicks, keystrokes, scrolls), GUI grounding (element detection, OCR, layout parsing), web navigation, accessibility tree vs. screenshot approaches, grounding models (SoM, UGround). **Models**: dual-path architecture (vision + accessibility tree). **Implementation**: GUI agent with Claude computer-use API on a file management task. **Benchmarks**: OSWorld, ScreenSpot, WebArena, Mind2Web. **Frontier**: efficient GUI grounding, robust cross-OS generalization, GUI world models.

`module-22-computer-use-gui-agents`

## Chapter 23: Self-Improving Agents

**Theory**: recursive self-improvement, bootstrapping, Constitutional AI, RLHF, DPO, STaR (self-taught reasoner), iterative self-play, automated prompt optimization. Safety constraints on self-modification. **Models**: self-distillation pipeline, STaR loop. **Implementation**: STaR-style self-improvement on GSM8K; Constitutional AI self-critique loop (Claude API). **Benchmarks**: GSM8K improvement curve across iterations. **Frontier**: open-ended self-improvement, safety certificates for self-modifying systems.

`module-23-self-improving-agents`

## Chapter 24: Multi-Modal Agents

**Theory**: vision-language models (VLMs) as policies, audio-language agents, multi-modal tool use, cross-modal reasoning, tokenizing non-text modalities, co-training on heterogeneous data. **Models**: VLM agent architecture (visual encoder + LLM + action head). **Implementation**: multi-modal agent that interprets screenshots, reads PDFs, and calls tools. **Benchmarks**: MMBench, MMMU, MathVista. **Frontier**: universal multi-modal agents, video-language agents.

`module-24-multimodal-agents`

## Chapter 25: Agent Evaluation

**Theory**: evaluation methodology for autonomous agents (static vs. dynamic, single-turn vs. multi-turn, human vs. automated), benchmark contamination, calibration, LLM-as-judge, process vs. outcome evaluation, evaluation validity. **Models**: automated evaluation pipeline, judge calibration. **Implementation**: agent evaluation harness (AgentBench + LLM judge + cost tracker). **Benchmarks**: GAIA, AgentBench, τ-bench, WebArena. **Frontier**: evaluation of open-ended creativity, long-horizon autonomy, emergent capabilities.

`module-25-agent-evaluation`

## Chapter 26: Tools of the Trade: LLM Agent Stack

Comparative guide: LangGraph, AutoGen/AG2, CrewAI, smolagents, OpenAI Agents SDK, Anthropic Claude Code SDK, Semantic Kernel. LangSmith for tracing and evaluation. Prompt management, versioning, and testing. Decision guide for framework selection.

`module-26-tools-llm-agent-stack`

---

# Part IV: Multi-Agent and Deployed Systems

## Chapter 27: Foundations of Multi-Agent Systems

**Theory**: game theory basics, Nash equilibrium, Pareto optimality, mechanism design, communication protocols, shared vs. competitive environments, Dec-POMDP formulation. **Models**: normal-form game, extensive-form game, Dec-POMDP diagram. **Implementation**: two-agent negotiation game (LangGraph). **Benchmarks**: matrix game suites. **Frontier**: equilibrium learning in large games, LLM-based mechanism design.

`module-27-foundations-multi-agent-systems`

## Chapter 28: Coordination and Negotiation

**Theory**: contract nets, auction mechanisms (Vickrey, combinatorial), coalition formation, distributed constraint optimization (DCOP), shared mental models, debate and critique protocols in LLM multi-agent systems. **Models**: contract-net protocol, combinatorial auction. **Implementation**: multi-agent task allocation via auction (LangGraph). **Benchmarks**: RoboCup, Overcooked, multi-agent debate benchmarks. **Frontier**: LLM-based negotiation, emergent communication.

`module-28-coordination-negotiation`

## Chapter 29: Multi-Agent Reinforcement Learning

**Theory**: MARL formulation, centralized training with decentralized execution (CTDE), QMIX, MADDPG, MAPPO, independent vs. joint learning, non-stationarity, credit assignment. **Models**: QMIX mixing network, MADDPG centralized critic. **Implementation**: QMIX on SMAC (PyMARL2). **Benchmarks**: SMAC, Google Research Football, Overcooked. **Frontier**: MARL at scale, emergent language, offline MARL.

`module-29-multi-agent-reinforcement-learning`

## Chapter 30: Swarm Intelligence and Emergence

**Theory**: stigmergy, ant colony optimization, particle swarm optimization, boid rules, self-organization, phase transitions in collective behavior. Emergence as a formal concept: synergy and redundancy in information theory. Collective problem solving, social learning, cultural evolution. **Models**: ACO pheromone equations, PSO velocity update, agent-based model. **Implementation**: PSO on optimization benchmarks + boid simulation (Mesa). **Benchmarks**: CEC optimization suite. **Frontier**: swarm robotics, LLM population emergence.

`module-30-swarm-intelligence-emergence`

## Chapter 31: Software Engineering Agents

**Theory**: code generation as search, program synthesis, test-driven development by agents, fault localization, automated refactoring, repository-level reasoning, multi-file context, CodeAct action space. **Models**: SWE-agent architecture, repo-level context management. **Implementation**: SWE-bench task agent with Claude + MCP (bash + editor + file tools). **Benchmarks**: SWE-bench Verified, SWE-bench Lite, HumanEval, MBPP. **Frontier**: fully autonomous software development, multi-agent coding teams. _The book's own codebase is the working example._

`module-31-software-engineering-agents`

## Chapter 32: Research and Scientific Agents

**Theory**: scientific method as agent loop, hypothesis generation, experiment design, result interpretation, literature search automation, novelty detection, AI Scientist architecture, FunSearch. **Models**: research loop (hypothesize → experiment → analyze → revise → write). **Implementation**: autonomous literature review and gap analysis agent (Claude + Semantic Scholar API). **Benchmarks**: ScienceWorld, MLAgentBench, DiscoveryBench. **Frontier**: AI co-scientists, automated theorem proving, self-directed research agents.

`module-32-research-scientific-agents`

## Chapter 33: AI Teams and Orchestration

**Theory**: role specialization in LLM teams, debate and critique protocols, majority voting, mixture-of-agents, orchestrator-worker patterns, inter-agent trust, emergent specialization. **Models**: orchestrator-subagent graph. **Implementation**: multi-agent software company (planner + coder + reviewer + tester) with AutoGen. **Benchmarks**: ChatDev benchmark, AgentVerse, MetaGPT eval. **Frontier**: dynamic role assignment, self-organizing agent teams.

`module-33-ai-teams-orchestration`

## Chapter 34: Observability, Tracing, and Cost Engineering

**Theory**: agent execution as a DAG, span-based tracing, token accounting, latency attribution, non-determinism and reproducibility. Token economy of agents (input/output/cache pricing), model routing by difficulty, speculative execution, prompt compression, KV-cache reuse, latency-quality Pareto frontier. **Models**: trace waterfall, difficulty classifier for model routing. **Implementation**: full LangSmith tracing on a multi-step agent; tiered model router (haiku for triage, sonnet for reasoning, opus for synthesis) with cost dashboard. **Benchmarks**: RouteLLM eval. **Frontier**: causal attribution in long traces, learned routing policies.

`module-34-observability-tracing-cost-engineering`

## Chapter 35: Embodied and Robotics Agents

**Theory**: kinematics and dynamics, motion planning (RRT, trajectory optimization), manipulation primitives, grasping, sim-to-real gap, domain randomization, VLA (vision-language-action) models, RT-series, π0. **Models**: VLA architecture (visual encoder + LLM + action head), occupancy map. **Implementation**: language-conditioned policy with OpenVLA on LIBERO. **Benchmarks**: Meta-World, LIBERO, BridgeData V2, FurnitureBench. **Frontier**: generalist robot foundation models, dexterous manipulation.

`module-35-embodied-robotics-agents`

## Chapter 36: Agent Safety and Red-Teaming

**Theory**: threat model for agentic systems (prompt injection, goal hijacking, jailbreaks in tool outputs, reward hacking, specification gaming), adversarial robustness, alignment problem, corrigibility, interruptibility, Constitutional AI, RLHF and its limits, scalable oversight, debate. **Models**: injection attack taxonomy, RLHF pipeline, Constitutional AI critique-revision loop. **Implementation**: prompt-injection attack and detection on a tool-using agent; Constitutional AI self-critique loop. **Benchmarks**: AgentHarm, BIPIA, HarmBench, SafetyBench. **Frontier**: formal verification of agent safety, superalignment.

`module-36-agent-safety-red-teaming`

## Chapter 37: Governance and Alignment

**Theory**: AI governance frameworks (EU AI Act, NIST AI RMF), multi-stakeholder alignment, human oversight requirements, liability in autonomous systems, auditing and certification, principal-agent problems in AI organizations, international coordination. **Models**: governance framework taxonomy, oversight mechanism layers. **Implementation**: policy enforcement layer (rate limits, action blocklists, human-in-the-loop gates) for an agent deployment. **Benchmarks**: governance compliance checklists. **Frontier**: global AI governance for agentic systems, constitutional AI at scale.

`module-37-governance-alignment`

## Chapter 38: Tools of the Trade: Deployed Agent Stack

Production deployment guide: Modal for serverless agent execution, Prefect for workflow orchestration, LangSmith for observability, Qdrant for vector memory, Docker + API gateway for agent services. Scaling, reliability, cost control, and monitoring patterns. Putting it all together: architecture of a production agentic system.

`module-38-tools-deployed-agent-stack`

---

# Appendices

## Appendix A: Mathematical Foundations

Probability and Bayesian inference; linear algebra for policy representations; dynamic programming; graph theory for agent interaction; information theory; convex optimization. Self-contained reference, used throughout the book.

## Appendix B: Agent Framework Ecosystem

Comparative guide to LangChain, LangGraph, AutoGen/AG2, CrewAI, Semantic Kernel, Haystack, OpenAI Agents SDK, Anthropic Claude Code SDK, smolagents, Google ADK. Installation, hello-world, tradeoffs.

## Appendix C: Simulation and Environment Platforms

Setup and usage for Gymnasium, Isaac Lab, MuJoCo, CARLA, NetLogo, Mesa, PettingZoo, BrowserGym. Hardware requirements and cloud alternatives (Modal, Vast.ai).

## Appendix D: Research Frontiers Index

Living table mapping each chapter's open problems to ArXiv IDs, benchmarks, and key research groups. Researcher fast-reference companion.

## Appendix E: Capstone Projects

Each capstone includes a project brief, architecture diagram, starter code scaffold, grading rubric, and `AGENT_PROMPT.md` for AI-assisted extension.

1. Personal AI Assistant with Long-Term Memory
2. Autonomous Research Agent (literature review to draft)
3. Coding Agent (SWE-bench task solver)
4. Multi-Agent Software Company
5. Swarm Intelligence Simulator
6. Autonomous Trading Agent
7. Robotics Navigation Agent (Isaac Lab)
8. Computer-Use Automation Agent
9. Self-Improving Reasoning Agent
10. Autonomous Scientific Research Team

---

# Style Rules (non-negotiable)

1. Never use em-dashes or double-dashes anywhere. Use commas, semicolons, colons, parentheses, or separate sentences.
2. Book hierarchy terminology: Part > Chapter > Section. Never use "course", "lecture", or "module" in reader-facing prose (directory names keep `module-NN` for tooling compatibility).
3. Every figure, table, code block, and callout must be referenced in surrounding prose.
4. Every chapter index ends with a "What's Next" section linking the next chapter.
5. No placeholder text of any kind. Every section ships complete or is not created.

---

# Epigraph Personas (agent-flavored)

- "A Utility Function That Forgot to Include Safety"
- "A Policy That Converged to the Wrong Optimum"
- "A Reward Signal With Unintended Consequences"
- "A Planning System That Ran Out of Time"
- "A Multi-Agent System Where Nobody Coordinated"
- "A Memory Module That Remembered Everything Except What Mattered"
- "A Tool-Calling Agent on Its Fourteenth Retry"
- "A Hierarchical Agent Whose Subgoals Escaped"
- "An LLM Agent That Hallucinated Its Own Tool Output"
- "A Swarm Intelligence That Agreed Unanimously on the Wrong Answer"
- "A Self-Improving Agent Whose Improvements Were Not Improvements"
- "A Reasoning Agent That Reasoned Itself Into a Corner"
- "A Corrigible Agent That Was a Little Too Corrigible"
- "A Knowledge Base With Outdated Beliefs About the World"
- "An Exploration Policy That Explored Everything Except the Solution"
