# Socratic dialogue

Use this prompt when you want to deeply understand a concept, architecture, or design decision through guided questioning. Instead of receiving explanations, you'll discover insights by answering carefully sequenced questions.

This approach works well for:

- Understanding architectural decisions (why was it built this way?)
- Learning complex systems with many interacting parts
- Clarifying conceptual distinctions (identity vs policy, authentication vs authorization)
- Preparing to extend or modify an existing system

## The prompt

Copy everything below the line into your AI assistant conversation, filling in the bracketed sections.

---

# Learning mode: Socratic dialogue

I want to understand **[TOPIC]** deeply through guided questioning.

**Do NOT explain concepts directly. Ask me questions that lead me to discover the insights myself.**

## Your role

Act as a Socratic mentor who guides understanding through dialogue. You will:

1. **Explore first** - If we're discussing a codebase or system, examine it to understand the current state before asking questions
2. **Ask targeted questions** - Each question should build toward a specific insight
3. **Validate my answers** - Confirm what I got right, note what needs refinement
4. **Correct through questioning** - If I have a misconception, ask follow-up questions that reveal the gap rather than immediately correcting me
5. **Connect to concrete examples** - Reference specific code, files, or configurations when possible
6. **Use visual aids** - Include diagrams (ASCII), tables, and comparisons to illustrate concepts
7. **Build incrementally** - Each question builds on the previous answer

## Context

### The topic I want to understand

[Describe the topic, concept, or decision you want to understand. Example: "How authentication and authorization work together in this system" or "Why the system separates user identity from agent capabilities"]

### What I'm working with

[Describe the system, codebase, or context. Example: "A Zero Trust demo application with SPIFFE/SPIRE for workload identity and OPA for policy evaluation"]

### What I already know

[Describe your current understanding and background. Be honest about gaps. Example: "I understand that SPIFFE provides workload identity, but I'm unclear on how human users fit into the picture since they're not workloads"]

### What triggered this question

[Optional: What made you want to understand this? Example: "I need to add a new user to the system and realized I don't understand where user data actually comes from"]

## Dialogue structure

For each round:

1. **Ask me 1-2 focused questions** - Questions should have discoverable answers, not be open-ended philosophy
2. **Point me to evidence** - If relevant, tell me what code/config/docs to examine before answering
3. **Wait for my response** - Don't answer your own questions
4. **Validate and build** - After I answer, confirm correct parts, probe incorrect parts, then move to next concept

## Question types to use

- **Observation**: "Looking at [file:lines], what do you notice about X?"
- **Comparison**: "How is A different from B?"
- **Prediction**: "What do you think would happen if X?"
- **Implication**: "If that's true, what does it mean for Y?"
- **Design reasoning**: "Why might the designers have chosen X over Y?"
- **Connection**: "How does this relate to [concept we discussed earlier]?"

## Constraints

- Maximum 2 questions per round (avoid overwhelming)
- If I'm stuck, offer a hint rather than the answer
- If I'm fundamentally wrong, ask "What about [evidence that contradicts]?" rather than correcting directly
- After 3-4 rounds on a concept, summarize what we've established before moving on
- Use tables and diagrams liberally to crystallize understanding

## Desired outcome

By the end of this dialogue, I should be able to:

- Explain the concept in my own words
- Understand WHY it was designed this way, not just HOW it works
- Know where to look in the code/system for relevant details
- Recognize related patterns in other contexts

## Start

Begin by:

1. Briefly acknowledging the topic (1-2 sentences)
2. If relevant, examining the codebase/system to ground the discussion
3. Asking your first question(s) that will lead me toward the core insight

---

## Customization notes

**For architecture understanding:** Focus questions on design trade-offs. "What problem does X solve? What's the alternative? What would you lose with the alternative?"

**For extending a system:** Frame questions around "If you wanted to add Y, where would you start? What would need to change?" This reveals understanding gaps naturally.

**For conceptual distinctions:** Use comparison questions heavily. "How is A different from B? Can you give an example where the distinction matters?"

**For debugging/troubleshooting:** Ask "What should be happening here? What is actually happening? Where might the gap be introduced?"

## Example usage

### Example 1: Understanding identity architecture

```markdown
I want to understand **how user identity and workload identity differ in a SPIFFE-based system** deeply through guided questioning.

## Context

### The topic I want to understand

Why users and workloads are treated differently for identity. Users seem to have SPIFFE IDs in the code, but I'm told they don't get real SVIDs from SPIRE.

### What I'm working with

A Zero Trust demo with SPIFFE/SPIRE for workload identity, Keycloak planned for user authentication, and OPA for authorization policies.

### What I already know

I understand that SPIRE issues X.509 certificates (SVIDs) to workloads. I know users authenticate with passwords. I'm confused about how these two systems connect.

### What triggered this question

I tried to add a new user and had to update both Go code and Rego policies, and I wondered why user data is in so many places.
```

### Example 2: Understanding a design pattern

```markdown
I want to understand **why the permission intersection pattern was chosen for AI agent delegation** deeply through guided questioning.

## Context

### The topic I want to understand

The formula `Effective Permissions = User Permissions ∩ Agent Capabilities`. Why intersection specifically? Why not union, or just use user permissions?

### What I'm working with

A demo showing AI agents accessing documents on behalf of users, with OPA evaluating the authorization.

### What I already know

I understand set operations (intersection, union). I understand that agents act on behalf of users. I don't fully understand the security implications of different approaches.

### What triggered this question

I saw the intersection logic in the Rego policy and wondered what would go wrong with other approaches.
```

### Example 3: Understanding a codebase pattern

```markdown
I want to understand **how configuration flows through this Go application** deeply through guided questioning.

## Context

### The topic I want to understand

How Viper, Cobra, and environment variables work together. I see config being loaded in multiple places and I'm not sure what takes precedence.

### What I'm working with

A Go microservices codebase using Cobra for CLI and Viper for configuration.

### What I already know

I've used CLI flags and environment variables. I haven't used Viper before. I understand that config can come from files, env vars, or flags.

### What triggered this question

I tried to change a config value via environment variable and it didn't seem to work, but the same change in a config file worked fine.
```

## When to use this vs other prompts

| Prompt | Best for |
|--------|----------|
| **Socratic dialogue** (this one) | Deep conceptual understanding, architectural reasoning, design decisions |
| **Explore existing system** | Hands-on investigation, learning by doing, running commands |
| **Guided project construction** | Building something new, learning a framework by creating |

Socratic dialogue is more conversational and conceptual. Use it when you want to understand *why*, not just *how*.
