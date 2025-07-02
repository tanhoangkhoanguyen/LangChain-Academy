## **LangGraph Studio Setup**
```bash
git clone https://github.com/langchain-ai/langchain-academy.git
cd 'LangChain-Academy/Introduction to LangGraph/'

# On Windows
python -m venv lc-academy-env
lc-academy-env\Scripts\activate
pip install -r requirements.txt

# Launch Studio
cd studio
langgraph dev
```

## **Module 1**
### **Simple Graph**
Steps to build a LangGraph:
1. *Define State Schema* – the structure of the shared data (`TypedDict`, `dataclass`, or `Pydantic`).
2. *Create Node Functions* – each node represents a step in the graph.
3. *Construct Graph* – connect nodes with flow logic.

### **Chain**
- LangChain supports many message types (e.g. AIMessage, HumanMessage).
- Wrap chat models.
- *State Reducers*: `add_messages` is commonly used to track conversation.
- Add *Tools* + *State Reducers* to graph for chaining logic.

### **Router**
- Route flow to different tools/functions based on condition.
- Key components: `from langgraph.prebuilt import ToolNode, tools_condition`

### **Agent**
- Turns tool usage into an intelligent agent:
  - The graph loops back to the `tool_call_llm` node after execute the Tool functions.
- LangSmith connection issues

### **Agent with Memory**
- Add `MemorySaver` to store chat history. Use `thread_id` for session persistence `config = {"configurable": {"thread_id": "some_id"}}`.

## **Module 2: Advanced Usage**
### **State Schema**
- Three common ways to define:
  - `TypedDict`, `dataclass`
  - `Pydantic`: adds validation
- Differences include setup syntax and access code.

### **State Reducers**
Reducers are functions that update the state after each node runs.
- `add_messages`: automatically appends in `state['messages']`
  - Messages with the same ID will be overwritten
  - You can also remove messages using `RemoveMessage`
- `add`: enables **parallel execution** of nodes
- **Branching**: run multiple paths concurrently
- You can define **custom reducers** to control state updates as needed.