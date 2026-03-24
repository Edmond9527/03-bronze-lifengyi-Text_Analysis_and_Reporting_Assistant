# JupyPilot: A Notebook-Native Engineering Assistant with Prompt-Orchestrated Tooling <!-- required -->

[中文版本](./README_ZH.md)

## Project Overview <!-- required -->

JupyPilot is a notebook-native engineering assistant that unifies code QA, patch generation, test generation, style checking, and scaffold planning under one orchestration workflow.  
It uses a layered architecture (`Orchestrator`, `ToolRuntime`, prompt registry, and `ipywidgets` UI) so model outputs remain grounded in real repository evidence rather than free-form guesses.  
The system includes validation-retry logic, single-turn fallback, context-budget control, and event logging to improve reliability in long-context and multi-step tool-calling scenarios.

## Activity Information <!-- required -->

- **Competition / Workshop:** 2026 NJUPT Winter Battle <!-- required: replace with your activity name -->
- **Team Members:** Hao Luo <!-- required: list all team members -->
- **Awarded:** Silver <!-- required: use N/A if not yet announced -->

## Environment <!-- required -->

- **Base Image:** Basic GPU Environment (aup-learning-cloud)
- **Extra Dependencies:** `ipywidgets>=8.1`, `requests>=2.31` (see `requirements.txt`) <!-- required: briefly describe key packages if any, or write "None" -->

## Quick Start <!-- required -->

1. In aup-learning-cloud, select **Basic GPU Environment** and set the Git URL to this repository
2. Navigate to `cases/2026-03-njupt-winter-battle/[wabibabo]-[JupyPilot]/`
3. Install project dependencies first: `!python -m pip install -e .`
4. Open `main.ipynb` (English) or `main_zh.ipynb` (Chinese)
5. Run all notebook cells to complete environment checks and launch `JupyPilotApp`
6. For CLI launch (optional), run `python run.py --no-browser` in this folder

## Project Structure (Reviewer Reading Order)

- `README_ZH.md` / `README.md`: project overview and run instructions.
- `main_zh.ipynb`, `main.ipynb`: submission notebooks and runnable demo entrypoints.
- `jupypilot/`: core source code (orchestrator, tool runtime, RAG, UI, logging).
- `prompts/`: prompt templates and versioned prompt-engineering assets.
- `requirements.txt`, `pyproject.toml`: dependency and packaging definitions.
- `run.py`, `config.example.yaml`: optional CLI startup and config example.

## Technical Highlights

- **Unified task orchestration:** Supports code_qa, code_patch, testgen, refactor, and scaffold tasks in one consistent tool-loop workflow.
- **Controlled tool execution:** Restricts model actions to whitelisted tools (`search_code`, `open_file`, `run_task`, etc.) with read-only defaults.
- **Reliability engineering:** Adds output-contract validation, correction retries, single-turn fallback, stream timeout caps, and output-size guards.
- **Long-context handling:** Uses sliding windows, memory summarization, and token-budgeted context assembly for 32K-class context workloads.
- **Observability and replay:** Persists event logs, session snapshots, and patch artifacts for debugging, demonstration, and review.

## Results / Demo

This submission can demonstrate the following end-to-end workflow:
- Notebook-based initialization and interactive UI startup;
- Repository-grounded code QA, patch generation, and verification flow;
- Prompt-engineering and tool-orchestration design in practical implementation.
- ![demo](./png/1.png)
- ![demo1](gif/1.gif)
- ![demo](./png/2.png)
- ![demo1](gif/2.gif)
- ![demo](./png/3.png)
- ![demo1](gif/3.gif)
- ![demo](./png/4.png)
- ![demo1](gif/4.gif)
- ![demo](./png/5.png)
- ![demo1](gif/5.gif)
## References

- Jupyter Notebook
- Ollama API
- Internal `jupypilot/` source modules and `prompts/` prompt-engineering assets
