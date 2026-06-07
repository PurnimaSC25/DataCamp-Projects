# Enriching Stock Market Data using the OpenAI API

Analyzes Nasdaq 100 California-headquartered companies by merging financial performance data, classifying each stock into a sector, and generating AI-powered investment recommendations using the OpenAI API.

# Project Objective
The Goal
Nasdaq 100 data in raw CSV form is just a list of company names and price numbers which tells you what happened (stock went up 42% YTD) but not why it matters or what to do with it. The goal was to turn that raw data into something actionable by layering in two things: sector context and investment reasoning, something which a spreadsheet can't give.

# The Question
Given the year-to-date performance of Nasdaq 100 companies headquartered in California, which sectors and specific stocks are worth investing in right now?

# The code solves the below things in sequence:
Merge CSVs -> The company names and performance numbers live in two separate files so they need to be connected  by merging on the symbol column
Sector classification -> Raw data has no sector labels because of which we can't compare "Apple vs Pfizer" meaningfully without knowing one is Tech and the                                 other is Healthcare                                          
AI recommendation -> Even with sectors and YTD numbers, a human still has to interpret them, the LLM does that interpretation at scale in seconds

# Tools & Technologies Used
Language: Python
Libraries: Pandas, openai, json
Environment: DataCamp DataLab

# What the Project Does?
• Ingests two CSV datasets (company info + price performance) and merges them on a shared key using pandas, producing a clean, analysis-ready DataFrame     
• Calls the OpenAI Chat Completions API (gpt-4o-mini) to classify 100 Nasdaq-listed companies into one of 10 sectors: Technology, Healthcare, Financials, and more   
• Sends a structured prompt with all 100 companies to the API in a single batched call, returning a JSON array that is parsed and mapped back to the DataFrame, replacing a naive per-row approach that would have made ~100 separate API calls     
• Constructs a second prompt that passes the enriched dataset (symbol, name, sector, YTD) to the model as a senior equity analyst persona, generating a natural-language recommendation of the two best sectors and top stock picks with rationale     
• Stores the final recommendation as a variable (`stock_recommendations`) for downstream use or reporting

# Key Engineering Decisions
→ Batched API call over row-wise apply(). This reduced ~100 network round-trips to 1, cutting latency from ~2 to 5 minutes to seconds    
→ Prompt design instructs the model to return strict JSON with no markdown or preamble, enabling reliable json.loads() parsing without brittle string cleanup    
→ Persona prompting ("you are a senior equity analyst") used to anchor the model's output style and improve recommendation quality

# 📈 Key Insights & Results
important things discovered in the data:                       
**Insight 1:** What did the data show?
Technology and Communication dominated YTD performance: the AI-powered analysis identified these as the two strongest sectors, with Technology averaging 46.5%    YTD and Communication averaging 45.9% YTD across all classified companies in the dataset.

**Insight 2:** What was surprising?
Nvidia (NVDA) stood out as the single biggest outlier with a 217.27% YTD return, it outperformed every other company in the dataset by a wide margin, driven by surging demand for GPUs in AI infrastructure. Meta (META) was a close second surprise at 153.78%, reflecting a strong advertising rebound after a difficult prior year. This is by far the unexpected finding in the dataset.

**Conclusion:** What action should someone take based on your data?
Based on the data, concentrating exposure in Technology (NVDA, ADBE, AVGO) and Communication (META, GOOGL, NFLX) offered the strongest risk-adjusted upside among Nasdaq 100 CA companies during this period.
