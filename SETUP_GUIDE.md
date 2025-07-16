# Aider Setup Guide

This guide will help you set up Aider for development or usage.

## Prerequisites

- Python 3.10, 3.11, or 3.12
- Git
- API key for one of the supported LLM providers (OpenAI, Anthropic, DeepSeek, etc.)

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/Aider-AI/aider.git
cd aider
```

### 2. Create a Virtual Environment

It's recommended to create a virtual environment outside of the repository to keep your development environment isolated.

```bash
python -m venv /path/to/aider_venv
```

### 3. Activate the Virtual Environment

#### On Windows

```bash
/path/to/aider_venv/Scripts/activate
```

#### On Unix or macOS

```bash
source /path/to/aider_venv/bin/activate
```

### 4. Install Aider in Development Mode

This allows you to make changes to the source code and have them take effect immediately without reinstalling the package.

```bash
pip install -e .
```

### 5. Install Dependencies

```bash
pip install -r requirements.txt
```

For development, install the development dependencies:

```bash
pip install -r requirements/requirements-dev.txt
```

## Configuration

Create a `.aider.conf.yml` file in your home directory or project root with your preferred settings. A sample configuration file is provided in the repository.

## Running Aider

### Basic Usage

```bash
# Change directory into your codebase
cd /to/your/project

# Run with DeepSeek model
aider --model deepseek --api-key deepseek=<key>

# Run with Claude 3.7 Sonnet
aider --model sonnet --api-key anthropic=<key>

# Run with OpenAI o3-mini
aider --model o3-mini --api-key openai=<key>
```

### Development Testing

To run the tests:

```bash
pytest
```

To run specific test files:

```bash
pytest tests/basic/test_coder.py
```

## Troubleshooting

If you encounter issues:

1. Check that your API keys are correctly set
2. Verify that you're using a supported Python version (3.10-3.12)
3. Make sure all dependencies are installed correctly
4. Check the [troubleshooting documentation](https://aider.chat/docs/troubleshooting.html)

## Additional Resources

- [Official Documentation](https://aider.chat/docs/)
- [GitHub Repository](https://github.com/Aider-AI/aider)
- [Discord Community](https://discord.gg/Y7X7bhMQFV)