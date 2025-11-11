# DATA CLASSIFICATION AND SUMMARIZATION PROJECT  
### ChatGPT Mobile App Sentiment Review Using LLM: IBM Granite  
**By Muhammad Abdurrasyid Fahrurozi**

---

## Overview  
This project evaluates **Large Language Model (LLM)** capabilities for sentiment classification and summarization on user reviews from the ChatGPT mobile app.  
The goal is to compare prompting strategies and parameter settings to find a reliable, human-aligned approach for large-scale review analysis.

---

## Dataset  
- **Rows:** 2,292  
- **Columns:** 4 (`date`, `title`, `review`, `rating`)  
- **No missing values** detected.  
- `title` and `review` are rich and unique, suitable for text analysis.  
- `rating` is intentionally excluded to preserve a zero-shot setup.

---

## Data Preparation  
1. Combined `title` and `review` into one field for full feedback context.  
2. Dropped `date` and `rating` since they’re not used in text-only inference.  
3. Checked text length distribution to ensure compatibility with LLM limits.

---

## Methodology  
- Model: **IBM Granite Instruct**  
- Two prompting strategies:  
  - **Basic Prompting:** zero-shot, no examples.  
  - **Few-Shot Prompting:** includes labeled examples to guide reasoning.  

Parameter sweeps were performed for:
- `temperature`
- `top_p`
- `max_output_tokens`

to observe effects on stability, nuance, and verbosity.

---

## Experiment Summary  
- **Basic prompting:** consistent but oversimplifies mixed reviews.  
- **Few-shot prompting:** improves nuance and mixed-sentiment accuracy.  
- **Parameter effects:**  
  - Lower temperature → more deterministic.  
  - Higher `top_p` → more expressive but less repeatable.  
- Three experiment types: deterministic, creative, and hybrid.

---

## Key Findings  
- Few-shot examples improve mixed sentiment detection.  
- Deterministic runs are best for large-scale automation.  
- Creative setups yield better human-like explanations.  
- Hybrid config provides the best trade-off between accuracy and reasoning.

---

## Conclusion  
After extensive testing, the **Hybrid Configuration** (moderate temperature, moderate `top_p`, and contextual few-shot examples) was chosen as the final setup.  
It delivers the best balance between reproducibility and contextual sensitivity for sentiment analysis and summarization of ChatGPT mobile app reviews.

---

**Author:** Muhammad Abdurrasyid Fahrurozi  
**Decision:** Adopt Hybrid Configuration for further experiments and reporting.
