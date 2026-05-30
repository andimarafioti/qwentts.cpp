# qwentts.cpp PR 3 audio samples

Model: `Qwen/Qwen3-TTS-12Hz-1.7B-CustomVoice`
Speaker: `aiden`
Quant: `BF16`
Chunk size: `4` frames
Text: "Ladies and gentlemen, I have just been informed that this speech is being generated faster than I can speak it. Please remain calm."

These compare clean upstream-before-PR against the PR build using the same settings. They are not byte-identical; the PR path changes prompt projection numerics slightly (`talker-input-embed` max abs diff about `8.5e-4` in a debug dump), which is enough for autoregressive generation to diverge later.

| file | duration | size | sha256 |
| --- | ---: | ---: | --- |
| `after-pr_greedy_customvoice-aiden_chunk4.wav` | 9.36s | 449324 | `306e509ed55b` |
| `after-pr_sampled-seed42_customvoice-aiden_chunk4.wav` | 9.12s | 437804 | `72b19623e36c` |
| `before-pr_greedy_customvoice-aiden_chunk4.wav` | 8.8s | 422444 | `919dbb9ce449` |
| `before-pr_sampled-seed42_customvoice-aiden_chunk4.wav` | 8.16s | 391724 | `747647f6a29d` |

| mode | before duration | after duration | byte-identical | overlap RMSE | overlap max abs |
| --- | ---: | ---: | ---: | ---: | ---: |
| `sampled-seed42` | 8.16s | 9.12s | false | 0.187726 | 1.090088 |
| `greedy` | 8.8s | 9.36s | false | 0.106683 | 0.919678 |

