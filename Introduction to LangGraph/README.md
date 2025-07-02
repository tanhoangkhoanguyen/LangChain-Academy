## **LangGraph studio setup steps**
```
git clone https://github.com/langchain-ai/langchain-academy.git

cd '.\LangChain-Academy\Introduction to LangGraph\'

python -m venv lc-academy-env
lc-academy-env\Scripts\activate
pip install -r requirements.txt

cd .\studio\
langgraph dev
```

## **Module 1:**
### **Simple graph**
Steps to construct a graph:
1. Define State schema
2. Build node functions
3. Construct graph
### **Chain**
- Various message types that LangChain supports
- Chat models
- Introduce state_reducers: add_messages
- Construct a graph with Tools and state_reducers
### **Router**
- Instruct combining tools with graph construction
- MVP: `from langgraph.prebuilt import ToolNode, tools_condition`