# Three-Layer Agent

> A structured analysis framework based on the Three-Layer Thinking methodology (Logic → Conversion → Experience) for Claude Code.

## What is Three-Layer Thinking?

Three-Layer Thinking is a methodology for analyzing business problems through three interconnected layers:

```
Logic Layer   (想通价值体现) — Is the value proposition sound?
    ↓
Conversion Layer (系统产出实现) — Can we produce and deliver that value?
    ↓
Experience Layer (用户端产出) — Does the user actually feel that value?
```

This skill turns that methodology into a structured Claude Code agent that guides you through the analysis step by step.

## Two Modes

| Mode | Direction | Use When |
|------|-----------|----------|
| **Startup** (自上而下) | Logic → Conversion → Experience | You have an idea and want to validate it |
| **Diagnose** (自下而上) | Experience → Conversion → Logic | You have a business problem and need to find the root cause |

## Installation

### Option 1: Manual Install

Copy the `three-layer-agent` directory into your Claude Code skills folder:

```bash
# macOS / Linux
cp -r three-layer-agent ~/.claude/skills/

# Windows
xcopy three-layer-agent %USERPROFILE%\.claude\skills\three-layer-agent\ /E /I
```

### Option 2: Clone & Link

```bash
git clone https://github.com/yuxing28/three-layer-agent.git
ln -s $(pwd)/three-layer-agent ~/.claude/skills/three-layer-agent
```

After installation, restart Claude Code. The skill will auto-trigger when you use relevant phrases.

## Usage

### Trigger Phrases

The skill activates when you say things like:

- `/three-layer` or `/三层思维`
- "Help me validate a startup idea"
- "帮我分析一下这个想法"
- "帮我诊断一下问题"

### Examples

**Startup analysis (default brief mode):**
```
/three-layer startup 我想做一个面向自由职业者的AI税务助手
```

**Full depth analysis:**
```
/three-layer startup --depth=full 我想做一个面向自由职业者的AI税务助手
```

**Business diagnosis:**
```
/three-layer diagnose 我的产品用户流失率从5%涨到了15%，不知道哪里出了问题
```

### Output Depth

| Flag | Behavior | Output Length |
|------|----------|--------------|
| `--depth=brief` (default) | Core conclusions per layer | ~800 words |
| `--depth=full` | Detailed tables and analysis per layer | ~2000-3000 words |

## What Each Step Does

### Startup Mode

1. **Step 0** — Information check: Do you have enough info to start?
2. **Step 1** — Logic Layer: 5 core questions (positioning, value, market, competition, roadmap)
3. **Step 2** — Conversion Layer: Production line design, key nodes, risks, MVP plan
4. **Step 3** — Experience Layer: User journey, touchpoints, differentiation, experience baseline
5. **Step 4** — Consistency Check: Devil's advocate challenges across all three layers
6. **Step 5** — Summary Report: Executive summary with action items

### Diagnose Mode

1. **Step 0** — Problem information check
2. **Step 1** — Problem positioning (which layer is affected?)
3. **Step 2** — Layer-by-layer diagnosis (Experience → Conversion → Logic)
4. **Step 3** — Root cause analysis (5 Why with evidence)
5. **Step 4** — Fix proposals with ROI estimates
6. **Step 5** — Diagnostic report

## Project Structure

```
three-layer-agent/
├── SKILL.md                              # Main skill definition
├── README.md                             # This file
├── LICENSE                               # MIT License
└── references/                           # Detailed templates (read on demand)
    ├── logic-layer-prompt.md             # Logic layer detailed framework
    ├── conversion-layer-prompt.md        # Conversion layer detailed framework
    ├── experience-layer-prompt.md        # Experience layer detailed framework
    ├── consistency-check-prompt.md       # Consistency check detailed framework
    ├── diagnosis-mode.md                 # Diagnose mode detailed flow
    └── output-format.md                  # Full report format template
```

## Key Design Principles

- **Framework stays, methods expand** — The three-layer structure is fixed; specific analysis methods adapt to your industry
- **Industry-adaptive** — Experience dimensions, production line mapping, and competitive analysis adjust to your domain (software, retail, food service, logistics, etc.)
- **Data honesty** — All data is tagged with confidence levels (sourced / estimated / needs verification)
- **Devil's advocate built in** — Every analysis includes a mandatory consistency check that challenges the conclusions

## Version

0.1.2 — Synced all reference files with SKILL.md v0.1.1 rules. Fixed 5 Why human-attribution example in diagnosis-mode.md, aligned data annotation system across all files, added industry adaptation to experience-layer-prompt.md, strengthened consistency-check-prompt.md with fear-proof and positive-evidence rules.

## License

[MIT](LICENSE)
