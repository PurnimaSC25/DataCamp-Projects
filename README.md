# Enriching Stock Market Data using the OpenAI API

Analyzes Nasdaq 100 California-headquartered companies by merging financial performance data, classifying each stock into a sector, and generating AI-powered investment recommendations using the OpenAI API.

# Project Objective
The Goal
Nasdaq 100 data in raw CSV form is just a list of company names and price numbers which tells you what happened (stock went up 42% YTD) but not why it matters or what to do with it. The goal was to turn that raw data into something actionable by layering in two things: sector context and investment reasoning, something which a spreadsheet can't give.

# The Question
Given the year-to-date performance of Nasdaq 100 companies headquartered in California, which sectors and specific stocks are worth investing in right now?

# The code solves the below things in sequence:
Merge CSVs ------------------> The company names and performance numbers live in two separate files so they need to be connected  
Sector classification -------> Raw data has no sector labels because of which we can't compare "Apple vs Pfizer" meaningfully without knowing one is Tech and the                                 other is Healthcare                                          
AI recommendation -----------> Even with sectors and YTD numbers, a human still has to interpret them, the LLM does that interpretation at scale in seconds

# Tools & Technologies Used
Language: Python
Libraries: Pandas, openai, json
Environment: DataCamp DataLab

# 📈 Key Insights & Results
important things you discovered in the data:
**Insight 1:** What did the data show?
Technology and Communication dominated YTD performance — the AI-powered analysis identified these as the two strongest sectors, with Technology averaging 46.5%    YTD and Communication averaging 45.9% YTD across all classified companies in the dataset.

**Insight 2:** What was surprising?
Nvidia (NVDA) stood out as the single biggest outlier — with a 217.27% YTD return, it outperformed every other company in the dataset by a wide margin, driven by surging demand for GPUs in AI infrastructure. Meta (META) was a close second surprise at 153.78%, reflecting a strong advertising rebound after a difficult prior year. This is by far the unexpected finding in the dataset.
5. **Conclusion:** What action should someone take based on your data?
