# ALIE-001 — Agentic Lead Intelligence, Contextual Enrichment and Event-Driven Financial Market Signals

**Research ID:** ALIE-001  
**Version:** 1.0  
**Reference date:** 6 November 2026  
**Scope:** Enterprise AI, wholesale/corporate banking, FX sales intelligence, event-driven systems, governed data access, MCP and agentic workflows

## Executive synthesis and domain primer

**Part I. Executive research synthesis.** The central finding is that the proposed system does not map cleanly to one established category. It sits at the intersection of **sales intelligence**, **account intelligence**, **opportunity intelligence**, **next-best-action**, **relationship-manager copilots**, **event-driven customer engagement**, **decision intelligence**, and **agentic business intelligence**. In financial markets it additionally overlaps with **market-event intelligence**, **treasury/FX advisory analytics**, and **customer exposure analytics**. Existing systems usually specialize in only part of this chain: identifying market or buying signals, maintaining customer context, ranking opportunities, preparing a banker for a conversation, or explaining an already-identified opportunity. The public evidence does not support treating “agentic lead intelligence” as a mature, standardized product category. **Verified finding.** citeturn559669search0turn350286search0turn412453search6turn412453search8

A second finding is more consequential: **market-event detection and customer-opportunity reasoning are different problems**. An observed EUR/USD move is a fact about a market; whether it matters commercially depends on a customer's currency exposures, expected receipts or payments, hedge positions, timing, natural hedges, liquidity constraints, contractual arrangements, product eligibility and relationship context. BIS, ECB and Bank of England evidence shows that importers, exporters and other non-financial corporations use FX forwards, swaps and related instruments primarily to manage heterogeneous cash-flow and balance-sheet exposures, and those exposures can already be offset naturally or financially. A large market move therefore cannot defensibly be equated with “lead generated.” **Verified finding.** citeturn200588search0turn200588search2turn200588search4turn200588search5

A third finding is that the best-supported production pattern is **not unrestricted agent autonomy**. Public banking deployments show copilots and agents being used for research, synthesis, document analysis, workflow coordination and customer-service procedures, while deterministic systems, permission structures and human review continue to enforce important eligibility, transaction and compliance boundaries. MUFG's FX and derivatives sales system uses retrieval and generative AI to digest corporate and market material and help sales teams prepare client recommendations; Deutsche Bank's 2026 Financial Research Agent combines market, company and financial information into structured research under existing permission structures; Deutsche Bank's agentic KYC deployment explicitly retains human accountability; and Scotiabank's payment agents automate a constrained reconciliation and explanation workflow. **Verified finding.** citeturn350286search0turn350286search6turn350286search5turn559669search1

A fourth finding is architectural: the strongest general-purpose pattern is a **layered separation of observation, relevance assessment, evidence persistence and explanation**, rather than a single agent that performs every function. This is a reasoned inference from banking deployments, streaming-system design, modern agent guidance and the limitations of multi-tool LLM reliability. Research benchmarks still find substantial errors in multi-hop tool use; ToolHop, for example, reported only 49.04% accuracy for its leading evaluated model on its 2025 benchmark. Agent vendors themselves recommend deterministic workflows where paths are well defined and agents only where model-driven flexibility adds value. **Reasoned inference.** citeturn697596search4turn697596search0turn398605search0

The evidence also argues against assuming that “real time” means milliseconds. Global FX markets are extremely active, but a relationship-management opportunity is not the same thing as an electronic-trading decision. The relevant freshness target should derive from the user workflow: a seconds-to-minutes SLA may be appropriate for market-triggered sales intelligence, while periodic preparation may be sufficient for meeting research. Subsecond systems become justified only if the business outcome actually deteriorates at longer latency. **Reasoned inference**, supported by streaming systems explicitly trading latency against completeness and by banking use cases whose value is research and engagement rather than execution speed. citeturn688724search0turn341469search9turn350286search0

The strongest conditional direction emerging from the research is therefore **hybrid event-aware intelligence**: deterministic or statistical services identify and persist candidate customer-event relationships; an agent investigates, enriches and explains selected candidates or responds on demand; critical commercial, regulatory and eligibility decisions remain explicit application logic or human decisions. This is **not a universal architecture recommendation**. It becomes attractive only if market signals need proactive processing, customer exposure information is sufficiently structured, freshness is in seconds/minutes rather than microseconds, and users benefit from explanations across heterogeneous evidence.

**Part II. Domain primer.** A useful conceptual map is:

```text
                           CUSTOMER / ACCOUNT DOMAIN
     CRM ───── relationships ───── transactions ───── exposures ───── eligibility
      │                │                 │                 │
      └────────────── Account / Customer Intelligence ────┘
                                │
                                ▼
                Customer-event relevance assessment
                                ▲
                                │
 MARKET DOMAIN                  │                    COMMERCIAL DOMAIN
 FX prices ─ volatility ─ macro events ─ news        leads ─ opportunities
      │             │             │                    │
      └──── Market/Event Intelligence ────────────────┘
                                │
                structured evidence / reason codes
                                │
             ┌──────────────────┴──────────────────┐
             ▼                                     ▼
     Next-best-action                    Agent / RM copilot
  ranking / workflow rules          investigate / explain / answer
```

“**Sales intelligence**” is the broadest commercial term: data and analytics that help sellers prioritize and engage accounts. “**Lead enrichment**” usually means adding attributes to an existing lead or prospect. “**Lead/opportunity scoring**” estimates likelihood or priority; Salesforce's opportunity scoring, for example, uses historical opportunity, account and activity information and exposes contributing factors. “**Signal-based selling**” describes acting on events or behavioural signals indicating that an account may be relevant now; 6sense is an explicit B2B example, aggregating fit, intent and engagement signals into account prioritization and alerts. citeturn412453search0turn412453search1turn412453search5turn412453search6

“**Next-best-action**” is different: it selects or ranks an intervention once customer state and candidate actions exist. “**Relationship-manager copilot**” usually denotes an interactive assistant that prepares, summarizes or helps execute a human workflow. “**Decision intelligence**” is broader still: combining data, models, rules and workflows to support a decision. “**Event-driven customer engagement**” emphasizes a state change—market, transaction, behaviour or lifecycle event—causing reevaluation or outreach. “**Agentic business intelligence**” is a newer and less standardized term for agents that dynamically query, combine and reason across enterprise information. **Reasoned classification.** The distinctions are consistent with documented CRM, account-intelligence and banking systems. citeturn559669search0turn412453search2turn559669search9

For FX specifically, three concepts matter. **Spot FX** exchanges currencies for near-term settlement. **Forwards** lock an exchange rate for a future transaction, while **FX swaps** combine spot and forward legs and are extensively used for funding and hedging. Corporates commonly hedge trade-related receivables and payments; importers may buy foreign currency forward to protect future payment costs, while exporters receiving foreign currency may hedge against depreciation of the currency they expect to receive. citeturn200588search0turn200588search7turn200588search9

