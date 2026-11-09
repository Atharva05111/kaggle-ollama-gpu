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

## Benchmark: Qwen 2.5 on Kaggle 2x T4 (Ollama, Q4, temperature 0)

| Model | Generation speed | Avg time / answer | VRAM used |
|---|---|---|---|
| qwen2.5:7b | 28.3 tok/s | 12.1 s | 6.6 GB (1 GPU) |
| qwen2.5:14b | 24.8 tok/s | 14.4 s | 16.3 GB (split across 2 GPUs) |

Averaged over 3 prompts (MQTT explanation, Modbus CRC16 code, edge-AI list).
VRAM includes the 32K context cache.

**Takeaway:** the 14B is only ~12% slower than the 7B but gives noticeably more
accurate answers (the 7B swapped MQTT QoS 0 and 1 in testing), so it's the
better default on Kaggle's 2x T4.
