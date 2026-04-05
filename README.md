<div align="center">
<img src="https://img.shields.io/badge/📚_API_Doc_Generator-Local_LLM_Powered-blue?style=for-the-badge&labelColor=1a1a2e&color=16213e" alt="Project Banner" width="600"/>
<br/>
<img src="https://img.shields.io/badge/Gemma_4-Ollama-orange?style=flat-square&logo=google&logoColor=white" alt="Gemma 4"/>
<img src="https://img.shields.io/badge/Python-3.9+-blue?style=flat-square&logo=python&logoColor=white" alt="Python"/>
<img src="https://img.shields.io/badge/Streamlit-Web_UI-red?style=flat-square&logo=streamlit&logoColor=white" alt="Streamlit"/>
<img src="https://img.shields.io/badge/Click-CLI-green?style=flat-square&logo=gnu-bash&logoColor=white" alt="Click CLI"/>
<img src="https://img.shields.io/badge/License-MIT-yellow?style=flat-square" alt="License"/>
<br/><br/>
<strong>Part of <a href="https://github.com/kennedyraju55/90-local-llm-projects">90 Local LLM Projects</a> collection</strong>
</div>
<br/>

---

## 🏗️ Architecture

```mermaid
graph LR
    A[Python Source] -->|AST Parse| B[Code Extractor]
    B --> C[Functions & Classes]
    C -->|Prompt| D[Ollama / Gemma 4]
    D --> E[Markdown Docs]
    D --> F[OpenAPI Spec]
    E --> G[CLI / Web UI Output]
    F --> G
    G --> H[Export: MD / YAML / JSON]
```

```
┌──────────────┐     ┌──────────────────┐     ┌─────────────┐
│  Source Code  │────▶│  AST Extractor    │────▶│  Ollama API │
│  • File      │     │  • Functions      │     │  (Gemma 4)  │
│  • Directory │     │  • Classes        │     └─────────────┘
│  • Upload    │     │  • Decorators     │            │
└──────────────┘     └──────────────────┘            │
                            │                  ┌────▼────────┐
                     ┌──────▼──────┐           │ Markdown    │
                     │  OpenAPI    │           │ API Docs    │
                     │  Skeleton   │           └─────────────┘
                     │  Generator  │
                     └─────────────┘
```

## ✨ Features

| Feature | Description |
|---------|-------------|
| 📝 **Markdown Documentation** | Professional API reference docs with examples |
| 📄 **OpenAPI/Swagger** | Generate OpenAPI 3.0 specs from code structure |
| 🔍 **AST-based Analysis** | Accurate code parsing using Python's AST module |
| 📁 **Directory Scanning** | Recursively process entire project directories |
| 🔄 **Async Support** | Properly documents async functions and methods |
| 🏷️ **Decorator Detection** | Captures route decorators and annotations |
| 📊 **Code Inspection** | Inspect source structure without generating docs |
| 🌐 **Streamlit Web UI** | Upload files, preview docs, export with one click |
| 📥 **Multiple Export Formats** | Markdown, YAML (OpenAPI), JSON |
| ⚙️ **YAML Configuration** | Flexible config with environment overrides |

## 📸 Screenshots
<div align="center">
<table>
<tr>
<td><img src="https://via.placeholder.com/400x250/1a1a2e/e94560?text=CLI+Interface" alt="CLI"/></td>
<td><img src="https://via.placeholder.com/400x250/16213e/e94560?text=Web+UI" alt="Web UI"/></td>
</tr>
<tr><td align="center"><em>CLI Interface</em></td><td align="center"><em>Streamlit Web UI</em></td></tr>
</table>
</div>

## 📦 Installation

```bash
cd 25-api-doc-generator
pip install -r requirements.txt
pip install -e .

ollama serve && ollama pull gemma4
```

## 🚀 CLI Usage

```bash
# Generate docs for a single file
python -m api_doc_gen.cli generate --source module.py

# Generate docs for a directory
python -m api_doc_gen.cli generate --source src/

# Save to a file
python -m api_doc_gen.cli generate --source src/ --output docs.md

# Generate OpenAPI specification
python -m api_doc_gen.cli openapi --source src/ --output openapi.yaml

# Inspect code structure (no LLM needed)
python -m api_doc_gen.cli inspect --source src/

# Verbose mode
python -m api_doc_gen.cli -v generate --source module.py
```

## 🌐 Web UI Usage

```bash
streamlit run src/api_doc_gen/web_ui.py
# Open http://localhost:8501
```

**Web UI Features:**
- 📁 Upload Python files directly
- 📂 Specify local directory path
- 📚 Preview generated documentation
- 📄 Toggle OpenAPI spec generation
- 📥 Download as Markdown or YAML

## 📋 Example Output

```
╭──────────────────────────────────────────────────╮
│  📚 API Doc Generator                            │
│  Generate API docs from Python source code       │
╰──────────────────────────────────────────────────╯

Source: src/
Found 5 Python file(s)

╭── 📚 API Documentation ─────────────────────────╮
│ # API Reference                                  │
│                                                  │
│ ## `add(a: int, b: int) -> int`                  │
│ Add two numbers together.                        │
│                                                  │
│ | Param | Type | Description        |            │
│ |-------|------|---------------------|            │
│ | a     | int  | First number       |            │
│ | b     | int  | Second number      |            │
│                                                  │
│ **Returns:** `int` — Sum of a and b              │
│                                                  │
│ **Example:**                                     │
│ ```python                                        │
│ result = add(3, 5)  # returns 8                  │
│ ```                                              │
╰──────────────────────────────────────────────────╯

Files processed: 5 | Items documented: 23
```

## 🧪 Testing

```bash
python -m pytest tests/ -v
python -m pytest tests/ -v --cov=src/api_doc_gen --cov-report=term-missing
```

## 📁 Project Structure

```
25-api-doc-generator/
├── src/api_doc_gen/
│   ├── __init__.py          # Package metadata
│   ├── core.py              # Doc generation engine
│   ├── cli.py               # Click CLI interface
│   ├── web_ui.py            # Streamlit web interface
│   ├── config.py            # YAML/env configuration
│   └── utils.py             # AST extraction, OpenAPI skeleton
├── tests/
│   ├── __init__.py
│   ├── test_core.py         # Core logic tests
│   └── test_cli.py          # CLI tests
├── config.yaml              # Default configuration
├── setup.py                 # Package setup
├── requirements.txt         # Dependencies
├── Makefile                 # Dev commands
├── .env.example             # Environment template
└── README.md                # This file
```

## ⚙️ Configuration

```yaml
model: "gemma4"
temperature: 0.3
max_tokens: 4096
output_format: "markdown"
include_examples: true
include_openapi: false
```

| Environment Variable | Description | Default |
|---------------------|-------------|---------|
| `OLLAMA_BASE_URL` | Ollama server URL | `http://localhost:11434` |
| `OLLAMA_MODEL` | LLM model name | `gemma4` |
| `LOG_LEVEL` | Logging level | `INFO` |

## 🤝 Contributing

1. Fork → Branch → Commit → Push → PR

## 📄 License

Part of [90 Local LLM Projects](../README.md). See root [LICENSE](../LICENSE).

## ⚙️ Requirements

- Python 3.10+
- Ollama running locally with Gemma 4 model
