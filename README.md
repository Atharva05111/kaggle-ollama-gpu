# Run Open LLMs on Kaggle's Free GPU (Ollama)

Run models like Qwen 2.5 7B/14B on Kaggle's free 2x T4 GPUs using Ollama.

## Setup
1. Create a Kaggle notebook and verify your phone number
2. Session options -> Accelerator: **GPU T4 x2**, Internet: **On**
3. Run the cells in order: install Ollama -> start server -> pull model -> query

## Limits
- 12 hours max per session
- ~30 GPU hours per week (check Session options)
- Models must be re-pulled each session

## Usage
```python
ask("your prompt")                       # qwen2.5:7b
ask("your prompt", model="qwen2.5:14b")  # after uncommenting its pull
```
