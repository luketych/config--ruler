## Task Runner Rules:
  * Use just + POSIX-compatible scripts as the standard task runner


** Rationale for keeping just scripts POSIX-compatible
  * Works from any interactive shell, including fish, zsh, and bash
  * Internally uses a configurable shell (sh by default — override with set shell := [...])
  * Supports scripts written in clean Bash or any other CLI-compatible language (Python, Node, etc.)
  * Enables wrapping or delegating to complex tools while remaining declarative
  * Fully portable across OSes when written using POSIX-compatible commands


## Implementation Guidelines
  * Define all task logic in a justfile at the project root
  * Use set shell := ["bash", "-cu"] for consistent behavior unless targeting stricter portability
  * Avoid using shell-specific features unless scoped properly
  * Make all tasks callable from any shell environment (no hard reliance on bash-isms unless declared)
  * Prefer piping, redirection, and logging using portable syntax
  * Optional: provide a run.sh wrapper for environments without just installed
