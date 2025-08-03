## FEATURE:

Build an agent that handles learner questions by first checking our Redis-Search cache and, on cache-miss, invoking SerperDevTool for up-to-date web results and invokeLLM for structured Q&A generation.


## EXAMPLES:

- **`examples/agent/InteractiveTutorAgent.py`**  
  Shows how to define the agent class, register the `serperSearch` and `invokeLLM` tools, and implement the cache-lookup → tool-chain logic.
- **`examples/tools/serper_search.py`**  
  Wrapper for the SerperDevTool integration, demonstrating scoped JWT injection and result normalization.
- **`examples/tools/invoke_llm.py`**  
  Pattern for calling our core GPT-4 and Llama fallback models through the MCP façade with short-lived tokens.


## DOCUMENTATION:

- **FastAPI Facade**: input schema, authentication, and routing logic (see `assistio/api/routes/learn.py`).
- **MCP Server Guide**: configuration of tool scopes & tokens in `examples/mcs-server-guide.md`.
https://github.com/crewaiinc/crewai
https://docs.crewai.com/en/introduction
https://docs.langchain.com/ has a bunch of information

- Saas scaffold - https://github.com/chipgpt/full-stack-saas-mcp
- **Redis-Search Cache**: schema and vector index setup for question embeddings (see `infra/redis vector setup.md`).
- **Bloom-Taxonomy Validator**: prompt templates and expected schema in `assistio/agents/pedagogy/prompts.md`.
- Create agentic framework using pydantic. 
Pydantic AI documentation: https://ai.pydantic.dev/

## OTHER CONSIDERATIONS:

create a folder for this app, create the app's own venv where you will install tools and maintain robust documentation on which tools are used and how they are setup and what security precautions we took and what needs work. 

