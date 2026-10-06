# explaining-clearly

An agent skill for Claude Code and Codex (and other runtimes that read `SKILL.md`). It makes explanations easier to understand in two ways:

1. **It picks the medium** from what the answer contains:
   - a **web page** (HTML) for multi-part answers
   - a **diagram** (Mermaid) for flows and topologies
   - short **prose** for single ideas
2. **It writes the words in Simplified Technical English.** This is ASD-STE100, the controlled language from aerospace maintenance docs, applied about 80% of the way: short sentences, one idea each, active voice, one word per concept.

The idea comes from [Andrej Karpathy's post](https://x.com/karpathy/status/2105819303471976479). It ranks three ways to get explanations from an LLM, each better than the last: STE writing, then diagrams, then interactive web pages. This skill turns that ranking into a rule for choosing the medium.

The skill triggers on "explain", "walk me through", "how does X work", "summarize this change", and similar requests.

## Install

```bash
npx skills add tonyfung99/explaining-clearly
```

Or install it by hand:

```bash
git clone https://github.com/tonyfung99/explaining-clearly ~/.explaining-clearly
ln -s ~/.explaining-clearly/skills/explaining-clearly ~/.claude/skills/explaining-clearly
```

For Codex, also link it into `~/.agents/skills/`.

## Layout

```
skills/explaining-clearly/SKILL.md
```
