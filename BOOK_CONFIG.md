# Book Configuration

This file contains all book-specific details for the textbook production pipeline
(the `book-skills` 42-agent team). The pipeline skill and its agent definitions are
generic; this file is the only place where content specific to THIS book lives.

## Book Identity

- **Title**: Building Agentic AI: From Goals to Autonomous Systems
- **Subtitle**: Deep Theory and Production Code for Agent Foundations, Reinforcement Learning, LLM Agents, and Autonomous Systems
- **Series**: Hands-On AI Science
- **Authors**: Alexander Apartsin & Yehudit Aperstein
- **Target Audience**: Engineers and researchers with Python experience and basic probability and linear algebra who want rigorous theory and production-ready code in equal measure. Prior deep learning knowledge (at the level of Building Language AI or Building Vision AI) assumed for Parts III and IV.
- **Output Format**: HTML chapter files linking to the shared stylesheet `styles/book.css`
- **Author/Footer line**: `© 2026 Alexander Apartsin · <a href="../../toc.html">Contents</a>` (adjust relative depth per file location)
- **Edition line for footers**: `Building Agentic AI: From Goals to Autonomous Systems, First Edition`

## The Four-Part Arc

1. **Part I: Foundations of Agency** (Ch 0-6): agent loop, architectures, decision theory, planning, knowledge, classical stack.
2. **Part II: Learning Agents** (Ch 7-15): MDPs, reinforcement learning, deep RL, model-based, hierarchical, memory, lifelong and meta-learning, self-reflection.
3. **Part III: LLM-Powered Agents** (Ch 16-26): LLM foundations, prompt engineering, reasoning, tool use, memory/RAG, autonomous tasks, computer use, self-improvement, multi-modal, evaluation.
4. **Part IV: Multi-Agent and Deployed Systems** (Ch 27-38): multi-agent systems, coordination, MARL, swarms, software engineering agents, research agents, AI teams, observability and cost, embodied agents, safety, governance, production stack.

A recurring narrative thread: concepts introduced in classical form return in learned form. The utility function (Ch 3) becomes the reward signal (Ch 7). The search tree (Ch 4) becomes MCTS (Ch 8) and chain-of-thought reasoning (Ch 18). The knowledge base (Ch 5) becomes agentic RAG (Ch 20). Tool use in planners (Ch 4) returns in LLM function calling (Ch 19) and software engineering agents (Ch 31). Agents should exploit these arcs for cross-references.

## Visual Style

- **Stylesheet**: every HTML file links `styles/book.css` (full callout system). Code highlighting uses Prism (vendor). Math uses KaTeX (vendor).
- **Illustrations**: inline SVG diagrams with `<figure class="diagram">` and numbered `<figcaption>`.
- **Application Examples**: `.callout.practical-example` boxes, realistic industry mini-stories.
- **Library Shortcut**: `.callout.library-shortcut` after every from-scratch implementation, showing the same task in a few lines with the canonical library. State the line-count reduction and name what the library handles.
- **Bibliographies**: card layout on each chapter index, 8 to 15 hyperlinked annotated entries.
- **Epigraphs**: humorous quotes attributed to a fictional AI agent persona, format "A [Adjective] [Agent Role]".

### Epigraph Personas (agent-flavored)

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

## HTML Head Boilerplate

Section files (`part-*/module-*/section-N.M.html`) use this head:

```html
<meta charset="utf-8"/>
<meta content="width=device-width, initial-scale=1.0" name="viewport"/>
<meta content="Section N.M: Title. One-sentence description." name="description"/>
<title>Section N.M: Title | Building Agentic AI</title>
<link href="../../styles/book.css" rel="stylesheet"/>
<link href="../../styles/pygments.css" rel="stylesheet"/>
<link href="../../vendor/katex/katex.min.css" rel="stylesheet"/>
<script defer="" src="../../vendor/katex/katex.min.js"></script>
<script defer="" onload="renderMathInElement(document.body, {
  delimiters: [
  {left: '$$', right: '$$', display: true},
  {left: '$', right: '$', display: false}
  ],
  throwOnError: false
  });" src="../../vendor/katex/contrib/auto-render.min.js"></script>
<link href="../../vendor/prism/prism-theme.css" rel="stylesheet"/>
<script defer="" src="../../vendor/prism/prism-bundle.min.js"></script>
<script defer="" src="../../scripts/book.js"></script>
```

