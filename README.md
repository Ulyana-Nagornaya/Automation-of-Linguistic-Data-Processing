# Automation of Linguistic Data Processing
This project is aimed at building basic skills for retrieving data from external WWW resources and processing it for future linguistic
research. The idea is to automatically obtain a dataset that has a certain structure and appropriate content, perform morphological
analysis using various natural language processing (NLP) libraries.

## Project Overview  
This project consists of two core modules:  
1. **Web Scraper**: Crawls media websites to collect articles and metadata.  
2. **Processing Pipeline**: Performs linguistic analysis (POS tagging, morphological features, syntactic patterns) on scraped data.  

---

## Key Features  
### Web Scraper  
- 🕵️♂️ **Recursive Crawling**: Discovers articles across multiple pages using seed URLs.  
- 📄 **Metadata Extraction**: Captures titles, authors, dates (ISO 8601), and topics.  
- 🔒 **Robust Requests**: Configurable headers, timeouts, and SSL verification.  

### Processing Pipeline  
- 🧹 **Text Cleaning**: Removes punctuation and normalizes case.  
- 🔍 **Morphological Analysis**: Generates CoNLL-U annotations via **spaCy-UDPipe** and **Stanza**.  
- 📊 **POS Visualization**: Creates bar charts of part-of-speech distributions.  
- 🌐 **Syntactic Pattern Detection**: Identifies dependency structures (e.g., verb-noun-preposition chains).  

---

## Installation  
```bash  
pip install -r requirements.txt  
```  
**Dependencies**:  
- `beautifulsoup4`, `requests` (Scraper)  
- `spacy_udpipe`, `stanza`, `networkx`, `matplotlib` (Pipeline)  

---


## Technical stack
------------------
| Library                | Description               | Component          |
|------------------------|---------------------------|--------------------|
| `pathlib`              | working with file paths   | Scraper            |
| `requests`             | downloading web pages     | Scraper            |
| `BeautifulSoup4`       | finding information on web| Scraper            |
| `lxml`                 | parsing HTML              | Scraper            |
| `datetime`             | working with dates        | Scraper            |
| `json`                 | working with json format  | Scraper , Pipeline |
| `spacy_udpipe`         | for morphological analysis| Pipeline           |
| `stanza`               | for morphological analysis| Pipeline           |
| `networkx`             | working with graphs       | Pipeline           |


For detailed documentation, see:  
- [Scraper README](Web Scraper/README.rst)  
- [Pipeline README](Pipeline/README.rst)



## Project tasks
1) Creating **Web Scraper** which could automatically parse a media website, save texts and its metadata in a proper format.
2) Creating **Pipeline** can automatically process raw texts from previous step, make point-of-speech tagging and basic morphological analysis.


This project is a part of a compulsory course `Computer Tools for Linguistic Research <https://nnov.hse.ru/ba/ling/courses/835194706.html>`__ in `National Research University Higher School of Economics <https://www.hse.ru/>`__. Github: https://github.com/fipl-hse/2023-2-level-ctlr