# Web Scraper for Media Content Extraction  

## Overview  
This web scraper is designed to automatically collect articles and associated metadata from media websites, forming a structured dataset for downstream linguistic analysis and NLP tasks. The tool crawls specified entry points, extracts article URLs, parses content, and saves raw text alongside metadata in a standardized format.  

---

## Key Features  
1. **Recursive Crawling**  
   - Starts from a single seed URL and recursively explores linked pages to discover all available articles.  
   - Dynamically adjusts depth and breadth of crawling to meet the target number of articles.  

2. **Comprehensive Metadata Extraction**  
   - Captures:  
     - Article ID and URL  
     - Title, author(s), and publication date (normalized to `YYYY-MM-DD HH:MM:SS`)  
     - Topics/keywords (if available)  

3. **Robust Web Interaction**  
   - Configurable request headers, timeouts, and SSL verification.  
   - Graceful handling of unavailable pages (skips errors without crashing).  

4. **Structured Output**  
   - Saves each article as:  
     - `ID_raw.txt`: Raw text content  
     - `ID_meta.json`: Metadata in JSON format  
   - Output directory: `tmp/articles/`  

---

## Configuration  
The scraper is controlled via `scrapper_config.json`:  

| Parameter                  | Description                                   | Example Value                     |  
|----------------------------|-----------------------------------------------|-----------------------------------|  
| `seed_urls`                | List of starting URLs for crawling            | `["www.securitylab.ru/news"]`    |  
| `total_articles_to_find`   | Target number of articles to collect          | `150`                             |  
| `headers`                  | Custom HTTP headers                           | `{"User-Agent": "Mozilla/5.0"}`   |  
| `encoding`                 | Page encoding (e.g., `utf-8`)                 | `"utf-8"`                         |  
| `timeout`                  | Request timeout (seconds)                     | `10`                              |  
| `should_verify_certificate`| Enable/disable SSL verification               | `true`                            |  

---

## Usage  
1. **Run the Scraper**  
   ```bash  
   python scrapper.py  
   ```  

2. **Output Structure**  
   ```  
   tmp/  
   └── articles/  
       ├── 1_raw.txt       # Article text  
       ├── 1_meta.json     # Metadata  
       ├── 2_raw.txt  
       ├── 2_meta.json  
       └── ...  
   ```  

---

## Implementation Details  
- **Crawler**:  
  - Uses a recursive strategy to explore pages linked from the seed URL.  
  - Detects and filters article URLs based on site-specific patterns.  

- **Parser**:  
  - Leverages `BeautifulSoup` for HTML parsing.  
  - Normalizes dates to a unified format using `datetime`.  

- **Error Handling**:  
  - Retries failed requests and skips unreachable pages.  
  - Validates configuration parameters at startup.  

---

## Applications  
This scraper generates a clean dataset for:  
- Linguistic analysis (word frequency, readability, etc.)  
- Training NLP models (POS tagging, named entity recognition)  
- Trend analysis over time using publication dates  

For further processing, integrate with the **Pipeline** module for morphological analysis.