Every page carries the standard header:

```html
<header class="chapter-header">
<nav class="header-nav">
<a class="book-title-link" href="../../index.html">Building Agentic AI: From Goals to Autonomous Systems</a>
<a class="toc-link" href="../../toc.html" title="Table of Contents"><span class="toc-icon">&#9776;</span> Contents</a>
</nav>
<div class="part-label"><a href="../index.html">Part [ROMAN]: [PART TITLE]</a></div>
<div class="chapter-label"><a href="index.html">Chapter [N]: [CHAPTER TITLE]</a></div>
<h1>[SECTION TITLE]</h1>
</header>
```

## Chapter Map

Module directory numbers equal global chapter numbers (0 to 38). The canonical
section-level breakdown lives in `toc.html`; this map is the chapter-level source of truth.

```
Part 1: Foundations of Agency (part-1-foundations-of-agency/)
  Ch 0: The Agent Development Stack              module-00-agent-development-stack
  Ch 1: What Is an Agent?                        module-01-what-is-an-agent
  Ch 2: Agent Architectures                      module-02-agent-architectures
  Ch 3: Utility and Decision Theory              module-03-utility-decision-theory
  Ch 4: Planning as Goal Pursuit                 module-04-planning-goal-pursuit
  Ch 5: Knowledge and Reasoning in Agents        module-05-knowledge-reasoning
  Ch 6: Tools of the Trade: Classical Agent Stack  module-06-tools-classical-agent-stack

Part 2: Learning Agents (part-2-learning-agents/)
  Ch 7:  Markov Decision Processes               module-07-markov-decision-processes
  Ch 8:  Reinforcement Learning Foundations      module-08-reinforcement-learning-foundations
  Ch 9:  Deep Reinforcement Learning             module-09-deep-reinforcement-learning
  Ch 10: Model-Based Agents                      module-10-model-based-agents
  Ch 11: Hierarchical Agents                     module-11-hierarchical-agents
  Ch 12: Agent Memory Systems                    module-12-agent-memory-systems
  Ch 13: Lifelong and Meta-Learning Agents       module-13-lifelong-meta-learning
  Ch 14: Self-Reflective Agents                  module-14-self-reflective-agents
  Ch 15: Tools of the Trade: Learning Agent Stack  module-15-tools-learning-agent-stack

Part 3: LLM-Powered Agents (part-3-llm-powered-agents/)
  Ch 16: Foundations of LLM Agents              module-16-foundations-llm-agents
  Ch 17: Prompt Engineering for Agents           module-17-prompt-engineering-agents
  Ch 18: Reasoning Agents                        module-18-reasoning-agents
  Ch 19: Tool-Using Agents                       module-19-tool-using-agents
  Ch 20: Memory-Augmented Agents and Agentic RAG module-20-memory-augmented-agentic-rag
  Ch 21: Autonomous Task Agents                  module-21-autonomous-task-agents
  Ch 22: Computer-Use and GUI Agents             module-22-computer-use-gui-agents
  Ch 23: Self-Improving Agents                   module-23-self-improving-agents
  Ch 24: Multi-Modal Agents                      module-24-multimodal-agents
  Ch 25: Agent Evaluation                        module-25-agent-evaluation
  Ch 26: Tools of the Trade: LLM Agent Stack     module-26-tools-llm-agent-stack

Part 4: Multi-Agent and Deployed Systems (part-4-multi-agent-deployed-systems/)
  Ch 27: Foundations of Multi-Agent Systems      module-27-foundations-multi-agent-systems
  Ch 28: Coordination and Negotiation            module-28-coordination-negotiation
  Ch 29: Multi-Agent Reinforcement Learning      module-29-multi-agent-reinforcement-learning
  Ch 30: Swarm Intelligence and Emergence        module-30-swarm-intelligence-emergence
  Ch 31: Software Engineering Agents             module-31-software-engineering-agents
  Ch 32: Research and Scientific Agents          module-32-research-scientific-agents
  Ch 33: AI Teams and Orchestration              module-33-ai-teams-orchestration
  Ch 34: Observability, Tracing, and Cost Engineering  module-34-observability-tracing-cost-engineering
  Ch 35: Embodied and Robotics Agents            module-35-embodied-robotics-agents
  Ch 36: Agent Safety and Red-Teaming            module-36-agent-safety-red-teaming
  Ch 37: Governance and Alignment                module-37-governance-alignment
  Ch 38: Tools of the Trade: Deployed Agent Stack  module-38-tools-deployed-agent-stack
```

