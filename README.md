Home Restaurant Automated Assistant (n8n Workflow)

💡 Project Overview
This project implements a robust, automated customer service and order processing system for the fictional HomeTaste Restaurant using n8n.io. It leverages a powerful AI model, contextual memory, and Google Sheets integrations to handle customer inquiries, manage inventory, and log orders in real-time.

The workflow is currently configured for a testing environment (Manual Trigger) but is designed for quick deployment via a WhatsApp API trigger.

🛠️ Technology Stack
* Workflow Automation: n8n.io (Self-hosted or Cloud)
* Core Intelligence: AI Agent Node (configured with a model like OpenChat or similar LLM)
* Data Storage: Google Sheets (for Inventory, Orders, and FAQs)
* Context Management: Simple Memory Node
* Future Deployment Target: WhatsApp API (via a dedicated n8n Trigger/Send Message Node)

✨ Key Features
1. Context-Aware AI Chat: Uses a Simple Memory Node to maintain conversation history, allowing the AI to follow complex, multi-step customer requests.
2. Multilingual Support: The AI Agent is prompted to detect and reply in the customer's input language (specifically Roman Urdu and English).
3. Real-Time Inventory Management: Before confirming an order, the AI checks the Google Sheets Inventory for item availability and automatically reduces stock upon confirmation.
4. Automated Order Logging: Confirmed orders are immediately saved with all details (Customer Name, Item, Quantity, Date) into the Google Sheets Order Database.
5. Instant FAQ Handling: Customer queries regarding timings, delivery, or payment methods are answered instantly by fetching data from the dedicated FAQ sheet.

🔄 Workflow Logic (Step-by-Step)
The workflow follows a clear logical path for every incoming customer message:

1. Trigger: A message is received (currently via Manual Trigger for testing).
2. Memory & Context: The message is passed to the Simple Memory Node to update the conversation history.
3. AI Processing: The AI Agent Node (using the custom system prompt) analyzes the message intent:
    * If Order: Interacts with the Inventory Sheet (Check Stock) -> If confirmed, updates Order Sheet (Log Order) -> Optional: Updates Inventory (Reduce Stock).
    * If FAQ: Interacts with the FAQ Sheet (Fetch Answer).
    * If Status Check: Interacts with the Order Sheet (Retrieve Status).
4. Reply: The final reply formulated by the AI is sent back to the customer (currently displayed in the n8n output window).

🚀 Setup and Installation

Prerequisites
You need access to:
1. An active n8n instance (Desktop, Cloud, or Self-hosted).
2. An API Key for your chosen Large Language Model (LLM) (e.g., OpenChat API credentials).
3. A Google Service Account and the necessary Google Sheets setup for API access.

Google Sheets Setup
Create the following three Google Sheets with these header structures (at minimum):
- Inventory Sheet: Item Name, Available Quantity, Price
- Order Sheet: Order ID, Customer Name, Item, Quantity, Status, Date
- FAQ Sheet: Question, Answer

n8n Configuration
1. Import: Import the .json file of the workflow (not provided here, but this is where the user would place their n8n export) into your n8n canvas.
2. Credentials Update: Update the credentials for the following nodes:
    * AI Agent Node: Insert your LLM API Key.
    * Google Sheets Nodes: Insert your Google Sheets Service Account credentials and update the Spreadsheet ID for all three sheets.
3. Testing: Use the Manual Trigger Node to input test messages (e.g., "I want Biryani x 2") and execute the workflow to verify functionality.

👨‍🏫 Acknowledgement
Special thanks to Sir Zafar Iqbal for the guidance and mentorship provided throughout the development and successful implementation of this complex n8n workflow.
