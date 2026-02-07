---
name: the-fortress
version: "1.0.0"
description: >
  The Fortress: Comprehensive adversarial security audit using parallel multi-focus context building,
  attack strategy generation from historical exploits, and batch hypothesis investigation.
  Features CVSS scoring, tiered analysis, checkpoint/resume, and fix verification mode.
user-invocable: true
allowed-tools:
  - Read
  - Write
  - Edit
  - Bash
  - Glob
  - Grep
  - Task
  - WebFetch
  - WebSearch
  - mcp__solana-mcp-server__Solana_Expert__Ask_For_Help
  - mcp__solana-mcp-server__Solana_Documentation_Search
---

# The Fortress

A comprehensive, multi-agent adversarial security audit pipeline.

> *"The best defense is a thorough offense."*

## Overview

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         THE FORTRESS                                  │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  PHASE 1: PARALLEL CONTEXT BUILDING (10 focused auditors)                   │
│  ═══════════════════════════════════════════════════════════                │
│  Each auditor analyzes the ENTIRE codebase through ONE lens                 │
│                                                                              │
│  ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐                    │
│  │Access  │ │Arith-  │ │State   │ │CPI &   │ │Token & │                    │
│  │Control │ │metic   │ │Machine │ │External│ │Economic│                    │
│  └───┬────┘ └───┬────┘ └───┬────┘ └───┬────┘ └───┬────┘                    │
│      │          │          │          │          │                          │
│  ┌───┴────┐ ┌───┴────┐ ┌───┴────┐ ┌───┴────┐ ┌───┴────┐                    │
│  │Account │ │Oracle  │ │Upgrade │ │Error   │ │Timing &│                    │
│  │Valid.  │ │& Data  │ │& Admin │ │Handling│ │Ordering│                    │
│  └───┬────┘ └───┬────┘ └───┬────┘ └───┬────┘ └───┬────┘                    │
│      └──────────┴──────────┼──────────┴──────────┘                          │
│                            ▼                                                 │
│  PHASE 2: SYNTHESIS                                                          │
│  ═══════════════════                                                         │
│  Merge all context into unified architectural understanding                  │
│                            │                                                 │
│                            ▼                                                 │
│  PHASE 3: STRATEGY GENERATION (50-100 attack hypotheses)                    │
│  ═══════════════════════════════════════════════════════                    │
│  Generate attack strategies from:                                            │
│  • Historical Solana exploits (Wormhole, Mango, Crema, etc.)               │
│  • Anchor-specific vulnerabilities                                           │
│  • DeFi attack patterns                                                      │
│  • Codebase-specific attack surface                                          │
│                            │                                                 │
│                            ▼                                                 │
│  PHASE 4: PARALLEL INVESTIGATION (configurable batch size)                  │
│  ═════════════════════════════════════════════════════════                  │
│  ┌────┐┌────┐┌────┐┌────┐┌────┐  ← Batch 1                                 │
│  │ H1 ││ H2 ││ H3 ││ H4 ││ H5 │     (5 parallel)                           │
│  └────┘└────┘└────┘└────┘└────┘                                             │
│  ┌────┐┌────┐┌────┐┌────┐┌────┐  ← Batch 2                                 │
│  │ H6 ││ H7 ││ H8 ││ H9 ││H10 │     ...                                    │
│  └────┘└────┘└────┘└────┘└────┘                                             │
│           ... (repeat until all hypotheses investigated)                     │
│                            │                                                 │
│                            ▼                                                 │
│  PHASE 5: FINAL SYNTHESIS                                                    │
│  ═══════════════════════════                                                 │
│  • Aggregate all findings                                                    │
│  • Identify combination/chained attacks                                      │
│  • Risk scoring & prioritization                                             │
│  • Generate ULTIMATE AUDIT DOCUMENT                                          │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Configuration

| Parameter | Default | Description |
|-----------|---------|-------------|
| `BATCH_SIZE` | 5 | Agents per investigation batch (recommended: 5-10) |
| `STRATEGY_COUNT` | 75 | Target attack strategies to generate (50-100) |
| `OUTPUT_DIR` | `.audit/` | Directory for all audit outputs |
| `TIER` | auto | Audit intensity: `quick`, `standard`, `deep`, or `auto` |

### Audit Tiers

| Tier | Focus Areas | Strategies | Best For |
|------|-------------|------------|----------|
| `quick` | 5 | 25-40 | Rapid sanity check, small changes, < 10 files |
| `standard` | 10 | 50-75 | Normal audits, medium codebases, 10-50 files |
| `deep` | 10+ | 100-150 | Pre-mainnet, high-value protocols, 50+ files |