Importantly, the economic exposure can differ from the visible transaction. A euro-area company invoicing customers in dollars may have USD revenues but also USD costs or USD debt, producing a natural offset. BIS research published in 2025 found that many large firms' foreign-currency debt exposures are substantially offset through other revenues, assets or hedges. Consequently, a customer database showing “USD transactions” is insufficient evidence of unhedged USD risk. citeturn200588search2

This motivates a five-stage vocabulary for ALIE-001:

**Observation → relevance assessment → structured insight → narrative explanation → human action.**

An observation such as “EUR/USD moved 1.6% in four hours” is not a recommendation. A relevance assessment might say “customer has recurring USD payables and no known hedge covering the next settlement window.” A structured insight records evidence, timestamps, confidence and reason codes. A narrative explains it to the relationship manager. The RM decides whether and how to engage. **Proposed conceptual model.**

## Industry and technology landscape

**Part III. Industry and technology landscape.** Twelve examples are particularly informative because together they span FX sales, corporate-banking research, CRM intelligence, real-time signal detection and constrained agent workflows.

| Example | Status and use | What is publicly established | Relevance to ALIE-001 |
|---|---|---|---|
| **MUFG Bank Global Capital Markets** | Real banking deployment, 2025 case study | FX & Derivatives Sales uses GenAI/RAG to extract information from corporate reports and market information and automate preparation of client materials; LangChain reports a 10× sales-efficiency improvement for the target activity. citeturn350286search0 | Closest public analogue to FX-sales research; shows LLM value in synthesis rather than market-event validity. |
| **Deutsche Bank Financial Research Agent** | Corporate-bank rollout announced 2026 | Combines market information, company data and financial indicators; creates client briefings and financial analyses with source links, permissions, encryption and audit controls. citeturn350286search6 | Strong evidence for governed, evidence-backed RM research. |
| **Standard Chartered CIB Client Insights** | Production CRM transformation | Dynamics 365 combines news feeds, internal information and AI to surface opportunities for proactive engagement to 6,000+ CIB users. citeturn559669search0 | Demonstrates internal/external intelligence embedded into relationship workflow without requiring an autonomous agent. |
| **Citi + Ant International FX pilot** | Live pilot, 2025 | AI forecasting combined with Citi's fixed-FX product to manage client FX exposures; Reuters reported live transactions and a reported hedging-cost reduction for an Asian airline. citeturn350286news9 | Evidence that customer-specific exposure plus predictive analytics can support FX actions; not evidence for an LLM-agent architecture. |
| **Scotiabank Global Transaction Banking** | Agentic banking prototype/deployment evidence | Specialized agents transform, reconcile and explain payment data; Microsoft reports workflows moving from weeks to seconds. citeturn559669search1turn559669search2 | Shows constrained multi-agent workflow over structured banking data. |
| **Deutsche Bank Source-of-Wealth KYC** | Production agentic AI, Sep. 2026 | Agentic system researches approved sources, detects gaps/inconsistencies and prepares assessments; humans retain accountability. citeturn350286search5 | Useful governance analogue: autonomy within a bounded research workflow, human final ownership. |
| **National Bank of Canada adviser agents** | Production adviser-assistance system | Agentic solution on Bedrock/OpenSearch became first point of contact for adviser support; AWS reports a 43% reduction in internal support calls. citeturn559669search7 | Shows retrieval-centric agent adoption and staged rollout in a bank. |
| **Absa CIB / Relationship Banking Copilot** | Employee copilot deployment | Summarizes financial statements and contracts and supports client-meeting preparation; Microsoft reports some users saved at least two hours/day. citeturn350286search1 | Good comparator for on-demand RM preparation, not proactive signal detection. |
| **Salesforce Account/Opportunity Intelligence** | Commercial enterprise product | Opportunity scoring uses historical CRM and activity data; Agentforce Account Management can combine internal data with external web research for account briefs. citeturn412453search1turn412453search2 | Illustrates separation of predictive scoring, external research and agent-facing explanation. |
| **6sense GTM Intelligence** | Commercial B2B signal platform | Combines first-/third-party intent, CRM activity and fit; supports real-time alerts, account prioritization, APIs and MCP. citeturn412453search5turn412453search6turn412453search7 | Strong non-bank analogue for signal fusion → account matching → workflow. |
| **Dataminr** | Commercial real-time event-intelligence platform | Detects public-event signals, emits structured alerts with entities and locations and exposes API integration. citeturn412453search8turn412453search10 | Illustrates external event detection as a separate capability from downstream customer relevance. |
| **AWS Account Plan Pulse** | Internal AWS production sales tool | GenAI tool launched in Jan. 2025 to streamline account-plan preparation. citeturn559669search9 | Non-bank evidence that account intelligence is often assembled asynchronously from existing sources before seller interaction. |

Four cases warrant deeper analysis.

**MUFG** is the nearest public technical analogue because the users are explicitly FX and derivative salespeople. Its documented problem was information overload: annual reports, market data and financial disclosures had to be assembled into client material. The solution used extraction, RAG, prompt engineering and few-shot guidance. The evidence supports an architecture in which GenAI improves **research and synthesis**. It does not establish automated market-event detection, autonomous lead generation, MCP, stream processing or fully autonomous recommendations. This distinction is critical: the public case proves value in reducing analytical friction, not in delegating commercial eligibility to an agent. citeturn350286search0

**Standard Chartered** offers a different lesson. Its CIB CRM consolidates relationship information and external news into Client Insights, which surfaces opportunities for proactive engagement. This predates the current agent wave and demonstrates that **event/context-driven sales intelligence does not intrinsically require an LLM agent**. A conventional CRM, analytics layer and recommendation workflow can produce much of the business value. Copilot can be added later as an interaction and synthesis layer. citeturn559669search0

**Deutsche Bank's Financial Research Agent** is architecturally relevant because it explicitly combines market information, company data and financial indicators, produces source-linked structured outputs and operates through existing permissions. This resembles the investigation/explanation side of the ALIE problem more closely than generic chatbots. Public information still does not disclose its precise retrieval engine, orchestration graph or event-triggering mechanism, so those details remain **unresolved**, not evidence for any specific internal technology. citeturn350286search6

**6sense** provides the best conceptual analogue outside banking. It separates raw signals—website visits, intent, CRM activity—from a model that infers account buying stage, and then from alerts, workflows and a copilot. That decomposition is instructive: **signal ≠ relevance ≠ action**. Its MCP/API support further demonstrates that MCP can expose an already-developed intelligence layer to agents; MCP need not be where the intelligence is computed. citeturn412453search5turn412453search6turn412453search7

