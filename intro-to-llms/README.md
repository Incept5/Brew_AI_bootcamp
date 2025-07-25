
# Introduction to LLMs - Configuration Test Scripts

This directory contains simple Python scripts designed to verify that your environment is properly configured to interact with Large Language Models (LLMs) through both local (Ollama) and cloud-based APIs (Groq).

## Purpose

These scripts serve as initial configuration tests to ensure:
- Local setup: Ollama is installed and running locally with required models
- Cloud setup: API keys are configured for cloud-based LLM services
- Python environment can successfully communicate with both local and cloud APIs
- Basic LLM functionality is working as expected

## Why Groq? Understanding Our Cloud LLM Provider

### What is Groq?

Groq is an AI inference company that has developed specialized hardware called Language Processing Units (LPUs) designed specifically for running large language models at exceptional speed. Unlike traditional GPU-based inference, Groq's LPU architecture provides:

- **Ultra-fast inference**: Response times often under 100ms for first token
- **Consistent performance**: Predictable latency without the variability of shared GPU resources
- **Cost-effective**: Competitive pricing with generous free tiers for development
- **Developer-friendly**: Simple REST API with excellent documentation

### Why We Chose Groq for This Course

1. **Speed**: Groq's LPU technology delivers some of the fastest LLM inference available, making it ideal for interactive learning and rapid prototyping
2. **Reliability**: Consistent, low-latency responses enhance the learning experience
3. **Accessibility**: Generous free tier allows students to experiment without immediate cost concerns
4. **Simplicity**: Clean, straightforward API that's easy to integrate and understand
5. **Model Selection**: Access to popular, high-quality models including Llama, Mixtral, and Gemma families

### Groq Model Support

Groq supports several high-performance model families:

**Llama Models:**
- `llama-3.3-70b-versatile` - Latest Llama 3.3 model, excellent for general tasks
- `llama-3.1-70b-versatile` - Llama 3.1 70B, high-quality responses
- `llama-3.1-8b-instant` - Smaller, faster Llama 3.1 model
- `llama3-70b-8192` - Llama 3 70B with 8K context
- `llama3-8b-8192` - Llama 3 8B with 8K context

**Mixtral Models:**
- `mixtral-8x7b-32768` - Mixtral 8x7B MoE model with 32K context

**Gemma Models:**
- `gemma2-9b-it` - Google's Gemma 2 9B instruction-tuned model
- `gemma-7b-it` - Gemma 7B instruction-tuned model

**Specialized Models:**
- `llama-3.2-90b-text-preview` - Large context model for text processing
- `llama-3.2-11b-text-preview` - Medium-sized text processing model

### Alternative Cloud LLM Providers

While we use Groq for this course, the LLM ecosystem offers many excellent alternatives:

**OpenAI:**
- **Models**: GPT-4, GPT-4 Turbo, GPT-3.5 Turbo
- **Strengths**: Industry leader, most capable models, extensive tooling
- **Considerations**: Higher cost, rate limits, less control over infrastructure
- **Best for**: Production applications requiring highest quality

**Anthropic (Claude):**
- **Models**: Claude 3.5 Sonnet, Claude 3 Opus, Claude 3 Haiku
- **Strengths**: Strong safety focus, excellent reasoning, large context windows
- **Considerations**: Limited availability in some regions, newer to market
- **Best for**: Applications requiring careful, nuanced responses

**Google Cloud (Gemini/PaLM):**
- **Models**: Gemini Pro, Gemini Flash, PaLM 2
- **Strengths**: Integration with Google Cloud, multimodal capabilities
- **Considerations**: Complex pricing, requires Google Cloud setup
- **Best for**: Enterprise applications already using Google Cloud

**AWS Bedrock:**
- **Models**: Claude, Llama, Titan, Jurassic
- **Strengths**: Multiple model providers, AWS integration, enterprise security
- **Considerations**: Complex setup, primarily enterprise-focused
- **Best for**: Large-scale enterprise deployments

**Azure OpenAI:**
- **Models**: GPT-4, GPT-3.5, DALL-E, Codex
- **Strengths**: Enterprise-grade OpenAI access, Microsoft ecosystem integration
- **Considerations**: Approval process required, complex pricing
- **Best for**: Enterprise customers needing compliance and support

**Cohere:**
- **Models**: Command, Generate, Embed
- **Strengths**: Enterprise focus, excellent embeddings, multilingual support
- **Considerations**: Smaller model selection, less community adoption
- **Best for**: Enterprise NLP applications, embedding services

**Together AI:**
- **Models**: Various open-source models (Llama, Mistral, Code Llama)
- **Strengths**: Access to latest open-source models, competitive pricing
- **Considerations**: Newer platform, variable model availability
- **Best for**: Developers wanting access to cutting-edge open-source models

### Local vs Cloud Trade-offs