Front matter lives in `front-matter/`, appendices in `appendices/` (A-E), capstones in `capstone/`. See `toc.html` for the full plan.

## Relative Path Rules

- Same part: `../module-XX-name/index.html`
- Different part: `../../part-N-name/module-XX-name/index.html`
- To book root from a section file: `../../`

## Batch Partitioning (for parallel agent runs)

- Batch A: Part 1 (Ch 0-6, 7 modules)
- Batch B: Part 2 (Ch 7-15, 9 modules)
- Batch C: Part 3 (Ch 16-26, 11 modules)
- Batch D: Part 4 (Ch 27-38, 12 modules)

Two agents must never edit the same file at overlapping times. One chapter equals one file set; different chapters may proceed in parallel; agent waves within a chapter run strictly in sequence.

## Canonical Software Stack

| Layer | Primary | Alternatives shown |
|---|---|---|
| LLM API | Anthropic Claude (claude-opus-4-8) | OpenAI, Gemini |
| Agent framework | LangGraph | AutoGen/AG2, CrewAI, smolagents |
| Tool use / MCP | Anthropic MCP SDK | OpenAI function calling |
| Memory | mem0, Qdrant, Chroma | Pinecone, Weaviate |
| Reinforcement learning | Stable-Baselines3, CleanRL | RLlib |
| Robotics simulation | Isaac Lab, MuJoCo, Gymnasium | PyBullet |
| Evaluation | AgentBench, GAIA, SWE-bench | BrowserGym, WebArena |
| Observability | LangSmith | W&B Weave, Phoenix Arize |
| Orchestration | Modal, Prefect | Ray, Celery |

## QA Audit Pipeline

1. `C:\Python314\python.exe scripts\audit_book.py`: AgenticAI-specific content canaries (file completeness vs toc.html, dash discipline, per-section structure, link integrity).
2. `scripts\run_audit.cmd`: the book-skills audit-plugin pipeline (P0-P3 checks). P0 includes KDP/Kindle blockers (strict XHTML, bare-dollar math, unresolvable font weights).

## Style Rules (non-negotiable)

1. Never use em-dashes or double-dashes. Use commas, semicolons, colons, parentheses, or separate sentences.
2. Book hierarchy terminology: Part > Chapter > Section. Never use "course", "lecture", or "module" in reader-facing prose.
3. Every figure, table, code block, and callout must be referenced in surrounding prose.
4. Code captions (`<div class="code-caption">`) go BELOW the code block, are specific, and are unique within a file.
5. Every chapter index ends with a "What's Next" section linking the next chapter, placed before the bibliography.
6. No placeholder text of any kind. Every section ships complete or is not created.
7. Every from-scratch implementation is followed by a `.callout.library-shortcut` showing the same task with the canonical library.

## KDP Listing

- **Book Title**: Building Agentic AI
- **Subtitle**: From Goals to Autonomous Systems
- **Series**: Hands-On AI Science
- **Edition**: 1
- **Author (primary)**: Alexander Apartsin
- **Contributor**: Yehudit Aperstein (role: Author)
- **AI content**: Contains AI-generated or AI-assisted content. Disclose per KDP policy.

### Keywords (7)

1. AI agents LLM autonomous systems LangGraph LangChain
2. reinforcement learning deep RL policy gradient PyTorch
3. multi-agent systems swarm intelligence emergent behavior
4. prompt engineering ReAct chain-of-thought reasoning agents
5. agentic RAG retrieval augmented generation vector database
6. software engineering agents SWE-bench computer use GUI agents
7. agent safety alignment governance RLHF Constitutional AI

### Categories

1. Nonfiction > Computers & Technology > Computer Science > AI & Machine Learning
2. Nonfiction > Computers & Technology > Computer Science > Natural Language Processing
3. Nonfiction > Computers & Technology > Programming > Algorithms or Machine Theory