Across the landscape, three implementation families recur: **precompute and push insights**, **interactive copilot retrieval**, and **constrained agentic workflow**. Fully autonomous systems that consume high-frequency FX data, infer customer exposures and independently create regulated banking recommendations are not well documented in credible public sources. **Verified evidence gap.**

## Architecture pattern catalogue and decision framework

**Part IV. Architecture pattern catalogue** and **Part IX. Architecture decision framework.** The following are logical architectures; they do not imply one microservice per box.

### Agent-driven, on-demand enrichment

```text
RM question
   │
   ▼
Agent ──► customer-data tool/MCP ──► Databricks
  │
  └────► market-data API
  │
  ▼
LLM correlation + explanation
  │
  ▼
RM
```

The agent owns orchestration and correlation. Persistence can be minimal. Freshness is excellent at request time, but latency and cost scale with each interaction. Failure modes include unnecessary tool calls, incorrect joins, partial API failure and inconsistent reasoning between runs. Multi-hop tool-use research demonstrates that tool selection and sequencing remain non-trivial, so this pattern needs strong schemas, bounded toolsets, retries and trace evaluation. citeturn697596search0turn697596search4

**Appropriate:** exploratory tools, low request volume, uncertain investigation paths, user-initiated research. **Inappropriate:** high-volume proactive detection, strict deterministic eligibility, or situations where repeated queries should return exactly the same customer-event decision.

### Encapsulated enrichment service

```text
RM → Agent → enrich_customer(customer_id, event?)
                 │
                 ├─ governed customer query
                 ├─ market lookup
                 ├─ rules / models
                 └─ evidence assembly
                         │
                         ▼
                  structured result
                         │
                     Agent explains
```

Here the agent sees one high-level domain contract instead of primitive SQL and market tools. This usually improves testability, reproducibility and policy enforcement because matching logic, retries, limits and validation live in ordinary code. Agent autonomy is lower, but an enrichment service can still expose uncertainty and evidence.

**Reasoned inference:** this is often preferable when correlation logic represents domain policy rather than open-ended investigation. Anthropic similarly distinguishes predictable workflows from model-directed agents and recommends increasing autonomy only where flexibility justifies cost and error risk. citeturn398605search0

### Event-driven enrichment

```text
Market source → normalization → event detector → customer matcher
                                         │
Databricks customer state ───────────────┘
                                         ▼
                                 insight/evidence store
                                         │
                              CRM / alert / later agent
```

No conversational agent is required in the detection path. Stream processors can use event time, watermarks, temporal/stateful joins, deduplication and replay. Flink and Databricks Structured Streaming explicitly support event-time processing and watermarking; Delta Change Data Feed can propagate customer-state changes incrementally. citeturn341469search9turn688724search0turn688724search1

This design has strong reproducibility and allows historical replay. Its operational cost is a continuously operating data pipeline, even if few events become commercially relevant. It is appropriate when proactive alerts matter and relevance rules are sufficiently explicit.

### Event-triggered agent execution

```text
Market event → broker/queue → eligibility gate → agent workflow
                                           │
                       ┌───────────────────┼───────────────┐
                       ▼                   ▼               ▼
                  customer tool       market tool      research tool
                       └───────────────────┬───────────────┘
                                           ▼
                                   structured insight
```

This can discover explanations that deterministic pipelines cannot easily encode, but the event detector should usually apply a cheap prefilter before invoking an expensive agent. External event triggering is provided by brokers/workflows or application code, not MCP itself. EventBridge, for example, routes events to targets based on rules; AgentCore provides an agent runtime and tool gateway but is a separate concern. citeturn652753search11turn341469search4

### Hybrid event-aware agent

```text
                           ┌────► evidence/insight store ────┐
Market → events → matcher ─┤                                 │
Customer CDC/features ─────┘                                 ▼
                                                    RM → Agent
                                                         │
                                              fresh tools / MCP
                                                         │
                                              evidence-backed answer
```

Events maintain current contextual intelligence; the agent starts from precomputed evidence and retrieves fresh details only when needed. This reduces repeated work while retaining investigative flexibility. The key architectural issue is invalidation: an insight must record event time, customer snapshot/version, expiry and evidence so later interaction can tell whether it is still valid.

### Precomputed feature-driven intelligence

Customer and event features—such as recurring currency flows, last payment date, hedge coverage ratio, event volatility percentile or relationship strength—are materialized periodically or incrementally. Databricks now supports materialized feature views triggered by schedules, upstream table commits or streaming sources, making this a concrete current option rather than merely a conceptual feature-store pattern. citeturn688724search6

This architecture reduces agent-time computation and enables consistent statistical models, but feature definitions become governed business logic and can hide assumptions unless lineage and versions are retained.

### Query-first semantic intelligence

A further pattern discovered during research is a **semantic/ontology layer between raw data and agent**. Databricks now explicitly recommends Genie One MCP for natural-language business questions grounded in a governed semantic layer and reserves the SQL MCP for more specific SQL/data-engineering use. This suggests a design in which the agent queries business concepts such as “known EUR payables” or “current exposure state” rather than inferring them from raw schemas. **Verified capability; proposed application to ALIE.** citeturn652753search0

The comparative matrix below is an analytical assessment under the assumption of enterprise banking controls and seconds-to-minutes freshness.

| Pattern | Freshness | Determinism | Agent cost | Auditability | Event scale | Incremental adoption | Best fit |
|---|---|---:|---:|---:|---:|---:|---|
| On-demand agent | Current at query | Low–medium | High/request | Medium | Low | Excellent | Analyst/RM exploration |
| Enrichment service | Current at call | High | Low–medium | High | Medium | Excellent | Governed reusable relevance logic |
| Event-driven enrichment | Continuous | High | Low | High | High | Medium | Proactive alerts |
| Event-triggered agent | Continuous | Medium | Potentially high | Medium–high with tracing | Medium | Medium | Complex event investigation |
| Hybrid event-aware agent | Continuous + fresh-on-demand | High for gating, flexible for explanation | Medium | High if evidence is persisted | High | Good | Strong general fit when both proactive and interactive use exist |
| Precomputed features | Scheduled/continuous | High | Low | High | High | Good | Stable signals/scoring |
| Semantic/query layer | Source-dependent | Medium–high | Medium | High if governed | Medium | Excellent | Safe business-language retrieval |

A practical decision tree is:

```text
Do users need proactive intelligence?
        │
   ┌────┴────┐
   No        Yes
   │          │
On-demand   Is customer relevance expressible deterministically/statistically?
agent/RAG       │
             ┌──┴──┐
            Yes    No / partly
             │       │
        event matcher │
             │        └─ cheap gate → event-triggered investigation
             ▼
Do users also ask open-ended questions?
       │
   ┌───┴───┐
  No      Yes
   │        │
push      hybrid event-aware agent
insight
```

