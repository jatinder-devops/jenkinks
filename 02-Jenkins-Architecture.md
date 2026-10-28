# Stage 2 — Jenkins Architecture

## Objective
Understand the controller, agents, executors, jobs, and workspaces.

## Main components
- **Controller:** Hosts the UI and coordinates jobs and scheduling.
- **Agent:** Executes work assigned by the controller.
- **Executor:** A slot that can run a task on a node.
- **Workspace:** Directory where a job checks out and works with files.
- **Queue:** Holds work waiting to be scheduled.

## Simplified diagram
```text
User
 |
 v
Jenkins Controller
 | schedules work
 +----------+
 |          |
 v          v
Agent A    Agent B
Build      Test
```

For a beginner lab, the built-in node may be enough. Separate agents are useful for isolation and scaling; avoid running untrusted builds on a privileged controller.

