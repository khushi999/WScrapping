# Scrape the Web with entities extraction using OpenAI Function

## What is this?

This codebase allows you to scrape any website and extract relevant data points easily using [OpenAI Functions](https://openai.com/blog/function-calling-and-other-api-updates) and [LangChain](https://python.langchain.com/docs/get_started/introduction).
Create a schema in `schemas.py`, pick a url, and use them with `scrape_with_playwright()` in `main.py` to start scraping.

Tip: each website has the bulk of content either in `<p>`, `<span>` or `<h>` tags. For best performance, choose a combination of tags that work for you.

### Example

1. Define the schema of the website you want to scrape in `schemas.py` (Pydantic class or dictionary are both fine):

   ```python
   class SchemaNewsWebsites(BaseModel):
       news_headline: str
       news_short_summary: str
   ```

2. To start scraping, in `main.py`, run something like this:

   ```python
   asyncio.run(scrape_with_playwright(
           url="https://www.bbc.com",
           tags=["span"],
           schema_pydantic=SchemaNewsWebsites
       ))
   ```
