# Task Proposal

## Repository
`vercel/commerce` at commit `3761e52e60df9c6a316e067dbfd7032e494d3634`.

## Question
When the same render-created increment action is invoked twice before a new render commits, what quantity does the backend receive?

## Expected Conclusion
A render with quantity `2` creates payload quantity `3`. Two invocations of the same bound action submit `3` both times, while the optimistic UI can reach `4`.

## Common Wrong Conclusions
1. The second invocation submits `4` because the optimistic UI reached `3`.
2. The server calculates the next quantity from the latest cart quantity.

## Contamination Probe
The solver must distinguish the captured render-time payload from optimistic state and explain why a new React render can create a different payload.
