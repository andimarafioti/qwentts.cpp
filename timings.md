# qwentts.cpp CPU reset-before-alloc audio samples

Generated locally on 2026-06-09 with qwentts.cpp `eda8b59` plus the scheduler reset candidate:

```cpp
ggml_backend_sched_reset(sched);
if (!ggml_backend_sched_alloc_graph(sched, gf)) {
```

## Setup

- Backend: CPU, ARM/aarch64, 10 CPU threads
- Model: `Qwen/Qwen3-TTS-12Hz-1.7B-CustomVoice`
- Quant: BF16
- Speaker: `aiden`
- Language: `english`
- Chunking: `codec_chunk_sec = 8 / 12.5`, `codec_left_context_sec = 2.0`
- Sample rate: 24 kHz mono

## Samples

| file | mode | max frames | audio | first yield | native total | RMS | STT |
| --- | --- | ---: | ---: | ---: | ---: | ---: | --- |
| `samples/reset_before_greedy_20f_customvoice_bf16.wav` | greedy | 20 | 1.60 s | 3059 ms | 7833 ms | 0.1457 | `This is a short deterministic.` |
| `samples/reset_before_sampled_seed42_customvoice_bf16.wav` | sampled, seed 42 | 80 | 6.40 s | 5160 ms | 24610 ms | 0.1391 | `Hello from the QNTTS CPP Python wheel. This sample compares the same QN three.` |

## Native timings

### Greedy, 20 frames

```text
PromptBuild 11.7 ms
Prefill 1617.3 ms
TTFA 1705.4 ms
TalkerDecode 2383.4 ms (20 frames, 119.17 ms/frame)
CodePredictor 2173.0 ms (108.65 ms/frame)
HostCompose 0.7 ms
CodecDecode 1646.2 ms
Total 7832.5 ms (20 frames, 227.85 ms/frame AR, audio 1.60 s, RTF 4.895)
```

### Sampled, seed 42, 80 frames

```text
PromptBuild 13.4 ms
Prefill 2996.0 ms
TTFA 3254.5 ms
TalkerDecode 6900.6 ms (80 frames, 86.26 ms/frame)
CodePredictor 6795.4 ms (84.94 ms/frame)
HostCompose 3.9 ms
CodecDecode 7899.5 ms
Total 24609.7 ms (80 frames, 171.25 ms/frame AR, audio 6.40 s, RTF 3.845)
```

## Hashes

```text
699c509822f045cb46c7443ba0c2ad6a72f104da2e77332ec4281a467254a109  samples/reset_before_greedy_20f_customvoice_bf16.wav
f629fc7256555b4465d4d1b74d8e8e5544f9a8aa20f732ab4e6b17ca5afc3e28  samples/reset_before_sampled_seed42_customvoice_bf16.wav
```
