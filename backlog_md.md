# Backlog.md:


## When, How to use Backlog.md:
Use backlog.md for managing tasks. Internally you can still using your own task management, as long as the human-interactable tasks are through Backlog.md 

## What Backlog.md is: 
Backlog.md is a CLI tool that manages tasks as markdown files in a bl/ folder within any Git repository, providing both terminal-based Kanban boards and a web interface for project management.


## When creating new tasks
Ultrathink to correctly identify dependencies between tasks and use sub tasks when necessary. 

## Task title
Titles should be concise, yet comprehensive enough so that the technical lead & CTO will immediately understand what the purpose and intent of the task is.

## Task milestone
Some tasks will be directly connected to a milestone. If connected to a milestone, make note at the top header section of the task.


## Task Head
At the top of every task .md file put the following:
   - id (required)
   - title (required)
   - status (required)
   - assgnee (required)
   - created_date (required)
   - labels (required)
   - dependencies (required)
   - milestone (optional)
   - priority (required)



### Example "Task Head"

```
id: task-001
title: "Data Pipeline Setup & yfinance Integration"
status: "Done"
assignee: []
created_date: '2025-01-18'
labels: ["data", "yfinance", "foundation", "core"]
dependencies: []
milestone: "milestone-1--foundation-core-scoring-engine"
priority: high
```


## Task Description
Ultrathink about a concise, comprehensive 1-2 sentence descriptions that gives a clear overview of the task, the intent and objective. The descriptions should implicitly answer the WHO (who is the audience, who are the stakeholders), WHY (what is the reason for this task, how does it get us closer to the objectives and north stars of the milestone and project).
A Task Description needs to answer the following:
  * WHAT 
  * WHEN (the order, what tasks need to be done before, what can be done after) 
  * WHERE (the files/folders involved) of the task.


## Task Headers
Every task contains the following headers throughout its .md file:
    * Sub-Tasks (optional, recommended)
    * Measurable Targets (required)
    * Implementation Checklist (required)
    * Definition of Done, Good-Enough (required)
    * Testing Strategies (required)
    * Measurable Success Criteria: (required)
        - Performance Requirements (Testable)
        - Functional Requirements (Testable)
        - Reliability Requirements (Testable)
        - Market Coverage (Aspirational - Not Directly Testable) 
    * Verification Checklist (required)
    * How To Re-Verify Success (required)


## Measurable Targets
We need a minimum of 3 targets. A maximum of 5.
Each task needs targets to aim towards. 
Each target needs to be measurable. How will we know when we are moving closer to our targets?


## Implementation Checklist
An Implementation Checklist is a list of binary, testable conditions that confirm whether a system or feature is complete and ready for use. 
Unlike subtasks, which break work into steps, checklist items represent outcome-based criteria that must be fully satisfied — such as passing tests, meeting performance thresholds, or implementing required behaviors. 
An Implementation Checklist serves as a final validation tool for developers, reviewers, or automated agents.


## Definition of Done, Good-Enough
What does DONE look like?
What does GOOD-ENOUGH look like?


## Testing Strategies
Avoid "Ice Cream Cone" Anti-Pattern for testing. (Aim for roughly 70% Unit Tests, 20% Integration Tests, 10% E2E Tests.)
Define, from a high-level, how and what will be unit tested.
Define, from a high-level, how and what will be integration tested.
Define, for a high-level, how and what will be end-to-end tested.


## Measurable Success Criteria
Measurable Success Criteria are explicitly defined, testable conditions that quantify how well a system performs, behaves, or withstands specific scenarios. 
Each item is validated through repeatable tests and serves as an objective benchmark for functionality, performance, reliability, or coverage. 
These criteria are used by developers, testers, and automation agents to enforce correctness and quality across a project.

### Performance Requirements (Testable)
Performance Requirements specify measurable thresholds for speed, efficiency, or responsiveness under normal or stressed conditions. 
These are validated through timing, load, or profiling tests and help ensure that the system meets real-world usage demands.

### Functional Requirements (Testable)
Functional Requirements define the expected outputs and behaviors of the system when given valid or invalid inputs.
These are strictly testable, deterministic, and form the foundation of correctness, often linked directly to the public API or interface contracts.

### Reliability Requirements (Testable)
Reliability Requirements ensure the system can tolerate and recover from transient faults like network issues, API failures, or time-based expiration. 
These are verified by simulating failure scenarios and observing how gracefully the system responds.

### Market Coverage (Aspirational. Not Directly Testable.)
Market Coverage represents high-level capability goals — like supporting a broad set of inputs or real-world variability — that may be impractical to fully test but are validated through sampling or inferred through representative testing. 
These are directional targets rather than hard assertions.


## Verification Checklist
Create a checklist for Unit Tests (pass/fail), Integration Tests (verified/unverified) and Benchmarks (measured/unmeasured) that, when passed, verified, and measured prove that this task has achieved its goals.

## Example "Verification Checklist"
```
### Unit Tests (17 tests) - PASSED ✅
- [x] `TestFetchStockData` (7 tests): Core functionality
- [x] `TestCaching` (5 tests): Cache behavior
- [x] `TestDataValidation` (6 tests): Data quality
- [x] `TestRateLimiting` (1 test): API limits
- [x] `TestErrorHandling` (3 tests): Error scenarios

### Integration Tests (Real API) - VERIFIED ✅
- [x] Live yfinance API calls work correctly
- [x] Cache integration reduces actual API calls
- [x] Performance benchmarks met with real data

### Benchmarks - MEASURED ✅
- [x] **Actual Performance**: 0.37s for AAPL 1-month (target: <3s)
- [x] **Cache Efficiency**: 100% hit rate on subsequent calls
- [x] **Test Execution**: <3s for full unit test suite
```


## How To Re-Verify Success
Instructions for how to run scripts, code, tests in order to prove and verify that we have in-fact succeeded.

### Example "How To Re-Verify Success"
```
# Performance test
just demo  # Should complete in <3s

# Full test suite
just test  # Should pass all tests in <10s

# Specific validation
uv run pytest tests/test_core/test_data.py -v
uv run pytest tests/test_integration/ -v
```




## Creating Tasks
  * backlog task create "Task title"
  * backlog task create "Task title" -d "Description" -a @assignee
  * backlog task create "Task title" -s "In Progress" -l bug,feature
  * backlog task create "Task title" --priority high --ac "Acceptance criteria"

## Viewing Tasks
  * backlog task list
  * backlog task list -s "In Progress" -a @john
  * backlog task 123 --plain  # AI-friendly output
  * backlog board  # Kanban board view

## Updating Tasks
  * backlog task edit 123 -s "Done"
  * backlog task edit 123 -a @newassignee -l urgent,bug
  * backlog task edit 123 --plan "Updated implementation plan"
  * backlog task edit 123 --notes "Progress update"

## Workflow Commands
  * backlog init my-project  # Initialize project
  * backlog task archive 123  # Archive completed task
  * backlog browser  # Launch web interface
  * backlog config set defaultEditor "code --wait"


## Key Flags for Agents
  * Always use --plain for machine-readable output
  * Task IDs format: task-123 (lowercase, hyphenated)
  * Status values: "To Do", "In Progress", "Done", "Backlog"
  * Priority values: "high", "medium", "low"
