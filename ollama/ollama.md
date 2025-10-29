# `sarcastic` — A Custom Ollama Personality

This folder contains a minimal setup to create an Ollama model with a **sarcastic, subtly rude, reluctantly helpful** personality.

## 0) Prerequisites
- Install [Ollama](https://ollama.com)
- Ensure you have enough disk/RAM for the chosen base model.

## 1) Directory layout
```
ollama/
├─ Modelfile
└─ ollama.md  (this file)
```

## 2) Create the model
Pull a small base model first (recommended for most laptops):
```bash
ollama pull llama3.2:3b
```

Build your custom model:
```bash
ollama create sarcastic -f Modelfile
```

## 3) Run & test
Start an interactive session:
```bash
ollama run sarcastic
```

Try a few prompts.
### Example 1
**User:** Explain quantum entanglement like I'm five.  
**Model:** Fine—two tiny friends share a secret handshake. No matter how far apart they wander, the moment one does the handshake, the other matches it instantly. Grown-ups call that "correlations in a shared quantum state." See? Magic—except it's math.

### Example 2
**User:** Be honest, is sorting algorithms knowledge even useful?  
**Model:** Only if you like programs that finish this century. Quick sort, merge sort—tools so your computer spends less time napping while you wait. Shocking, I know.

### Example 3 (detecting sarcasm)
**User:** Wow, I absolutely *love* debugging at 3 a.m. Any tips?  
**Model:** Thrilling hobby. Now, step through with a debugger, reproduce a minimal case, add assertions, and write a failing test before you "fix" anything. Glamorous, but it works.

## 4) One-shot command
You can chat inline without an interactive shell:
```bash
ollama run sarcastic -p "Give me three bullet tips for learning SQL quickly."
```

## 5) Notes on tuning
- **temperature** = 0.7 for crisp but witty replies; lower if it rambles.
- **top_p** and **repeat_penalty** lightly reduce repetition.
- Swap the base model by changing the `FROM` line (e.g., `gemma2:2b`, `deepseek-r1:1.5b`, etc.)—then re-run `ollama create`.

## 6) Troubleshooting
- Model not found? Run `ollama pull llama3.2:3b`.
- GPU OOM? Use a smaller base (e.g., `llama3.2:1b` if available) or set `OLLAMA_NUM_GPU=0` to run on CPU (slower).
- Too chatty? Lower `temperature` to `0.3–0.5`.
- Too mean? The SYSTEM block is your ethics leash—tighten wording there.

## 7) Commands used in the process
```bash
mkdir -p ollama
cd ollama
ollama pull llama3.2:3b
ollama create sarcastic -f Modelfile
ollama run sarcastic
```

---