# FRS-700 — Code Runner & Execution Engine

## Purpose

The Code Runner is responsible for securely executing user-submitted code in isolated environments, validating outputs against test cases, enforcing execution limits, and returning normalized execution results.

**Important Boundary**

The Code Runner **does not**:

* Manage users
* Accept HTTP requests directly
* Store submissions
* Handle authentication
* Manage problems

It **only executes jobs**.

Think of it as a compute service.

### Scope

```
Execution Engine
│
├── Job Executor
├── Language Runtime
├── Sandbox
├── Testcase Executor
├── Resource Limiter
├── Output Validator
├── Verdict Generator
├── Worker Pool
├── Runner Queue
├── Execution Logs
├── Security
└── Runner Health
```

### High-Level Execution Flow

```
Submission
│
▼
Execution Job
│
▼
Worker
│
▼
Sandbox
│
▼
Compile
│
▼
Execute
│
▼
Run Test Cases
│
▼
Compare Output
│
▼
Generate Verdict
│
▼
Return Result
```

Notice:

Submission Service sends jobs.

Runner executes jobs.

***

## Execution Lifecycle

```
Created

↓

Waiting

↓

Worker Assigned

↓

Preparing Sandbox

↓

Compiling

↓

Executing

↓

Running Testcases

↓

Generating Verdict

↓

Cleaning Resources

↓

Completed
```

Every execution follows this lifecycle.



### Execution Engine Summary

| Category                | Requirements   |
| ----------------------- | -------------- |
| Job Intake              | FR-701         |
| Sandbox                 | FR-702, FR-718 |
| Package Loading         | FR-703–704     |
| Compilation & Execution | FR-705–709     |
| Resource Management     | FR-710–712     |
| Worker Management       | FR-713–715     |
| Extensibility           | FR-716–717     |
| Operations              | FR-718–720     |

## Architectural Principles

#### 1. Stateless Workers

Workers should not persist submissions, user data, or problem metadata. They receive a job, execute it, return the result, and are immediately ready for the next job. This allows horizontal scaling.

#### 2. Problem Packages

The runner should never understand Markdown, editorials, or AI sessions. It consumes a compiled **problem package** containing only execution-related assets such as wrappers, test cases, validators, and limits.

#### 3. Sandbox Per Job

Each execution gets a fresh sandbox. Sandboxes are never reused across users to avoid state leakage and security issues.

#### 4. Execution Isolation

A worker process may handle many jobs over time, but each job executes in its own isolated environment with enforced CPU, memory, filesystem, and network restrictions.

#### 5. Separation of Concerns

* **Submission Service** → Creates and tracks submissions.
* **Execution Queue** → Schedules jobs.
* **Code Runner** → Executes jobs.
* **Problem Compiler** → Builds problem packages.
* **Problem Service** → Manages problem content.
