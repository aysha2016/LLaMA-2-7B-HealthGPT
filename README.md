# LLaMA-2-7B-HealthGPT (Prototype)

Fine-tuned LLaMA-2-7B model for health-related reasoning, focused on Sri Lanka’s healthcare context.

## 🚀 Features
- Reasoning-heavy responses to healthcare-related prompts
- Optimized for low-resource devices with 4-bit quantization
- Early-stage fine-tuning using synthetic data from GPT-4

## 🔧 Training
- Base: `NousResearch/llama-2-7b-chat-hf`
- Adapter: LoRA (r=64, alpha=16)
- Optimizer: `paged_adamw_32bit`

- GPU: Google Colab Pro (13-15GB VRAM)
- Issues: Faced GPU memory overflow; resolved with restart and 4-bit tuning

## 📄 Sample Prompt

```txt
[INST] <>
Given a puzzle-like, reasoning-heavy question about Sri Lanka's healthcare system.
<>

How can rural health workers improve maternal outcomes in Sri Lanka? [/INST]


from transformers import pipeline

pipe = pipeline("text-generation", model="llama-2-7b-custom-merged", tokenizer="llama-2-7b-custom-merged")
prompt = "[INST] <>\\nGiven a puzzle-like, reasoning-heavy question...<>\\n\\nHow can rural clinics manage high birth rates? [/INST]"
print(pipe(prompt)[0]["generated_text"])



🔮 Future Roadmap
✅ Multilingual data: Sinhala + Tamil

✅ Audio-based health chatbot (STT + TTS)

✅ Real-world medical transcripts

✅ Integration into WhatsApp/Telegram bots

📂 Output
llama-2-7b-custom-merged/ — merged model for deployment

train.jsonl, test.jsonl — data used


