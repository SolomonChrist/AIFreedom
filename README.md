# AI Freedom Kit

**Keep AI running locally.** A plan, checklist and recovery manual for building an offline AI workstation on Windows 11 that still works if cloud AI services go away, get blocked, or stop being available to you.

The kit has two parts:

| File | What it is |
|---|---|
| [`AI_Freedom_500GB_Offline_Kit_BACKUP_SolomonChristAI.pdf`](AI_Freedom_500GB_Offline_Kit_BACKUP_SolomonChristAI.pdf) | The full 13-page **Offline Recovery Manual**: storage layout, model and app inventory, download and install steps, offline test matrix, backup and checksum procedure, and an agent execution contract. |
| [`AI_Freedom_Master_Checklist_One_Page_Overview_SolomonChristAI.pdf`](AI_Freedom_Master_Checklist_One_Page_Overview_SolomonChristAI.pdf) | A one-page **capability checklist** and readiness gate you can print and tick off. |

## The goal

Prepare fully offline, open-weight AI tools while you still have internet access, then prove they work with the network turned off. Covered areas:

- **Chat and reasoning:** Qwen3, Gemma 3, gpt-oss-20b, DeepSeek-R1-Distill
- **Coding:** Qwen2.5-Coder, Phi-4-mini, Mistral 7B, OpenCode
- **Vision and documents:** Qwen2.5-VL, LLaVA, OpenNotebook, EmbeddingGemma
- **Voice:** Whisper, whisper.cpp, Kokoro-82M, SolomonVoice
- **Images and video:** Stable Diffusion 1.5 / SDXL, FLUX.1-schnell, ComfyUI, Wan 2.1, LTX-Video (video is marked as a stretch goal)
- **Music and decisions:** ACE-Step 1.5 Turbo, LAYA
- **Agents and automation:** Hermes Agent, OpenClaw, n8n, Ollama, LM Studio, llama.cpp

## Status gates

The manual insists that these four states are not the same thing. Do not mark something "working" until it has passed the matching gate with evidence.

| Gate | Meaning |
|---|---|
| **ARCHIVED** | Exact files and dependencies are saved, with a manifest and SHA-256 checksum |
| **INSTALLABLE** | A fresh machine can install it using only the archive |
| **RUNNABLE** | One real task works with no network connection |
| **RECOVERABLE** | A cold restore from backup passes all critical workflows |

"Downloaded," "installed," "starts" and "works offline" are four different statuses.

## Quick start

1. **Read the one-page checklist** to see the full scope.
2. **Check your hardware.** The planning assumption is a GTX 1660 Ti with 6 GB VRAM. Confirm your own GPU and RAM. Larger models may need CPU offload or may only be practical as cold storage.
3. **Plan storage.** The manual sets a 500 GB layout under `D:\AI-Freedom\`: models, audio, creative tools, apps, docs, manifests and tests. Keep at least 50 GB unallocated until tests pass. One external drive is not a backup. Keep a second copy in a different physical location.
4. **Download while online.** Pin exact revisions and commit hashes. Do not use mutable "latest" tags. Save model cards, licenses, installers and dependency wheels.
5. **Generate a SHA-256 manifest** after files stop changing, and verify it on the backup copy.
6. **Disconnect and test.** Turn off Wi-Fi and Ethernet, restart, and run the acceptance matrix below on a clean machine or isolated VM.

## Acceptance matrix

The release gate is **tests 01–11 and 13–16 passing**, or a written exception explaining why a feature was intentionally excluded.

| # | Test | Pass criterion |
|---|---|---|
| 01 | General chat | Qwen or Gemma answers locally |
| 02 | Reasoning | DeepSeek or gpt-oss completes a local reasoning task |
| 03 | Coding | OpenCode + local model creates a small file in a sandbox |
| 04 | Vision | Qwen-VL or LLaVA answers a question about a local image |
| 05 | Speech to text | Whisper transcribes local audio |
| 06 | Speech output | Kokoro speaks a local response |
| 07 | SolomonVoice | Mic → STT → local LLM → TTS completes |
| 08 | Research | OpenNotebook indexes a PDF and answers with local references |
| 09 | Decision project | LAYA repository example runs with its archived checkpoint |
| 10 | Music | ACE-Step creates original local audio |
| 11 | Image | ComfyUI produces one local image |
| 12 | Video (stretch) | Archived video model generates a clip, or is marked impractical |
| 13 | Automation | n8n runs a local workflow and persists data |
| 14 | Agent | Hermes or OpenClaw completes a sandboxed local task |
| 15 | CPU fallback | llama.cpp runs a quantized GGUF on a second machine |
| 16 | Backup restore | Second-drive copy passes checksum and cold restore |

Failures are classified as **MISSING**, **BROKEN**, **NETWORK-DEPENDENT**, **HARDWARE-LIMITED** or **PASSED**. Every failure needs its exact error text, reproduction steps and a rerun result.

## Important notes

- **This is a plan, not a verified install.** The manual says the "agent-reported" status of several items (LAYA, SolomonVoice, ACE-Step, OpenNotebook, OpenClaw, n8n) is unverified. Treat those items as to-do items until they pass their tests.
- **Models have their own licenses.** The MIT license in this repository covers the documents here. Each model, runtime and tool keeps its own license terms. Check them before you redistribute anything.
- **Do not archive secrets.** API keys, n8n encryption keys and credentials belong in a separate encrypted vault, never in a shared archive.
- **Verify downloads.** A SHA-256 hash confirms a file has not changed. It does not confirm the upstream source was trustworthy. Compare against official checksums or signed releases where they exist.
- **Treat downloaded agent skills and workflows as untrusted code.** Run agents with minimum permissions and require human approval for writes, shell commands and deletions.

## Key upstream sources

- Models: [Hugging Face – Qwen](https://huggingface.co/Qwen), [Google](https://huggingface.co/google), [DeepSeek](https://huggingface.co/deepseek-ai), [gpt-oss-20b](https://huggingface.co/openai/gpt-oss-20b)
- Runtimes: [Ollama](https://ollama.com/download), [LM Studio](https://lmstudio.ai/), [llama.cpp](https://github.com/ggml-org/llama.cpp), [whisper.cpp](https://github.com/ggml-org/whisper.cpp), [ComfyUI](https://github.com/comfyanonymous/ComfyUI)
- Voice and research: [Whisper](https://github.com/openai/whisper), [Kokoro-82M](https://huggingface.co/hexgrad/Kokoro-82M), [SolomonVoice](https://github.com/SolomonChrist/SolomonVoice), [OpenNotebook](https://github.com/lfnovo/open-notebook), [LAYA](https://github.com/NandhaKishorM/laya)
- Agents and automation: [n8n](https://github.com/n8n-io/n8n), [OpenCode](https://github.com/anomalyco/opencode), [Hermes](https://github.com/hermes-agent-org/hermes), [OpenClaw](https://github.com/openclaw/openclaw)

## Author

Solomon Christ — [solomonchrist.com](https://solomonchrist.com) · [linkedin.com/in/solomonchristai](https://www.linkedin.com/in/solomonchristai/)

## License

MIT. See [LICENSE](LICENSE).
