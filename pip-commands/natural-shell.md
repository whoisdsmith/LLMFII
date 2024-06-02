---
tags: ["#ai", "#command-line", "#openai", "#python", "#nlp", "|", "#shell-commands", "#language-models", "#natural-language-to-shell"]
---

# Natural-shell

## Description

A tool for converting natural language to shell commands

## README

<!-- # NaturalShell 🐚✨

 NaturalShell, an AI-driven command-line tool, effortlessly translates natural language into shell commands. Say goodbye to complex syntax and hello to intuitive interaction with your system.
![Demo](https://user-images.githubusercontent.com/your_username/natural-shell/assets/demo.gif)

## Features ✨

- **Natural Language Processing**: NaturalShell employs cutting-edge language models to comprehend your natural language input and translate it into executable shell commands.
- **Multi-Model Support**: Choose from Google GenerativeAI, OpenAI, or Anthropic language models to align with your requirements.
- **Flexible Execution**: Effortlessly print or execute commands directly from your terminal using intuitive subcommands.
- **Customizable Configuration**: Tailor your API keys and language model preferences conveniently within a centralized `config.yaml` file.
- **Easy Installation**: Install NaturalShell swiftly with a few commands and kickstart your journey immediately.

## Installation 🚀

To install NaturalShell directly from its GitHub repository using pip, you can use the following command:

```bash
pip install git+https://github.com/theghostrat/NaturalShell.git
```

This command will clone the repository and install the package along with its dependencies.

Alternatively, if you want to install it in editable mode, allowing you to make changes to the code and see the changes reflected immediately without reinstalling, you can use:

```bash
pip install -e git+https://github.com/theghostrat/NaturalShell.git
```

This will install NaturalShell in editable mode, and any changes you make to the code will be reflected without needing to reinstall the package.

Both of these commands will fetch the latest version of NaturalShell from its GitHub repository and install it on your system.

### Manual Installation

NaturalShell isn't available on PyPI yet, but fret not, you can install it directly from the GitHub repository:

1. Clone the repository:

```bash
git clone https://github.com/theghostrat/NaturalShell.git
```

2. Navigate to the project directory:

```bash
cd natural-shell
```

3. Install the package and its dependencies:

```bash
pip install .
```

## Configuration

NaturalShell uses environment variables for configuration. You can set the following environment variables to customize its behavior:

- `NSHELL_CONFIG`: Path to the configuration file (default: `config.yaml` in the current directory).

For example, to specify a custom configuration file located at `/path/to/custom/config.yaml`, you can set the `NSHELL_CONFIG` environment variable as follows:

```bash
export NSHELL_CONFIG=/path/to/custom/config.yaml
```

1. Create a `config.yaml` file in the directory where you plan to use NaturalShell.

2. Open the `config.yaml` file in a text editor.

3. Add the following content to the `config.yaml` file:

```yaml
api_key: YOUR_API_KEY
model: google-genai or openai,etc
base_url: https://api.example.com/v1
```

Replace `YOUR_API_KEY` with your actual API key. You can choose the language model by setting the `model` field to one of the following options: `google-genai`, `openai`, or `anthropic`. If you're using a custom API endpoint for OpenAI, you can specify it in the `base_url` field.

## Usage 🤖

Post-installation, commence your NaturalShell experience right from your terminal or command prompt:

```bash

# Print the Shell Command

nshell "list all files in the current directory" print

# Execute the Shell Command

nshell "list all files in the current directory" exec
```

## Contributing 🤝

Community contributions are highly valued! If you're inclined to enhance NaturalShell, follow these steps:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/your-feature-name`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin feature/your-feature-name`)
5. Open a Pull Request

## License 📄

NaturalShell operates under the [MIT License](https://opensource.org/licenses/MIT).

## Acknowledgments 🙏

NaturalShell flourishes thanks to the remarkable contributions of the following open-source projects:

- [LangChain](https://github.com/hwchase17/langchain)
- [langchain-google-genai](https://github.com/hwchase17/langchain/tree/main/langchain/chains/llm)
- [langchain-openai](https://github.com/hwchase17/langchain/tree/main/langchain/llms/openai)
- [langchain-anthropic](https://github.com/hwchase17/langchain/tree/main/langchain/llms/anthropic)

We extend our gratitude to our phenomenal contributors and the vibrant open-source community for their invaluable support and contributions. -->

# NaturalShell 🐚✨

NaturalShell is an AI-driven command-line tool that effortlessly translates natural language into shell commands. Say goodbye to complex syntax and hello to intuitive interaction with your system.

![Demo](https://user-images.githubusercontent.com/your_username/natural-shell/assets/demo.gif)

## Features ✨

- **Natural Language Processing**: NaturalShell employs cutting-edge language models to comprehend your natural language input and translate it into executable shell commands.
- **Multi-Model Support**: Choose from Google GenerativeAI, OpenAI, or Anthropic language models to align with your requirements.
- **Flexible Execution**: Effortlessly fetch, print, or execute commands directly from your terminal using intuitive subcommands or within your Python scripts.
- **Customizable Configuration**: Tailor your API keys and language model preferences conveniently within a centralized `config.yaml` file or directly through your code.
- **Easy Installation**: Install NaturalShell swiftly with a few commands and kickstart your journey immediately.

## Installation 🚀

To install NaturalShell directly from its GitHub repository using pip, you can use the following command:

```bash
pip install git+https://github.com/theghostrat/NaturalShell.git
```

This command will clone the repository and install the package along with its dependencies.

Alternatively, if you want to install it in editable mode, allowing you to make changes to the code and see the changes reflected immediately without reinstalling, you can use:

```bash
pip install -e git+https://github.com/theghostrat/NaturalShell.git
```

This will install NaturalShell in editable mode, and any changes you make to the code will be reflected without needing to reinstall the package.

Both of these commands will fetch the latest version of NaturalShell from its GitHub repository and install it on your system.

### Manual Installation

NaturalShell isn't available on PyPI yet, but fret not, you can install it directly from the GitHub repository:

1. Clone the repository:

```bash
git clone https://github.com/theghostrat/NaturalShell.git
```

2. Navigate to the project directory:

```bash
cd natural-shell
```

3. Install the package and its dependencies:

```bash
pip install .
```

## Configuration

NaturalShell provides two ways to configure the library: through a `config.yaml` file or directly within your Python code.

### Configuration via `config.yaml`

NaturalShell uses environment variables for configuration. You can set the following environment variable to customize its behavior:

- `NSHELL_CONFIG`: Path to the configuration file (default: `config.yaml` in the current directory).

For example, to specify a custom configuration file located at `/path/to/custom/config.yaml`, you can set the `NSHELL_CONFIG` environment variable as follows:

```bash
export NSHELL_CONFIG=/path/to/custom/config.yaml
```

1. Create a `config.yaml` file in the directory where you plan to use NaturalShell.

2. Open the `config.yaml` file in a text editor.

3. Add the following content to the `config.yaml` file:

```yaml
api_key: YOUR_API_KEY
model: google-genai or openai,etc
base_url: https://api.example.com/v1
```

Replace `YOUR_API_KEY` with your actual API key. You can choose the language model by setting the `model` field to one of the following options: `google-genai`, `openai`, or `anthropic`. If you're using a custom API endpoint for OpenAI, you can specify it in the `base_url` field.

### Configuration via Code

You can also configure NaturalShell directly within your Python code by modifying the properties of the `LanguageModel` instance:

```python
from natural_shell import LanguageModel

# Create the LanguageModel instance
llm_instance = LanguageModel()

# Set custom configuration
llm_instance.api_key = 'your_api_key'
llm_instance.model = 'openai'
llm_instance.base_url = 'https://api.example.com/v1'

# Get the language model instance
language_model = llm_instance.get_language_model()
```

## Usage 🤖

NaturalShell provides two main functions: `fetch_command` and `execute_command`. You can use these functions either from the command line or within your Python scripts.

### Command-Line Usage

Post-installation, commence your NaturalShell experience right from your terminal or command prompt:

```bash
# Print the shell command
nshell "list all files in the current directory" print

# Execute the shell command
nshell "list all files in the current directory" exec
```

### Python Script Usage

You can also import and use the `fetch_command` and `execute_command` functions from your Python scripts:

```python
from natural_shell import fetch_command, execute_command, LanguageModel

# Create the LanguageModel instance
llm_instance = LanguageModel()

# Set custom configuration (optional)
llm_instance.api_key = 'your_api_key'
llm_instance.model = 'openai'
llm_instance.base_url = 'https://api.example.com/v1'

# Get the language model instance
language_model = llm_instance.get_language_model()

# Fetch the command without executing it
command = fetch_command("list all files in the current directory", language_model)
print("Command:", command)

# Execute the command and get the output
command, output = execute_command("list all files in the current directory", language_model)
print("Command:", command)
print("Output:", output)
```

In this example:

1. We import the necessary functions and classes from `natural_shell`.
2. We create an instance of the `LanguageModel` class.
3. (Optional) We set the custom configuration by modifying the properties of the `LanguageModel` instance.
4. We obtain the language model instance using the `get_language_model` method.
5. We use the `fetch_command` function to get the shell command as a string without executing it.
6. We use the `execute_command` function to execute the command and get the output.

By separating the command fetching and execution, you have the flexibility to handle the generated command as per your needs, whether it's executing it directly or using it in your own code.

## Contributing 🤝

Community contributions are highly valued! If you're inclined to enhance NaturalShell, follow these steps:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/your-feature-name`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin feature/your-feature-name`)
5. Open a Pull Request

## License 📄

NaturalShell operates under the [MIT License](https://opensource.org/licenses/MIT).

## Acknowledgments 🙏

NaturalShell flourishes thanks to the remarkable contributions of the following open-source projects:

- [LangChain](https://github.com/hwchase17/langchain)
- [langchain-google-genai](https://github.com/hwchase17/langchain/tree/main/langchain/chains/llm)
- [langchain-openai](https://github.com/hwchase17/langchain/tree/main/langchain/llms/openai)
- [langchain-anthropic](https://github.com/hwchase17/langchain/tree/main/langchain/llms/anthropic)

We extend our gratitude to our phenomenal contributors and the vibrant open-source community for their invaluable support and contributions.
