## **Module 1** 
### **Lesson 1 - tracing_basics**
- Decorate functions with `@traceable` for LangSmith to their execution.
- Pass metadata (e.g., model name, provider, experiment version) to `@traceable` to aid analysis.
- RAG (Retrieval-Augmented Generation) combines a retriever (for context from external data) and a generator (like GPT-4) for grounded responses.
### **Lesson 2 - type_of_runs** 
LangSmith supports many different types of Runs – you can specify what type your Run is in the @traceable decorator. The types of runs are:
- LLM: Invokes an LLM
- Retriever: Retrieves documents from databases or other sources
- Tool: Executes actions with function calls
- Chain: Default type; combines multiple Runs into a larger process
- Prompt: Hydrates a prompt to be used with an LLM
- Parser: Extracts structured data

### **Lesson 3 – alternative_tracing_methods**
| **Method** | **When to Use** |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `@traceable` | - Default way to set up tracing  <br> - Manages `RunTree`, inputs, and outputs |
| LangChain / LangGraph | - Get tracing out of the box! |
| `with trace():` | - Want more control over what inputs and outputs get logged  <br> - Cannot use decorators or wrappers (not tracing a function) |
| `wrap_openai()` | - Want to use the **OpenAI SDK** directly |
| RunTree | - Want more **low-level control** over tracing configuration  <br> - Need to know `run_id` (e.g., for adding user feedback or logging to another service) |
### **Lesson 4 - conversatonal_threads**
- A thread is a collection of traces representing a single conversation. Each turn is a separate trace, but they are linked via the thread ID.
- Used for debugging chat agents/ multi-turn interactions.


## **Module 2**
### **Lesson 1 - dataset_upload**
- Manually add/generate dataset (required openai_key).
- Each dataset contains input/output pairs.
### **Lesson 2 - evaluators**
- LangSmith supports built-in and custom evaluators for automated comparison between:
  - Output vs. Ground Truth.
  - Output A vs. Output B (for A/B testing).
### **Lesson 3 - experiments**
### **Lesson 4 - analyzing_experiments_results**
### **Lesson 5 - pairwise_experiment**
- Code fail.
- Compare two outputs (e.g., model A vs model B) for the same input.
### **Lesson 6 - summary_evaluators**
- Code fail.


## **Module 3**
### **Lesson 1 - playground_experiments**
- Introduction to LangSmith playground.
### **Lesson 2 - prompt-hub**
- Browse public/ create private prompts for chatbot.
- Pull a prompt into your workspace for conversation interaction.
- Push a customized prompt to hub.
### **Lesson 3 - prompt_engineering_lifecycle**
Design prompt --> Test locally --> Deploy in production --> Evaluate performance --> Improve based on feedback.
### **Lesson 4 - prompt_canvas**
- Introduce a convenient way to edit prompts in a structured, no-code way (required openai_key).


## **Module 3**
### **Lesson 1 - publishing_feedback**
- Code fail.
- Learn how to add feedback to runs, both manually in the LangSmith UI, programmatically in code.
### **Lesson 2 - annotation_queues**
- Use annotation queues to label or review model outputs.