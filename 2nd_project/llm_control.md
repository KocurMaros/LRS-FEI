# Natural language (LLM) control
In this assignment you will **control a simulated UAV using natural language commands interpreted by a Large Language Model (LLM)**. The goal is to integrate the LLM with your ROS control system to translate human text (or voice) commands into flight actions.
## Project specification
1. __Implement communication between the LLM and the ROS system.__
- Establish connection to an external API (e.g. OpenAI, Gemini, HuggingFace) or local model (e.g. Llama, Mistral).
- Ensure the model can receive text input, alongside with information about the drone, and return structured responses. 
2. __Implement LLM drone control.__
- Integrate the interpreted commands with your existing control pipeline (takeoff, land, position control).
- Ensure collision free flying capability implemented from the first assignment.
- You may achieve this using various techniques or their respective combinations: 
    - Prompt engineering
    - In context learning
    - Function calling / Tool use
    - (and so on ...) - be creative
3. __Implement and demonstrate 3 custom commands.__
- Define at least three custom natural language commands, such as:
    - “Fly in a circle.”
    - “Fly in a square 3m above the ground”
    - "Show me a picture from the camera"
    - (and so on ...) - be creative again
4. __Implement some safety mechanisms.__
- Prevent unsafe actions, such as taking off too high, flying through obstacles, or executing invalid trajectories.
 
### **Assignment points**
- Each section will be awarded 1/4 of total points (25), points for the last section will be awarded only if other sections are completed.
- **Minimal requirement is to have at least of 50% of points from this assignment. To successfully finish this assignment you have to complete 1. and 2.**

### **Notes**
If you wish to use an LLM through API, you may receive a **Google AI Studio or OpenAI API key** for the duration of the assignment from your lecturer, just make sure to **ask** for one.

If you want you can also generate a Google AI Studio API key at [GoogleAIStudio](https://aistudio.google.com/api-keys), which works for free for these kind of applications. With this API key you get access to Large Language Models like Gemini 2.5 Flash.

### **Potential starting points**
These are some potentially useful links, which may be useful to you.
- [ROS MCP Server](https://github.com/robotmcp/ros-mcp-server/tree/main)
- [ROSA - Robot Operation System Agent](https://github.com/nasa-jpl/rosa)
- [What is MCP?](https://modelcontextprotocol.io/docs/getting-started/intro) 
- [LangGraph](https://www.langchain.com/langgraph)
- [n8n](https://n8n.io/)