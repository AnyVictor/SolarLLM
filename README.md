Architecture

![Solar LLM Architecture](architecture/Solar%20LLM%20Architecture.png)

Our Summary structure (max. 1,000 words)

1. Product description, 
What Solar LLM is, who it’s for (students at our university), and what problem it solves.
- Providing free AI usage of open weights models (for example Llama, Mistral, or Qwen) for students at CODE university
- Using renewable energy provided by the solar panel on campus to power the GPU server that runs the open weights models
- SolarLLM is a prove of concept for decentralized AI that dynamically adapts to renewable enrgy availability rather than relying on constant energy from fossil fuels
- The goal is cheap and accessible AI (AI for the world)

2. Architecture components,
- UI: Users can access the service from web browsers and mobile apps.

- DNS: DNS translates human-friendly domain names (like solarllm.com) into computer-friendly numerical IP addresses (like 192.0.2.1).

- Server: The server handles requests from users and reads, writes, and updates the database. It sends requests to the queue, receives responses from the GPU server, and subscribes to solar status data from the broker to decide when queued requests are released.

- Database: Stores user data such as IP addresses, emails, names, and activity.

- Message queue: Every user request is added to the queue when it is created. Requests are only sent to the GPU server when solar power is sufficient.

- GPU server: Uses open-weight LLMs to avoid API costs. Users can choose between different models in the UI.

- Solar panel: The plan is to install our solar panel on the roof of the Delta campus. It powers the GPU server.

- Microcontroller (OpenDTU): Collects status data from the solar inverter (e.g. current power in W and energy generated in kWh) and publishes it to the MQTT broker.

- MQTT broker: Receives solar status data published by the microcontroller and forwards it to the server, which subscribes to it.

4. Communication flow, 
How data moves through the system
How the queue holds requests when power is low and releases them when power is good enough.

5. Energy supply,
How the solar panel powers the GPU server, and what happens when there isn’t enough sun.
- The GPU server is directly tied to the generated power from the solar paneland can only run when there is enough power
- For when there isn't enough sun (at nights or on cloudy days):
  - low power priority: when there isn't enough to power the GPU server, the backend server can still accpet student prompts and queue them
  - Dynamic model switching: during low sun exposure the orchestrator can route prompts to smaller LLMs
  - Grid Fallback or energy storage: In case of no sun exposure power could be also sourced from the energy grid or during peak sun hours the energy can be stored in a battery on campus 
