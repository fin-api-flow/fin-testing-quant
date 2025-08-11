# fin-testing-quant
Some financial testing apps leveraging LLM's. 


# fin-testing-quant

> **Financial testing apps, powered by Large Language Models (LLMs)**

![License](https://img.shields.io/badge/License-MIT-blue.svg) ![Python](https://img.shields.io/badge/Python-3.10%2B-blue)

---

## 📖 Overview

`fin-testing-quant` is a collection of experimental tools and mini‑apps that explore how modern LLMs can accelerate quantitative research and portfolio testing workflows. The repo bundles data connectors, prompt‑driven analysis helpers, and reproducible notebooks that show how to:

* Generate hypothesis‑driven trading strategies in plain English and translate them into executable Python back‑tests.
* Stress‑test models with synthetic market regimes produced by LLM‐guided scenario generation.
* Explain trade performance in natural language for automated report writing.

> **Disclaimer**
> This code is provided **for research and educational purposes only** and should **not** be considered investment advice in any form.

---

## ⚡️ Key Features

| Area                   | Highlights                                                                                       |
| ---------------------- | ------------------------------------------------------------------------------------------------ |
| **Prompt‑to‑Backtest** | Convert prose strategy specs into vectorized Pandas back‑tests via the `llm_backtester` package. |
| **Scenario Generator** | Leverage GPT‑4o to fabricate tail‑risk market paths for stress analysis.                         |
| **Explainability**     | Summarise P\&L drivers, drawdowns, and factor exposures in readable paragraphs.                  |
| **Plug‑and‑Play Data** | Built‑in loaders for Yahoo Finance, FRED, and Polygon.io (optional).                             |
| **Modular Design**     | Each component can be used standalone or orchestrated via a CLI.                                 |

---

## 🏗️ Repository Structure

```
fin-testing-quant/
├── apps/                # Streamlit & FastAPI front‑ends
├── data/                # Lightweight dataset samples (<1 MB)
├── llm_backtester/      # Core library – prompt parser → vectorized engine
├── notebooks/           # Jupyter demos & case studies
├── tests/               # Pytest suites & fixtures
├── .env.example         # Environment variable template
└── pyproject.toml       # Poetry build config
```

---

## 🚀 Quickstart

```bash
# 1. Clone the repo
$ git clone https://github.com/your‑org/fin-testing-quant.git && cd fin-testing-quant

# 2. Install dependencies (Poetry recommended)
$ poetry install --with dev

# 3. Set your OpenAI (or Azure OpenAI) key
$ cp .env.example .env  # then edit

# 4. Run a sample notebook
$ poetry run jupyter lab notebooks/01_basic_prompt_backtest.ipynb
```

> **Note:** GPU is **not** required; CPU works fine for the examples.

---

## 🛠️ Configuration

Environment variables (see `.env.example`):

| Variable         | Purpose                           |
| ---------------- | --------------------------------- |
| `OPENAI_API_KEY` | API key for OpenAI models         |
| `DATA_PROVIDER`  | `yfinance`, `polygon`, or `local` |
| `MAX_TOKENS`     | Token budget for LLM calls        |

---

## 💻 Usage Examples

### 1. English → Back‑Test

```python
from llm_backtester import StrategyLLM

spec = "Long the S&P 500 when the 50‑day SMA crosses above the 200‑day SMA; exit when it crosses below."
results = StrategyLLM().backtest(spec, ticker="SPY", start="2010-01-01")
results.plot_equity_curve()
```

### 2. Generate Stress Scenarios

```python
from llm_backtester import ScenarioFactory
scenarios = ScenarioFactory().generate("COVID‑style liquidity crunch lasting 3 months")
```

### 3. CLI Workflow

```bash
$ poetry run fin‑quant gen‑strategy --prompt "Pairs trade EURUSD vs GBPUSD based on PPP divergence"
```

---

## ✔️ Testing & Linting

```bash
$ poetry run pytest          # Run unit tests
$ poetry run coverage html   # Generate coverage report
$ poetry run ruff check .    # Static analysis
```

---

## 🗺️ Roadmap

* [ ] LangChain agent support for multi‑step research chains
* [ ] Vector‑store caching for prompt results
* [ ] Reinforcement learning loop to auto‑tune strategy parameters

Feel free to open issues or vote on features!

---

## 🤝 Contributing

1. Fork the project and create your branch: `git checkout -b feature/AmazingFeature`
2. Commit your changes: `git commit -m 'Add some AmazingFeature'`
3. Push to the branch: `git push origin feature/AmazingFeature`
4. Open a pull request

All contributions must pass CI (tests, lint, formatting) before review.

---

## 📄 License

Distributed under the **MIT License**. See `LICENSE` for more information.

---

## 📬 Contact & Credits

* **Maintainer:** [Your Name](mailto:you@example.com)
* Powered by [OpenAI](https://openai.com) and the amazing open‑source quant community.

---

*Happy back‑testing! 🚀*
