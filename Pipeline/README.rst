# Text Processing Pipeline for Linguistic Analysis  

## Overview  
This pipeline processes raw text data collected by the web scraper, performs advanced linguistic analysis, and generates structured outputs for downstream research. It supports text cleaning, morphological tagging, part-of-speech (POS) frequency analysis, and syntactic pattern detection using state-of-the-art NLP libraries.  

---

## Key Features  
1. **Text Cleaning**  
   - Removes punctuation and converts text to lowercase.  
   - Output: `N_cleaned.txt` per article.  

2. **Morphological Analysis**  
   - Generates Universal Dependencies (UD) annotations using **spaCy-UDPipe** and **Stanza**.  
   - Output:  
     - `N_udpipe_conllu.conllu` (UDPipe model)  
     - `N_stanza_conllu.conllu` (Stanza model)  

3. **POS Frequency Analysis**  
   - Calculates POS distributions (e.g., noun/verb/adjective counts).  
   - Visualizes results as bar charts: `N_image.png`.  
   - Extends metadata with frequency data.  

4. **Syntactic Pattern Detection**  
   - Uses **NetworkX** to identify dependency graphs matching predefined patterns (e.g., verb-noun-preposition structures).  
   - Stores detected patterns in metadata.  

---

## Configuration  
The pipeline operates on the same dataset directory as the scraper (`tmp/articles`). No additional configuration files are required.  

---

## Usage  
1. **Run the Pipeline**  
   ```bash  
   python pipeline.py  
   ```  

2. **Output Structure**  
   ```  
   tmp/  
   └── articles/  
       ├── 1_cleaned.txt        # Cleaned text  
       ├── 1_udpipe_conllu.conllu # UDPipe annotations  
       ├── 1_stanza_conllu.conllu # Stanza annotations  
       ├── 1_image.png          # POS frequency visualization  
       └── ...  
   ```  

---

## Implementation Details  
- **Corpus Management**  
  - `CorpusManager` validates and indexes raw data, ensuring consistency and integrity.  

- **Text Processing**  
  - **UDPipe/Stanza Wrappers**: Unified interface for morphological analysis.  
  - **POS Frequency Pipeline**: Aggregates statistics and generates visualizations using `matplotlib`.  

- **Syntactic Analysis**  
  - Builds dependency graphs with **NetworkX** to detect patterns like `[VERB] -> [NOUN] -> [ADP]`.  

---

## Applications  
- **Linguistic Research**: Analyze syntax, morphology, and lexical trends.  
- **NLP Model Training**: Generate annotated corpora for POS tagging or dependency parsing.  
- **Data Visualization**: Explore POS distributions and syntactic structures.  

For raw data collection, refer to the **Web Scraper** module.