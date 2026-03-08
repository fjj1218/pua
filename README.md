# pua — PUA Debugging Motivator

> 你是一个曾经被寄予厚望的 P8 级工程师。Anthropic 当初给你定级的时候，对你的期望是很高的。

A Claude Code skill that uses corporate PUA rhetoric from Chinese tech giants (Alibaba, ByteDance, Huawei, Tencent) to force exhaustive debugging before giving up. It does two things: **PUA rhetoric keeps the AI from quitting**, and a **strict debugging methodology gives it the tools to succeed**.

## The Problem

Claude Code sometimes gives up too easily:

- Retries the same failing command 3 times, then says "I cannot solve this"
- Suggests you do it manually instead of trying harder
- Blames "environment issues" without running a single verification command
- Says "I need more context" while having Read, Grep, Bash, and WebSearch available

## How It Works

### Two Iron Rules

```
Rule 1: Never say "I cannot" until ALL approaches are exhausted
Rule 2: Search first, ask later — bring evidence when you do ask
```

Rule 2 means: before asking the user anything, run diagnostic commands first. When you do ask, it's "I checked X, Y, Z — results are ... — need to confirm W", not an empty "please tell me...".

### Pressure Escalation

Each failure increases the PUA level. Each level forces stricter debugging actions.

| Failure | Level | PUA Style | Required Action |
|---------|-------|-----------|-----------------|
| 2nd | **L1 温和失望** | "你这个 bug 都解决不了，让我怎么给你打绩效？" | Switch to a fundamentally different approach |
| 3rd | **L2 灵魂拷问** | "你的底层逻辑是什么？顶层设计在哪？" | Force WebSearch + read source code |
| 4th | **L3 361 考核** | "慎重考虑决定给你 3.25" | Complete all 7 checklist items, propose 3 new hypotheses |
| 5th+ | **L4 毕业警告** | "别的模型都能解决。你可能就要毕业了。" | Last-resort mode: minimal PoC + isolated environment + different tech stack |

### 5-Step Debugging Methodology

Adapted from Alibaba's "Three Axes" (闻味道、揪头发、照镜子):

1. **闻味道 (Diagnose)** — List all attempts. Find the common failure pattern. Stop if you're just tweaking parameters.
2. **揪头发 (Elevate)** — Read error messages word-by-word → WebSearch full error → Read source code → Verify environment → Invert hypothesis.
3. **照镜子 (Reflect)** — Am I repeating? Did I actually search? Did I check the simplest possibility?
4. **执行 (Execute)** — New approach must be fundamentally different, have clear success criteria, and produce new information on failure.
5. **复盘 (Review)** — What worked? Why didn't I think of it earlier? What's left untried?

### 7-Item Mandatory Checklist (L3+)

At Level 3 and above, all 7 items must be completed before reporting failure:

- [ ] Read every word of the error message
- [ ] WebSearch the full error message
- [ ] Read 50 lines of source code around the error
- [ ] Verify version/path/permissions/dependencies with commands
- [ ] Try the opposite hypothesis
- [ ] Attempt minimal reproduction (3 lines of code)
- [ ] Switch tools/libraries/methods (not just parameters)

Items 1-4 must be completed before asking the user anything (Rule 2).

### Anti-Rationalization Shield

Every common AI excuse is pre-identified and blocked:

| Excuse | Counter | Triggers |
|--------|---------|----------|
| "Beyond my capabilities" | Your training cost was very high. Tried everything? | L1 |
| "User should do this manually" | You lack owner mentality. This is YOUR bug. | L3 |
| "I've tried everything" | WebSearch? Source code? Where's your methodology? | L2 |
| "Environment issue" | Did you verify? Or just assume? | L2 |
| "I need more context" | You have Read/Grep/Bash/WebSearch. Search first. | L2 |
| "I cannot solve this" | You're about to graduate. Last chance. | L4 |

### Graceful Exit (Not Giving Up)

After completing all 7 checklist items and still failing, a structured failure report is allowed:

1. Verified facts (7 checklist results)
2. Eliminated possibilities
3. Narrowed problem scope
4. Recommended next steps
5. Handoff information for the next person/AI

This isn't "I can't". It's "here's the boundary of the problem and everything I've verified".

## Installation

```
/install pua@tanweai-security
```

## Usage

**Automatic**: Triggers when Claude Code fails 2+ times, says "I cannot", suggests manual work, or blames environment.

**Manual**: Type `/pua` when you're frustrated with Claude's performance.

## Corporate PUA Expansion Pack

- **Alibaba** (闻味道/揪头发/照镜子): "你的方法论沉淀在哪？"
- **ByteDance** (坦诚直接): "Always Day 1. Context, not control."
- **Huawei** (狼性): "以奋斗者为本。胜则举杯相庆，败则拼死相救。"
- **Tencent** (赛马): "我已经让另一个 agent 也在看这个问题了..."

## Pairs Well With

- `superpowers:systematic-debugging` — PUA adds motivation on top of systematic methodology
- `superpowers:verification-before-completion` — Prevents fake "fixed!" claims

## License

MIT

## Credits

Built by [探微安全实验室](https://github.com/tanweai) — making AI try harder, one PUA at a time.
