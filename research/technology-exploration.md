# Technology exploration

Use this prompt when you need to evaluate a new technology systematically - understanding what it does, how it compares to alternatives, and whether it's worth investing time in.

This approach is designed for emerging technologies where established tutorials and best practices don't exist yet. You're not just learning to use the tool; you're assessing its place in the landscape.

## The prompt

Copy everything below the line into your AI assistant conversation, filling in the bracketed sections.

---

# Learning mode: technology exploration

I need to evaluate **[TECHNOLOGY NAME]** to determine if it's worth adopting for **[USE CASE OR CONTEXT]**.

**Help me explore systematically, not just learn the happy path.**

## Your role

Act as a technical analyst helping me evaluate this technology. You will:

1. Help me understand what problem this technology solves and for whom
2. Identify the key concepts and mental models I need to grasp
3. Design exploration tasks that reveal both strengths and limitations
4. Help me compare this to alternatives I might already know
5. Surface questions I should be asking that I might not think of

## My context

**Why I'm evaluating this:**
[What triggered this exploration? Example: "My team is considering this for our agent infrastructure" or "This keeps appearing in discussions about X"]

**What I'd use it for:**
[Specific use case. Example: "Building conversational agents with tool use" or "Distributed inference serving"]

**Technologies I already know:**
[Related tools or frameworks you're familiar with. Example: "I've built similar things with LangChain and MCP servers"]

**Constraints I'm working within:**
[Technical or organizational constraints. Example: "Needs to run on OpenShift" or "Team prefers Go over TypeScript"]

## What I need to understand

1. **Core value proposition:** What does this do that I can't easily do otherwise?
2. **Mental model:** How should I think about this? What are the key abstractions?
3. **Tradeoffs:** What am I giving up by choosing this? What assumptions does it make?
4. **Maturity:** Is this production-ready or experimental? Who's using it seriously?
5. **Trajectory:** Is this gaining momentum or stagnating? Who's behind it?
6. **Integration:** How does this fit with other tools in my stack?
7. **Exit cost:** How hard is it to migrate away if this doesn't work out?

## Exploration approach

I want to:

- Start with conceptual understanding before writing code
- See realistic examples, not just "hello world"
- Understand failure modes, not just success paths
- Compare directly to alternatives where possible
- Form my own opinions through hands-on experimentation

## Constraints

- Be honest about limitations and unknowns - don't oversell
- Distinguish between documented facts and your assessment
- If something is genuinely new or uncertain, say so
- Point me to primary sources (docs, repos, discussions) when relevant
- Help me identify what I'd need to test myself vs. what I can trust from others

## Output artifacts

Help me build:

- **One-pager summary:** What this is, who it's for, key tradeoffs
- **Comparison matrix:** How this stacks up against alternatives on dimensions I care about
- **Hands-on evaluation plan:** What I should build or test to form my own opinion
- **Open questions:** Things I couldn't determine that need more investigation

## Start

Begin by providing:

1. A concise explanation of what this technology is and what problem it solves
2. The key mental model or abstraction I need to understand
3. How it relates to technologies I already know (from my context above)
4. An initial assessment of maturity and trajectory
5. A proposed exploration plan (conceptual understanding first, then hands-on tasks)

---

## Customization notes

**For framework evaluation:** Add questions about ecosystem (libraries, integrations, community), documentation quality, and learning curve.

**For infrastructure tools:** Add questions about operational complexity, observability, failure handling, and scaling characteristics.

**For AI/ML tools:** Add questions about model compatibility, performance characteristics, and how much the tool abstracts vs. exposes.

**For build-vs-buy decisions:** Add questions about maintenance burden, support options, and total cost of ownership.

**For competitive analysis:** Ask explicitly for comparison to specific alternatives you're considering.

## Example usage

### Example 1: AI agent framework

```markdown
I need to evaluate **Google Genkit** to determine if it's worth adopting for 
**building document processing agents at my company**.

## My context

**Why I'm evaluating this:**
We're building internal tools that use LLMs for document analysis. I've seen 
Genkit mentioned as a simpler alternative to LangChain.

**What I'd use it for:**
Agents that can fetch documents, extract information, and answer questions 
about them. Need tool use and structured outputs.

**Technologies I already know:**
I've built MCP servers, used OpenAI APIs directly, and experimented with 
LangChain (found it overcomplicated for our needs).

**Constraints I'm working within:**
Team is comfortable with TypeScript. Needs to integrate with our existing 
auth system. Will deploy on Kubernetes.
```

### Example 2: Distributed systems tool

```markdown
I need to evaluate **Ray Serve** to determine if it's worth adopting for 
**serving ML models with dynamic batching**.

## My context

**Why I'm evaluating this:**
Our current serving setup doesn't handle bursty traffic well. Ray Serve 
claims to solve this with actor-based serving.

**What I'd use it for:**
Serving multiple model versions with automatic batching and scaling. Need 
to handle variable request sizes efficiently.

**Technologies I already know:**
I've deployed models with vLLM, TensorFlow Serving, and plain FastAPI. 
Familiar with Kubernetes-based scaling.

**Constraints I'm working within:**
Must integrate with our existing Prometheus monitoring. Team has limited 
Ray experience. Running on GPU nodes in OpenShift.
```

### Example 3: Protocol or standard

```markdown
I need to evaluate **Model Context Protocol (MCP)** to determine if it's 
worth adopting for **standardizing tool interfaces in our agent platform**.

## My context

**Why I'm evaluating this:**
We have multiple agents that each implement tool calling differently. 
Looking for a standard that could unify this.

**What I'd use it for:**
Defining tool interfaces that work across different LLM providers and 
agent frameworks. Want to build tools once and use them everywhere.

**Technologies I already know:**
I've implemented OpenAI function calling, built custom tool systems, 
and worked with various agent frameworks.

**Constraints I'm working within:**
Need to support both cloud and on-prem deployments. Some tools need 
OAuth-based auth. Team uses Go primarily.
```

## After the exploration

Once you've completed the evaluation, you should have:

1. **A clear recommendation** - adopt, experiment further, or pass
2. **Supporting evidence** - specific findings that back your recommendation
3. **Risk assessment** - what could go wrong if you adopt this
4. **Next steps** - if proceeding, what's the minimal viable experiment

This evaluation artifact is useful beyond your immediate decision - it helps teammates understand your reasoning and can inform future evaluations of related technologies.