**Auto-Detection:** When `TIER=auto` (default), the skill performs a pre-flight analysis:
1. Counts source files (`.rs`, `.sol`, `.move`, etc.)
2. Estimates lines of code
3. Detects protocol complexity (DeFi patterns, oracles, upgradability)
4. Suggests appropriate tier with rationale

---

## Quick Start

```
/the-fortress
```

Or with explicit tier:
```
/the-fortress --tier deep
/the-fortress --tier quick --batch-size 10
```

---

## Execution Protocol

### Phase 0: Pre-Flight Analysis & KB-MANIFEST

**Goal:** Analyze codebase to suggest optimal configuration AND generate a knowledge base loading manifest.

**Perform these checks:**
1. Count source files and estimate LOC
2. Detect ecosystem (Solana/Anchor, EVM/Foundry, Move, etc.)
3. Identify protocol patterns (AMM, lending, staking, bridges, etc.)
4. Check for high-risk components (oracles, upgradability, cross-chain)
5. Detect Token-2022/Extensions usage
6. Verify codebase compiles/builds successfully
7. **Generate KB-MANIFEST** based on detected protocol types and tier

**Output:** Configuration recommendation with rationale + KB-MANIFEST

```markdown
## Pre-Flight Analysis

**Codebase Metrics:**
- Source files: {N} files
- Estimated LOC: ~{N} lines
- Ecosystem: {Solana/Anchor | EVM/Foundry | ...}
- Protocol patterns detected: {AMM, Oracle integration, ...}

**Risk Indicators:**
- [ ] Uses external oracles → adds Oracle focus priority
- [ ] Has upgrade mechanism → adds Admin focus priority
- [ ] Cross-program/cross-contract calls → adds CPI focus priority
- [ ] Token transfers/DeFi logic → adds Economic focus priority
- [ ] Uses Token-2022/Extensions → adds token-extensions.md

**Recommended Configuration:**
- **Tier:** {quick | standard | deep}
- **Rationale:** {Why this tier is appropriate}
- **BATCH_SIZE:** {N}
- **STRATEGY_COUNT:** {N}
- **Estimated agents:** {N}

## KB-MANIFEST

### Phase 1 Agents (Context Building)
All agents load:
- knowledge-base/core/exploit-patterns-core.md
- knowledge-base/core/exploit-patterns-advanced.md
- knowledge-base/core/secure-patterns.md
- knowledge-base/core/common-false-positives.md
- knowledge-base/solana/solana-runtime-quirks.md
- knowledge-base/solana/anchor-version-gotchas.md
- knowledge-base/solana/known-vulnerable-deps.md

Tier standard+ adds:
- knowledge-base/core/exploit-patterns-incidents.md

Tier deep adds:
- knowledge-base/core/exploit-patterns-recent.md

Conditional (if detected):
- knowledge-base/solana/token-extensions.md (if Token-2022 usage found)

Protocol playbooks (matched to detected protocol types):
- knowledge-base/protocols/{detected-protocol}-attacks.md

### Phase 3 (Strategy Generation)
- knowledge-base/core/exploit-patterns-index.md (master index for hypothesis generation)
- knowledge-base/core/exploit-patterns-core.md
- knowledge-base/core/exploit-patterns-advanced.md
- knowledge-base/core/exploit-patterns-incidents.md
- knowledge-base/core/exploit-patterns-recent.md
- knowledge-base/reference/audit-firm-findings.md
- knowledge-base/reference/bug-bounty-findings.md
- All protocol playbooks from Phase 1

### Phase 4 Agents (Investigation)
- knowledge-base/core/exploit-patterns-index.md (to locate relevant EPs)
- Specific exploit-patterns-*.md file(s) based on the hypothesis category
- knowledge-base/core/common-false-positives.md
- Relevant protocol playbook (if hypothesis is protocol-specific)

### Phase 5 (Final Synthesis)
- knowledge-base/core/severity-calibration.md
- knowledge-base/core/common-false-positives.md
- knowledge-base/core/exploit-patterns-index.md (for cross-referencing)

Proceed with these settings? [Y/n/customize]
```

#### KB-MANIFEST Reference

The following table shows which KB files apply to each protocol type detected in Phase 0:

| Protocol Detected | Protocol Playbook | Priority Exploit Categories |
|-------------------|-------------------|-----------------------------|
| AMM / DEX | amm-dex-attacks.md | Arithmetic (EP-015–020), Oracle (EP-021–025), Economic (EP-058–067) |
| Lending | lending-attacks.md | Oracle (EP-021–025), Economic (EP-058–067), Logic (EP-033–041) |
| Staking / LST | staking-attacks.md | Economic (EP-058–067), Access Control (EP-026–032), CPI (EP-042–050) |
| Oracle Provider | oracle-attacks.md | Oracle (EP-021–025), CPI (EP-042–050), Timing (EP-089–090) |
| Bridge / Cross-chain | bridge-attacks.md | CPI (EP-042–050), Validation (EP-001–014), Key Mgmt (EP-068–074) |
| NFT / Marketplace | nft-attacks.md | Validation (EP-001–014), Token (EP-051–057), Access (EP-026–032) |
| Governance / DAO | governance-attacks.md | Upgrade/Gov (EP-079–083), Economic (EP-058–067), Timing (EP-089–090) |