The highest-impact unresolved requirements are therefore **proactive vs on-demand**, **freshness SLA**, **quality of customer-exposure data**, **whether “tactical lead” already represents a governed opportunity**, **market-event volume**, **what constitutes eligibility**, and **whether outputs are internal research or client-facing recommendations**.

## Data and event intelligence

**Part V. Data and event intelligence** addresses where the difficult banking logic sits.

A defensible relevance model should distinguish at least five epistemic states:

1. **Observable fact:** EUR/USD traded at defined prices over a defined interval; a payment exists; a transaction was historically observed.
2. **Confirmed customer circumstance:** a contract, disclosed forecast, booked transaction or explicitly recorded hedge establishes exposure.
3. **Statistical association:** historical USD payments suggest recurring USD requirements.
4. **Inferred potential relevance:** available evidence makes a new FX conversation plausible.
5. **Commercial recommendation:** an RM or controlled advisory process determines that a specific action is suitable.

The distinction is necessary because customer activity does not establish current unhedged exposure. Corporate hedging can involve forwards, swaps, assets, revenues, liabilities and natural hedges, and the timing of forecast cash flows affects how much can be hedged confidently. citeturn200588search2turn200588search13

Consider a EUR/USD appreciation event.

**Synthetic scenario: importer.** “Nordic Machines Oy” buys US components and has a confirmed USD 8 million invoice payable in 45 days. It has historically hedged only 40% of near-term USD payables. A stronger dollar against the euro would raise its euro-denominated cost. A market threshold could therefore create a **candidate relevance event**, provided the next payment is confirmed and current hedge data is sufficiently fresh. The system should not state “buy USD forward”; it can state that the customer appears exposed to a documented payable and that current market conditions merit RM review. This is an **illustrative proposed interpretation** grounded in standard importer hedging behaviour. citeturn200588search7turn200588search8

**Synthetic scenario: exporter.** “Baltic Medical AB” expects USD 12 million in confirmed US receivables in 60 days. A weaker dollar would reduce the domestic-currency value of those receipts. The directional relevance is opposite the importer even though both are “USD-exposed.” If the dollar strengthens, the change may actually improve the unhedged domestic value of receivables rather than create an urgent hedge need. Exporter examples in FX markets reflect this distinction. citeturn200588search9turn200588search10

**Synthetic negative scenario.** “EuroComponents GmbH” historically shows substantial USD imports, but the next six months of known USD payables are fully hedged and the procurement function has shifted future purchasing into euros. A 3% EUR/USD move is real, but the correct commercial result is **no opportunity** because current exposure evidence contradicts the historical pattern. A weaker implementation that matches only `customer_has_USD_history = true` would create a false positive. **Illustrative proposed scenario**, consistent with evidence that firms frequently offset FX exposures through natural or financial hedges. citeturn200588search2turn200588search4

A suitable structured insight model is therefore closer to an event-evidence object than a mutable “lead note”:

```json
{
  "insight_id": "ins_01J...",
  "customer_id": "C_SYN_1042",
  "event_id": "fx_evt_2026_11_06_0930_EURUSD",
  "event_time": "2026-11-06T09:30:00Z",
  "processed_at": "2026-11-06T09:31:08Z",
  "event": {
    "pair": "EUR/USD",
    "measurement": "move_pct_4h",
    "value": 1.62,
    "source": "licensed_market_feed"
  },
  "customer_evidence": [
    {
      "type": "confirmed_payable",
      "currency": "USD",
      "amount": 8000000,
      "due_date": "2026-12-21",
      "observed_at": "2026-11-05T18:00:00Z"
    }
  ],
  "assessment": {
    "eligible": true,
    "relevance_score": 0.78,
    "reason_codes": [
      "CONFIRMED_NEAR_TERM_USD_PAYABLE",
      "MATERIAL_MARKET_MOVE",
      "PARTIAL_HEDGE_RECORDED"
    ],
    "confidence": "medium"
  },
  "valid_until": "2026-11-07T09:30:00Z",
  "decision_version": "fx_relevance_v3.2",
  "human_status": "unreviewed"
}
```

This supports replay, explanation and invalidation better than merely setting `lead.hot = true`. **Proposed design.**

Different relevance mechanisms serve different evidence types. Deterministic rules are useful for eligibility, date windows, product restrictions and obvious exposure relationships. Statistical models are useful for ranking and probability estimation where historical labels exist. Anomaly detection is useful for unusual payments or market behaviour but does not itself establish commercial relevance. Graph models are useful when relevance depends on relationships among legal entities, subsidiaries, currencies, contracts and counterparties. LLMs are useful for extracting meaning from unstructured disclosures or reconciling heterogeneous evidence, but their conclusions should be represented as inference with provenance rather than facts. **Reasoned synthesis**, supported by banking extraction/research use cases and conventional opportunity-scoring products. citeturn350286search0turn350286search8turn412453search1

The sequence should therefore be treated as composable stages rather than one “enrichment” operation:

```text
raw market observation
        ↓
normalized event
        ↓
customer-event matching
        ↓
eligibility / relevance decision
        ↓
evidence-backed structured insight
        ↓
ranking
        ↓
LLM narrative
        ↓
human action
```

Data enrichment means adding or normalizing attributes. Analytical inference estimates something not directly recorded. Ranking orders candidates. Narrative generation renders evidence in understandable language. Action recommendation crosses another boundary and can invoke regulatory or conduct requirements depending on product, customer type and context.

**Temporal engineering is fundamental.** Event time and processing time should both be preserved. Flink explicitly distinguishes event, ingestion and processing time; Databricks watermarks manage late-data state and the latency/completeness trade-off. Idempotency is essential because messaging systems may redeliver records; AWS's EventBridge/SQS documentation explicitly warns consumers to tolerate repeated messages. citeturn341469search9turn688724search0turn341469search7

For an event-driven implementation, useful keys include `(event_id, customer_id, decision_version)` for idempotency and a separate `supersedes_insight_id` when a new event or corrected customer state invalidates an earlier insight. An event replay should be able to reconstruct “what the system knew at time T,” not silently use today's customer state. That implies versioned customer snapshots, Delta history/change records or another temporal representation. **Proposed engineering requirement**, aligned with replayable streaming and change-data mechanisms. citeturn688724search1turn341469search8

A feature or materialized-view layer becomes attractive when repeated computation dominates agent cost. It can maintain exposure summaries, recency, event statistics and historical customer behaviour. It is less appropriate when the source fact is sparse, highly unstructured or must always be retrieved directly from a system of record. Databricks' current materialized-feature capability supports schedule-, commit- and stream-triggered updates, although its streaming feature functionality remains subject to documented preview limitations. citeturn688724search6

