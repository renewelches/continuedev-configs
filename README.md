# Continue.dev VSCode Configuration

This repository contains Continue.dev configuration files for local and cloud-based AI coding assistants.

## Table of Contents

- [Setup](#setup)
- [Using Hugging Face Models](#using-hugging-face-models)
- [Configuration Examples](#configuration-examples)
- [Resources](#resources)

## Setup

### 1. Install Continue.dev Extension

1. Open VSCode
2. Go to Extensions (Cmd+Shift+X on Mac, Ctrl+Shift+X on Windows/Linux)
3. Search for "Continue", full extension name is Continue - open-source AI code agent"
4. Click Install on the Continue extension

### 2. Configuration File Location

Continue.dev uses a configuration file located at:
- **macOS/Linux**: `~/.continue/config.yaml`
- **Windows**: `%USERPROFILE%\.continue\config.yaml`

### 3. Apply Configuration

Copy the desired configuration file from this repository to your Continue.dev config location:

```bash
# Example for Mac/Linux
cp mac-mini-m4pro-48GB-config-yaml ~/.continue/config.yaml
```

## Using Hugging Face Models Via Ollama

Ollama supports loading GGUF quantized models directly from Hugging Face. 

#### Step 1: Install Ollama

Download and install Ollama from [ollama.ai](https://ollama.ai)

#### Step 2: Pull Models from Hugging Face

Ollama can pull models directly using the `hf.co/` prefix:

```bash
# Example: Pull a quantized model from Hugging Face
ollama pull hf.co/bartowski/FastApply-1.5B-v1.0-GGUF:latest

# Another example
ollama pull hf.co/QuantFactory/Qwen3-Reranker-4B-GGUF:latest
```

#### Step 3: Configure in Continue.dev

Add the model to your `config.yaml`:

```yaml
models:
  - name: FastApply 1.5B
    provider: ollama
    model: hf.co/bartowski/FastApply-1.5B-v1.0-GGUF:latest
    roles:
      - apply
    defaultCompletionOptions:
      contextLength: 32768
```



### Model Roles

Continue.dev supports several model roles:

- **autocomplete**: Code completion as you type
- **chat**: Chat-based interactions
- **edit**: Code editing suggestions
- **apply**: Applying code changes
- **embed**: Creating embeddings for retrieval
- **rerank**: Reranking search results


## Resources

- **Continue.dev Documentation**: [https://docs.continue.dev](https://docs.continue.dev)
- **Model Configuration Guide**: [https://docs.continue.dev/customization/models](https://docs.continue.dev/customization/models)
- **Ollama Documentation**: [https://github.com/ollama/ollama](https://github.com/ollama/ollama)
- **Hugging Face Models**: [https://huggingface.co/models](https://huggingface.co/models)
- **GGUF Models Guide**: [https://huggingface.co/docs/hub/gguf](https://huggingface.co/docs/hub/gguf)

## Contributing

Feel free to submit configurations for different hardware setups or model combinations!

## License

See [LICENSE](LICENSE) file for details.
