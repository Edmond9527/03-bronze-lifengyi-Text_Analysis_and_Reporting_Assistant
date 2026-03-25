# Intelligent Text Analysis and Reporting Assistant Based on LLM <!-- required -->



[中文版本](./README_ZH.md)

## Project Overview <!-- required -->

This project is an intelligent assistant system designed for data processing and text mining. Relying on a locally deployed LLM cluster, it aims to perform deep structural extraction and multi-dimensional analysis on massive unstructured Chinese and English texts (e.g. course materials, academic papers, and assignments). Core features include intelligent summarization, sentiment analysis, and key feature extraction. Advanced features support batch processing pipelines and multi-document comparative analysis.

## Activity Information <!-- required -->

- **Competition / Workshop:** 2026 NJUPT Winter Battle <!-- required: replace with your activity name -->
- **Team Members:** Fengyi Li, Hongqing Du <!-- required: list all team members -->
- **Awarded:** Bronze 

## Environment <!-- required -->

- **Base Image:** Basic GPU Environment (aup-learning-cloud)
- **Extra Dependencies:** Listed in `requirements.txt` <!-- required: briefly describe key packages if any, or write "None" -->
- **GPU:** AMD Radeon 8060S

## Quick Start <!-- required -->

<!-- Step-by-step instructions to run your notebook. Be specific. -->

1. In aup-learning-cloud, select **Basic GPU Environment** and set the Git URL to this repository
2. Navigate to `cases/2026-03-njupt-winter-camp/03-bronze-lifengyi-Text_Analysis_and_Reporting_Assistant`
3. Open `main.ipynb`
4. Run all cells from top to bottom, requirement is already in the first cell.

## Technical Highlights

* **Prompt Engineering:** Utilized System Roles, Few-shot prompting, and Chain-of-Thought (CoT) to ensure stable formatting and complex logical deduction
![result](./assets/few_shot.jpg)
***Context Window Management:** Implemented cascaded summary generation and an adaptive allocation algorithm to prevent Out-Of-Memory (OOM) errors with long texts
![result](./assets/single.png)
* **API Lifecycle Management:** Designed robust error handling with a linear backoff retry strategy to mitigate server rate limits and avoid "retry storms".
* **Robust Data Parsing:** Normalized polymorphic data streams and added a pre-execution circuit breaker to isolate corrupted files without crashing the pipeline.
* **Asynchronous Concurrency:** Used `ThreadPoolExecutor` to parallelize subtasks, masking network I/O latency and significantly boosting throughput.
* **I/O Optimization & Frontend:** Bypassed Jupyter WebSocket limits with a dual-modal I/O (including server-side direct read) and built an embedded GUI using native `ipywidgets`.
## Results / Demo

* **Real-time File Dashboard:** Provides a real-time monitor for file parsing status, extracted character count, and estimated Token consumption, including smart alerts for exceeding text limits.
* **Batch Analysis Pipeline:** Breaks single-request limits, automatically outputting standardized Markdown reports containing summaries, sentiment scores, and keywords to achieve machine-level efficient review.
* **Multi-Document Comparative Report:** Overcomes single-text limitations; the system automatically summarizes and generates a structured deep analysis report encompassing "core themes, commonalities, and key differences" across multiple documents.

![demo](./assets/longtext.gif)
## References
* **Ollama API Docs:** https://ollama.readthedocs.io/api/

