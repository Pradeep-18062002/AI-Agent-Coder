# AI Code Generator

An intelligent multi-agent system that automatically generates complete web applications from natural language descriptions.

## Overview

This project uses LangGraph and LLM agents to transform user prompts into fully functional web applications. The system consists of three specialized agents:

1. **Planner Agent**: Converts user requirements into a structured project plan
2. **Architect Agent**: Breaks down the plan into detailed implementation tasks
3. **Coder Agent**: Generates actual code files based on the tasks

## Features

- 🤖 Multi-agent architecture using LangGraph
- 📝 Natural language to code generation
- 🏗️ Automatic project structure creation
- 📦 Complete file generation (HTML, CSS, JavaScript, React, etc.)
- 🔄 Iterative code generation with state management
- ⚙️ Configurable recursion limits

## Installation

### Prerequisites

- Python 3.8+
- pip or uv package manager

### Setup

1. Clone the repository:
```bash
git clone 
cd wecode
```

2. Create a virtual environment:
```bash
python -m venv coder
source coder/bin/activate  # On Windows: coder\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Create a `.env` file with your API key:
```
GROQ_API_KEY=your_groq_api_key_here
```

## Usage

### Basic Usage

Run the main script:
```bash
python main.py
```

Enter your project prompt when asked:
```
Enter your project prompt: Build a calculator web app with basic arithmetic operations
```

### Custom Recursion Limit
```bash
python main.py --recursion-limit 200
```

Or using short form:
```bash
python main.py -r 150
```

## Example Prompts
```
Build a calculator web app with basic arithmetic operations
```
```
Create a todo list application with add, delete, and mark complete features
```
```
Build a weather dashboard that displays temperature, humidity, and forecast
```

## Project Structure
```
wecode/
├── main.py                 # Entry point
├── agent/
│   ├── graph.py           # LangGraph workflow
│   ├── prompts.py         # Agent prompts
│   ├── states.py          # State definitions
│   └── tools.py           # File manipulation tools
├── generated_project/     # Output directory for generated code
└── .env                   # API keys (not in git)
```

## How It Works

1. **Planning Phase**: User prompt → Planner Agent → Project plan with files and features
2. **Architecture Phase**: Project plan → Architect Agent → Detailed implementation tasks
3. **Coding Phase**: Implementation tasks → Coder Agent → Generated code files (loops through all tasks)

## Generated Output

All generated files are saved in the `generated_project/` directory with the complete project structure.

## Configuration

Edit `agent/graph.py` to customize:
- LLM model (currently using `openai/gpt-oss-120b` via Groq)
- Agent prompts
- Tool configurations

## Limitations

- Requires valid Groq API key
- Quality depends on the LLM's capabilities
- Complex projects may require multiple iterations
- Generated code may need manual review and testing

## Troubleshooting

### Error: "No module named 'agent'"
Make sure you're running from the project root directory.

### Error: "GROQ_API_KEY not found"
Create a `.env` file with your API key.

### Recursion limit exceeded
Increase the recursion limit:
```bash
python main.py -r 200
```

## Technologies Used

- **LangGraph**: Multi-agent workflow orchestration
- **LangChain**: LLM framework
- **Groq**: Fast LLM inference
- **Pydantic**: Data validation and schemas

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

MIT License

## Acknowledgments

- Built with LangGraph and LangChain
- Powered by Groq API
