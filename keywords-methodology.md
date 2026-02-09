# Methodical Approach to AI Responsibility Keywords for 10-K Filtering

**Purpose:** Identify companies with substantial AI activity and AI responsibility disclosures from SEC 10-K filings.

**Date:** 2026-02-09  
**Reproducibility:** All sources cited; methodology transparent.

---

## Part A: Keyword Extraction Methodology

### Step 1: Tiered Keyword Taxonomy

Based on literature review (sources cited below), keywords are organized into 5 tiers:

#### Tier 1: Core AI Terms (Presence Detection)
These identify any AI activity:
```
artificial intelligence
machine learning
deep learning
neural network
generative AI
large language model
LLM
GPT
natural language processing
NLP
computer vision
```

#### Tier 2: AI Technology Terms (Specificity)
```
transformer model
foundation model
predictive analytics
recommendation system
recommendation engine
automated decision
algorithmic
chatbot
virtual assistant
cognitive computing
reinforcement learning
supervised learning
unsupervised learning
convolutional neural network
recurrent neural network
```

#### Tier 3: AI Governance & Responsibility Terms (Maturity Signal)
```
AI ethics
responsible AI
AI governance
AI risk
algorithmic fairness
algorithmic bias
model governance
AI safety
AI audit
AI oversight
AI accountability
explainability
explainable AI
XAI
interpretability
human oversight
human-in-the-loop
```

#### Tier 4: Regulatory & Compliance Terms (Awareness Signal)
```
EU AI Act
NIST AI
AI Risk Management Framework
ISO 42001
algorithmic accountability
AI regulation
AI compliance
AI transparency
model risk management
```

#### Tier 5: Transparency Mechanism Terms (Advanced Maturity)
```
model card
data card
bias testing
fairness testing
red team
AI incident
algorithmic impact assessment
AI impact assessment
third-party audit
```

### Step 2: Keyword Sourcing (Transparent Attribution)

| Source | Contribution | Citation |
|--------|--------------|----------|
| arXiv 2508.19313 | 10-K AI risk keywords, regex patterns | "Are Companies Taking AI Risks Seriously?" (2025) |
| Columbia Law CLS Blue Sky | Two-step keyword + LLM approach | Cao et al. (2024) |
| NIST AI RMF 100-1 | Trustworthy AI characteristics | NIST (2023) |
| EU AI Act Annex IV | Documentation requirements | European Commission (2024) |
| Future of Life AI Safety Index | Safety domain indicators | FLI (2025) |

### Step 3: Filtering Pipeline

**Recommended Approach (from literature):**

1. **Initial Filter:** Search for Tier 1 terms in 10-K full text
2. **Section Extraction:** Focus on:
   - Item 1: Business Description
   - Item 1A: Risk Factors  
   - Item 7: MD&A (Management Discussion & Analysis)
3. **Context Extraction:** For each keyword match, extract 400 words before/after
4. **Classification:** Use LLM to categorize:
   - AI as revenue driver
   - AI as cost reducer
   - AI risks (legal, competitive, operational, societal)
   - AI governance/responsibility mentions
5. **Scoring:** Count Tier 3-5 terms to identify "AI responsibility mature" companies

**Tool Reference:** 
- SEC Analysis Tool: https://github.com/lucas-ubm/sec_analysis (from arXiv paper)
- SEC EDGAR Full-Text Search: https://efts.sec.gov/LATEST/search-index

---

## Part B: Curated Company List for Testing

### Selection Criteria

To test an AI Responsibility Index pipeline, select companies that:
1. **Vary in AI maturity** (frontier developers → AI adopters → minimal AI)
2. **Span sectors** (tech, finance, healthcare, retail, manufacturing)
3. **Have public 10-K filings** (US-listed)
4. **Represent different responsibility postures** (leaders vs. laggards)

### Recommended Test Set (30 Companies)

#### Tier A: Frontier AI Developers (from AI Safety Index)
*Expected: High AI activity, should have strong governance disclosures*

| Company | Ticker | Sector | Source |
|---------|--------|--------|--------|
| Microsoft | MSFT | Technology | AI Safety Index, Digital Inclusion |
| Alphabet/Google | GOOGL | Technology | AI Safety Index, RDR |
| Meta | META | Technology | AI Safety Index, RDR |
| Amazon | AMZN | Technology | RDR, Digital Inclusion |
| NVIDIA | NVDA | Semiconductors | AI Safety Index (supplier) |
| Salesforce | CRM | Technology | Digital Inclusion |
| IBM | IBM | Technology | Digital Inclusion |
| Adobe | ADBE | Technology | Digital Inclusion |
| Oracle | ORCL | Technology | Digital Inclusion |
| Palantir | PLTR | Technology | Known AI focus |

