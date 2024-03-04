# Key Resources and Configurations for Open Source Large Language Models (LLMs)

> Contributed by Xuekai Zhu, Kaiyan Zhang, [Jushi Kai](https://scholar.google.com/citations?user=W85K17gAAAAJ&hl=zh-CN)

**![figure_1](./figure_1.webp)We present a comprehensive table outlining the key resources and configurations for Open Source Large Language Models (LLMs). We hope this table can help you quickly check whether your accessible resource can join the LLMs party.**

-----



| Release Date | Model      | Affiliation                                 | Size            | Source Data Size (Tokens)              | Training Tokens                                              | Learning Rate    | Batch Size (tokens)     | Architecture      | Context Length | Vocabulary Size | Tokenizer                            | Precision                      | GPU Hours     | Infrastructure                   | Optimizer                                 | Training Layout                                    | Language          |
| ------------ | ---------- | ------------------------------------------- | --------------- | -------------------------------------- | ------------------------------------------------------------ | ---------------- | ----------------------- | ----------------- | -------------- | --------------- | ------------------------------------ | ------------------------------ | ------------- | -------------------------------- | ----------------------------------------- | -------------------------------------------------- | ----------------- |
| 2024/02      | StableLM 2 | Stability AI Language Team                  | 1.6B            | -                                      | 2T                                                           | 1e−3 (max)       | 8, 388, 608             | decoder-only      | 4096           | 100,352         | Arcade100k tokenizer                 | BF16/FP32 （mixed precision ） | 92k           | 512 NVIDIA A100 (40GB HBM2) GPUs | AdamW (0.9/0.95)                          | FlashAttention-2, ZeRO stage 1                     | multilingual      |
| 2024/02      | Gemma      | Gemma Team, Google DeepMind                 | 2B / 7B         | -                                      | 2T / 6T                                                      | -                | -                       | decoder-only      | 8192           | 256k            | Gemini tokenizer                     | -                              | -             | TPU                              | -                                         | similar ZeRO-3                                     | English           |
| 2024/02      | OLMo       | Allen Institute for Artificial Intelligence | 1B / 7B         | [3T](https://github.com/allenai/dolma) | 2T / 2.46T                                                   | 4e-4 / 3e-4      | ~4M(2048 * 2048)        | decoder-only      | 2048           | 50,280          | GPT-NeoX-20B                         | BF16(mixed precision)          |               | 216  NVIDIA A100 GPUs            | AdamW                                     | ZeRO optimizer strategy , PyTorch’s FSDP framework | English           |
| 2024/01      | miniCPM    | Modelbest Inc., THUNLP                      | 2B              | -                                      | 2T (1+1)                                                     | 1e-2 (max)       | ～4M                    | decoder-only      | -              | 122, 753        | sentencepiece(BPE)                   | BF16                           | -             | -                                | Warmup-Stable-Decay（WSD）(new proposed ) | cosine lr-scheduler                     | English / Chinese |
| 2024/01      | DeepSeek   | DeepSeek-AI                                 | 7B              | -                                      | 2T                                                           | 4.2e-4  (0.1 wd) | 9,437,184 (2304 * 4096) | decoder-only      | 4096           | 102, 400        | Byte-level Byte-Pair Encoding (BBPE) | BF16/FP32 （mixed precision ） | -             | -                                | AdamW                                     | Flash attention, ZeRO-1                            | English           |
| 2023/12      | phi-2      | Microsoft                                   | 2.7B            | 250B                                   | 1.4T                                                         | -                | -                       | encoder-decoder   | 2048           | -               | -                                    | -                              | 336 (14 days) | 96 A100 GPUs.                    | -                                         | -                                                  | English           |
| 2023/10      | Mistral    | Mistral AI                                  | 7B              | -                                      | [~ 8T]( https://www.interconnects.ai/p/gemma-google-ships-it?utm_source=profile&utm_medium=reader2) | -                | -                       | transformer-based | 8192           | 32000           | -                                    | -                              | -             | -                                | -                                         | sliding window attention, grouped-query attention  | English, code     |
| 2023/09      | Qwen       | Qwen Team, Alibaba Group                    | 1.8B / 7B / 14B | 3T                                     | 2.2T / 2.4T / 3.0T                                           | 3e-4             | ~ 4M                    | Decoder-only      | 2048           | 152K            | Qwen                                 | BF16                           | -             | -                                | AdamW                                     | Flash Attention, cosine learning rate schedule     | multilingual      |
| 2023/09      | phi-1.5    | Microsoft                                   | 1.3B            | 30B                                    | 150B                                                         | 2e−4 (0.1 wd)    | 4,194,304(2048 * 2048)  | encoder-decoder   | 2048           | -               | codegen-mono                         | FP16                           | 192(8 days)   | 32xA100-40G                      | Adam                                      | ZeRO-2                                             | English           |
| 2023/07      | LLaMA-2        | Meta                                  | 7B / 13B / 34B / 70B / chat | -        | 2.0T     | 3e-4 (7B, 13B), 1.5e-4 (34B, 70B)     | 4M        | decoder-only      | 4096      | 32k       | SentencePiece (BPE)     | -        | 184k (7B)      | A100-80GB     | AdamW     | cosine lr-scheduler, grouped-query attention, Ghost Attention     | English       |
| 2023/06      | phi-1      | Microsoft                                   | 1.3B            | 7B                                     | 50B                                                          | 1e-3 (0.1 wd)    | 2,097,152(1024*2048)    | encoder-decoder   | 2048           | -               | codegen-mono                         | FP16                           | 96 (4 days)   | 8 xA100                          | Adam                                      | Flash Attention                                    | English           |
| 2023/02       | LLaMA         | Meta                      | 7B / 13B / 33B / 65B      | -        | 1.0T(7B, 13B), 1.4T(33B, 65B)     | 3e-4 (7B, 13B), 1.5e-4 (33B, 65B)     | 4M        | decoder-only      | 2048      | 32k     | SentencePiece (BPE)     | -        | 82k (7B)     | A100-80GB     | AdamW     | cosine lr-scheduler     | English       |

----

**The figure below illustrates the combinations of model sizes and training tokens for LLMs.  We can see that most 2B models are pre-trained with approximately 2 trillion tokens.**



![key_resource](./key_resource.png)

### **Reference**

- Gemma: Open Models Based on Gemini Research and Technology
- Textbooks Are All You Need
- Textbooks Are All You Need II: phi-1.5 technical report
- **Phi-2: The surprising power of small language models**
- **Stable LM 2 1.6B Technical Report**
- [MiniCPM：**揭示端侧大语言模型的无限潜力](https://www.notion.so/MiniCPM-c805a17c5c8046398914e47f0542095a?pvs=21)
- DeepSeek LLM Scaling Open-Source Language Models with Longtermism
- Mistral 7B
