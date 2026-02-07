# The Fortress

A comprehensive adversarial security audit system for Solana/Anchor smart contracts, built as a Claude Code skill.

## What It Does

The Fortress performs a multi-phase security audit by deploying parallel specialized agents to analyze your codebase through different security lenses, then synthesizes findings into a prioritized report with attack trees and fix recommendations.

## Pipeline Overview

```
Phase 0   - Architectural analysis + KB manifest generation
Phase 0.5 - Static pre-scan (grep patterns + semgrep rules) -> HOT_SPOTS.md
Phase 1   - 10 parallel context auditors (+ conditional DeFi economic model analyzer)
Phase 1.5 - Output quality validation gate
Phase 2   - Context synthesis into unified architecture document
Phase 3   - Attack strategy generation (priority-tiered)
Phase 4   - Parallel hypothesis investigation (invariant-first, PoC reasoning, devil's advocate)
Phase 4.5 - Coverage verification against knowledge base
Phase 5   - Final synthesis (combination matrix, attack trees, severity re-calibration)
```

## Knowledge Base

128 exploit patterns across 17 files (~480KB), built from 200+ Exa research searches across 10 research waves:

| Category | Files | Content |
|----------|-------|---------|
| **Core** | 7 files | 128 exploit patterns (EPs) with CVSS, PoC outlines, detection rules, fix patterns |
| **Solana** | 4 files | Anchor version gotchas, runtime quirks, known vulnerable deps, token extensions |
| **Protocols** | 7 files | AMM/DEX, lending, staking, bridge, NFT, oracle, governance attack playbooks |
| **Reference** | 2 files | Bug bounty findings, audit firm patterns |

### Key Incidents Covered

- Wormhole ($320M), Mango Markets ($114M), Cashio ($52M), Crema Finance ($8.7M)
- MarginFi ($160M), Solend ($1.26M), Step Finance ($30-40M)
- Candy Machine V2 CVE, Metaplex pNFT bypasses, pump.fun exploits
- Agave validator crashes, Ed25519 offset bypass, multi-client divergence risks
- And 100+ more across DeFi, NFT, gaming, bridge, and infrastructure

## Focus Areas

The 10 parallel context auditors each analyze through one lens:

1. **Access Control** - Authority, signer checks, role matrices
2. **Arithmetic** - Overflow, precision loss, rounding
3. **State Machine** - Transitions, race conditions, invariants
4. **CPI & External** - Cross-program invocation, program validation
5. **Token & Economic** - Token flows, economic invariants, MEV
6. **Account Validation** - PDA derivation, type cosplay, ownership
7. **Oracle & Data** - Price feeds, staleness, manipulation
8. **Upgrade & Admin** - Upgradeability, admin functions, timelocks
9. **Error Handling** - Panics, error propagation, DoS
10. **Timing & Ordering** - Front-running, transaction ordering, atomicity

Plus a conditional **Economic Model Analyzer** for DeFi protocols.

## File Structure

```
the-fortress/
  SKILL.md                          # Main orchestrator prompt (40KB)
  agents/
    context-auditor.md              # Phase 1 agent template
    economic-model-analyzer.md      # Conditional DeFi agent
    hypothesis-investigator.md      # Phase 4 investigation agent
    final-synthesizer.md            # Phase 5 synthesis agent
  knowledge-base/
    core/                           # Exploit patterns, severity calibration, secure patterns
    solana/                         # Solana/Anchor-specific knowledge
    protocols/                      # Protocol-type attack playbooks
    reference/                      # Bug bounty and audit firm findings
  resources/
    focus-areas.md                  # Per-focus enrichment (10 areas x 9 sections)
    exploit-patterns.md             # Legacy single-file patterns (kept for reference)
    phase-05-patterns.md            # Grep pattern catalog for static pre-scan
    semgrep-rules/
      solana-anchor.yaml            # Custom Solana/Anchor semgrep rules
  templates/
    ARCHITECTURE.md                 # Phase 0 output template
    STRATEGIES.md                   # Phase 3 output template
    FINAL_REPORT.md                 # Phase 5 report template
    VERIFICATION_REPORT.md          # Phase 4.5 coverage verification template
  research/                         # Raw research from 10 waves of Exa deep-dives
```

## Usage

### Installation

Copy this directory into your project's `.claude/skills/`:

```bash
cp -R the-fortress/ your-solana-project/.claude/skills/the-fortress/
```

### Running an Audit

In Claude Code, invoke the skill:

```
/the-fortress
```

Or reference it directly in conversation:

> Run The Fortress audit on this codebase

### Audit Tiers

| Tier | Strategies | Agents | Use Case |
|------|-----------|--------|----------|
| Quick | 15-25 | 10 | Fast pre-commit check |
| Standard | 30-50 | 10-11 | Pre-launch audit |
| Comprehensive | 50-80 | 10-11 | Full security review |

### Output

The audit produces files in `.audit/`:

```
.audit/
  ARCHITECTURE.md       # Unified architecture understanding
  HOT_SPOTS.md          # Phase 0.5 static scan results
  context/              # 10-11 focus area context documents
  STRATEGIES.md         # Generated attack hypotheses
  findings/             # Individual investigation results
  VERIFICATION.md       # Coverage verification report
  FINAL_REPORT.md       # Prioritized findings with attack trees
```

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI
- A Solana/Anchor codebase to audit
- Optional: [semgrep](https://semgrep.dev/) for enhanced Phase 0.5 scanning

## Research

The `research/` directory contains raw research notes from 10 waves of investigation that built the knowledge base. These include Exa search results, compiled analyses, and gap assessments covering:

- Wave 1-5: Core Solana vulnerabilities, DeFi patterns, exploit history
- Wave 6: Gaming exploits, NFT attacks, MEV data, wallet drainers
- Wave 7: Bridge exploits, flash loans, governance attacks, reentrancy
- Wave 8: Protocol-specific deep dives (Raydium, Orca, Solend, Wormhole, Metaplex)
- Wave 9: Academic papers, security tooling, Agave 3.0, validator vulnerabilities
- Wave 10: Gap analysis, 2026 incidents, accuracy verification
