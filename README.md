# 📊 WhatsApp Chat Analysis: Link Down Messages and NET Ticket Extraction

## 🔍 Project Overview
This project analyzes WhatsApp chat data to identify "Link Down" incidents reported by a specific sender (e.g., Lnoc) and correlates them with follow-up messages that include NET ticket identifiers. It was designed to extract insights for network incident tracking and escalation.

## 📁 File Structure
- **whatsapp_chat.txt**: Raw WhatsApp chat exported from the app.
- **march_2025_chats.csv**, **april_2025_chats.csv**, **may_2025_chats.csv**: Parsed data per month.
- **march_link.csv**, **april_link.csv**, **may_link.csv**: Link down messages with associated NET tickets.
- **march_escalated_links.csv**, etc.: Final cleaned data with essential columns.

## ⚙️ How It Works

### Parsing the Chat
- The WhatsApp chat is parsed using regular expressions to extract date, time, sender, and message.
- The result is converted into a Pandas DataFrame with proper datetime formatting.

### Filtering by Date
- Messages are filtered for March, April, and May 2025.
- Each month's messages are saved to separate CSV files.

### Extracting Link Down Messages
- From each month's data, messages from the sender "Lnoc" that contain the keyword "Link Down" are selected.
- Within 15 minutes of each "Link Down" message, the script checks for any message containing a NET ticket pattern (e.g., NET123456).

### Cleaning Data
- Only the messages that had a matching NET ticket are retained.
- Extracted endpoints from messages are included in the cleaned output CSVs.

### Summary Output
- A combined summary of all link down incidents and associated NET tickets across all three months is printed and optionally displayed.

## 🧪 Technologies Used
- Python
- Pandas
- Regular Expressions
- Matplotlib (optional for future visualization)

## 📈 Output Examples
Each final cleaned CSV includes:
- **datetime**: Timestamp of the link down message.
- **link_endpoints**: Extracted link or site affected.
- **net_ticket**: NET ticket associated with the incident.

## ✅ Use Cases
- Automating escalation tracking for NOC teams.
- Improving visibility into incident patterns.
- Generating monthly reports for network performance reviews

## 🛠️ Setup Instructions
1. Place your WhatsApp chat export file as `whatsapp_chat.txt`.
2. Run the Python script (e.g., in Jupyter or VS Code).
3. Review and analyze the CSV outputs for escalated incidents.

## 📌 Notes
- Make sure the chat file format is not altered from WhatsApp export (txt format).
- The sender's name should match exactly (Lnoc in this case).
- The link down message should include `Link Down | <endpoints>` format for full accuracy.
