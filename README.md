# �� API Documentation Generator

**Auto-generate comprehensive API docs using local Gemma 3**

![Python](https://img.shields.io/badge/Python-3.8+-3776ab?style=flat-square&logo=python)
![Ollama](https://img.shields.io/badge/Ollama-Compatible-005a9c?style=flat-square)
![Gemma3](https://img.shields.io/badge/Gemma%203-LLM-4285f4?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)
![Privacy First](https://img.shields.io/badge/Privacy-First-ff69b4?style=flat-square)

## What It Does

- Analyzes API code and generates clear, detailed documentation with Gemma 3
- Produces OpenAPI/Swagger specs and markdown documentation
- Runs locally — documentation generation never touches external services

## Tech Stack

Python, Ollama, Gemma 3, OpenAPI

## Quick Start

1. Clone: git clone https://github.com/kennedyraju55/api-doc-generator.git && cd api-doc-generator
2. Install: pip install -r requirements.txt
3. Pull model: ollama pull gemma3:4b
4. Generate: python generate_docs.py

## Architecture

Parses API code and routes it through Gemma 3 via Ollama to produce structured documentation in multiple formats.

## Why Local?

- **No API Keys Required** — Zero external dependencies
- **Complete Privacy** — Code stays on your machine
- **Offline Operation** — Works without internet
- **Cost-Free** — No monthly API bills

## Contributing

Found a bug? Have an improvement? Open an issue or submit a PR! All contributions welcome.

## License

MIT License — See LICENSE file for details

---

**Part of 114+ privacy-first AI tools by Nrk Raju**