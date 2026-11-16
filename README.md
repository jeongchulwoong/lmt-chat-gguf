# lmt-chat-gguf

A small on-device translation model for chat messages (Korean ↔ English, Korean ↔ Japanese), in GGUF format for llama.cpp.

- **Base model:** [NiuTrans/LMT-60-1.7B](https://huggingface.co/NiuTrans/LMT-60-1.7B) (Apache-2.0, based on Qwen3)
- **Changes:** LoRA fine-tuning (r=16, merged into the weights) on synthetic Korean/Japanese/English chat sentence pairs, so that casual/polite tone, texting abbreviations and everyday words survive translation. Then converted to GGUF and quantized to Q4_K_M with llama.cpp.
- **License:** Apache-2.0 (same as the base model). See `LICENSE`.

## File

| file | size (bytes) | sha256 |
|---|---|---|
| `chat17-q4.gguf` | 1107408352 | `9054d3e22003b3bf4f327b1b1ea24a109bec4ae7e77bf2f3116a8b70fd1b4a0c` |

Download: `https://github.com/jeongchulwoong/lmt-chat-gguf/releases/download/chat17-v2/chat17-q4.gguf`

## Prompt format

Same as the base model:

```
<|im_start|>user
Translate the following text from Korean into English:
Korean: 오늘 몇 시에 끝나?
English:<|im_end|>
<|im_start|>assistant
```

## Limits

This is a 1.7B model quantized to 4 bits. It still mistranslates, especially rare words, idioms and long messages. Only Korean, Japanese and English were tuned; the other languages of the base model were only spot-checked with a handful of sentences and can be slightly worse than the base model. The training sentences are synthetic, not real conversations.