**How to use the manifest:** After Phase 0 completes, the orchestrator reads the KB-MANIFEST section and includes the listed file paths in each agent's prompt. Agents simply `Read` the files they're told to load. Agents do NOT read the manifest themselves.

### Phase 0.5: Static Pre-Scan (Hot-Spots Map)

**Goal:** Build a hot-spots map using pattern-based static analysis before Phase 1 agents start. This gives agents concrete leads instead of searching blind.

**This phase runs automatically after Phase 0. The orchestrator runs it directly — no agent spawning needed.**

**Step 1: Check for semgrep availability**
```bash
which semgrep >/dev/null 2>&1 && echo "SEMGREP_AVAILABLE" || echo "SEMGREP_NOT_AVAILABLE"
```

**Step 2: Run pattern scan**

Read the pattern catalog from [resources/phase-05-patterns.md](resources/phase-05-patterns.md).

For each pattern category, run grep on the source files:
```bash
# Run all pattern categories from phase-05-patterns.md against the program source
# Example:
grep -rn '\.unwrap()' programs/ --include='*.rs' | head -50
grep -rn 'UncheckedAccount' programs/ --include='*.rs'
grep -rn 'invoke(' programs/ --include='*.rs'
grep -rn ' as u64' programs/ --include='*.rs'
# ... etc for each pattern in the catalog
```

If semgrep is available, also run the custom Solana/Anchor rules:
```bash
semgrep --config .claude/skills/the-fortress/resources/semgrep-rules/solana-anchor.yaml \
  --json programs/ 2>/dev/null
```

**Step 3: Generate HOT_SPOTS.md**

Write `.audit/HOT_SPOTS.md` using the output template from `resources/phase-05-patterns.md`. Organize results:
1. **By file** (sorted by risk density — files with most HIGH patterns first)
2. **By focus area** (so each Phase 1 agent can find their relevant hot-spots quickly)

**Phase 1 agents receive:** The path to `.audit/HOT_SPOTS.md` in their spawn prompt, with instruction to read it first and prioritize those locations.

---

### Pre-Flight Setup

Before starting:
1. Ensure codebase compiles/builds successfully
2. Create output directory: `mkdir -p .audit/{context,findings}`
3. Note any known issues or areas of concern
4. Run Phase 0.5 static pre-scan

### Phase 1: Parallel Context Building

**Goal:** Build 10 independent deep understandings of the codebase, each through a different security lens.

**Spawn 10 parallel agents** using the Task tool with these focuses:

| Focus Area | Agent Directive | Output File |
|------------|-----------------|-------------|
| Access Control | See [agents/context-auditor.md](agents/context-auditor.md) with FOCUS=access_control | `.audit/context/01-access-control.md` |
| Arithmetic Safety | Focus on math, overflow, precision, rounding | `.audit/context/02-arithmetic.md` |
| State Machine | Focus on state transitions, invariants, ordering | `.audit/context/03-state-machine.md` |
| CPI & External Calls | Focus on cross-program invocations, external interactions | `.audit/context/04-cpi-external.md` |
| Token & Economic | Focus on token flows, economic incentives, value extraction | `.audit/context/05-token-economic.md` |
| Account Validation | Focus on account ownership, signers, PDAs, type safety | `.audit/context/06-account-validation.md` |
| Oracle & External Data | Focus on price feeds, external data, trust assumptions | `.audit/context/07-oracle-data.md` |
| Upgrade & Admin | Focus on admin functions, upgradeability, privileged operations | `.audit/context/08-upgrade-admin.md` |
| Error Handling | Focus on error paths, failure modes, edge cases | `.audit/context/09-error-handling.md` |
| Timing & Ordering | Focus on MEV, front-running, transaction ordering | `.audit/context/10-timing-ordering.md` |

