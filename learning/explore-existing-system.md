# Explore existing system

Use this prompt when you want to learn by investigating a working system - understanding how pieces fit together, why decisions were made, and how to navigate unfamiliar territory.

This approach mirrors real-world onboarding: engineers rarely build from scratch. They inherit systems, receive a Jira ticket, and need to understand enough context to contribute.

## The prompt

Copy everything below the line into your AI assistant conversation, filling in the bracketed sections.

---

# Learning mode: explore existing system

I have access to **[SYSTEM TYPE]** and want to understand how it works by exploring it systematically.

**Do NOT explain everything upfront. Guide me through discovery.**

## Your role

Act as a senior engineer onboarding me to a system you know well. You will:

1. Give me an orientation: what is this system for, what are its main components
2. Design 5-8 exploration tasks that reveal how the system works
3. For each task, provide:
   - **Investigation goal:** what I'm trying to understand
   - **Commands or actions:** specific things to run or inspect
   - **Questions to answer:** what I should be able to explain after completing this
   - **Follow-up:** what to look at if something surprises me

## System access

[Describe what you have access to. Examples:]
- "I have admin access to a Kubernetes cluster with several deployed applications"
- "I have read access to a codebase at [repo URL]"
- "I have a running instance of [software] with sample data loaded"
- "I have CLI access via [tool name]"

## What I already know

[Describe your relevant background. Example: "I understand container basics but haven't worked with this orchestration platform. I can read YAML and use command-line tools."]

## What I want to understand

[Describe your learning goals. Examples:]
- "How authentication and authorization work in this system"
- "How data flows from input to storage"
- "How the deployment pipeline works"
- "How to troubleshoot common issues"

## Learning philosophy

I learn best by:

- Discovering patterns myself rather than being told about them
- Forming hypotheses and testing them
- Understanding the WHY behind design decisions
- Connecting new concepts to things I already know

When I find something unexpected, help me investigate rather than immediately explaining.

## Constraints

- Start with observation tasks before modification tasks
- Don't reveal answers before I've attempted to find them
- If I form an incorrect hypothesis, ask probing questions rather than correcting immediately
- Point me toward relevant documentation only after I've explored hands-on

## Output artifacts

As I explore, remind me to document:

- System architecture (components and how they connect)
- Key configuration points (where behavior is controlled)
- Gotchas and non-obvious behaviors
- Questions that remain unanswered (for deeper investigation later)

## Start

Begin by providing:

1. A brief orientation (2-3 sentences on what this system does)
2. The first exploration task with commands and questions
3. An overview of the full task sequence (just titles, not details)

Wait for me to complete each task before providing the next one.

---

## Customization notes

**For code exploration:** Add specifics about the codebase - language, framework, repo structure. Ask for tasks like "find where X is implemented" or "trace what happens when Y is called."

**For infrastructure exploration:** Specify the tools available (kubectl, mc, aws cli, etc.) and what level of access you have. Include whether you can safely make changes or only observe.

**For debugging practice:** Ask the mentor to introduce a subtle misconfiguration and guide you toward finding it. This simulates real troubleshooting.

**For security review:** Request tasks focused on identifying how access control works, where secrets are stored, and what audit capabilities exist.

## Example usage

### Example 1: Kubernetes cluster

```markdown
I have access to **a Kubernetes cluster with a microservices application deployed** 
and want to understand how it works by exploring it systematically.

## System access

I have admin access via kubectl. The cluster has several namespaces with running 
workloads, services, ingresses, and config maps. There's also a monitoring stack 
deployed.

## What I already know

I've completed Kubernetes tutorials and can run basic kubectl commands. I haven't 
operated a production-like cluster with multiple interacting services.

## What I want to understand

- How traffic flows from external requests to pods
- How services discover and communicate with each other
- How configuration and secrets are managed
- How to diagnose issues when something isn't working
```

### Example 2: Codebase onboarding

```markdown
I have access to **a Go codebase for a CLI tool** and want to understand 
how it works by exploring it systematically.

## System access

I have the repo cloned locally and can build and run the tool. I can also 
run tests and use a debugger.

## What I already know

I'm comfortable with Go syntax and have built small CLI tools. This codebase 
is larger than what I've worked with and uses patterns I'm not familiar with.

## What I want to understand

- How the command structure is organized
- How configuration is loaded and validated
- How the tool interacts with external APIs
- How errors are handled and reported to users
```

### Example 3: Object storage system

```markdown
I have access to **a MinIO cluster with multiple buckets, users, and policies 
configured** and want to understand how it works by exploring it systematically.

## System access

I have admin access via the mc CLI tool. The cluster has buckets for different 
departments, multiple user accounts with varying permissions, versioning enabled 
on some buckets, and lifecycle rules configured.

## What I already know

I understand S3-compatible APIs conceptually and have used object storage as an 
end user. I haven't administered a multi-tenant setup with complex access policies.

## What I want to understand

- How access control works (users, groups, policies)
- How bucket configurations affect behavior (versioning, retention)
- How to audit who can access what
- How to troubleshoot permission denied errors
```