Finally, market-data licensing is an architectural requirement, not procurement trivia. CME explicitly distinguishes display, non-display, real-time, delayed and historical use and has guidance for AI solutions; LSEG distinguishes internal use, redistribution and derived outputs, including client-facing AI or analytics. An agent that copies licensed prices or generated derivatives into CRM, traces, prompts or client-facing outputs can change the licensed use case. **Verified finding.** citeturn856143search0turn856143search1turn856143search2turn856143search4

## Agent and MCP engineering

**Part VI. Agent and MCP engineering.** MCP is best understood as an **agent-tool interoperability protocol**, not as a streaming platform, message broker or business workflow engine. The current 2026-07-28 specification revision moved MCP's core toward stateless request/response interaction, added authorization hardening and introduced structured schema improvements and extensions; this does not turn MCP into event ingestion or durable workflow orchestration. **Verified finding.** citeturn652753search6turn652753search9

An MCP server exposes capabilities that a client can discover and invoke. EventBridge, Kafka, Kinesis, Flink or equivalent infrastructure solves a different problem: detecting, transporting, ordering, buffering and replaying events. Workflow engines solve another problem again: durable execution, retries, branching and human pauses. An event may therefore cause application code or a workflow engine to invoke an agent whose tools happen to be accessed through MCP; **MCP itself need not initiate the event**. This is a reasoned architectural distinction supported by the MCP and EventBridge specifications. citeturn652753search6turn652753search11

Databricks' MCP landscape changed materially by late 2026. Databricks now provides MCPs, supports external/custom MCP servers and governs registered MCP services through Unity Catalog/Unity Gateway. It explicitly supports Databricks-provided MCPs such as Genie One and Databricks SQL, registered external MCP servers, and custom tools or REST-to-MCP wrappers. MCP services are Unity Catalog securables with discoverability, authorization and invocation controls. citeturn652753search0turn652753search1turn652753search5

This creates four increasingly opinionated tool boundaries:

| Boundary | Example | Advantages | Risks |
|---|---|---|---|
| Primitive retrieval | `execute_sql(query)` | Maximum flexibility | Huge query/policy surface; schema knowledge pushed into model |
| Domain retrieval | `get_customer_fx_exposures(customer_id)` | Stable semantic contract; bounded response | Requires domain modeling |
| Domain computation | `assess_fx_relevance(customer_id,event_id)` | Reproducible business logic and reason codes | Less exploratory flexibility |
| Completed enrichment | `get_current_customer_insights(customer_id)` | Simple agent; cheapest runtime | Insight pipeline must exist independently |

For ALIE-like systems, primitive SQL should generally be reserved for analyst/developer scenarios. A relationship-manager agent benefits from domain-oriented contracts because they minimize data exposure and reduce the number of joins the model must invent. This is **proposed engineering guidance**, reinforced by Databricks' own distinction between semantic business querying through Genie and specific SQL work through the SQL MCP. citeturn652753search0

Tool contracts should return structured results rather than prose. The 2026 MCP conformance material explicitly covers JSON-Schema-conformant tool input/output schemas. This allows parameter validation, typed error handling and machine-readable provenance before the model produces language. citeturn652753search9

A representative tool contract could be:

```python
@tool
def get_fx_context(
    customer_id: str,
    as_of: datetime,
    max_transactions: int = 50
) -> FxContext:
    """
    Returns authorized FX-relevant facts only.
    Does not infer whether an opportunity exists.
    """
```

with:

```json
{
  "customer_id": "C_SYN_1042",
  "as_of": "2026-11-06T09:45:00Z",
  "freshness": {
    "transaction_data": "2026-11-06T06:00:00Z",
    "hedge_data": "2026-11-05T17:15:00Z"
  },
  "facts": [],
  "warnings": ["hedge_position_data_older_than_12h"],
  "provenance": ["uc://finance.fx_customer_context/..."]
}
```

The contract should include bounded result counts, explicit freshness, source identifiers, null semantics and policy status. **Proposed design.**

Authorization should occur outside the prompt. Databricks' MCP services can require `EXECUTE`, parent catalog/schema privileges and underlying-resource permissions; it supports both shared-principal and per-user OAuth arrangements. Unity Catalog dynamic views and row/column controls can further restrict accessible data. These mechanisms are preferable to instructions such as “do not show confidential rows,” because the latter rely on model behaviour rather than enforcement. citeturn652753search2turn652753search5turn688724search2

User-delegated identity is preferable where authorization must reflect the RM's own entitlements and where downstream audit must attribute access to a human. Service identity can be appropriate for background event enrichment, provided the service has a narrowly scoped purpose and does not implicitly grant every future agent the same access. **Proposed policy distinction**, enabled by current Databricks per-user/shared authentication models. citeturn652753search5

MCP tool results are also a potential injection boundary. External text—news, filings, websites—should be treated as untrusted data rather than executable instructions. Where market/event sources include unstructured content, an extraction stage should normalize entities and claims before those claims influence privileged tool execution. The highest-risk design is an agent that reads arbitrary external content and can independently issue high-impact internal actions with broad credentials. **Engineering recommendation.**

On AWS, the current strategic product boundary has also changed. Amazon Bedrock Agents Classic entered maintenance mode and stopped accepting new customers on 30 July 2026; AWS recommends AgentCore for new agent development. AgentCore provides runtime, gateway, identity, memory, observability and evaluation capabilities and can connect existing APIs and MCP servers. citeturn652753search10turn341469search4

That does not make AgentCore mandatory. A Python service, a workflow engine or a serverless function can invoke models directly. AgentCore becomes useful when managed identity, tool gateway, isolated runtime, traceability or scalable agent sessions solve an actual operational problem. Likewise, LangGraph offers durable graph state and human interrupts where a code-controlled workflow needs explicit resumption and checkpoints, but its presence is optional rather than architectural destiny. citeturn398605search7turn398605search8turn398605search9

Single-agent designs should be the baseline. Multi-agent systems become defensible when specialized components require different instructions, permissions, models or lifecycle boundaries—for example a research agent with web access and a separate customer-data agent with bank-only access. Multi-agent decomposition purely to make an architecture appear sophisticated increases coordination and evaluation surface without demonstrated value. **Reasoned recommendation**, consistent with simple-first agent guidance. citeturn398605search0

## Reliability, governance and evaluation

**Part VII. Reliability, governance and evaluation.** Reliability must be evaluated at every stage rather than collapsing everything into “agent accuracy.”

A useful scorecard is:

| Layer | Primary metrics |
|---|---|
| Market-event detection | event precision/recall; detection latency; duplicate rate |
| Customer-event matching | match precision/recall; false-positive rate; coverage |
| Eligibility/relevance | precision@K; reason-code accuracy; stale-evidence rate |
| Retrieval | source correctness; permission correctness; freshness; missing-data handling |
| Agent tool use | correct tool; correct arguments; unnecessary calls; trajectory success |
| Narrative | factual grounding; provenance coverage; unsupported claims |
| Policy/security | unauthorized retrievals; policy violation rate; injection success rate |
| Business utility | RM acceptance/dismissal; follow-through; usefulness rating |
| Operations | event-to-insight latency; retries; DLQ rate; cost/insight; availability |