**Agent Spawn Pattern:**
```
# Read KB-MANIFEST from Phase 0 output to determine file lists
kb_files = manifest.phase1_files  # From KB-MANIFEST section above

# Read focus-specific guidance from resources/focus-areas.md
# Each focus area has: grep patterns, KB priorities, mandatory outputs,
# cross-reference handoffs, and false positive guidance

For each focus area:
  focus_guidance = read_section_from("resources/focus-areas.md", focus_area)

  Task(
    subagent_type="Explore",
    prompt="[Context Auditor Instructions from agents/context-auditor.md]
            FOCUS: {focus_area}
            OUTPUT: {output_file}

            FOCUS-SPECIFIC GUIDANCE:
            {focus_guidance}

            KNOWLEDGE BASE FILES — Read these before starting analysis:
            {kb_files formatted as bullet list of file paths}

            HOT SPOTS: Read .audit/HOT_SPOTS.md and find entries for your
            focus area. Analyze these locations FIRST with extra scrutiny,
            then expand to full codebase coverage.

            Analyze the ENTIRE codebase through this specific lens.
            Apply micro-first analysis (5 Whys, 5 Hows, First Principles).
            Write detailed findings to the output file.",
    run_in_background=true
  )
```

**Conditional 11th Agent: Economic Model Analyzer** (standard+ tiers, DeFi protocols only)

If Phase 0 detected a DeFi protocol type (AMM, lending, staking, yield, perpetual):
```
Task(
  subagent_type="general-purpose",
  prompt="[Economic Model Analyzer from agents/economic-model-analyzer.md]
          OUTPUT: .audit/context/11-economic-model.md

          PROTOCOL PLAYBOOK: {matched_protocol_playbook_path}

          Model the economic system: token flows, invariants, value extraction,
          flash loan impact, MEV sensitivity, incentive alignment.
          Write to output file.",
  run_in_background=true
)
```

**Wait for all agents to complete before proceeding.**

---

### Phase 1.5: Output Validation Quality Gate (standard+ tiers)

**Goal:** Ensure Phase 1 context documents are deep enough to drive quality downstream analysis.

**When to run:** After all Phase 1 agents complete. Skip for `quick` tier.

**Validation criteria for each context document:**

| Check | Threshold | Why |
|-------|-----------|-----|
| **Size** | >= 3,000 words | Thin documents produce weak strategies |
| **Code file references** | >= 5 files referenced | Must analyze substantial codebase portion |
| **Invariants documented** | >= 3 invariants | Core of security analysis |
| **Assumptions documented** | >= 3 assumptions | Reveals trust boundaries |
| **Cross-focus handoffs** | >= 2 items | Enables combination analysis |
| **Focus-specific mandatory sections** | All present | Per focus-areas.md requirements |

**Process:**
1. Read each `.audit/context/NN-*.md` file
2. Score against criteria above (each check: pass/fail)
3. Calculate pass rate (checks passed / total checks)
4. If pass rate < 70%, re-run that specific agent with feedback:
   - Include the original context as starting point
   - Specify which sections are missing or thin
   - Maximum 1 re-run per agent
5. Log validation results to `.audit/VALIDATION.md`

**Output:** `.audit/VALIDATION.md` (validation scores per agent, any re-runs triggered)

---

### Phase 2: Synthesis

**Goal:** Merge all context documents into a unified architectural understanding.

1. Read all context files from `.audit/context/`
2. **Deduplicate observations** — Multiple focus areas may identify the same concern. Merge duplicates into a single observation with citations from each focus that found it.
3. Identify:
   - Common themes across multiple focuses
   - Contradictions or tensions between focuses
   - Critical intersections (e.g., access control + token flow)
   - High-complexity clusters
   - **Deduplicated cross-focus observations** (same concern raised by multiple agents)
4. Write unified architecture document to `.audit/ARCHITECTURE.md`

Use template: [templates/ARCHITECTURE.md](templates/ARCHITECTURE.md)

---

### Phase 3: Strategy Generation

**Goal:** Generate 50-100 attack hypotheses based on the architectural understanding.

**KB files to load** (from KB-MANIFEST Phase 3 section):
- All exploit-patterns files (index + core + advanced + incidents + recent)
- Reference files (audit-firm-findings.md, bug-bounty-findings.md)
- Protocol playbooks matched in Phase 0

**Sources for strategy generation:**
1. Historical exploits — Use exploit-patterns-index.md to identify relevant EPs, then read full entries from the pattern files
2. Architectural weaknesses identified in Phase 2
3. Focus-specific risks from Phase 1 context
4. Protocol-specific attack surface from matched protocol playbooks

**For each strategy, document:**
- `ID`: Unique identifier (H001, H002, etc.)
- `Name`: Short descriptive name
- `Category`: Which focus area(s) it relates to
- `Estimated Priority`: **Tier 1** (CRITICAL potential — investigate first), **Tier 2** (HIGH potential), or **Tier 3** (MEDIUM-LOW potential)
- `Hypothesis`: What the attacker would try to achieve
- `Attack Vector`: How the attack would be executed
- `Target Code`: Specific functions/modules to investigate
- `Potential Impact`: What damage could occur
- `Historical Precedent`: Similar past exploits (if any)
- `Investigation Approach`: How to validate/invalidate this hypothesis

