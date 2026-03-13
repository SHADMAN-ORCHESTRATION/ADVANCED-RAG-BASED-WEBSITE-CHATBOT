
# ADVANCED-RAG-BASED-WEBSITE-CHATBOT
a smart assistant that can remember conversations, look up company policy, save leads to a sheet, book calendar slots and even place an outbound call when needed.

The goal of the project is to handle incoming chat messages automatically and respond using an AI assistant that can also perform real actions like saving leads or booking appointments.

Instead of building a full backend chat system from scratch, this workflow uses a webhook as the entry point. When a visitor sends a message from the website chat widget, the message is sent to the webhook endpoint. From there the workflow processes the request and forwards it to an AI agent.

Before the message reaches the AI, the workflow runs a small normalization step. This step cleans the incoming payload and converts it into a simple format that always contains the message text, the user identifier, and the sender name. This helps keep the rest of the workflow consistent even if the website sends slightly different request structures.

Once the message is normalized, the workflow checks whether the message actually contains useful text. Empty requests or system pings are filtered out so the AI only processes real user messages.

The message is then passed to an AI agent that acts as the chat assistant. The assistant is designed to reply quickly and keep responses short, similar to how a real live chat agent would respond. The AI can also use several tools when needed.

For example, when a visitor shares contact information, the assistant can store the data in Google Sheets so it becomes a lead entry. If the visitor wants to schedule a meeting, the assistant can create a new event in Google Calendar and automatically generate a one-hour appointment slot. The system also stores recent conversation history inside MongoDB so the assistant can remember the context of the conversation.

To help the AI answer company related questions, the workflow can connect to a vector database using Pinecone. This allows the assistant to search company documents, policies, or knowledge base data and respond with relevant answers during the conversation.

The overall goal of the system is to behave like a lightweight automated receptionist for a website. A visitor sends a message, the assistant understands the request, replies instantly, and performs useful actions when required.

Because everything is built inside n8n, the workflow is easy to extend. New tools, APIs, or integrations can be added without rewriting the entire system.

This project is mainly meant as an example of how AI agents, automation workflows, and external services can be combined to create a functional website chat assistant.
