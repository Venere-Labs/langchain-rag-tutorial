# LangChain RAG Tutorial

![Python](https://img.shields.io/badge/python-3.10--3.13-blue.svg)
![LangChain](https://img.shields.io/badge/langchain-%3E%3D1.0-green.svg)
![License](https://img.shields.io/badge/license-MIT-blue.svg)
![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4o--mini-orange.svg)
![Docker](https://img.shields.io/badge/docker-ready-2496ED.svg?logo=docker&logoColor=white)
![Tests](https://img.shields.io/badge/tests-pytest-0A9EDC.svg?logo=pytest&logoColor=white)

A hands-on tutorial for building **Retrieval-Augmented Generation (RAG)** systems with LangChain 1.x,
from a first retrieval chain to graph-based, agentic and multimodal architectures.

**Contents:** 21 Jupyter notebooks (an index plus 01-20) covering 15 RAG architectures, RAGAS evaluation and embedding
fine-tuning; a reusable `shared/` module; FastAPI, Streamlit and AWS Lambda deployment templates;
Docker support, a pytest suite and GitHub Actions CI.

## Quick Start

```bash
git clone https://github.com/gianlucamazza/langchain-rag-tutorial.git
cd langchain-rag-tutorial

python3 -m venv venv                # Python 3.10-3.13
source venv/bin/activate            # Windows: venv\Scripts\activate
pip install -r requirements.txt

cp .env.example .env                # then set OPENAI_API_KEY
jupyter notebook notebooks/00_index.ipynb
```

Prerequisites: Python 3.10-3.13, an OpenAI API key, about 2 GB of RAM and disk space. Notebooks 08
and 10 also use a Tavily API key for web search; notebook 17 needs Tesseract and Poppler.
See [Getting Started](docs/GETTING_STARTED.md) for the guided path and
[Installation](docs/INSTALLATION.md) for details.

## Notebooks

**Fundamentals** ([notebooks/fundamentals/](notebooks/fundamentals/), 30-40 min):
document loading and splitting (01), OpenAI vs HuggingFace embeddings (02), simple RAG (03).

**Advanced architectures** ([notebooks/advanced_architectures/](notebooks/advanced_architectures/), 4-5 hours):

| #   | Notebook                                                                                                   | Complexity | Use case            | Key technique                    |
| --- | ---------------------------------------------------------------------------------------------------------- | ---------- | ------------------- | -------------------------------- |
| 04  | [Memory RAG](notebooks/advanced_architectures/04_rag_with_memory.ipynb)                                    | 2/5        | Chatbots            | Conversation history             |
| 05  | [Branched RAG](notebooks/advanced_architectures/05_branched_rag.ipynb)                                     | 3/5        | Research            | Multi-query parallel retrieval   |
| 06  | [HyDE](notebooks/advanced_architectures/06_hyde.ipynb)                                                     | 3/5        | Ambiguous queries   | Hypothetical documents           |
| 07  | [Adaptive RAG](notebooks/advanced_architectures/07_adaptive_rag.ipynb)                                     | 4/5        | Mixed workloads     | Query routing                    |
| 08  | [Corrective RAG](notebooks/advanced_architectures/08_corrective_rag.ipynb)                                 | 4/5        | High accuracy       | Relevance grading + web fallback |
| 09  | [Self-RAG](notebooks/advanced_architectures/09_self_rag.ipynb)                                             | 5/5        | Self-correcting     | Self-critique and refinement     |
| 10  | [Agentic RAG](notebooks/advanced_architectures/10_agentic_rag.ipynb)                                       | 5/5        | Complex reasoning   | Multi-tool agent loop            |
| 11  | [Comparison](notebooks/advanced_architectures/11_comparison.ipynb)                                         | -          | Benchmarking        | Side-by-side evaluation          |
| 12  | [Contextual RAG](notebooks/advanced_architectures/12_contextual_rag.ipynb)                                 | 3/5        | Technical docs      | Context-augmented chunks         |
| 13  | [Fusion RAG](notebooks/advanced_architectures/13_fusion_rag.ipynb)                                         | 3/5        | Ranking quality     | Reciprocal Rank Fusion           |
| 14  | [SQL RAG](notebooks/advanced_architectures/14_sql_rag.ipynb)                                               | 4/5        | Analytics/BI        | Natural language to SQL          |
| 15  | [GraphRAG](notebooks/advanced_architectures/15_graphrag.ipynb)                                             | 5/5        | Knowledge graphs    | Entity graph + multi-hop         |
| 16  | [RAGAS Evaluation](notebooks/advanced_architectures/16_evaluation_ragas.ipynb)                             | -          | Quality metrics     | RAG assessment                   |
| 17  | [Multimodal RAG](notebooks/advanced_architectures/17_multimodal_rag.ipynb)                                 | 4/5        | Images + text       | Vision model + OCR               |
| 18  | [Fine-tuning Embeddings](notebooks/advanced_architectures/18_finetuning_embeddings.ipynb)                  | 4/5        | Domain retrieval    | Custom embedding models          |
| 19  | [Hybrid Search + Reranking](notebooks/advanced_architectures/19_hybrid_search_reranking.ipynb)             | 3/5        | Identifiers, jargon | BM25 + dense + cross-encoder     |
| 20  | [Parent-Document and Multi-Vector](notebooks/advanced_architectures/20_parent_multivector_retrieval.ipynb) | 3/5        | Chunk-size dilemma  | Search small, return large       |

For help choosing an architecture see the [FAQ](docs/FAQ.md#which-architecture-should-i-choose);
for latency and cost figures see [Performance](docs/PERFORMANCE.md).

## Documentation

| Guide                                      | Contents                                     |
| ------------------------------------------ | -------------------------------------------- |
| [Getting Started](docs/GETTING_STARTED.md) | Five-minute setup and learning path          |
| [Installation](docs/INSTALLATION.md)       | Detailed setup, dependencies, configuration  |
| [Architecture](docs/ARCHITECTURE.md)       | Architecture patterns and design decisions   |
| [API Reference](docs/API_REFERENCE.md)     | The `shared` module                          |
| [Examples](docs/EXAMPLES.md)               | Code patterns built on the `shared` module   |
| [Performance](docs/PERFORMANCE.md)         | Latency, cost and optimization               |
| [Deployment](docs/DEPLOYMENT.md)           | Docker, templates and production practices   |
| [Troubleshooting](docs/TROUBLESHOOTING.md) | Common errors and fixes                      |
| [FAQ](docs/FAQ.md)                         | Frequently asked questions                   |
| [Contributing](docs/CONTRIBUTING.md)       | Development workflow, tooling, pull requests |
| [Changelog](docs/CHANGELOG.md)             | Version history                              |
| [Security](SECURITY.md)                    | Security policy and vulnerability reporting  |

## Project Structure

```text
langchain-rag-tutorial/
|-- notebooks/
|   |-- 00_index.ipynb              # Start here: navigation and environment check
|   |-- fundamentals/               # 01-03
|   `-- advanced_architectures/     # 04-20
|-- shared/                         # config, utils, loaders, prompts, retrievers
|-- templates/                      # fastapi/, streamlit/, lambda/
|-- scripts/build_vector_stores.py  # Pre-builds FAISS vector stores
|-- tests/                          # pytest suite for shared/
|-- docs/                           # Documentation
|-- data/                           # Vector stores, Chinook DB (gitignored)
|-- Dockerfile, docker-compose.yml
|-- Makefile, ruff.toml, pytest.ini, .pre-commit-config.yaml
|-- requirements.txt, requirements-dev.txt
`-- .env.example
```

## Deployment

- **Docker**: after `cp .env.example .env`, `docker compose up -d` starts Jupyter (port 8888) and
  the FastAPI template (port 8000).
- **Templates**: [FastAPI](templates/fastapi/README.md), [Streamlit](templates/streamlit/README.md)
  and [AWS Lambda](templates/lambda/README.md). The chat model is read from `DEFAULT_MODEL`
  (default `gpt-4o-mini`).

See [Deployment](docs/DEPLOYMENT.md) for details.

## Development

```bash
pip install -r requirements-dev.txt && pre-commit install
make test     # pytest with coverage
make lint     # ruff check + ruff format --check + mypy
make format   # ruff format + ruff check --fix
```

CI runs tests on Python 3.10, 3.11, 3.12 and 3.13, and linting on 3.12. See
[Contributing](docs/CONTRIBUTING.md) for the full workflow.

## License

MIT License.

## Getting Help

- Read the [FAQ](docs/FAQ.md) and [Troubleshooting](docs/TROUBLESHOOTING.md) guides.
- Search or open [GitHub Issues](https://github.com/gianlucamazza/langchain-rag-tutorial/issues).
- Ask in [GitHub Discussions](https://github.com/gianlucamazza/langchain-rag-tutorial/discussions).
- LangChain documentation: [docs.langchain.com](https://docs.langchain.com/).

---

**Latest version:** v1.4.0 (2026-09-21): hybrid search and reranking (notebook 19), parent-document and
multi-vector retrieval (notebook 20), full contextual retrieval in notebook 12.
See the [Changelog](docs/CHANGELOG.md).