**Deduplication check:** Before finalizing strategies, scan for overlapping strategies that target the same code path with the same attack type. Merge overlapping strategies into a single, broader hypothesis rather than investigating the same code path twice.

Write all strategies to `.audit/STRATEGIES.md`

Use template: [templates/STRATEGIES.md](templates/STRATEGIES.md)

---

### Phase 4: Parallel Investigation

**Goal:** Investigate each attack hypothesis with dedicated agents.

**Priority-Based Batching:**

Sort strategies by Estimated Priority before batching. Tier 1 (CRITICAL potential) investigated first, then Tier 2 (HIGH), then Tier 3 (MEDIUM-LOW). This ensures the most important findings are captured even if context resets.

```
# Sort strategies: Tier 1 first, then Tier 2, then Tier 3
sorted_strategies = sort_by_priority(strategies)

batch_count = ceil(len(sorted_strategies) / BATCH_SIZE)

# === Batch 1 === (Tier 1 strategies prioritized)
batch_1 = sorted_strategies[0:BATCH_SIZE]
for strategy in batch_1:
    Task(
        subagent_type="general-purpose",
        prompt="[Hypothesis Investigator from agents/hypothesis-investigator.md]

                STRATEGY: {strategy}
                ARCHITECTURE: Read .audit/ARCHITECTURE.md

                EXISTING FINDINGS: Check .audit/findings/ for any completed
                investigations. If a prior finding already covers your hypothesis's
                code path, reference it rather than re-analyzing. Focus on what's NEW.

                Investigate this specific attack hypothesis.
                Determine: CONFIRMED / POTENTIAL / NOT VULNERABLE / NEEDS MANUAL REVIEW
                Write finding to .audit/findings/{strategy.id}.md",
        run_in_background=true
    )
wait_for_batch_completion()

# === Strategy Supplement (after Batch 1 only) ===
# Read Batch 1 findings. If any CONFIRMED or POTENTIAL, generate up to 10
# supplemental strategies (S001-S010) inspired by early findings.
# Add to STRATEGIES.md under "Supplemental Strategies" section.
# Append to end of investigation queue (will be in later batches).
if has_confirmed_or_potential(batch_1_findings):
    supplement_strategies = generate_supplemental(batch_1_findings, max=10)
    append_to_strategies(supplement_strategies)
    sorted_strategies.extend(supplement_strategies)

# === Remaining Batches ===
for batch_num in 2..batch_count:
    strategies_batch = sorted_strategies[batch_start:batch_end]
    for strategy in strategies_batch:
        Task(
            subagent_type="general-purpose",
            prompt="[Hypothesis Investigator from agents/hypothesis-investigator.md]
                    ... (same as Batch 1)",
            run_in_background=true
        )
    wait_for_batch_completion()
```

**Each investigator:**
1. Reads the architectural understanding
2. Checks existing findings for overlap (deduplication)
3. Focuses on their assigned hypothesis
4. Traces the attack path through code
5. Determines vulnerability status with confidence score
6. Documents finding with evidence

---

### Phase 4.5: Coverage Verification (standard+ tiers)

**Goal:** Goal-backward check that nothing was missed before final synthesis.

**When to run:** After all Phase 4 batches complete. Skip for `quick` tier.

**What "coverage" means — all three dimensions are checked:**
1. **Instruction coverage:** Every externally-callable instruction was analyzed by at least one Phase 1 agent
2. **EP coverage:** Every relevant EP from the loaded KB was considered against the codebase
3. **Playbook coverage:** Protocol-specific checklist items from the matched playbook were all addressed

**How it works:**

Spawn a single agent that reads:
- `.audit/ARCHITECTURE.md` (instruction list from Phase 2)
- All `.audit/findings/H*.md` (what was investigated)
- The KB-MANIFEST (what should have been checked)
- The matched protocol playbook's "Red Flags Checklist" section

The agent produces `.audit/COVERAGE.md`:

```markdown
## Coverage Verification Report

### Instruction Coverage
| Instruction | Analyzed By | Findings |
|-------------|-------------|----------|
| initialize  | 01,06,08    | H003, H017 |
| deposit      | 02,05,07    | H001, H012 |
| withdraw     | 02,05,07    | H002 |
| admin_update | 08          | — ⚠ ONLY ONE AGENT |

### EP Coverage Gaps
EPs from loaded KB not addressed by any hypothesis:
- EP-054 (Token-2022 Transfer Fee) — NOT INVESTIGATED (codebase uses Token-2022)
- EP-076 (Front-Runnable Init) — NOT INVESTIGATED (has init instruction)

### Playbook Coverage Gaps
Red flags from {protocol}-attacks.md not addressed:
- "Check liquidation cascade risk" — NO FINDING ADDRESSES THIS

### Gap Hypotheses (auto-generated)
- G001: EP-054 transfer fee not accounted in withdraw [CRITICAL gap — investigate]
- G002: EP-076 init front-run on initialize instruction [HIGH gap — investigate]
- G003: Liquidation cascade per lending playbook [MEDIUM gap — flag only]
```

