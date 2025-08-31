# LinkedIn Automation Workflow - ReadMe

## Overview  
This workflow automates the discovery, summarization, formatting, and posting of drone-related news articles on LinkedIn using AI and API integrations. It enables scheduled, consistent, and engaging LinkedIn content publishing.

---

## Workflow Steps

### 1. Scheduled Trigger  
- The workflow runs daily at a specified time using a cron-based Schedule Trigger node.

### 2. Date Generator  
- Dynamically calculates today's date and a start date (e.g., 2-4 days earlier) to fetch recent news articles.

### 3. News Discovery  
- Sends a request to a news API (Tavily) using keywords related to drones and filters for trusted news domains.
- Retrieves article metadata such as titles, URLs, publication dates, and raw content.

### 4. Article Splitting & Image Search  
- Splits the list of articles into individual items.
- For each article, performs an image search fetching only valid images (.jpg, .jpeg, .png).

### 5. AI Summarization  
- Uses an AI language model (Groq Chat) to generate concise summaries (2-3 paragraphs), extract relevant hashtags, and identify trending keywords from the article content.

### 6. Content Formatting  
- Another AI agent formats the summary, hashtags, call-to-action, and hook line into a social media–ready caption.
- Selects suitable image URLs from the provided list.

### 7. Parsing AI Output  
- Parses the AI-generated JSON content and selects the first valid image URL for posting.

### 8. Image Download  
- Downloads the selected image to prepare it for upload on LinkedIn.

### 9. Post to LinkedIn  
- Posts the formatted content and image on LinkedIn via API.
- Posts include:
  - Uppercase hook line
  - Summary paragraph
  - Hashtags spaced (no commas)
  - Call-to-action with article link
- Post visibility is set to public.

### 10. Logging  
- Post details like title, summary, URL, image link, publication date, and status are appended to a Google Sheet for record-keeping.

---

## Technologies & Integrations  
- **n8n**: Workflow orchestration platform.  
- **Tavily API**: News and image search engine.  
- **Groq Chat Model (LangChain AI)**: Produces summaries and formatted content.  
- **LinkedIn API**: Automates post publishing.  
- **Google Sheets API**: Records logs of posts.

---

## Scheduling & Timezone  
- Cron trigger set at `30 23 * * *` (11:30 PM daily).  
- Ensure server or system timezone set to **IST (Asia/Kolkata)** to align with Indian time zone.

---

## Usage Instructions  
1. Configure API credentials for Tavily, Groq AI, LinkedIn, and Google Sheets in n8n.  
2. Set system timezone or environment timezone to IST.  
3. Activate workflow and schedule trigger.  
4. Monitor logs in Google Sheets.

---

## Notes & Recommendations  
- Hashtags formatted with spaces, no commas, for LinkedIn compatibility.  
- Hook is uppercased as LinkedIn does not support Markdown bold formatting.  
- Only images with correct formats (.jpg, .jpeg, .png) are used to avoid posting issues.  
- Add error handling and retries to increase robustness.  
- Customize keywords, sources, and frequency as per requirements.

---

This workflow streamlines consistent LinkedIn content generation and posting around drone technology news using AI and automation.