#### Tier B: AI-Mature Financial Services (from Evident AI Index)
*Expected: Operational AI use, risk-focused disclosures*

| Company | Ticker | Sector | Source |
|---------|--------|--------|--------|
| JPMorgan Chase | JPM | Banking | Evident AI Index (#1) |
| Capital One | COF | Banking | Evident AI Index (top 10) |
| Wells Fargo | WFC | Banking | Evident AI Index |
| Bank of America | BAC | Banking | Evident AI Index |
| Goldman Sachs | GS | Banking | Evident AI Index |

#### Tier C: AI-Adopting Non-Tech (from Digital Inclusion / AICDI)
*Expected: Moderate AI mentions, varying governance*

| Company | Ticker | Sector | Source |
|---------|--------|--------|--------|
| Walmart | WMT | Retail | AICDI, S&P 500 |
| UnitedHealth | UNH | Healthcare | S&P 500, known AI use |
| CVS Health | CVS | Healthcare | S&P 500 |
| Johnson & Johnson | JNJ | Healthcare | S&P 500 |
| Coca-Cola | KO | Consumer | S&P 500 (control) |
| Procter & Gamble | PG | Consumer | S&P 500 |
| Caterpillar | CAT | Industrial | S&P 500 |
| John Deere | DE | Industrial | Known AI/automation |
| Tesla | TSLA | Automotive | Known AI focus |
| General Motors | GM | Automotive | S&P 500 |

#### Tier D: Control Group (Low Expected AI Activity)
*Expected: Minimal AI mentions, baseline for comparison*

| Company | Ticker | Sector | Rationale |
|---------|--------|--------|-----------|
| Berkshire Hathaway | BRK.B | Conglomerate | Traditional operations |
| ExxonMobil | XOM | Energy | Legacy industry |
| Duke Energy | DUK | Utilities | Regulated utility |
| Simon Property | SPG | Real Estate | REIT |
| Kroger | KR | Retail | Traditional grocery |

### Data Access

**SEC EDGAR Filings:**
```
https://www.sec.gov/cgi-bin/browse-edgar?action=getcompany&CIK={TICKER}&type=10-K&dateb=&owner=include&count=40
```

**Bulk Download:**
- SEC EDGAR Full-Text Search API
- Financial Modeling Prep API
- Wharton WRDS (academic access)

---

## Validation Approach

### Ground Truth Sources

1. **AI Safety Index scores** (for frontier AI companies)
2. **Evident AI Index scores** (for banks)
3. **Digital Inclusion Benchmark scores** (for tech companies)
4. **Manual annotation** (sample of 5-10 filings reviewed by human)

### Expected Correlations

- Companies with more Tier 3-5 keywords → higher external index scores
- Frontier AI developers → highest keyword density
- Control group → lowest keyword density

---

## References

1. Soudagar et al. (2025). "Are Companies Taking AI Risks Seriously? A Systematic Analysis of Companies' AI Risk Disclosures in SEC 10-K forms." arXiv:2508.19313. https://arxiv.org/abs/2508.19313

2. Cao et al. (2024). "What Firms Disclose About Their Use of AI." Columbia Law School CLS Blue Sky Blog. https://clsbluesky.law.columbia.edu/2024/12/19/what-are-companies-disclosing-about-their-use-of-ai/

3. Weil, Gotshal & Manges LLP (2023). "SEC Disclosures of Artificial Intelligence Technologies." https://www.weil.com/-/media/mailings/2023/q4/sec-disclosures-of-artificial-intelligence-technologies-112723.pdf

4. Future of Life Institute (2025). "AI Safety Index: Summer 2025." https://futureoflife.org/ai-safety-index-summer-2025/

5. Evident Insights (2025). "Evident AI Index." https://evidentinsights.com/ai-index/

6. World Benchmarking Alliance (2023). "Digital Inclusion Benchmark." https://www.worldbenchmarkingalliance.org/publication/digital-inclusion/

7. NIST (2023). "AI Risk Management Framework (AI RMF 1.0)." NIST AI 100-1. https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf

---

*Document generated for reproducible AI responsibility index development.*