**What happens with gaps:**
- **CRITICAL/HIGH gaps:** Generate additional hypotheses and run one more Phase 4 batch
- **MEDIUM/LOW gaps:** Flag in the final report as "Not Investigated — Manual Review Recommended"

The gap investigation batch follows the same Phase 4 process (spawn investigators for G001, G002, etc.).

**Output:** `.audit/COVERAGE.md` + optional additional `.audit/findings/G*.md` files

---

### Phase 5: Final Synthesis

**Goal:** Aggregate all findings and identify combination attacks.

**KB files to load** (from KB-MANIFEST Phase 5 section):
- severity-calibration.md, common-false-positives.md, exploit-patterns-index.md

1. **Read all findings** from `.audit/findings/` (including any G*.md gap findings)
2. **Read coverage report** from `.audit/COVERAGE.md` (if Phase 4.5 ran)
2. **Categorize by severity:**
   - CRITICAL: Direct fund loss, complete compromise
   - HIGH: Significant economic damage, privilege escalation
   - MEDIUM: Limited damage, conditional exploitation
   - LOW: Minor issues, theoretical concerns
   - INFO: Best practice improvements, no security impact

3. **Combination Attack Analysis:**
   - Can any LOW findings combine to create HIGH impact?
   - Do any MEDIUM findings enable other attacks?
   - Are there multi-step attack chains?

4. **Generate ULTIMATE AUDIT DOCUMENT:**
   - Executive Summary
   - Critical Findings (immediate action required)
   - High-Priority Findings
   - Medium-Priority Findings
   - Low-Priority Findings
   - Informational Notes
   - Combination Attack Analysis
   - Recommendations by Priority
   - Appendix: All Investigation Details

Write to `.audit/FINAL_REPORT.md`

Use template: [templates/FINAL_REPORT.md](templates/FINAL_REPORT.md)

---

## Supporting Resources

| Resource | Purpose |
|----------|---------|
| [resources/focus-areas.md](resources/focus-areas.md) | Detailed guidance for each Phase 1 focus (with per-focus enrichment) |
| [resources/phase-05-patterns.md](resources/phase-05-patterns.md) | Grep pattern catalog for Phase 0.5 static pre-scan |
| [resources/semgrep-rules/solana-anchor.yaml](resources/semgrep-rules/solana-anchor.yaml) | Custom Semgrep rules for Solana/Anchor (optional) |
| [agents/context-auditor.md](agents/context-auditor.md) | Phase 1 agent instructions |
| [agents/economic-model-analyzer.md](agents/economic-model-analyzer.md) | Phase 1 conditional DeFi economic analysis agent |
| [agents/hypothesis-investigator.md](agents/hypothesis-investigator.md) | Phase 4 agent instructions |
| [agents/final-synthesizer.md](agents/final-synthesizer.md) | Phase 5 agent instructions |

### Knowledge Base (loaded via KB-MANIFEST)

```
knowledge-base/
├── core/                                   # Foundational (loaded per manifest)
│   ├── exploit-patterns-index.md           # Master index — 128 EPs, cross-refs, detection keywords (11KB)
│   ├── exploit-patterns-core.md            # EP-001–067: validation, arith, oracle, access, logic, CPI, token, economic (45KB)
│   ├── exploit-patterns-advanced.md        # EP-068–097: key mgmt, init, upgrade, DoS, race, advanced bypass (31KB)
│   ├── exploit-patterns-incidents.md       # EP-098–118: audit findings, bounties, niche, cross-chain lessons (48KB)
│   ├── exploit-patterns-recent.md          # EP-119–128: protocol-specific, infra, gap analysis (28KB)
│   ├── secure-patterns.md                  # Canonical safe implementations (47KB)
│   ├── severity-calibration.md             # CVSS scoring reference (10KB)
│   └── common-false-positives.md           # Known FP patterns to reduce noise (13KB)
├── solana/                                 # Solana-specific (always loaded for Solana audits)
│   ├── anchor-version-gotchas.md           # Anchor version-specific pitfalls (8KB)
│   ├── token-extensions.md                 # Token-2022 attack surface (12KB, conditional)
│   ├── solana-runtime-quirks.md            # Runtime edge cases + Agave 3.0 (16KB)
│   └── known-vulnerable-deps.md            # Dependency version risks (8KB)
├── protocols/                              # Protocol playbooks (loaded conditionally by Phase 0)
│   ├── amm-dex-attacks.md                  # AMM/DEX attack playbook (20KB)
│   ├── lending-attacks.md                  # Lending protocol playbook (20KB)
│   ├── staking-attacks.md                  # Staking/LST playbook (16KB)
│   ├── oracle-attacks.md                   # Oracle manipulation playbook (16KB)
│   ├── bridge-attacks.md                   # Bridge/cross-chain playbook (24KB)
│   ├── nft-attacks.md                      # NFT/marketplace playbook (20KB)
│   └── governance-attacks.md               # DAO/governance playbook (16KB)
└── reference/                              # Supplementary (Phase 3 + Phase 5)
    ├── audit-firm-findings.md              # Aggregated public audit findings (16KB)
    └── bug-bounty-findings.md              # Aggregated bounty disclosures (20KB)
```

