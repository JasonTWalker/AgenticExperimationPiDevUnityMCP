# Agentic Experimentation Project
The primary goal of this project is to serve as a playground to test various agentic engineering workflows within a language and programming environment I'm familiar in:
  - Unity
  - C#
  - VSCode

## Resources Used
The expandability and open community nature of the Pi agent harness makes it a tool I wish to become more familiar with. The pi.dev community has readily available MCP extensions, and in order for the agent to execute
tasks within Unity - an open source project 'Coplay' (https://github.com/CoplayDev/unity-mcp) will serve as the MCP for interacting with the Unity client itself, 
though it should be noted that Unity does have its own internal MCP (https://docs.unity3d.com/Packages/com.unity.ai.assistant@2.0/manual/unity-mcp-overview.html) which may be worth looking into. Ollama will be used to host
an LLM locally. I'm on RTX 3060 hardware with 12GB VRAM, hopefully this cuts the mustard.
  - Pi.Dev
  - Coplay Unity MCP
  - Ollama
  - Qwen3-Coder-7b (to try and just get something running, with the opportunity to upgrade the model down the line if needed)

### Notes
Like I say, this is just for experimentation. If I come across any useful information during implementation that might help someone as clueless as me get an agent running, I'll add a section here. Until then, it's time
to try and figure all this stuff out. 
