# Task format

This document defines the standard format for learning tasks used across prompts in this repository.

## How to use this template

This template works together with the prompts in the `learning/` and `research/` folders. Here's the workflow:

### Step 1: Choose and customize a learning prompt

Pick the appropriate prompt for your learning goal:

- `learning/guided-project-construction.md` - for building something new
- `learning/explore-existing-system.md` - for understanding existing code or infrastructure
- `research/technology-exploration.md` - for evaluating whether to adopt something

Copy the prompt and fill in the bracketed placeholders with your specific context.

### Step 2: Append the task format specification

After your customized prompt, add this instruction block:

```markdown
## Task format

Generate all tasks following this structure:

- **Objective:** What I'm trying to accomplish or understand
- **Context:** Why this task matters and how it connects to the bigger picture
- **Steps:** Specific actions to take (numbered list)
- **Hints:** Pointers toward the solution, not the solution itself
- **Success criteria:** How I'll know I've completed this successfully
- **Pitfalls to avoid:** (Optional) Common mistakes to watch for
- **Capture:** What to document after completing this task

Calibrate tasks to medium difficulty (30-60 minutes each). Make hints directional, not complete solutions.
```

### Step 3: Start the conversation

Paste the combined prompt into your AI assistant conversation. The AI will generate properly structured tasks that follow both your learning goals and the consistent task format.

### Quick reference

If you've already started a conversation and want to improve task formatting, paste just this:

```markdown
Please format all tasks with: Objective, Context, Steps, Hints (not solutions), 
Success criteria, Pitfalls (optional), and Capture prompts. Target 30-60 minutes per task.
```

---

## Task format specification

The rest of this document defines the standard format in detail.

## Standard task structure

Every learning task should include these elements:

```markdown
## Task [N]: [Short descriptive title]

**Objective:** What you're trying to accomplish or understand.

**Context:** Why this task matters and how it connects to the bigger picture.

**Steps or actions:**
1. Specific thing to do
2. Another specific thing to do
3. ...

**Hints:**
- Relevant concept, API, or pattern to look into
- Another hint if needed
- (Not the solution, just pointers)

**Success criteria:** How you'll know you've completed this successfully.

**Pitfalls to avoid:** (Optional) Common mistakes or misconceptions.

**Capture:** What to document after completing this task.
```

## Element details

### Objective

One or two sentences describing the goal. Should answer "what will I be able to do or understand after this?"

Good: "Implement a handler that responds to tool calls and returns structured results."

Weak: "Work on tool handling." (Too vague)

### Context

Brief explanation of why this task is in the sequence and what it builds toward. Helps the learner stay oriented.

Good: "This is the core of agent functionality - without tool handling, the agent can only generate text. This task connects to the previous task where you defined the tool schema."

Weak: "This is important." (Doesn't explain why)

### Steps or actions

Concrete, actionable items. For exploration tasks, these might be commands to run or things to inspect. For construction tasks, these describe what to build.

Good:
1. Create a new file `tools/handler.go`
2. Define a function that takes a tool call request and returns a response
3. Route incoming tool calls to the appropriate handler based on tool name
4. Test with a simple echo tool before adding real functionality

Weak:
1. Make the tool handler work (Too vague, no guidance)

### Hints

Pointers toward the solution without giving it away. These should reduce frustration without eliminating productive struggle.

Good:
- Look at the `ToolCall` struct in the SDK - it has fields you'll need to extract
- The Go `switch` statement works well for routing by tool name
- Consider what happens if an unknown tool is requested

Weak:
- Here's the code: `func HandleTool(tc ToolCall) ...` (This is a solution, not a hint)

### Success criteria

Observable or testable outcomes. The learner should be able to verify completion independently.

Good:
- Running `go test ./tools/...` passes
- Calling the echo tool returns the input message unchanged
- Calling an unknown tool returns an error, not a panic

Weak:
- It works (Not specific enough to verify)

### Pitfalls to avoid

Optional but valuable. Warns about common mistakes without over-explaining.

Good:
- Don't forget to handle the error case - a nil tool call can crash your agent
- The tool name is case-sensitive in most SDKs

### Capture

Prompts the learner to document what they learned. This builds the habit of extracting durable knowledge from hands-on work.

Good:
- Note the pattern for dispatching tool calls
- Document any SDK quirks you discovered
- Add any error messages you encountered to your troubleshooting notes

## Task sequencing principles

When designing a sequence of tasks:

**Progressive complexity.** Early tasks should be achievable quickly to build momentum. Later tasks can be more challenging.

**Dependencies are explicit.** If task 4 requires completing task 3, say so. Don't assume the learner will do them in order.

**Mix task types.** Alternate between:
- Construction tasks (build something)
- Exploration tasks (investigate something)
- Integration tasks (connect pieces together)
- Debugging tasks (find and fix an issue)

**Include checkpoints.** Every 2-3 tasks, include a moment to step back and verify everything works together.

## Difficulty calibration

Tasks should be challenging but achievable. Use this rough guide:

| Difficulty | Time estimate | Hints provided | Suitable for |
|------------|---------------|----------------|--------------|
| Easy | 10-15 minutes | 2-3 specific hints | Building confidence, core patterns |
| Medium | 30-60 minutes | 1-2 directional hints | Main learning content |
| Hard | 1-2 hours | Minimal hints | Stretch goals, deeper understanding |

A typical learning sequence might have: 2 easy → 3-4 medium → 1-2 hard

## Example: complete task

Here's a fully-formed task following this format:

```markdown
## Task 3: Add tool call handling to the agent

**Objective:** Implement the handler that executes tools when the LLM requests them and returns results.

**Context:** In the previous task, you defined tool schemas that tell the LLM what tools are available. Now you need to actually execute those tools when called. This is where your agent gains the ability to take actions, not just generate text.

**Steps:**
1. Create `internal/tools/handler.go`
2. Define a `Handler` struct that holds references to your tool implementations
3. Implement a `Handle(ctx context.Context, call ToolCall) (ToolResult, error)` method
4. Route calls to the appropriate tool based on `call.Name`
5. Wrap tool responses in the `ToolResult` struct the SDK expects
6. Add error handling for unknown tools and tool execution failures
7. Write a test using a mock tool that returns a fixed response

**Hints:**
- Look at how `ToolCall` is structured - the `Arguments` field is typically JSON you'll need to unmarshal
- A type switch or map of handlers both work for routing; pick based on how many tools you have
- The SDK example in `examples/tools/` shows the expected response format

**Success criteria:**
- `go test ./internal/tools/...` passes
- You can manually test by creating a `ToolCall` struct and passing it to your handler
- Unknown tool names return an error with a clear message
- A panic in a tool implementation doesn't crash the entire agent

**Pitfalls to avoid:**
- Don't unmarshal arguments until you've verified the tool exists - fail fast
- Remember that tool execution might be slow; consider whether you need timeouts
- Error messages from tools should be returned to the LLM, not swallowed

**Capture:**
- Document the pattern you used for routing (switch vs map vs interface)
- Note any differences between the SDK documentation and actual behavior
- List the error cases you handle and how
```

## Adapting for different learning modes

### For guided project construction

Tasks focus on building components. Each task adds a piece to the project. Success criteria emphasize working code.

### For explore existing system

Tasks focus on investigation. Steps are commands to run or things to inspect. Success criteria emphasize questions you can now answer.

### For technology exploration

Tasks focus on evaluation. Steps include both hands-on testing and research. Success criteria emphasize informed opinions you can now defend.