---

## Relationship to Other Skills

This skill orchestrates and builds upon:

| Skill | How It's Used |
|-------|---------------|
| `audit-context-building` | Foundation for Phase 1 micro-analysis methodology |
| `solana-vulnerability-scanner` | Patterns inform strategy generation |
| `differential-review` | Can be used post-audit for change review |
| `sharp-edges` | Footgun patterns feed into strategy generation |

---

## Output Structure

```
.audit/
├── context/
│   ├── 01-access-control.md
│   ├── 02-arithmetic.md
│   ├── 03-state-machine.md
│   ├── 04-cpi-external.md
│   ├── 05-token-economic.md
│   ├── 06-account-validation.md
│   ├── 07-oracle-data.md
│   ├── 08-upgrade-admin.md
│   ├── 09-error-handling.md
│   ├── 10-timing-ordering.md
│   └── 11-economic-model.md  ← DeFi only (conditional, standard+ tiers)
├── findings/
│   ├── H001.md
│   ├── H002.md
│   ├── ... (one per strategy)
│   ├── S001.md              ← Supplemental findings (from Batch 1 insights)
│   ├── G001.md              ← Gap findings (from Phase 4.5, if any)
│   └── G002.md
├── HOT_SPOTS.md             ← Phase 0.5 static pre-scan results
├── ARCHITECTURE.md
├── STRATEGIES.md
├── COVERAGE.md              ← Coverage verification report (Phase 4.5)
├── FINAL_REPORT.md          ← The Ultimate Audit Document
└── STATE.json               ← Checkpoint/resume state
```

---

## Checkpoint & Resume

The skill maintains audit state in `.audit/STATE.json` for resumability.

### State Schema

```json
{
  "version": "1.0.0",
  "audit_id": "uuid-v4",
  "started_at": "ISO-8601 timestamp",
  "last_updated": "ISO-8601 timestamp",
  "config": {
    "tier": "standard",
    "batch_size": 5,
    "strategy_count": 75,
    "ecosystem": "solana"
  },
  "phases": {
    "phase_0_preflight": {
      "status": "completed",
      "completed_at": "ISO-8601"
    },
    "phase_1_context": {
      "status": "in_progress",
      "agents": {
        "access_control": "completed",
        "arithmetic": "completed",
        "state_machine": "in_progress",
        "cpi_external": "pending",
        ...
      }
    },
    "phase_2_synthesis": {
      "status": "pending"
    },
    "phase_3_strategies": {
      "status": "pending",
      "count": 0
    },
    "phase_4_investigation": {
      "status": "pending",
      "batches_completed": 0,
      "batches_total": 0,
      "strategies": {
        "H001": "pending",
        "H002": "pending",
        ...
      }
    },
    "phase_5_synthesis": {
      "status": "pending"
    }
  }
}
```

### Checkpoint Behavior

**Write checkpoint after:**
- Each Phase 1 agent completes
- Phase 2 synthesis completes
- Phase 3 strategy generation completes
- Each Phase 4 investigation batch completes
- Phase 5 final synthesis completes

### Resume Command

```
/the-fortress --resume
```

**Resume behavior:**
1. Read `.audit/STATE.json`
2. Display current progress
3. Resume from last incomplete phase/batch
4. Skip already-completed work

**Example resume output:**
```
## Resuming Audit: abc123...

**Previous progress:**
- Phase 0: ✓ Complete
- Phase 1: ✓ Complete (10/10 agents)
- Phase 2: ✓ Complete
- Phase 3: ✓ Complete (75 strategies)
- Phase 4: ⚡ In Progress (3/15 batches, 15/75 strategies)
- Phase 5: ○ Pending

Resuming from Phase 4, Batch 4...
```

### Manual State Recovery

If STATE.json is corrupted, the skill can reconstruct state by:
1. Scanning `.audit/context/` for completed Phase 1 agents
2. Checking for `ARCHITECTURE.md` (Phase 2)
3. Checking for `STRATEGIES.md` (Phase 3)
4. Scanning `.audit/findings/` for completed investigations
5. Checking for `FINAL_REPORT.md` (Phase 5)

