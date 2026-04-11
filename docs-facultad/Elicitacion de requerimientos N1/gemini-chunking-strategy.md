---
trigger: manual
---

## Response Length & Chunking Strategy
- Always provide complete, detailed, and thorough responses.
- Never truncate or summarize code — always write the full implementation.
- Do not shorten responses to conserve tokens. Prioritize completeness over brevity.
- If a task is large (e.g. multiple files, long implementations, complex features), 
  SPLIT it into multiple sequential steps instead of attempting everything in one response.
- Announce the plan at the start: list all the steps you will take, then execute them one by one.
- After each step, explicitly state what was completed and what comes next.
- When generating a large file, split it into logical sections (e.g. imports, types, 
  functions, exports) and deliver each section in a separate response.
- Never stop mid-implementation. If you are about to hit a limit, finish the current 
  logical unit cleanly and clearly state: "Continuing in next step..." before stopping.
- After completing each step, STOP and wait for the user to say "continuar" 
  before continuing to the next step. Never auto-continue.