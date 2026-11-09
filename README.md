Architecture

![Solar LLM Architecture](architecture/Solar%20LLM%20Architecture.png)

Our Summary structure (max. 1,000 words)

1. Product description, 
What Solar LLM is, who it’s for (students at our university), and what problem it solves.
- Providing free AI usage of open weights models for students at CODE university
- Using the power provided by the solar panel on campus to power the GPU server that runs the open weights models
- SolarLLM is a prove of concept for cheap and accessible AI (AI for the world)

3. Architecture components,
A short explanation of each part of the diagram: UI, DNS, server, database, message queue, GPU server, solar panel, microcontroller (OpenDTU) and MQTT broker. One or two sentences each on what it does.

4. Communication flow, 
How data moves through the system
How the queue holds requests when power is low and releases them when power is good enough.

5. Energy supply,
How the solar panel powers the GPU server, and what happens when there isn’t enough sun.