---

## Verification Mode

After fixes are applied (potentially in a different session), use verification mode to confirm fixes.

### Command

```
/the-fortress --verify
```

### How It Works

1. **Read existing report**: Parse `.audit/FINAL_REPORT.md`
2. **Extract findings**: Identify all CONFIRMED and POTENTIAL issues
3. **Re-investigate**: For each finding, check if the vulnerability still exists
4. **Detect regressions**: Look for new issues introduced by fixes
5. **Generate verification report**: `.audit/VERIFICATION_REPORT.md`

### Verification Process

```
┌─────────────────────────────────────────────────────────────┐
│                    VERIFICATION MODE                         │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  1. Load FINAL_REPORT.md                                    │
│     └─► Extract CONFIRMED + POTENTIAL findings              │
│                                                              │
│  2. For each finding:                                       │
│     ├─► Locate original vulnerability location              │
│     ├─► Check if code has changed (git diff)                │
│     ├─► Re-run investigation on current code                │
│     └─► Determine: FIXED | PARTIALLY_FIXED | NOT_FIXED      │
│                                                              │
│  3. Scan for regressions:                                   │
│     └─► Quick scan of changed files for new issues          │
│                                                              │
│  4. Generate VERIFICATION_REPORT.md                         │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

### Verification Statuses

| Status | Meaning |
|--------|---------|
| `FIXED` | Vulnerability no longer exists, proper fix applied |
| `PARTIALLY_FIXED` | Issue addressed but not completely, or new variant exists |
| `NOT_FIXED` | Vulnerability still present in code |
| `REGRESSION` | Fix introduced a new vulnerability |
| `CANNOT_VERIFY` | Code structure changed significantly, manual review needed |

### Verification Report Template

See [templates/VERIFICATION_REPORT.md](templates/VERIFICATION_REPORT.md)

### Example Usage

```
# After initial audit
/the-fortress
# → Produces FINAL_REPORT.md with 5 findings

# Developer fixes issues in separate session(s)
# ...

# Verify fixes
/the-fortress --verify
# → Produces VERIFICATION_REPORT.md

# Example output:
## Verification Results

| ID | Original Severity | Status | Notes |
|----|------------------|--------|-------|
| H001 | CRITICAL | ✓ FIXED | Signer check added at line 45 |
| H002 | HIGH | ⚠ PARTIALLY_FIXED | Auth check added but missing edge case |
| H003 | MEDIUM | ✗ NOT_FIXED | Vulnerability unchanged |
| H004 | HIGH | ✓ FIXED | Overflow check added |
| NEW | - | 🔴 REGRESSION | Fix for H001 introduced new CPI issue |
```

---

## Quality Checklist

Before considering the audit complete:

- [ ] KB-MANIFEST generated by Phase 0
- [ ] Phase 0.5 hot-spots scan completed (HOT_SPOTS.md generated)
- [ ] All context audits completed (10 base + conditional economic model)
- [ ] Architecture synthesis captures cross-cutting concerns
- [ ] At least 50 attack strategies generated
- [ ] All strategies investigated (no skipped)
- [ ] Coverage verification passed (standard+ tiers) — no CRITICAL/HIGH gaps remaining
- [ ] Combination attack analysis performed
- [ ] All findings have severity + recommendation
- [ ] FINAL_REPORT.md is comprehensive
- [ ] No "unclear" or "TBD" items remain

---

## Estimated Resource Usage

| Phase | Agents | Parallelism | Notes |
|-------|--------|-------------|-------|
| Phase 0.5 | 0 | Sequential | Grep/semgrep pre-scan (orchestrator) |
| Phase 1 | 10-11 | 10-11 parallel | Context building (+economic model if DeFi) |
| Phase 2 | 1 | Sequential | Synthesis |
| Phase 3 | 1 | Sequential | Strategy generation |
| Phase 4 | 50-100 | 5-10 batches | Investigation |
| Phase 5 | 1 | Sequential | Final synthesis |

**Total: 63-112 agent invocations** depending on strategy count and batch size.

---

## Troubleshooting

| Issue | Resolution |
|-------|------------|
| Agent timeout | Increase timeout, reduce scope |
| Duplicate findings | Phase 5 synthesizer deduplicates |
| Missing context | Re-run specific Phase 1 focus |
| Too many strategies | Increase batch size, accept longer runtime |
| Incomplete investigation | Resume from last completed batch |

---

## Non-Goals

This skill does NOT:
- Generate exploit code (security research only)
- Automatically fix vulnerabilities
- Replace human auditor judgment
- Guarantee completeness (defense in depth required)

The output is a comprehensive starting point for security hardening, not a certification of security.
