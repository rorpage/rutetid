# AGENTS.md

Rules and conventions for all contributors to this project, including AI agents.

## Writing style

Never use em dashes (---, &mdash;) anywhere: in code comments, documentation, commit messages, or UI copy. Use commas, colons, semicolons, or rewrite the sentence instead.

## Git workflow

Commit directly to `main`. Do not open pull requests or create feature branches unless explicitly asked. Keep commits focused and write clear commit messages in the imperative mood (e.g. "Add ferry mode filter" not "Added ferry mode filter").

## Documentation

Every function must have a JSDoc comment describing what it does, its parameters, and its return value. Every new file must have a header comment explaining its purpose. Update the README whenever behavior or structure changes.

Example:

```js
/**
 * Fetches live vehicle positions for a given Entur codespace.
 * @param {string} codespace - The operator codespace ID (e.g. "RUT" for Oslo).
 * @returns {Promise<Array>} Array of vehicle objects with location and line info.
 */
async function fetchVehicles(codespace) { ... }
```

## Testing

Write a test for every function that contains logic. Tests live in a `tests/` directory and mirror the structure of the source. Use plain Node.js `assert` or a lightweight test runner; do not introduce heavy frameworks without discussion. Run tests before committing.
