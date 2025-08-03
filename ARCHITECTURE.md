 User_Request
        [UI/API ➔ JSON payload, auth token]
                     |
               Orchestrator
     [Validate auth • Parse intent • Throttle]
                     |
        Router / Agent_Selector
  [Rule/ML-based dispatch logic (e.g. intent)]
           /         |          \
          /          |           \
     LLM_Agent   Data_Retrieval   Compliance
   [embed + prompt]   Agent         Agent
          |              |            |
  ┌───────┴───────┐  ┌───┴───┐     ┌──┴──┐
  │ Vector_DB     │  │Secrets│     │Policy│
  │ (context idx) │  │Store  │     │Store │
  └───────────────┘  └───┬───┘     └──────┘
      │                │
  ┌───┴───┐      ┌─────┴────┐
  │LLM     │      │External │
  │Provider│      │API      │
  └───┬───┘      └─────────┘
      \              /
       \            /
        \          /
         \        /
         Aggregator
   [Merge • Sanitize • Format]
             |
        User_Response
  [JSON / UI update / callback]
