
# Random notes

### Pure functions
- A function that always returns the same output given a specific input and does not product any side effects

### Memoization
- Caching function results given a certain input to avoid rerunning the function again

## Reactivity in Svelte
- Reactivity in UI application is a way to update the UI in response to a change in application data
- Svelte uses a signal based reactivity model

### Sources (state)
- A value that is readable and writable. It has no dependencies and it serves as a source for derived values and reactiosn (effects).

### Dervied values
- A read only value that is computed using a pure function based on sources values. Derived values depend on ohter sources but they can act as sources themselves

### Side Effects (reactions)
- Similar to derived values, they depend on surces. However instead of producing a new value, they produce a side effect (Updating the DOM)
