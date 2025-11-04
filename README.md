# HMAS Agents

Project for the blog: https://sionwilliams.com/posts/2025-11-03-my-agent-army/

## Agent Architecture

The HMAS Agents system uses a hierarchical agent architecture with specialized roles for different aspects of software development.

### Agent Hierarchy

```mermaid
graph TD
    A[Orchestrator<br/>Primary AI Project Manager] --> B[Planner<br/>Product Manager]
    A --> C[Architect<br/>Knowledge Architect]
    A --> D[Coder<br/>Developer]
    A --> E[Test<br/>QA Engineer]
    A --> F[Debugger<br/>Root Cause Analyst]
    A --> G[Security<br/>Security Auditor]

    B --> D
    C --> D
    D --> E
    D --> G
    E --> F
```

### Development Workflow

```mermaid
sequenceDiagram
    participant U as User
    participant O as Orchestrator
    participant P as Planner
    participant A as Architect
    participant C as Coder
    participant T as Test
    participant D as Debugger
    participant S as Security

    U->>O: User Request
    O->>P: Create detailed specs
    O->>A: Define technical constraints
    P-->>O: User stories & acceptance criteria
    A-->>O: Technology selection & architecture
    O->>C: Implement code
    C-->>O: Code implementation
    O->>T: Run tests
    O->>S: Security audit
    T-->>O: Test results
    S-->>O: Security report

    alt Tests fail
        O->>D: Perform root cause analysis
        D-->>O: RCA report & fix suggestion
        O->>C: Apply fix
        C-->>O: Fixed code
        O->>T: Re-run tests
        O->>S: Re-run security audit
    end

    O->>U: Final validated result
```

### Verification Loop

```mermaid
flowchart TD
    A[Code Implementation] --> B{Verification Loop}
    B --> C[Test Suite]
    B --> D[Security Audit]

    C --> E{Tests Pass?}
    D --> F{Audit Pass?}

    E -->|Yes| G[Success]
    F -->|Yes| G

    E -->|No| H[Invoke Debugger]
    F -->|No| I[Report Security Issues]

    H --> J[Root Cause Analysis]
    J --> K[Suggest Fix]
    K --> L[Apply Fix to Code]
    L --> B

    G --> M[Aggregate Results]
    M --> N[Report to User]
```

## Agent Roles

- **Orchestrator**: Manages the entire development workflow and delegates tasks to specialized subagents
- **Planner**: Breaks down high-level goals into detailed specifications, user stories, and acceptance criteria
- **Architect**: Defines technical constraints, selects technologies, and ensures architectural alignment
- **Coder**: Implements code based on plans from Planner and Architect
- **Test**: Generates and runs tests, performs self-healing for simple failures
- **Debugger**: Performs root cause analysis when tests fail
- **Security**: Audits code for vulnerabilities and compliance issues