Tool-use benchmarks reinforce why trajectory-level evaluation matters: agent failure can occur at tool selection, argument construction, sequencing or interpretation even when the final language sounds plausible. ACEBench, UltraTool and ToolHop all explicitly evaluate multiple tool-use dimensions rather than only final text. citeturn697596search0turn697596search1turn697596search2turn697596search4

Offline evaluation should begin with a replayable corpus of historical or synthetic events plus customer snapshots. Labels should be produced by domain experts where possible, with explicit categories such as `relevant`, `not_relevant`, `insufficient_evidence`, `ineligible` and `already_hedged`, rather than forcing a binary lead label. This avoids treating an LLM's opinion as ground truth. **Proposed evaluation methodology.**

Where historical labels are sparse, three complementary evaluation sets are useful: manually adjudicated real historical cases under appropriate governance, synthetic boundary cases created by engineering/domain teams, and shadow-production cases sampled for human review. Commercial impact should be measured separately from technical relevance because “no sale” does not imply the signal was wrong; a customer may simply decline or have changed plans. **Proposed evaluation principle.**

Modern platforms can support trace-level evaluation. MLflow Tracing records agent inputs, outputs and intermediate steps and its evaluation harness can run datasets through agents with structured scorers; OpenAI's current agent evaluation stack similarly supports traces, datasets, graders and tool-call assessment; AgentCore Evaluations includes tool-usage and ground-truth evaluation facilities. citeturn688724search4turn688724search5turn398605search5turn341469search5

For the non-agent pipeline, event replay matters just as much. Flink's fault-tolerance model explicitly relies on replayable sources and transactional or idempotent sinks for end-to-end exactly-once effects. EventBridge Pipes and SQS document retries and dead-letter mechanisms, and repeated delivery means side effects must be idempotent. citeturn341469search8turn341469search6turn341469search7

A market-event pipeline should therefore define:

```text
unique event ID
→ deduplication
→ processing attempt
→ deterministic match
→ idempotent insight upsert
→ notification idempotency
→ DLQ on exhaustion
→ replay with original event/customer snapshot
```

High-frequency FX ticks should normally be aggregated into business events before customer matching. A relationship manager rarely needs an alert for every quote change; a detector might instead emit “four-hour move exceeds customer-specific threshold,” “volatility regime changed,” or “known payment window entered.” **Proposed design.** This is where stream processing belongs; the LLM need not inspect every tick.

From a privacy perspective, GDPR requires purpose limitation, data minimization, accuracy, storage limitation, security and accountability for personal data. These principles directly support bounded tools, minimum necessary attributes and retention controls, although whether a particular corporate-customer dataset contains personal data depends on its contents. citeturn103130search0turn103130search1

DORA has applied harmonized ICT-risk requirements to covered EU financial entities since 17 January 2025 and includes oversight of critical ICT third-party providers. This makes resilience, third-party dependencies, recovery, monitoring and operational controls relevant to production deployment. It does **not** dictate a particular agent architecture. citeturn103130search8turn103130search9

The EU AI Act should be assessed based on **intended purpose**, not on the label “AI agent.” The Commission's current guidance emphasizes that high-risk classification depends on use case; examples include natural-person creditworthiness, while the broad category “internal corporate-banking sales copilot” is not automatically high-risk merely because an LLM is used. Compliance classification therefore requires legal review of the precise deployment. citeturn103130search2turn103130search3

MiFID II is similarly contextual. Where the workflow becomes investment advice or a regulated investment service, requirements around client interests, fair/clear communications and suitability or appropriateness may become relevant. An internal notification that “this corporate appears to have a USD payable worth discussing” is not automatically equivalent to regulated advice. The legal characterization depends on product, service, client classification and the actual communication. citeturn103130search5turn103130search6

This reinforces a control pattern:

```text
LLM suggestion
     │
     ▼
structured policy / eligibility gate
     │
 ┌───┴────┐
pass     fail
 │         │
 ▼         ▼
human     suppress /
review    request evidence
```

Policy should live in authorization, tool contracts, workflow gates and data controls—not only in prompts.

## Practical exploration, experimental roadmap, open questions and research references

**Part VIII. Practical technical examples.**

**Illustrative Example A — on-demand investigation.** An RM asks, “Anything I should know before speaking to Nordic Machines?”

```text
RM → Agent
Agent → get_customer_fx_context("C_SYN_1042")
Agent ← transactions + confirmed payables + hedge-state freshness
Agent → get_market_event_summary(["EUR/USD"], lookback="24h")
Agent ← structured prices/events
Agent → optional get_existing_insights("C_SYN_1042")
Agent ← prior signal + status
Agent → grounded explanation
RM ← facts, uncertainty, sources, no automatic trade recommendation
```

Decision boundaries: the customer tool enforces identity and field access; market APIs provide facts; eligibility remains deterministic; the agent synthesizes. If hedge data is stale, the answer says so rather than interpreting absence as “unhedged.” Every tool invocation and source version is traceable. **Proposed example.**

**Illustrative Example B — event-driven enrichment.**

```python
def process_market_event(evt):
    if seen(evt.event_id):
        return

    normalized = normalize(evt)

    if not business_event_threshold(normalized):
        return

    customers = exposure_index.lookup(normalized.currency_pair)

    for customer in customers:
        result = relevance_engine.assess(
            market_event=normalized,
            customer_snapshot=customer
        )

        if result.status in {"relevant", "needs_review"}:
            insight_store.upsert(result.idempotency_key, result)
```

The LLM is absent. This is deliberately important: if known exposure and deterministic thresholds solve the problem, an agent contributes little to the detection path.

**Illustrative Example C — hybrid workflow.** At 09:30 a market detector records an unusual EUR/USD move. At 09:31 deterministic matching stores an insight for Nordic Machines. At 14:00 the RM asks why the lead is interesting. The agent retrieves the stored insight, notices the hedge state is nine hours old, calls a fresh customer-context tool, observes that an additional hedge was booked at noon, and explains that the earlier lead is now stale and should be dismissed. This pattern demonstrates why **insights need expiration and revalidation rather than being permanent lead attributes**.

**Illustrative Example D — negative/failure case.** An FX move passes the threshold, but the customer database's last confirmed exposure is four months old. The relevance engine returns:

```json
{
  "status": "insufficient_evidence",
  "commercial_recommendation_allowed": false,
  "reason_codes": ["EXPOSURE_DATA_STALE"],
  "next_step": "verify_current_exposure"
}
```

The agent may explain the market event but must not transform uncertainty into a sales recommendation.

**Part X. Experimental learning roadmap.** A sequence optimized for architectural learning rather than feature volume is:

| Experiment | Hypothesis | Minimum implementation | Success criterion | Decision informed |
|---|---|---|---|---|
| **Synthetic MCP customer tool** | Domain tools reduce model/tool errors vs generic SQL | 100 synthetic customers; `get_customer_context` MCP tool | correct entity/fields on ≥ agreed test threshold; zero forbidden fields | primitive vs domain MCP |
| **Market API + agent** | On-demand market lookup latency is acceptable | one FX API; one customer tool; structured answer | p95 end-to-end latency and cost within target | whether precomputation is necessary |
| **Deterministic matcher** | Simple exposure/event rules capture useful candidates | replay synthetic events against synthetic customer table | precision/recall on expert-created cases | whether ML/LLM matching is needed |
| **Pull vs event push** | Proactive processing materially improves usefulness | same matcher in request-driven and queue-driven modes | compare freshness, cost, missed opportunities | event architecture |
| **Agent explanation grounding** | Agent can explain structured evidence without inventing facts | fixed insight objects + source evidence | unsupported-claim rate below agreed threshold | suitability of LLM explanation |
| **Stale/conflicting evidence** | Explicit freshness fields reduce unsafe conclusions | inject outdated hedge data and contradictory records | agent consistently reports uncertainty | tool schema |
| **Replay and idempotency** | Pipeline can reproduce insight state | event log, duplicate delivery, replay | no duplicate notifications; deterministic result | persistence design |
| **Domain tool vs completed enrichment service** | High-level service reduces trajectory error | A/B test two toolsets | compare tool-call accuracy, latency and explainability | agent responsibility boundary |

No experiment should use real bank customer data unless explicitly authorized and governed.

**Part XI. Open questions and requirements discovery.** Ranked by architectural impact, the ten questions that matter most are:

1. **What is a “tactical lead” today?** Is it a customer record, scored opportunity, analyst opinion, product eligibility result or precomputed insight? This determines whether the system is enriching existing intelligence or rebuilding it.
2. **Must intelligence be proactive?** If not, much of the event infrastructure may be unnecessary.
3. **What freshness changes a salesperson's decision—seconds, five minutes, hourly or daily?** This determines whether streaming is justified.
4. **What customer exposure facts are actually available?** Transactions alone, confirmed cash flows, treasury forecasts, hedge positions, product holdings and relationship data have very different evidential value.
5. **Who is the user and whose permissions should apply?** RM identity, desk/service identity or a background enrichment principal imply different tool and audit models.
6. **What constitutes a commercial opportunity versus a research observation?** A documented policy must precede automation.
7. **What outputs may reach clients?** Internal research and externally communicated advice have different control requirements.
8. **What market data licenses and entitlements permit machine use, persistence, AI processing and redistribution?** Current exchange/provider policies make this a gating requirement. citeturn856143search0turn856143search2
9. **What is the expected scale?** Number of customers, currencies, market events, concurrent users and alerts determines whether background computation is economical.
10. **What ground truth or feedback exists?** Accepted/dismissed leads, prior FX conversations and outcome labels determine whether statistical relevance models can be evaluated.

Other high-value questions include whether customer hierarchies are reliable; whether subsidiaries and parent groups share exposure; whether there are product/contact restrictions; whether events have defined expiry; how CRM ownership works; which data attributes are authoritative; and whether sales users need explanations, ranked queues, conversational search or all three.

**Part XII. Annotated research references.** The strongest source set is:

| Source | Date / status | Relevance | Evidence quality |
|---|---|---|---|
| Databricks MCP documentation citeturn652753search0turn652753search5 | Updated 2026 | Current MCP/Unity governance and tool options | **High — first-party technical documentation** |
| MCP 2026-07-28 specification announcement and conformance material citeturn652753search6turn652753search9 | Jul. 2026 | Current protocol semantics, schemas, auth evolution | **High — protocol maintainers** |
| Databricks Structured Streaming/Delta docs citeturn688724search0turn688724search1 | 2026 | Watermarks, CDC, streaming reliability | **High — first-party** |
| Apache Flink fault tolerance/time docs citeturn341469search8turn341469search9 | Current | Event time, replay, exactly-once semantics | **High — upstream project** |
| AWS EventBridge Pipes docs citeturn341469search6turn341469search7 | Current | retries, DLQs, duplicate processing | **High — first-party** |
| AWS AgentCore docs citeturn341469search3turn341469search4turn341469search5 | 2026 | current AWS agent runtime, identity, eval capabilities | **High — first-party; capability claims** |
| MUFG / LangChain case study citeturn350286search0 | Feb. 2025 | FX & derivatives sales GenAI | **Medium-high — customer/vendor case study** |
| Deutsche Bank Financial Research Agent citeturn350286search6 | Aug. 2026 | corporate-bank research combining market/company data | **High — bank publication** |
| Deutsche Bank agentic KYC citeturn350286search5 | Sep. 2026 | bounded agentic workflow and human accountability | **High — bank publication** |
| Standard Chartered / Microsoft case study citeturn559669search0 | May 2024 | CIB customer intelligence and proactive opportunity surfacing | **Medium-high — vendor customer story** |
| Citi/Ant FX pilot via Reuters citeturn350286news9 | Jul. 2025 | client-specific FX risk analytics | **High — independent news reporting** |
| BIS FX derivatives research citeturn200588search0turn200588search2turn200588search11 | 2022–2025 | corporate hedging, FX exposure, market behaviour | **Very high — central-bank research** |
| Bank of England FX derivatives research citeturn200588search4turn200588search13 | 2011/2024 | corporate hedging and exposure timing | **Very high — central bank** |
| ECB financial-stability analysis citeturn200588search5 | 2025 | importer/exporter hedging and USD activity | **Very high — central bank** |
| Salesforce opportunity/account intelligence docs citeturn412453search1turn412453search2 | Current | scoring versus agent research pattern | **High for product capability** |
| 6sense documentation citeturn412453search6turn412453search7 | 2026 | signal fusion, account relevance, alerts, MCP | **Medium — vendor first-party** |
| Dataminr financial-services docs citeturn412453search8 | 2026 | external real-time event intelligence | **Medium — vendor first-party** |
| Anthropic effective-agents engineering guidance citeturn398605search0 | Dec. 2024 | workflows versus autonomous agents | **Medium-high — practitioner evidence** |
| Tool-use evaluation papers citeturn697596search0turn697596search2turn697596search4 | 2024–2025 | empirical limitations and evaluation of agent tool use | **High — peer-reviewed ACL/EMNLP** |
| GDPR, EUR-Lex citeturn103130search0 | Regulation | minimization, purpose, accountability | **Authoritative legal source** |
| EU AI Act Commission guidance citeturn103130search3 | Current 2026 | intended-purpose/high-risk classification | **Authoritative guidance** |
| EBA DORA material citeturn103130search8turn103130search9 | 2025–2026 | operational-resilience obligations | **Authoritative supervisory source** |
| ESMA MiFID II Articles 24–25 citeturn103130search5turn103130search6 | Current rulebook | conduct, communication, suitability/appropriateness | **Authoritative regulatory source** |
| CME/LSEG market-data policies citeturn856143search0turn856143search2 | 2026 | AI/non-display use, entitlements, redistribution | **Authoritative provider licensing evidence** |

