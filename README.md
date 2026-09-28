# Ultimate-Company-Research-Automation
I built an n8n workflow that automates company research. It takes a list of companies from Google Sheets, scrapes Trustpilot reviews and websites, pulls LinkedIn data, and uses GPT-4o-mini to generate review summaries and structured company profiles. Everything is saved back to Google Sheets.
Scrapes Trustpilot reviews using the Firecrawl API.
Cleans the data (a JavaScript Code node extracts company name, trust score, total reviews, and each review's rating, title and text using regex).
Summarizes customer feedback with GPT-4o-mini: overall sentiment, sentiment per product, and the top 2-3 improvement areas.
Scrapes the company website through Jina AI (r.jina.ai), which converts pages to clean text.
Builds a structured company profile as JSON (basics, business overview, products and services, market position, culture) using an Information Extractor node.
Pulls LinkedIn company data (followers, industry, HQ, founded year, about-us) through the Proxycurl (Nubela) API.
Saves everything into a Google Sheet, one row per company.
Flow

Manual Trigger → Google Sheets (read company list) → Loop Over Items → Firecrawl (Trustpilot) → Set → Code (parse reviews) → LLM review summary → Jina (website) → Information Extractor (company profile) → Proxycurl (LinkedIn) → Wait → Google Sheets (append results)

Tools used
Tool	Purpose
n8n	Workflow automation platform
Google Sheets	Input list and output database
Firecrawl API	Scraping Trustpilot reviews
Jina AI Reader (r.jina.ai)	Turning websites into clean text
Proxycurl / Nubela API	LinkedIn company data
OpenAI GPT-4o-mini	Review summarizing and website analysis
LangChain nodes	Basic LLM Chain, Information Extractor
n8n logic nodes	Set, Code (JavaScript), Split In Batches (loop), Wait
Skills demonstrated
Workflow automation and orchestration
Web scraping through APIs (Firecrawl, Jina)
REST API integration with authentication (HTTP Request nodes)
Prompt engineering for summarization and structured JSON extraction
Data cleaning with JavaScript and regex
Batch processing with loops and a Wait node for rate limits
Data enrichment (combining reviews, website and LinkedIn data)
Sentiment analysis
Business use case

It suits sales teams, marketers and agencies for lead research, competitor analysis and market research. It replaces hours of manual research per company with an automated pipeline.