**Local LLMs (Ollama) Advantages:**
- Complete privacy and data control
- No API costs or rate limits
- Works offline
- Full customization capability

**Cloud LLMs (Groq/Others) Advantages:**
- No hardware requirements
- Access to largest, most capable models
- Consistent performance
- No setup or maintenance
- Latest model updates automatically available

### Getting Started with Alternatives

If you want to experiment with other providers, here are the key setup steps:

**OpenAI:**
```bash
pip install openai
# Add OPENAI_API_KEY to your .env file
```

**Anthropic:**
```bash
pip install anthropic
# Add ANTHROPIC_API_KEY to your .env file
```

**Google:**
```bash
pip install google-generativeai
# Add GOOGLE_API_KEY to your .env file
```

All providers follow similar patterns: install the SDK, configure API keys, and make requests through their respective APIs.

## ⚠️ Important Note: Optional Advanced Scripts

**The basic configuration test scripts (`local_llm_using_ollama.py` and `cloud_llm_using_groq.py`) are the only scripts required for this course.**

The advanced model testing and comparison scripts (`model_comparison_test.py`, `model_size_test.py`, `streaming_performance_test.py`) are **optional extras** provided for:
- Users who want to dive deeper into LLM performance characteristics
- Understanding model trade-offs and selection criteria
- Exploring advanced performance testing methodologies
- Self-directed learning beyond the course requirements

**You do not need to run the advanced scripts to complete the course successfully.** They are educational resources for those interested in expanding their understanding of LLM capabilities and performance analysis.

## Prerequisites

Before running these scripts, ensure you have:

### For Local LLM (Ollama):
1. **Ollama installed** - Download from [ollama.ai](https://ollama.ai)
2. **Ollama running** - Start with `ollama serve` in your terminal
3. **Required models downloaded** - Pull models using `ollama pull <model-name>`

### For Cloud LLM (Groq):
1. **Groq API Key** - Sign up at [groq.com](https://groq.com) and get your API key
2. **Environment variables** - Set up `.env` file with your API key

### General:
3. **Python environment** - With required dependencies installed

## Scripts

### `local_llm_using_ollama.py`
A basic test script that:
- Connects to the local Ollama API (http://localhost:11434)
- Uses the Qwen3 1.7B model
- Sends a simple "Hello" prompt
- Displays the response or any error messages

**Usage:**
```bash
python local_llm_using_ollama.py
```

**Expected Output:**
If everything is configured correctly, you should see a greeting response from the Qwen3 model.

**Troubleshooting:**
- If you get a connection error, ensure Ollama is running (`ollama serve`)
- If you get a model not found error, download the model (`ollama pull qwen3:1.7b`)
- Check that the Ollama API is accessible at `http://localhost:11434`

### `cloud_llm_using_groq.py`
A basic test script that:
- Connects to the Groq cloud API using your API key
- Uses the Llama 3.3 70B Versatile model
- Sends a simple "Hello" prompt
- Displays the response from the cloud-based model

**Usage:**
```bash
python cloud_llm_using_groq.py
```

**Setup Requirements:**
1. Create a `.env` file in the project root with:
   ```
   GROQ_API_KEY=your_groq_api_key_here
   ```
2. Ensure you have a valid Groq API key from [groq.com](https://groq.com)

**Expected Output:**
If everything is configured correctly, you should see a greeting response from the Llama 3.3 70B model.

**Troubleshooting:**
- If you get an authentication error, check your API key in the `.env` file
- Ensure the `.env` file is in the correct location (project root)
- Verify your Groq account has API access and sufficient credits

## Dependencies

The scripts in this directory require:
- `requests` library for HTTP communication with Ollama
- `groq` library for Groq API communication
- `python-dotenv` library for environment variable management

Install with:
```bash
pip install requests groq python-dotenv
```

## Setup for Advanced Test Scripts

### Recommended Ollama Models
For comprehensive testing, install these models:

```bash
# Small models (fast)
ollama pull qwen3:1.7b
ollama pull llama3.2:3b
ollama pull phi3:3.8b
ollama pull gemma2:7b

# Medium models (balanced)
ollama pull llama3.1:8b
ollama pull qwen2.5:14b
ollama pull mixtral:8x7b
ollama pull gemma2:9b

# Large models (high quality, requires significant resources)
ollama pull llama3.1:70b    # ~40GB RAM recommended
ollama pull llama3.3:70b    # ~40GB RAM recommended
```

**Note:** Large models (70B parameters) require substantial system resources:
- RAM: 40GB+ recommended
- Storage: 40GB+ per model
- CPU: Multi-core processor recommended
- Time: Several hours to download

### System Requirements

**Minimum for Small/Medium Models:**
- RAM: 8GB
- Storage: 20GB free space
- Internet: For initial model downloads

**Recommended for Large Models:**
- RAM: 32GB+ (64GB preferred)
- Storage: 100GB+ free space
- GPU: Optional but significantly improves performance

### Cloud API Setup

**Groq API (Recommended for Fast Cloud Inference):**
1. Sign up at [console.groq.com](https://console.groq.com)
2. Generate an API key
3. Add to your `.env` file:
   ```
   GROQ_API_KEY=your_groq_api_key_here
   ```

**Alternative Cloud Providers:**
The scripts can be extended to support:
- OpenAI GPT models
- Anthropic Claude
- Google Gemini
- Azure OpenAI

## Advanced Test Scripts (Optional - For Extended Learning)

**Note: These scripts are not required for the course but are provided as educational resources for users who want to explore LLM performance analysis in greater depth.**

### `model_comparison_test.py`
Comprehensive test suite that evaluates multiple models across different categories:

**Features:**
- Tests small (< 10B), medium (10B-30B), and large (> 30B parameter) models
- Supports both Ollama (local) and Groq (cloud) providers
- Performance timing and tokens-per-second calculation
- Multiple test prompts covering reasoning, creativity, and technical tasks
- Detailed logging and error handling
- JSON export of results with timestamps
- Model availability checking before testing

**Models Tested:**
- **Small**: qwen3:1.7b, llama3.2:3b, phi3:3.8b, gemma2:7b
- **Medium**: llama3.1:8b, qwen2.5:14b, mixtral:8x7b, groq models
- **Large**: llama3.1:70b, llama3.3:70b, groq large models

**Usage:**
```bash
python model_comparison_test.py
```

**Sample Output:**
- System availability check
- Individual model test results with timing
- Success/failure status for each model
- Summary report with fastest/slowest models per category
- Overall statistics and success rates
- Saved JSON results file

### `model_size_test.py`
Focused comparison of different model sizes to evaluate performance vs quality trade-offs:

**Features:**
- Simple size-based categorization (Small/Medium/Large)
- Standardized test prompts designed to show quality differences
- Speed ranking across all successful models
- Size category analysis with average response times
- Basic response quality indicators
- Interactive prompt selection

**Test Categories:**
- **Basic**: Simple greetings and interactions
- **Reasoning**: Math problems and logical thinking
- **Creative**: Poetry and creative writing tasks
- **Technical**: Programming and technical explanations

**Usage:**
```bash
python model_size_test.py
```

**Key Insights:**
- Small models: Fastest response, suitable for simple tasks
- Medium models: Balanced performance for most use cases
- Large models: Best quality but slower, ideal for complex reasoning

### `streaming_performance_test.py`
Advanced performance testing focusing on streaming vs non-streaming response delivery:

**Features:**
- Time to First Token (TTFT) measurement - critical for perceived responsiveness
- Tokens per Second (TPS) calculation for both streaming and non-streaming
- Side-by-side comparison of streaming vs non-streaming performance
- Multiple prompt lengths to test different response scenarios
- Detailed performance metrics and analysis
- Model-by-model comparison reports

**Key Metrics:**
- **TTFT (Time to First Token)**: How quickly the model starts responding (streaming only)
- **TPS (Tokens per Second)**: Throughput measurement
- **Total Response Time**: Complete generation time
- **Streaming Advantage**: Performance difference between modes

**Test Scenarios:**
- **Short Response**: Quick answers (greetings, simple questions)
- **Medium Response**: Explanations and descriptions
- **Long Response**: Detailed guides and tutorials
- **Code Generation**: Programming tasks with comments

**Usage:**
```bash
python streaming_performance_test.py
```

**Sample Insights:**
- Streaming provides immediate feedback with TTFT typically under 0.5s
- Cloud models (Groq) often have better TTFT than local models
- Large models may have higher TPS despite longer TTFT
- Non-streaming can be faster for very short responses
- Streaming is essential for user experience with longer responses

## What's Next

Planned additional test scripts:
- Streaming response performance tests
- Cost analysis for cloud API usage
- Conversation context handling tests
- Specialized task performance (coding, math, creative writing)
- Multi-language support evaluation
- Fine-tuned vs base model comparisons

## Quick Start

### Local LLM Setup (Ollama):
1. Ensure Ollama is running:
   ```bash
   ollama serve
   ```

2. Download the Qwen3 model:
   ```bash
   ollama pull qwen3:1.7b
   ```

3. Run the local test script:
   ```bash
   cd intro-to-llms
   python local_llm_using_ollama.py
   ```

### Cloud LLM Setup (Groq):
1. Create a `.env` file in the project root:
   ```bash
   echo "GROQ_API_KEY=your_api_key_here" > ../.env
   ```

2. Install dependencies:
   ```bash
   pip install groq python-dotenv
   ```

3. Run the cloud test script:
   ```bash
   cd intro-to-llms
   python cloud_llm_using_groq.py
   ```

If you see responses from both local and cloud models, your environment is ready for more advanced LLM development!