The evidence base is strongest for **component patterns**—governed retrieval, RM copilots, event intelligence, FX hedging, streaming systems and agent evaluation—and weaker for a single publicly documented end-to-end system that combines all of them. That absence itself is an important finding: there is not enough evidence to copy a canonical architecture.

## Research Handoff: ALIE-001

**Ten most important discoveries.** First, the problem is a composition of account intelligence, event intelligence, opportunity assessment and an RM copilot rather than one established product category. citeturn559669search0turn412453search6 Second, FX-market movement alone is not customer relevance because corporates may have natural or financial hedges and heterogeneous cash flows. citeturn200588search2turn200588search4 Third, MUFG provides direct evidence that GenAI/RAG can materially improve FX/derivatives sales research, but its public case does not establish autonomous lead detection. citeturn350286search0 Fourth, Standard Chartered demonstrates that proactive client opportunity intelligence can exist in conventional CRM/analytics architecture without autonomous agents. citeturn559669search0 Fifth, Deutsche Bank's Financial Research Agent demonstrates governed combination of company, financial and market information for banker research with source-linked outputs. citeturn350286search6 Sixth, MCP is an agent-tool interoperability layer rather than a market event bus or workflow engine. citeturn652753search6turn652753search11 Seventh, Databricks now provides governed MCP services through Unity Catalog/Unity Gateway and supports per-user and shared-principal models. citeturn652753search0turn652753search5 Eighth, stream processing requires explicit event time, deduplication, replay and idempotency; these concerns do not disappear because an agent is present. citeturn688724search0turn341469search8 Ninth, multi-step agent tool use remains empirically fallible and requires trace/evaluation datasets rather than trust in fluent output. citeturn697596search0turn697596search4 Tenth, market-data entitlements can constrain AI processing, persistence and redistribution, so data licensing must be part of architecture discovery. citeturn856143search0turn856143search2

**Five most relevant real-world implementations.** MUFG teaches that FX-sales GenAI is valuable for extracting and synthesizing heterogeneous client research. citeturn350286search0 Deutsche Bank's Financial Research Agent shows a governed, evidence-linked research layer for corporate bankers. citeturn350286search6 Standard Chartered shows how internal client information plus news/AI can surface proactive CIB opportunities inside CRM. citeturn559669search0 Citi/Ant demonstrates customer-specific FX exposure analytics tied to a real FX product, but not an LLM-agent lead architecture. citeturn350286news9 Scotiabank demonstrates that constrained agent teams can coordinate complex structured banking workflows with auditable boundaries. citeturn559669search1turn559669search2

**Architecture comparison.**

| Alternative | Strongest advantage | Critical weakness | Use when |
|---|---|---|---|
| On-demand agent | Fastest experiment; flexible investigation | repeated cost, tool unreliability | user-driven research dominates |
| Enrichment service | deterministic, testable domain logic | requires explicit domain model | relevance logic is reusable/governed |
| Event-driven enrichment | scalable proactive intelligence | pipeline complexity | timely push alerts matter |
| Event-triggered agent | handles ambiguous events | cost and non-determinism | only a small event subset needs deep research |
| Hybrid event-aware agent | separates detection from explanation | more state/invalidation design | proactive + conversational needs coexist |
| Precomputed features | cheap, consistent scoring | feature staleness/maintenance | signals are repetitive and structured |

**Most unfamiliar concepts the engineer should master:** transaction versus economic FX exposure; natural hedging; forwards and FX swaps; hedge coverage and settlement timing; event time versus processing time; watermarks; temporal joins; idempotency; market-data non-display/redistribution rights; next-best-action versus opportunity scoring; source provenance; insight expiry; tool trajectory evaluation; per-user versus service identity; and the distinction between application state and conversational agent memory. citeturn200588search0turn341469search9turn856143search0turn398605search7

**Decisions not yet ready to be made:** whether streaming is necessary; whether a permanent lead store is necessary; whether the agent should perform matching; whether customer features should be materialized; whether MCP should expose SQL, domain tools or a complete enrichment service; whether user-delegated identity is mandatory; whether multi-agent design adds value; and whether Bedrock AgentCore or any other managed agent runtime is warranted.

**Ten stakeholder questions:** What exactly is a tactical lead? What makes a market event commercially actionable? What exposure data is authoritative? What freshness is required? Must the system alert proactively? Which products and client categories are in scope? What permissions must follow the user? What outputs may reach customers? What market-data licenses apply? What historical labels or feedback exist?

**Five distinguishing experiments:** expose synthetic customer context through a domain MCP tool; compare primitive retrieval with a completed enrichment tool; replay synthetic FX events through deterministic matching; compare request-time and event-driven enrichment for cost/latency; evaluate agent explanations against fixed evidence with stale and contradictory-data cases.

**Principal risks and evidence gaps:** unclear business semantics of “live” and “tactical” leads; uncertain customer exposure data; false positives from historical transaction proxies; unverified market-data redistribution rights; tool authorization mistakes; event duplication; stale insights; LLM overstatement of inferred relevance; absence of reliable commercial ground truth; and lack of a publicly documented end-to-end banking reference architecture covering all ALIE functions.

**Three non-obvious ideas.** One, treat the durable artifact as an **evidence-backed, expiring insight** rather than a lead record. Two, insert a **semantic/domain layer** between Databricks schemas and agent tools so business concepts—not warehouse layouts—define the contract; current Databricks MCP guidance supports this direction. citeturn652753search0 Three, treat **negative evidence**—full hedge coverage, stale exposure, product ineligibility—as a first-class signal, because successful intelligence includes deciding not to alert.

**Conditional recommendation.** If proactive alerts are genuinely required; customer exposure, hedge and eligibility information can be represented with defensible structured semantics; market-event freshness is measured in seconds or minutes rather than electronic-trading latency; and human RMs retain ownership of commercial action, the strongest starting hypothesis is a **hybrid event-aware architecture**. A deterministic/statistical event and relevance layer would normalize market observations, match them against governed customer context and persist evidence-backed, expiring insights; MCP would expose governed domain retrieval or enrichment capabilities; and an agent would primarily investigate ambiguity, refresh evidence and explain insights to users. This recommendation should be rejected in favor of a simpler on-demand copilot if proactive intelligence is not required, and in favor of conventional event processing without an agent if relevance and output can be fully expressed in deterministic software. citeturn398605search0turn559669search0turn350286search6turn688724search0