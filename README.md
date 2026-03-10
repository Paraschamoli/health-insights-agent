<p align="center">
  <img src="https://raw.githubusercontent.com/getbindu/create-bindu-agent/refs/heads/main/assets/light.svg" alt="bindu Logo" width="200">
</p>

<h1 align="center">health-insights-agent</h1>

<p align="center">
  <strong>HIA is a sophisticated AI-powered health insights agent designed specifically for analyzing blood reports and providing medical insights.</strong>
</p>

<p align="center">
  <a href="https://github.com/Paraschamoli/health-insights-agent/actions/workflows/main.yml?query=branch%3Amain">
    <img src="https://img.shields.io/github/actions/workflow/status/Paraschamoli/health-insights-agent/main.yml?branch=main" alt="Build status">
  </a>
  <a href="https://img.shields.io/github/license/Paraschamoli/health-insights-agent">
    <img src="https://img.shields.io/github/license/Paraschamoli/health-insights-agent" alt="License">
  </a>
  <a href="https://img.shields.io/badge/python-3.12+-blue.svg">
    <img src="https://img.shields.io/badge/python-3.12+-blue.svg" alt="Python 3.12+">
  </a>
</p>

---

## 📖 Overview

HIA (Health Insights Agent) is a sophisticated AI-powered health insights agent designed specifically for analyzing blood reports and providing medical insights. Built on the [Bindu Agent Framework](https://github.com/getbindu/bindu) for the Internet of Agents, HIA provides comprehensive medical analysis with the same accuracy as professional medical interpretation.

**Key Capabilities:**
- 🔍 **Comprehensive Blood Report Analysis**: CBC, metabolic panels, liver function, kidney function, lipid profiles, thyroid tests
- ✅ **Health Indicator Extraction**: Automatically identifies and extracts 20+ medical markers from unstructured text
- 🚨 **Abnormality Detection**: Compares values against evidence-based reference ranges and flags abnormalities
- � **Risk Assessment**: Provides age and gender-specific health risk evaluation
- 💡 **Personalized Recommendations**: Offers actionable lifestyle and medical guidance
- 🩺 **Medical Disclaimer Integration**: Responsible AI with appropriate medical warnings

---

## 🚀 Quick Start

### Prerequisites

- Python 3.12+
- [uv](https://github.com/astral-sh/uv) package manager
- API keys for OpenRouter and Mem0 (both have free tiers)

### Installation

```bash
# Clone the repository
git clone https://github.com/Paraschamoli/health-insights-agent.git
cd health-insights-agent

# Create virtual environment
uv venv --python 3.12.9
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
uv sync

# Configure environment
cp .env.example .env
```

### Configuration

Edit `.env` and add your API keys:

| Key | Get It From | Required |
|-----|-------------|----------|
| `OPENROUTER_API_KEY` | [OpenRouter](https://openrouter.ai/keys) | ✅ Yes |
| `MEM0_API_KEY` | [Mem0 Dashboard](https://app.mem0.ai/dashboard/api-keys) | ✅ Yes |
| `MODEL_NAME` | OpenRouter Models | Optional (default: anthropic/claude-3.5-sonnet) |

### Run the Agent

```bash
# Start the agent
uv run python -m health_insights_agent

# Agent will be available at http://localhost:3773
```

### GitHub Setup

```bash
# Initialize git repository and commit your code
git init -b main
git add .
git commit -m "Initial commit"

# Create repository on GitHub and push (replace with your GitHub username)
gh repo create Paraschamoli/health-insights-agent --public --source=. --remote=origin --push
```

---

## 💡 Usage

### Example Queries

```bash
# Basic blood report analysis
"Analyze this blood test report: Complete Blood Count - Hemoglobin: 13.5 g/dL, WBC: 7,500 /µL, RBC: 4.8 M/µL, Platelets: 250,000 /µL. Metabolic Panel - Glucose: 95 mg/dL, Creatinine: 0.9 mg/dL, Sodium: 140 mEq/L, Potassium: 4.2 mEq/L."

# Cholesterol analysis with demographics
"Please analyze these lab results and tell me about any abnormalities: Total Cholesterol: 220 mg/dL, LDL: 135 mg/dL, HDL: 38 mg/dL, Triglycerides: 190 mg/dL. I'm a 45-year-old female."

# Liver function evaluation
"Evaluate my liver function tests: ALT: 85 U/L, AST: 65 U/L, ALP: 180 U/L, Bilirubin: 1.8 mg/dL. Are these values concerning?"

# Risk assessment query
"Based on these results for a 55-year-old male - Hemoglobin: 11.2 g/dL, Glucose: 145 mg/dL, Creatinine: 1.6 mg/dL, what are my health risks and what should I do?"

# Simple health question
"Is a hemoglobin level of 12.5 g/dL normal for a 30-year-old woman?"
```

### Input Formats

**Plain Text Medical Report:**
```
Complete Blood Count:
Hemoglobin: 13.5 g/dL
WBC: 7,500 /µL
RBC: 4.8 M/µL
Platelets: 250,000 /µL

Metabolic Panel:
Glucose: 95 mg/dL
Creatinine: 0.9 mg/dL
Sodium: 140 mEq/L
Potassium: 4.2 mEq/L
```

**JSON with Patient Context:**
```json
{
  "report_text": "Complete medical report text...",
  "patient_age": 35,
  "patient_gender": "female",
  "analysis_type": "comprehensive"
}
```

### Output Structure

The agent returns structured medical analysis with:
- **Patient Summary**: Demographics and overall health status
- **Test Results Analysis**: Detailed breakdown of all indicators
- **Abnormal Findings**: Values outside reference ranges with clinical significance
- **Health Insights**: System-by-system analysis (CBC, liver, kidney, metabolic, thyroid)
- **Risk Assessment**: Overall risk level and specific health risk factors
- **Recommendations**: Personalized lifestyle and medical guidance
- **Next Steps**: Follow-up timeline and urgency recommendations

---

## 🔌 API Usage

The agent exposes a RESTful API when running. Default endpoint: `http://localhost:3773`

### Quick Start

For complete API documentation, request/response formats, and examples, visit:

📚 **[Bindu API Reference - Send Message to Agent](https://docs.getbindu.com/api-reference/all-the-tasks/send-message-to-agent)**

### Example API Call

```bash
curl -X POST http://localhost:3773/analyze \
  -H "Content-Type: application/json" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Analyze this blood test: Hemoglobin 13.5 g/dL, Glucose 95 mg/dL..."
      }
    ]
  }'
```

### Additional Resources

- 📖 [Full API Documentation](https://docs.getbindu.com/api-reference/all-the-tasks/send-message-to-agent)
- 📦 [Postman Collections](https://github.com/GetBindu/Bindu/tree/main/postman/collections)
- 🔧 [API Reference](https://docs.getbindu.com)

---

## 🎯 Skills

### health_insights (v1.0.0)

**Primary Capability:**
- Comprehensive medical report analysis with health insights and risk assessment

**Features:**
- Blood report text extraction and validation
- Health indicator identification and extraction
- Reference range comparison and abnormality detection
- Multi-system health analysis (CBC, liver, kidney, metabolic, thyroid)
- Risk assessment based on age, gender, and medical findings
- Personalized health recommendations and lifestyle guidance
- Medical disclaimer integration for responsible AI

**Best Used For:**
- Analyzing blood test reports and laboratory results
- Extracting health indicators from medical documents
- Understanding abnormal lab values in context
- Getting preliminary health insights before doctor visits
- Monitoring health trends over time
- Educational purposes for understanding medical reports

**Not Suitable For:**
- Emergency medical situations - call emergency services
- Replacing professional medical diagnosis or treatment
- Making critical health decisions without doctor consultation
- Analyzing complex medical imaging or specialized tests
- Pediatric patients (reference ranges differ significantly)

**Performance:**
- Average processing time: ~2 seconds
- Max concurrent requests: 5
- Memory per request: 256MB

---

## 🐳 Docker Deployment

### Local Docker Setup

```bash
# Build and run with Docker Compose
docker-compose up --build

# Agent will be available at http://localhost:3773
```

### Docker Configuration

The agent runs on port `3773` and requires:
- `OPENROUTER_API_KEY` environment variable
- `MEM0_API_KEY` environment variable

Configure these in your `.env` file before running.

### Production Deployment

```bash
# Use production compose file
docker-compose -f docker-compose.prod.yml up -d
```

---

## 🌐 Deploy to bindus.directory

Make your agent discoverable worldwide and enable agent-to-agent collaboration.

### Setup GitHub Secrets

```bash
# Authenticate with GitHub
gh auth login

# Set deployment secrets
gh secret set BINDU_API_TOKEN --body "<your-bindu-api-key>"
gh secret set DOCKERHUB_TOKEN --body "<your-dockerhub-token>"
```

Get your keys:
- **Bindu API Key**: [bindus.directory](https://bindus.directory) dashboard
- **Docker Hub Token**: [Docker Hub Security Settings](https://hub.docker.com/settings/security)

### Deploy

```bash
# Push to trigger automatic deployment
git push origin main
```

GitHub Actions will automatically:
1. Build your agent
2. Create Docker container
3. Push to Docker Hub
4. Register on bindus.directory

---

## 🛠️ Development

### Project Structure

```
health-insights-agent/
├── health_insights_agent/
│   ├── skills/
│   │   └── health-insights/
│   │       ├── skill.yaml          # Skill configuration
│   │       └── __init__.py
│   ├── __init__.py
│   ├── __main__.py
│   ├── main.py                     # Agent entry point
│   ├── tools.py                    # Medical analysis tools
│   └── agent_config.json           # Agent configuration
├── tests/
│   └── test_main.py                # Test suite
├── .env.example
├── docker-compose.yml
├── Dockerfile.agent
└── pyproject.toml
```

### Running Tests

```bash
uv run pytest tests/ -v              # Run all tests
uv run pytest tests/ -v --cov       # With coverage report
```

### Code Quality

```bash
uv run ruff format .                  # Format code
uv run ruff check .                   # Run linters
uv run pre-commit run --all-files     # Format + lint + test + type check
```

### Pre-commit Hooks

```bash
# Install pre-commit hooks
uv run pre-commit install

# Run manually
uv run pre-commit run -a
```

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'Add amazing feature'`
4. Push to the branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Powered by Bindu

Built with the [Bindu Agent Framework](https://github.com/getbindu/bindu)

**Why Bindu?**
- 🌐 **Internet of Agents**: A2A, AP2, X402 protocols for agent collaboration
- ⚡ **Zero-config setup**: From idea to production in minutes
- 🛠️ **Production-ready**: Built-in deployment, monitoring, and scaling

**Build Your Own Agent:**
```bash
uvx cookiecutter https://github.com/getbindu/create-bindu-agent.git
```

---

## 📚 Resources

- 📖 [Full Documentation](https://Paraschamoli.github.io/health-insights-agent/)
- 💻 [GitHub Repository](https://github.com/Paraschamoli/health-insights-agent/)
- 🐛 [Report Issues](https://github.com/Paraschamoli/health-insights-agent/issues)
- 💬 [Join Discord](https://discord.gg/3w5zuYUuwt)
- 🌐 [Agent Directory](https://bindus.directory)
- 📚 [Bindu Documentation](https://docs.getbindu.com)

---

## ⚠️ Medical Disclaimer

**This AI-generated analysis is for informational purposes only and should not be considered as a replacement for professional medical advice. Always consult with a qualified healthcare provider for proper medical diagnosis and treatment.**

---

<p align="center">
  <strong>Built with 💛 by the team from Amsterdam 🌷</strong>
</p>

<p align="center">
  <a href="https://github.com/Paraschamoli/health-insights-agent">⭐ Star this repo</a> •
  <a href="https://discord.gg/3w5zuYUuwt">💬 Join Discord</a> •
  <a href="https://bindus.directory">🌐 Agent Directory</a>
</p>
