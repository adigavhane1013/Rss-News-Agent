# RSS News Agent (n8n)

A simple n8n automation that collects news from multiple RSS feeds, cleans and deduplicates them, summarizes the top stories using an AI model, and sends a daily news digest to Telegram.

This project is built as a **learning exercise** to understand how small AI-powered automations work end to end.

---

## What This Workflow Does

1. Triggers automatically on a schedule  
2. Fetches news from multiple RSS sources  
3. Cleans and normalizes article data  
4. Removes duplicate news articles  
5. Sorts news by latest publish date  
6. Selects the top 10 articles  
7. Uses an AI agent to summarize them into 5 bullet points  
8. Sends the final summary to a Telegram chat

---

## Workflow Overview

![Workflow Diagram](./workflow.png)

---

## Output Example

![Telegram Output](./output.png)

---

## Nodes Used

- **Schedule Trigger** – Runs the workflow daily  
- **RSS Feed Read** – Fetches news from RSS sources (BBC, The Hindu)  
- **Code Node (Merge and Format News)** –  
  - Normalizes article fields  
  - Removes duplicates  
  - Sorts by date  
  - Limits results  
- **AI Agent (Google Gemini)** – Summarizes news into 5 bullet points  
- **Telegram Node** – Sends the formatted summary to Telegram  

---

## Key Logic (Merge and Format News)

The Code node:
- Merges articles from multiple RSS feeds  
- Handles missing or inconsistent RSS fields  
- Removes duplicate articles using the title  
- Sorts articles by publish date  
- Outputs only the top 10 articles as a single structured object  

This keeps the AI and Telegram steps clean and predictable.

---

## How to Use

1. Open **n8n**
2. Import the workflow JSON file:
3. Configure credentials:
- RSS feeds (if changed)
- Google Gemini API
- Telegram Bot API
4. Set your Telegram `chatId`
5. Activate the workflow

---

## Notes

- This is a **basic version** intended for learning
- No long-term storage or memory is implemented yet
- Duplicate checking is based only on article titles
- Designed to be extended later with persistence, filtering, and personalization

---

## Future Improvements (Planned)

- Store already-sent articles to avoid repeats across days  
- Better duplicate detection using article links or hashes  
- Topic-based filtering  
- User-specific news preferences  
- Error handling and logging  

---

## License

MIT
