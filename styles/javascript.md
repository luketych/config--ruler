  * Use explicit Node.js error handling with try/catch; avoid silently swallowing errors in JavaScript or Node.js code.
  
  * Always document exported Node.js functions and JavaScript components with JSDoc or TypeDoc comments to maintain Node.js code clarity.
  
  * Prefer composition over inheritance in Node.js and JavaScript; use factory functions or higher-order functions/components instead of class inheritance.
  
  * Keep Node.js functions under 100 lines when implementing them, and under 50 lines after refactoring.

  * Keep components under 200 lines; split large JavaScript or Node.js functions into logical, maintainable units.
  
  * Avoid shared mutable state in your Node.js applications; prefer pure functions and controlled side effects in JavaScript code.
  
  * Use Result or Either-like patterns in Node.js (e.g., with fp-ts or custom implementations) for predictable and functional JavaScript error handling.
  
  * Define domain errors as custom Node.js error classes (e.g., class ValidationError extends Error) and throw them explicitly in your JavaScript code.
  
  * Don’t rely on instanceof checks in Node.js or JavaScript for cross-realm type safety; prefer tag-based discriminated unions in TypeScript for Node.js projects.
  
  * Avoid class inheritance in Node.js and JavaScript unless modeling a strict type hierarchy; favor object composition with functions or closures in Node.js applications.
