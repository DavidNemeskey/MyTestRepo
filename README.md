# Advances in Automated Failure Attribution

## Abstract

Since the introduction of the Who&When benchmark [[1]](#ref-1), automatic failure attribution in LLM-based multi-agent systems has rapidly diversified across at least five methodological paradigms. Causal and counterfactual approaches (AgenTracer [[2]](#ref-2), CHIEF [[3]](#ref-3), DoVer [[4]](#ref-4)) attempt to verify whether correcting a specific action would avert failure. Graph and dependency-based methods (GraphTracer [[5]](#ref-5)) model information flow across agents rather than relying on temporal order. Spectrum-based analysis (FAMAS [[6]](#ref-6)) adapts software fault localization techniques through trajectory replay. Iterative reasoning pipelines (RAFFLES [[7]](#ref-7), ECHO [[8]](#ref-8)) employ structured multi-pass evaluation with consensus mechanisms. Schema-based knowledge transfer (CORRECT [[9]](#ref-9)) reuses distilled error patterns at inference time without training. Compact fine-tuned models (AgenTracer-8B, GraphTracer-8B) can outperform much larger proprietary models by up to 18.18% [[2]](#ref-2)[[5]](#ref-5), while training-free methods like RAFFLES achieve over 43% agent-step pair accuracy through prompting alone [[7]](#ref-7). Agent-level attribution now reaches approximately 68% [[8]](#ref-8), but step-level accuracy remains below 50% even for the best methods [[10]](#ref-10), and state-of-the-art reasoning models still fail to achieve practical usability [[1]](#ref-1).

The benchmark landscape has expanded considerably beyond Who&When. TracerTraj-2.5K provides counterfactual replay-verified annotations [[2]](#ref-2), CORRECT-Error offers 2,000+ trajectories with error injection guided by real-world distributions [[9]](#ref-9), AgentHallu targets hallucination attribution across 7 frameworks with the best model achieving only 41.1% step localization [[11]](#ref-11), and AgentFail addresses platform-orchestrated systems with a root cause taxonomy that boosts LLM identification accuracy by 15–20 percentage points [[12]](#ref-12). Multiple independent failure taxonomies (MAST [[13]](#ref-13), AgentErrorTaxonomy [[14]](#ref-14), AgentHallu [[11]](#ref-11)) converge on the finding that failures are heterogeneous and often stem from system design rather than model limitations [[13]](#ref-13)[[15]](#ref-15). A critical methodological concern is that ground-truth annotations in existing benchmarks may be ambiguous—multiple distinct interventions can independently repair the same failure [[4]](#ref-4)—suggesting that some reported low accuracies reflect benchmark limitations rather than purely methodological shortcomings.

---

## Flow Diagram

```
Records from Elicit search
        n = 500
           |
           ↓
Papers screened using: Multi-Agent System Focus, Automatic Failure Attribution,
Agent System Specificity, Core Topic Relevance, LLM-Based Multi-Agent Systems,
Methodological Contribution
        n = 500
         /     \
        ↓       ↓
Papers included    Papers screened out
for extraction         n = 475
    n = 25
```

---

## Paper Search

We performed a semantic search across over 138 million academic papers from the Elicit search engine, which includes all of Semantic Scholar and OpenAlex.

We ran this query: *"Elaborate on the state of automatic failure attribution. I have already read "Which Agent Causes Task Failures and When? On Automated Failure Attribution of LLM Multi-Agent Systems" (Zhang et al, 2025) and "Abduct, Act, Predict: Scaffolding Causal Inference for Automated Failure Attribution in Multi-Agent Systems" (West, 2025?). List the new papers / directions in this field. I am also interested in related benchmarks."*

The search returned 500 total results from Elicit. We retrieved 500 papers most relevant to the query for screening.

---

## Screening

We screened in sources based on their abstracts that met these criteria:

- **Multi-Agent System Focus:** Does this study focus on multi-agent systems (rather than solely single-agent systems)?
- **Automatic Failure Attribution:** Does this study address automatic/automated failure attribution methods (rather than manual or human-only approaches)?
- **Agent System Specificity:** Does this study specifically focus on agent systems (rather than general software debugging or testing without agent context)?
- **Core Topic Relevance:** Does this study focus on automatic failure attribution in multi-agent systems as a primary research topic?
- **LLM-Based Multi-Agent Systems:** Does this study involve LLM-based multi-agent systems and their failure analysis, OR does it present methods directly applicable to such systems?
- **Methodological Contribution:** Does this study present novel methodologies, algorithms, frameworks for failure attribution, OR evaluate benchmarks for failure attribution, OR apply causal inference methods to multi-agent system failures?

We considered all screening questions together and made a holistic judgement about whether to screen in each paper.

---

## Data Extraction

We asked a large language model to extract each data column below from each paper. We gave the model the extraction instructions shown below for each column.

- **Technical Approach:**
  Extract the novel method or framework proposed for automatic failure attribution in LLM-based multi-agent systems, including:
  - Name of the approach/framework
  - Key technical innovation or contribution
  - How it differs from existing methods
  - Core methodology (e.g., counterfactual reasoning, graph-based analysis, causal inference)
  - Any specialized training or data requirements
  - Computational efficiency considerations

- **Benchmark Performance:**
  Extract all evaluation details for automatic failure attribution methods, including:
  - Benchmark datasets used (e.g., Who&When, TracerTraj)
  - Evaluation metrics (agent-level accuracy, step-level accuracy, etc.)
  - Quantitative results and performance comparisons
  - Baseline methods compared against
  - Performance improvements over state-of-the-art
  - Any new benchmarks or evaluation frameworks introduced

- **Field Challenges:**
  Extract the current state and limitations of automatic failure attribution identified in the work, including:
  - Specific problems with existing failure attribution methods
  - Fundamental challenges in multi-agent system debugging
  - Performance gaps or inadequacies of current approaches
  - Why current methods fail (e.g., low accuracy, inability to handle complexity)
  - Identified weaknesses in the field's current capabilities

- **Future Directions:**
  Extract forward-looking insights about automatic failure attribution research, including:
  - Remaining limitations of the proposed approach
  - Suggested future research directions
  - Open problems in automatic failure attribution
  - Potential applications or extensions mentioned
  - Areas needing further development
  - Emerging trends or promising research paths identified

- **System Applications:**
  Extract details about the multi-agent systems and application contexts for failure attribution, including:
  - Types of multi-agent systems tested (e.g., MetaGPT, MaAS)
  - Application domains or use cases
  - System complexity characteristics (number of agents, interaction patterns)
  - Real-world deployment results or integration outcomes
  - Practical impact on system performance or debugging workflows

---

## Results

### Characteristics of Included Studies

The following table summarizes the 25 sources identified in this review. Since the user has already read the Zhang et al. (2025) Who&When paper and the West et al. (2025) A2P paper, these are included for completeness but the discussion emphasizes the remaining 23 sources. Studies span a range of contributions: some propose novel failure attribution methods evaluated on shared benchmarks, others introduce new benchmarks or taxonomies, and several address failure attribution in adjacent domains (cloud systems, cybersecurity, robotics) using multi-agent architectures.

| Study | Full text retrieved? | Study Type | Primary Contribution | Target Domain |
|---|---|---|---|---|
| Shaokun Zhang et al., 2025 | Yes | Benchmark + Methods | Who&When dataset and three baseline attribution methods [[1]](#ref-1) | LLM multi-agent systems [[1]](#ref-1) |
| Alva West et al., 2025 | No (abstract only) | Method | A2P Scaffolding for causal inference-based failure attribution [[10]](#ref-10) | LLM multi-agent systems [[10]](#ref-10) |
| Heng Zhang et al., 2025 | No (abstract only) | Method | GraphTracer: Information Dependency Graphs for failure tracing [[5]](#ref-5) | Multi-turn deep search [[5]](#ref-5) |
| Gui-Min Zhang et al., 2025 | Yes | Method + Benchmark | AgenTracer: counterfactual replay and programmatic fault injection with TracerTraj dataset [[2]](#ref-2) | LLM multi-agent systems (MetaGPT, MaAS, OWL) [[2]](#ref-2) |
| Yawen Wang et al., 2026 | No (abstract only) | Method | CHIEF: hierarchical causal graph with oracle-guided backtracking [[3]](#ref-3) | LLM multi-agent systems [[3]](#ref-3) |
| Chenyang Zhu et al., 2025 | Yes | Method | RAFFLES: iterative reasoning pipeline with Judge and Evaluators [[7]](#ref-7) | LLM multi-agent systems [[7]](#ref-7) |
| Xuyan Ma et al., 2025 | Yes | Benchmark + Taxonomy | AgentFail dataset and root cause taxonomy for platform-orchestrated systems [[12]](#ref-12) | Platform-orchestrated agentic systems (e.g., Dify) [[12]](#ref-12) |
| Adi Banerjee et al., 2025 | Yes | Method | ECHO: hierarchical context representation with consensus voting [[8]](#ref-8) | LLM multi-agent systems [[8]](#ref-8) |
| Fanqi Kong et al., 2025 | No (abstract only) | Data generation + Method | AEGIS: automated error injection and identification framework [[16]](#ref-16) | Multi-agent systems [[16]](#ref-16) |
| Ming-Jie Ma et al., 2025 | Yes | Method | DoVer: intervention-driven debugging with active verification [[4]](#ref-4) | LLM multi-agent systems (Magnetic-One, AG2) [[4]](#ref-4) |
| Feng Fu et al., 2025 | Yes | Method | MA-RCA: multi-agent root cause analysis with retrieval and validation agents [[17]](#ref-17) | Cloud-native platforms, power metering infrastructure [[17]](#ref-17) |
| Divya Pathak et al., 2025 | Yes | Benchmark + Method | Anomaly detection pipeline for silent failures in agentic trajectories [[18]](#ref-18) | Stock market analysis, research writing assistants [[18]](#ref-18) |
| Yifan Yu et al., 2025 | Yes | Method + Benchmark | CORRECT: training-free schema-based error recognition with CORRECT-Error benchmark [[9]](#ref-9) | Software development, scientific research, web navigation [[9]](#ref-9) |
| Taeyoon Kim et al., 2026 | No (abstract only) | Empirical analysis | Process-level failure analysis of LLM-based RCA agents with pitfall taxonomy [[15]](#ref-15) | Cloud root cause analysis [[15]](#ref-15) |
| Zongyi Lyu et al., 2026 | No (abstract only) | Analysis framework | CAM: causality-based analysis for multi-agent code generation systems [[19]](#ref-19) | Code generation [[19]](#ref-19) |
| Bohan Li et al., 2025 | Yes | Method | AgentAsk: edge-level clarification module to arrest error propagation [[20]](#ref-20) | Math reasoning, QA, code generation [[20]](#ref-20) |
| Yu Ge et al., 2025 | Yes | Method | FAMAS: spectrum-based failure attribution via trajectory replay [[6]](#ref-6) | LLM multi-agent systems [[6]](#ref-6) |
| M. Cemri et al., 2025 | Yes | Taxonomy + Benchmark | MAST: empirically grounded failure taxonomy with LLM-as-a-judge pipeline [[13]](#ref-13) | Seven MAS frameworks including MetaGPT, ChatDev [[13]](#ref-13) |
| Kunlun Zhu et al., 2025 | Yes | Taxonomy + Method + Benchmark | AgentDebug: modular error taxonomy with debugging framework and AgentErrorBench [[14]](#ref-14) | Single-agent systems (ALFWorld, GAIA, WebShop) [[14]](#ref-14) |
| Kartik Nagpal et al., 2025 | Yes | Method | LLM-MCA/LLM-TACA: LLM-based credit assignment for cooperative multi-agent RL [[21]](#ref-21) | Robotics, warehouse management [[21]](#ref-21) |
| Xuannan Liu et al., 2026 | No (abstract only) | Benchmark | AgentHallu: hallucination attribution benchmark for LLM-based agents [[11]](#ref-11) | 7 agent frameworks across 5 domains [[11]](#ref-11) |
| Manish Shukla et al., 2025 | Yes | Monitoring framework | AMDM: adaptive multi-dimensional monitoring for agentic AI [[22]](#ref-22) | Enterprise agentic workflows [[22]](#ref-22) |
| Yinfang Chen et al., 2025 | Yes | System | STRATUS: multi-agent SRE system with transactional no-regression safety [[23]](#ref-23) | Cloud reliability engineering [[23]](#ref-23) |
| Lingzhe Zhang et al., 2025 | Yes | Method | RCLAgent: multi-agent recursion-of-thought for microservice root cause localization [[24]](#ref-24) | Microservice systems [[24]](#ref-24) |
| Nanda Rani et al., 2025 | Yes | System | AURA: multi-agent framework for cyber threat attribution [[25]](#ref-25) | Cybersecurity / APT attribution [[25]](#ref-25) |

Of the 25 sources, 17 had full texts available and 8 were abstract-only. The majority of studies (approximately 14) directly address failure attribution in LLM-based multi-agent systems, while the remainder apply multi-agent architectures to failure attribution in adjacent domains such as cloud operations, microservices, and cybersecurity. Several studies focus primarily on taxonomy and benchmark construction rather than proposing new attribution algorithms.

---

### Technical Approaches to Failure Attribution

The field has rapidly diversified in methodology since the introduction of the Who&When benchmark. The following table organizes the core technical innovations across the primary attribution methods.

| Method | Core Methodology | Key Innovation | Requires Training? | Evaluated on Who&When? |
|---|---|---|---|---|
| A2P Scaffolding | Structured causal inference (abduction, action, prediction) [[10]](#ref-10) | Single-pass counterfactual reasoning within an LLM [[10]](#ref-10) | No [[10]](#ref-10) | Yes [[10]](#ref-10) |
| GraphTracer | Information Dependency Graphs (IDGs) [[5]](#ref-5) | Graph-based tracing of information flow rather than temporal sequences [[5]](#ref-5) | Yes (graph-aware synthetic data, fine-tuned 8B model) [[5]](#ref-5) | Yes [[5]](#ref-5) |
| AgenTracer | Counterfactual replay + programmatic fault injection [[2]](#ref-2) | Automated annotation pipeline producing TracerTraj-2.5K; multi-granular RL training [[2]](#ref-2) | Yes (RL-trained 8B model) [[2]](#ref-2) | Yes [[2]](#ref-2) |
| CHIEF | Hierarchical causal graph + oracle-guided backtracking [[3]](#ref-3) | Transforms flat logs into hierarchical graphs; progressive causal screening [[3]](#ref-3) | Not specified [[3]](#ref-3) | Yes [[3]](#ref-3) |
| RAFFLES | Iterative multi-component pipeline (Judge + Evaluators) [[7]](#ref-7) | Iterative refinement with hypothesis history; task-agnostic design [[7]](#ref-7) | No (prompt-based) [[7]](#ref-7) | Yes [[7]](#ref-7) |
| ECHO | Hierarchical context representation + consensus voting [[8]](#ref-8) | Positional-based leveling with multiple objective analysis agents [[8]](#ref-8) | No [[8]](#ref-8) | Yes [[8]](#ref-8) |
| AEGIS | Automated error injection into successful trajectories [[16]](#ref-16) | Context-aware LLM-based adaptive manipulator for controllable error generation [[16]](#ref-16) | Yes (SFT, RL, contrastive learning explored) [[16]](#ref-16) | Not specified [[16]](#ref-16) |
| DoVer | Intervention-driven debugging with active verification [[4]](#ref-4) | Validates hypotheses through targeted interventions rather than log-only analysis [[4]](#ref-4) | No [[4]](#ref-4) | Yes (as reference) [[4]](#ref-4) |
| FAMAS | Spectrum-based analysis via trajectory replay [[6]](#ref-6) | Novel suspiciousness formula integrating agent behavior and action behavior groups [[6]](#ref-6) | No (requires multiple replays) [[6]](#ref-6) | Yes [[6]](#ref-6) |
| CORRECT | Online cache of distilled error schemata [[9]](#ref-9) | Training-free schema reuse for knowledge transfer across failures [[9]](#ref-9) | No (training-free) [[9]](#ref-9) | Yes [[9]](#ref-9) |
| AgentDebug | Modular error taxonomy + counterfactual debugging [[14]](#ref-14) | Fine-grained root-cause isolation with corrective feedback for iterative recovery [[14]](#ref-14) | No (prompt engineering with GPT-4.1) [[14]](#ref-14) | No (uses ALFWorld, GAIA, WebShop) [[14]](#ref-14) |
| AgentAsk | Edge-level clarification module [[20]](#ref-20) | Proactive error prevention via supervised distillation and E-GRPO reinforcement learning [[20]](#ref-20) | Yes (distillation + RL) [[20]](#ref-20) | No (uses GSM8K, MATH, MMLU, etc.) [[20]](#ref-20) |

The methods can be grouped into several paradigmatic approaches. First, **causal and counterfactual reasoning methods** (A2P, AgenTracer, CHIEF, DoVer) attempt to determine whether correcting a specific action would have averted the failure. A2P performs this reasoning in a single inference pass [[10]](#ref-10), while AgenTracer uses actual counterfactual replay with programmatic fault injection to generate ground-truth annotations [[2]](#ref-2). CHIEF constructs hierarchical causal graphs and applies progressive causal screening to distinguish root causes from propagated symptoms [[3]](#ref-3). DoVer goes further by actively executing interventions (e.g., editing messages, altering plans) and measuring whether failures are resolved, flipping 18–28% of failed trials into successes on Magnetic-One [[4]](#ref-4).

Second, **graph and dependency-based approaches** (GraphTracer, CHIEF) explicitly model information flow. GraphTracer constructs Information Dependency Graphs to capture how agents reference prior outputs, enabling attribution that accounts for cross-agent dependencies rather than relying on temporal order alone [[5]](#ref-5).

Third, **spectrum and replay-based methods** (FAMAS) borrow from software fault localization. FAMAS estimates, from variations across repeated MAS executions, the likelihood that each action is responsible for failure, using a novel suspiciousness formula that integrates agent activation patterns and action activation patterns [[6]](#ref-6).

Fourth, **iterative reasoning approaches** (RAFFLES, ECHO) employ structured multi-pass analysis. RAFFLES uses a Judge that systematically investigates faults alongside specialized Evaluators that assess both the system's components and the Judge's own reasoning quality [[7]](#ref-7). ECHO combines hierarchical context representation with consensus voting across multiple objective analysis agents [[8]](#ref-8).

Fifth, **knowledge transfer and schema-based methods** (CORRECT) take a distinctive approach by extracting structural error patterns ("schemata") from past failures and applying them to new instances at inference time, achieving up to 19.8% improvement in step-level localization without any training [[9]](#ref-9).

Finally, **proactive prevention methods** (AgentAsk) shift from post-hoc attribution to real-time intervention, treating every inter-agent message as a potential failure point and inserting clarification questions to arrest error propagation before it compounds [[20]](#ref-20).

---

### Benchmarks and Evaluation Frameworks

A central theme across these studies is the development and critique of benchmarks. The following table summarizes all benchmarks and evaluation datasets identified.

| Benchmark / Dataset | Introduced By | Scale | Annotation Type | Key Metrics | Domain |
|---|---|---|---|---|---|
| Who&When | Shaokun Zhang et al., 2025 [[1]](#ref-1) | 127 MAS, 184 failure logs [[1]](#ref-1) | Agent and step responsible for failure [[1]](#ref-1) | Agent-level accuracy, step-level accuracy [[1]](#ref-1) | General LLM MAS [[1]](#ref-1) |
| TracerTraj-2.5K | Gui-Min Zhang et al., 2025 [[2]](#ref-2) | ~2,500 annotated trajectories [[2]](#ref-2) | Counterfactual replay-verified failure annotations [[2]](#ref-2) | Agent-level accuracy, step-level accuracy [[2]](#ref-2) | General LLM MAS [[2]](#ref-2) |
| AgentFail | Xuyan Ma et al., 2025 [[12]](#ref-12) | 307 failure logs from 10 systems [[12]](#ref-12) | Root cause with fine-grained taxonomy [[12]](#ref-12) | Root cause identification accuracy [[12]](#ref-12) | Platform-orchestrated systems [[12]](#ref-12) |
| CORRECT-Error | Yifan Yu et al., 2025 [[9]](#ref-9) | 2,000+ annotated trajectories [[9]](#ref-9) | Error-injection guided by real-world distributions [[9]](#ref-9) | Step-level accuracy, accuracy@k [[9]](#ref-9) | Diverse MAS (multi-hop QA, math, science, agentic tasks) [[9]](#ref-9) |
| AgentErrorBench | Kunlun Zhu et al., 2025 [[14]](#ref-14) | Trajectories from ALFWorld, GAIA, WebShop [[14]](#ref-14) | Step, module, and error type annotations [[14]](#ref-14) | Step accuracy, step+module accuracy, all-correct [[14]](#ref-14) | Single-agent tasks [[14]](#ref-14) |
| AgentHallu | Xuannan Liu et al., 2026 [[11]](#ref-11) | 693 trajectories across 7 frameworks and 5 domains [[11]](#ref-11) | Binary labels, hallucination-responsible steps, causal explanations [[11]](#ref-11) | Step localization accuracy [[11]](#ref-11) | Hallucination attribution [[11]](#ref-11) |
| AEGIS dataset | Fanqi Kong et al., 2025 [[16]](#ref-16) | Generated via error injection into successful trajectories [[16]](#ref-16) | Controllable, traceable error labels [[16]](#ref-16) | Not specified [[16]](#ref-16) | General MAS [[16]](#ref-16) |
| MAST taxonomy + data | M. Cemri et al., 2025 [[13]](#ref-13) | 200+ tasks across 7 MAS frameworks [[13]](#ref-13) | 14 failure modes in 3 categories, Cohen's Kappa 0.88 [[13]](#ref-13) | Cohen's Kappa for agreement [[13]](#ref-13) | Seven MAS frameworks [[13]](#ref-13) |
| Silent failure datasets | Divya Pathak et al., 2025 [[18]](#ref-18) | 4,275 and 894 trajectories [[18]](#ref-18) | Anomaly labels for drift, cycles, missing details [[18]](#ref-18) | Accuracy, macro-F1 [[18]](#ref-18) | Agentic workflow anomalies [[18]](#ref-18) |
| OpenRCA | Taeyoon Kim et al., 2026 [[15]](#ref-15) | 1,675 agent runs across 5 models [[15]](#ref-15) | 12 pitfall types across 3 categories [[15]](#ref-15) | Pitfall classification [[15]](#ref-15) | Cloud RCA [[15]](#ref-15) |

The Who&When benchmark remains the most widely used evaluation resource, with at least 10 of the methods reviewed here reporting results on it [[1]](#ref-1). However, several studies have raised concerns about its limitations. Ming-Jie Ma et al. (2025) identify uncertainty in the Who&When ground-truth annotations, noting that multiple distinct interventions can independently repair a failed task, making single-step attribution "ill-posed" [[4]](#ref-4). Their prompt refinements improved GPT-4o step attribution from 6% to 24%, but absolute accuracy remained low due to annotation ambiguity [[4]](#ref-4). This finding suggests that some of the low step-level accuracies reported across studies may reflect benchmark limitations rather than purely methodological shortcomings.

The introduction of TracerTraj-2.5K by AgenTracer addresses annotation quality through counterfactual replay verification [[2]](#ref-2), while CORRECT-Error provides a larger-scale dataset with error injection guided by real-world error distributions and validated through human evaluation [[9]](#ref-9). AgentHallu focuses specifically on hallucination attribution across 7 agent frameworks, introducing a 5-category hallucination taxonomy [[11]](#ref-11). AgentFail targets a distinct niche—platform-orchestrated systems built on low-code platforms—with a root cause taxonomy rather than step-level annotations [[12]](#ref-12).

---

### Performance Comparison on Who&When

The following table compiles reported performance on the Who&When benchmark across methods, where available. Note that different studies may use slightly different evaluation protocols.

| Method | Agent-Level Accuracy | Step-Level Accuracy (Algorithm-Generated) | Step-Level Accuracy (Hand-Crafted) | Agent-Step Pair Accuracy |
|---|---|---|---|---|
| Baseline (Zhang et al., 2025) | 53.5% [[1]](#ref-1) | 16.67% (implied) [[10]](#ref-10) | 12.07% (implied) [[10]](#ref-10) | 14.2% [[1]](#ref-1) |
| A2P Scaffolding | Not reported | 47.46% [[10]](#ref-10) | 29.31% [[10]](#ref-10) | Not reported |
| RAFFLES | Not separately reported | 43%+ [[7]](#ref-7) | 20%+ [[7]](#ref-7) | 43%+ (AG), 20%+ (HC) [[7]](#ref-7) |
| ECHO | ~68% [[8]](#ref-8) | 27–28% (exact match) [[8]](#ref-8) | Not separately reported | Not reported |
| FAMAS | 57.61% [[6]](#ref-6) | Not separately reported | Not separately reported | 29.35% (action-level) [[6]](#ref-6) |
| AgenTracer-8B | Outperforms baselines [[2]](#ref-2) | Not separately reported | Not separately reported | Up to 18.18% above SOTA models [[2]](#ref-2) |
| GraphTracer-8B | Up to 18.18% above SOTA [[5]](#ref-5) | Not separately reported | Not separately reported | Not reported |
| CHIEF | Outperforms 8 baselines [[3]](#ref-3) | Not separately reported | Not separately reported | Not reported |
| CORRECT | Up to 19.8% improvement over advances [[9]](#ref-9) | Not separately reported | Not separately reported | Not reported |

Step-level accuracy remains the harder task across all methods. The best reported step-level accuracy on the Algorithm-Generated subset is 47.46% by A2P [[10]](#ref-10), representing a 2.85x improvement over the baseline's 16.67% [[10]](#ref-10). On the more complex Hand-Crafted subset, A2P achieves 29.31% [[10]](#ref-10), while RAFFLES achieves over 20% [[7]](#ref-7). Agent-level accuracy is notably higher, with ECHO reaching approximately 68% [[8]](#ref-8) and FAMAS achieving 57.61% [[6]](#ref-6). Even state-of-the-art reasoning models such as OpenAI o1 and DeepSeek R1 fail to achieve practical usability on this benchmark [[1]](#ref-1).

---

### Failure Taxonomies

Several studies contribute structured taxonomies of failure modes, which serve as complementary resources to attribution methods:

- **MAST** (Cemri et al., 2025) identifies 14 failure modes organized into three categories: specification issues, inter-agent misalignment, and task verification, developed through rigorous inter-annotator agreement studies achieving a Cohen's Kappa of 0.88 [[13]](#ref-13). A key finding is that improvements in base model capabilities alone are insufficient to address all failure modes, as many failures stem from system design issues [[13]](#ref-13).

- **AgentErrorTaxonomy** (Kunlun Zhu et al., 2025) provides a modular classification spanning memory, reflection, planning, action, and system-level operations for single-agent systems [[14]](#ref-14). The AgentDebug framework built on this taxonomy achieves 24% higher all-correct accuracy and 17% higher step accuracy compared to the strongest baseline [[14]](#ref-14).

- **AgentFail taxonomy** (Xuyan Ma et al., 2025) characterizes root causes in platform-orchestrated systems, finding that providing the taxonomy as guidance to LLMs boosts root cause identification accuracy by 15–20 percentage points (from 8.3–13.0% to 24.1–33.6%) [[12]](#ref-12).

- **Pitfall taxonomy** (Taeyoon Kim et al., 2026) classifies 12 pitfall types across intra-agent reasoning, inter-agent communication, and agent-environment interaction for cloud RCA agents, finding that the most prevalent pitfalls (hallucinated data interpretation, incomplete exploration) persist across all models regardless of capability tier [[15]](#ref-15).

- **AgentHallu taxonomy** (Xuannan Liu et al., 2026) organizes hallucinations into 5 categories (Planning, Retrieval, Reasoning, Human-Interaction, Tool-Use) and 14 sub-categories, with tool-use hallucinations being the most challenging at just 11.6% localization accuracy [[11]](#ref-11).

---

### Adjacent Domains and Applied Systems

Several studies extend failure attribution concepts to operational domains beyond general-purpose LLM multi-agent benchmarks:

- **MA-RCA** applies multi-agent collaboration to root cause analysis in cloud-native platforms and power metering infrastructure, achieving 95.2% F1 on the Nezha benchmark and 82.8% F1 on power monitoring data [[17]](#ref-17). Its key innovation is the use of a Retrieval Agent for grounding hypotheses in historical knowledge and a Validation Agent for dynamic verification [[17]](#ref-17).

- **STRATUS** implements autonomous site reliability engineering with specialized agents for detection, diagnosis, mitigation, and undo operations, solving 69.2% of mitigation problems in AIOpsLab and 50.0% in ITBench [[23]](#ref-23). Its Transactional No-Regression safety specification is a notable contribution for ensuring safe exploration during failure mitigation [[23]](#ref-23).

- **RCLAgent** introduces a recursion-of-thought strategy for root cause localization in microservice systems, outperforming state-of-the-art methods by 2–9% in Recall@10 and 32.53% in MRR while requiring only a single request rather than aggregating multiple requests [[24]](#ref-24).

- **AURA** applies multi-agent intelligence to cyber threat attribution, using retrieval-augmented generation to link threat behaviors to known APT groups, achieving 63.33% top-1 accuracy for group-wise attribution with GPT-4o [[25]](#ref-25).

- **AMDM** provides an adaptive monitoring framework for agentic AI systems, cutting anomaly detection latency from 12.3s to 5.6s and reducing false-positive rates from 4.5% to 0.9% compared to static thresholds [[22]](#ref-22).

These applied systems demonstrate that the principles developed for LLM multi-agent failure attribution—causal reasoning, multi-agent decomposition, retrieval-augmented verification—are transferable to operational reliability contexts.

---

## Synthesis

The apparent inconsistency in reported performance levels across studies can be largely explained by three factors: task granularity, benchmark construction methodology, and whether methods perform post-hoc analysis versus active intervention.

**Task granularity drives the accuracy gap.** Agent-level attribution is substantially easier than step-level attribution across all methods. ECHO achieves approximately 68% agent-level accuracy [[8]](#ref-8) while step-level accuracy for even the best methods remains below 50% [[10]](#ref-10). This pattern holds because identifying the responsible agent requires only coarse-grained reasoning about role boundaries, whereas pinpointing the exact step demands fine-grained counterfactual analysis across long interaction traces [[1]](#ref-1). Performance further declines with increasing context length, particularly affecting step-level accuracy [[1]](#ref-1).

**Ground-truth annotation quality materially affects reported results.** DoVer's analysis reveals that multiple distinct interventions can independently repair the same failed task, making single-step attribution fundamentally ambiguous in many cases [[4]](#ref-4). Simple prompt refinements (adding explicit step indices and guidance reminders) improved GPT-4o step accuracy from 6% to 24% on Who&When without any algorithmic change [[4]](#ref-4), suggesting that a portion of previously reported failures reflect evaluation artifacts rather than genuine attribution limitations. Studies using counterfactual replay to verify annotations (AgenTracer [[2]](#ref-2), CORRECT-Error [[9]](#ref-9)) may produce more reliable ground truth, though this comes at significant computational cost.

**Active intervention versus passive analysis.** Methods that merely analyze logs to identify failure points (most approaches) face a fundamental validation gap—their hypotheses remain untested [[4]](#ref-4). DoVer addresses this by executing targeted interventions and measuring whether failures are resolved, recovering 18–28% of failed trials in Magnetic-One and 49% in AG2 [[4]](#ref-4). Similarly, AgentAsk prevents errors proactively by inserting clarification questions at potential failure points, keeping overhead below 5% in latency and cost [[20]](#ref-20). This distinction between post-hoc attribution and actionable debugging represents a meaningful methodological divide, with intervention-based approaches producing results whose practical utility is directly measurable.

**Trained lightweight models versus prompted large models.** A notable trend is that compact, fine-tuned models (AgenTracer-8B, GraphTracer-8B) can outperform much larger proprietary models. AgenTracer-8B surpasses Gemini-2.5-Pro and Claude-4-Sonnet by up to 18.18% on attribution accuracy [[2]](#ref-2)[[5]](#ref-5), while AEGIS demonstrates that fine-tuned models can be competitive with proprietary systems an order of magnitude larger [[16]](#ref-16). This suggests that domain-specific training data—whether generated through counterfactual replay [[2]](#ref-2), graph-aware synthesis [[5]](#ref-5), or controlled error injection [[16]](#ref-16)—is more important than raw model scale for this task. Conversely, training-free methods like CORRECT achieve strong results through schema reuse at near-zero overhead [[9]](#ref-9), and RAFFLES demonstrates that iterative prompt-based reasoning can reach over 43% pair accuracy without any training [[7]](#ref-7).

**The taxonomy gap.** Multiple independent efforts to build failure taxonomies (MAST [[13]](#ref-13), AgentErrorTaxonomy [[14]](#ref-14), AgentFail [[12]](#ref-12), AgentHallu [[11]](#ref-11)) converge on a shared observation: failures in multi-agent systems are heterogeneous and often originate from system design rather than individual model limitations [[13]](#ref-13)[[15]](#ref-15). Providing taxonomic structure as guidance to LLMs consistently improves attribution performance—by 15–20 percentage points in AgentFail's experiments [[12]](#ref-12)—suggesting that structured knowledge about failure modes is a prerequisite for accurate attribution.

In summary, the field has moved beyond the initial framing of failure attribution as flat pattern recognition over logs. The most promising directions include causal graph construction [[3]](#ref-3)[[5]](#ref-5), intervention-driven verification [[4]](#ref-4), schema-based knowledge transfer [[9]](#ref-9), and spectrum analysis [[6]](#ref-6). The key bottleneck is not the absence of methods but rather the quality and scale of evaluation infrastructure: ground-truth ambiguity in existing benchmarks constrains the ability to distinguish genuine methodological progress from evaluation artifacts [[4]](#ref-4), and the field would benefit from benchmarks that explicitly account for the multi-solution nature of failure repair.

---

## References

<a id="ref-1"></a>1. Shaokun Zhang, Ming Yin, Jieyu Zhang, et al (2025) *Which Agent Causes Task Failures and When? On Automated Failure Attribution of LLM Multi-Agent Systems.* International Conference on Machine Learning. https://doi.org/10.48550/arXiv.2505.00212

<a id="ref-2"></a>2. Gui-Min Zhang, Junhao Wang, Junjie Chen, et al (2025) *AgenTracer: Who Is Inducing Failure in the LLM Agentic Systems?* arXiv.org. https://doi.org/10.48550/arXiv.2509.03312

<a id="ref-3"></a>3. Yawen Wang, Wenjie Wu, Junjie Wang, Qing Wang (2026) *From Flat Logs to Causal Graphs: Hierarchical Failure Attribution for LLM-based Multi-Agent Systems*

<a id="ref-4"></a>4. Ming-Jie Ma, Jue Zhang, Fangkai Yang, et al (2025) *DoVer: Intervention-Driven Auto Debugging for LLM Multi-Agent Systems.* arXiv.org. https://doi.org/10.48550/arXiv.2512.06749

<a id="ref-5"></a>5. Heng Zhang, Yuling Shi, Xiaodong Gu, et al (2025) *GraphTracer: Graph-Guided Failure Tracing in LLM Agents for Robust Multi-Turn Deep Search.* arXiv.org. https://doi.org/10.48550/arXiv.2510.10581

<a id="ref-6"></a>6. Yu Ge, Linna Xie, Zhong Li, et al (2025) *Who is Introducing the Failure? Automatically Attributing Failures of Multi-Agent Systems via Spectrum Analysis.* arXiv.org. https://doi.org/10.48550/arXiv.2509.13782

<a id="ref-7"></a>7. Chenyang Zhu, Spencer Hong, Jingyu Wu, et al (2025) *RAFFLES: Reasoning-based Attribution of Faults for LLM Systems.* arXiv.org. https://doi.org/10.48550/arXiv.2509.06822

<a id="ref-8"></a>8. Adi Banerjee, Anirudh Nair, Tarik Borogovac (2025) *Where Did It All Go Wrong? A Hierarchical Look into Multi-Agent Error Attribution.* arXiv.org. https://doi.org/10.48550/arXiv.2510.04886

<a id="ref-9"></a>9. Yifan Yu, Moyan Li, Shaoyuan Xu, et al (2025) *CORRECT: COndensed eRror RECognition via knowledge Transfer in multi-agent systems.* arXiv.org. https://doi.org/10.48550/arXiv.2509.24088

<a id="ref-10"></a>10. Alva West, Yixuan Weng, Minjun Zhu, et al (2025) *Abduct, Act, Predict: Scaffolding Causal Inference for Automated Failure Attribution in Multi-Agent Systems.* arXiv.org. https://doi.org/10.48550/arXiv.2509.10401

<a id="ref-11"></a>11. Xuannan Liu, Xiao Yang, Zekun Li, et al (2026) *AgentHallu: Benchmarking Automated Hallucination Attribution of LLM-based Agents.* arXiv.org. https://doi.org/10.48550/arXiv.2601.06818

<a id="ref-12"></a>12. Xuyan Ma, Xiaofei Xie, Yawen Wang, et al (2025) *Demystifying the Lifecycle of Failures in Platform-Orchestrated Agentic Workflows*

<a id="ref-13"></a>13. M. Cemri, Melissa Z. Pan, Shuyi Yang, et al (2025) *Why Do Multi-Agent LLM Systems Fail?* arXiv.org. https://doi.org/10.48550/arXiv.2503.13657

<a id="ref-14"></a>14. Kunlun Zhu, Zijia Liu, Bingxuan Li, et al (2025) *Where LLM Agents Fail and How They can Learn From Failures.* arXiv.org. https://doi.org/10.48550/arXiv.2509.25370

<a id="ref-15"></a>15. Taeyoon Kim, Woohyeok Park, Hoyeong Yun, Kyungyong Lee (2026) *Why Do AI Agents Systematically Fail at Cloud Root Cause Analysis?*

<a id="ref-16"></a>16. Fanqi Kong, Ruijie Zhang, Huaxiao Yin, et al (2025) *Aegis: Automated Error Generation and Attribution for Multi-Agent Systems*

<a id="ref-17"></a>17. Feng Fu, Hong Ding, Yong Qin, et al (2025) *Leveraging multi-agent framework for root cause analysis.* Complex & Intelligent Systems. https://doi.org/10.1007/s40747-025-02096-0

<a id="ref-18"></a>18. Divya Pathak, Harshit Kumar, Anuska Roy, et al (2025) *Detecting Silent Failures in Multi-Agentic AI Trajectories.* arXiv.org. https://doi.org/10.48550/arXiv.2511.04032

<a id="ref-19"></a>19. Zongyi Lyu, Zhenlan Ji, Songqiang Chen, et al (2026) *CAM: A Causality-based Analysis Framework for Multi-Agent Code Generation Systems*

<a id="ref-20"></a>20. Bohan Li, Kuo Yang, Ying Lai, et al (2025) *AgentAsk: Multi-Agent Systems Need to Ask.* arXiv.org. https://doi.org/10.48550/arXiv.2510.07593

<a id="ref-21"></a>21. Kartik Nagpal, Dayi Dong, Jean-Baptiste Bouvier, Negar Mehr (2025) *Leveraging Large Language Models for Effective and Explainable Multi-Agent Credit Assignment.* Adaptive Agents and Multi-Agent Systems. https://doi.org/10.48550/arXiv.2502.16863

<a id="ref-22"></a>22. Manish Shukla (2025) *Adaptive monitoring and real-world evaluation of agentic AI systems.* AI and Ethics. https://doi.org/10.1007/s43681-026-00990-y

<a id="ref-23"></a>23. Yinfang Chen, Jiaqi Pan, Jackson Clark, et al (2025) *STRATUS: A Multi-agent System for Autonomous Reliability Engineering of Modern Clouds.* arXiv.org. https://doi.org/10.48550/arXiv.2506.02009

<a id="ref-24"></a>24. Lingzhe Zhang, Tong Jia, Kangjin Wang, et al (2025) *Adaptive Root Cause Localization for Microservice Systems with Multi-Agent Recursion-of-Thought.* arXiv.org. https://doi.org/10.48550/arXiv.2508.20370

<a id="ref-25"></a>25. Nanda Rani, S. K. Shukla (2025) *AURA: A Multi-Agent Intelligence Framework for Knowledge-Enhanced Cyber Threat Attribution.* arXiv.org. https://doi.org/10.48550/arXiv.2506.10175
