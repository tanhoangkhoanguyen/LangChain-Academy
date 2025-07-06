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

### **Agent with Memory**
- Add `MemorySaver` to store chat history. Use `thread_id` for session persistence `config = {"configurable": {"thread_id": "some_id"}}`.

## **Module 2**
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




### **Multiple Schema**
We can define the in/output of the node 

### **Filtering and trimming messages**
There are a method, we can do to reduce the messages passed to LLM
- reducer: add_messages + RemoveMessage
- only pass the recent message to LLM `chat.invoke(state["messages"][-1:])`
- trim_messages: can be implemented. However, if the lastest message is beyond 100 tokens, trim_messages will return an empty string (unwanted).

### **Chatbot with message summarization**
- To access the schema of a specific thread id, we use `graph.get_state(config).values.get("parameter","")`

### **Chatbot with message summarization & external DB memory**
- Squlite functions the same as MemorySaver in terms of `:memory:`
- If we supply a path db, it will be different


## **Module 3**
### **Streaming**
- Stream full state:
  - values:
  - Update
- Streaming tokens -> live streaming the output

### **Breakpoints & Editing graph state**
- we can terminate the graph while it running with `graph = builder.compile(interrupt_before = ["node"])`
- update graph state with `update_state`

## **Time Travel**
- Browsing History: Get the history
- Replaying: replay at a specific step
- Forking: update the entire history, reset it to the forking step and rerun (if ya want)


## **Module: 4**
### **Parallelization**
- Order of adding `operator.add`
- Customize the Tool `operator.add`

### **Sub-graph**
- Simple sub-graphs connection to the entry graph

### **Map reduce**
- map-reduce technique
- with_structured_output(prompt): It tells the LLM to format its output in a way that can be parsed directly into the Subjects schema.

### **Research Asisstant**
- For Human-in-the-loop, we use stream
- Mainly revision