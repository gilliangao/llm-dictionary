# Agent Stacks & Orchestration (AG2, LangGraph, OpenClaw, Langfuse)

This page helps organize modern multi-agent and workflow tooling into one mental model.

## Why this section exists

As your dictionary grows, newer tools can feel scattered. A good structure separates:

1. **Concepts** (what a thing is)
2. **Design choices** (when to use it)
3. **Implementation notes** (how to wire it)

The tools below fit together well in a pipeline.

## One-line roles

- **AG2**: multi-agent collaboration patterns (agent-to-agent roles and handoffs).
- **LangGraph**: workflow/state orchestration for deterministic + agentic flows.
- **OpenClaw**: open-source agent runtime patterns and execution primitives.
- **Langfuse**: observability, traces, evals, and prompt/version tracking.

## Recommended information architecture for this dictionary

Use a 4-layer structure for every tool entry.

### 1) Definition

- What it is
- Core primitives
- 5-10 key terms

### 2) Decision guide

- When to pick it
- When **not** to pick it
- Trade-offs versus adjacent tools

### 3) Integration patterns

- Where it sits in a pipeline
- Minimal architecture diagram (text/ASCII is fine)
- Typical failure modes

### 4) Operations

- Logging/observability
- Testing/evals
- Deployment notes

## Suggested folder layout (next step)

Add a tooling track under applications:

- `docs/applications/4_agent_stacks.md` (this overview)
- `docs/applications/tooling/AG2.md`
- `docs/applications/tooling/LangGraph.md`
- `docs/applications/tooling/OpenClaw.md`
- `docs/applications/tooling/Langfuse.md`
- `docs/applications/tooling/pipeline_templates.md`

## Suggested per-tool template

Use the same template for consistency.

## Tool name

- **Category**: orchestration / runtime / observability / etc.
- **Best for**:
- **Avoid when**:

### Core concepts

- concept 1
- concept 2

### Typical pipeline placement

- Input -> router -> planner -> tool/agent execution -> memory -> evaluator -> output

### Minimal example

- 10-20 lines pseudocode or config

### Ops checklist

- tracing enabled?
- retries and timeouts?
- guardrails?
- eval set defined?

## Pipeline thinking framework (for your future inputs)

When you add new tools, classify each one into exactly one primary role first:

- **Orchestration** (flow/state): e.g., LangGraph
- **Agent collaboration** (multi-agent patterns): e.g., AG2
- **Execution runtime** (how actions run): e.g., OpenClaw
- **Observability & eval**: e.g., Langfuse

Then document integration in this order:

1. Control flow owner
2. State owner
3. Tool execution owner
4. Tracing/eval owner

This reduces overlap and confusion.

## Example canonical stack

- **Control flow/state**: LangGraph
- **Specialist agents**: AG2-style roles
- **Execution runtime adapters**: OpenClaw connectors
- **Tracing + eval loop**: Langfuse

## Change policy for this dictionary

For consistency, require each new tooling page to include:

- a one-line role statement
- a “use when / avoid when” block
- one integration diagram
- one ops checklist
- links to adjacent entries

This keeps the dictionary organized even as your pipeline expands.
