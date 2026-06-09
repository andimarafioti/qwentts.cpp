# qwentts.cpp all-options audio and timings

Generated locally on 2026-06-09 with local GGUF files; model downloads are not included.

Common settings: `Qwen/Qwen3-TTS-12Hz-1.7B-CustomVoice`, BF16, speaker `aiden`, English, seed `42`, chunk `8 / 12.5s`, left context `2.0s`.

The stale `cpu_wheel` venv still has the old failing CPU backend path, so it is not listed as a passing option here. The CPU row below is the reset-before-alloc native candidate.

## Summary

| option | source | load | mode | audio | first yield | native total | STT |
| --- | --- | ---: | --- | ---: | ---: | ---: | --- |
| `cpu_reset_before_local` | local native CPU, reset-before-alloc candidate | 1.71s | `greedy_20f` | 1.60s | 2880ms | 5893ms | `This is a short deterministic.` |
| `cpu_reset_before_local` | local native CPU, reset-before-alloc candidate | 1.71s | `sampled_seed42` | 6.40s | 4172ms | 28631ms | `Hello from the Quince TPP Python wheel. This sample compares the same Quen 3 custom voice settings.` |
| `cuda13_reset_before_local` | local native CUDA 13.0, reset-before-alloc candidate | 7.18s | `greedy_20f` | 1.60s | 692ms | 1102ms | `This is a short determination.` |
| `cuda13_reset_before_local` | local native CUDA 13.0, reset-before-alloc candidate | 7.18s | `sampled_seed42` | 6.40s | 259ms | 2713ms | `Hello from the Quint GPP Python wheel. This sample compares the same Quen 3 custom voice settings.` |
| `cu128_wheel` | installed CUDA 12.8 wheel | 7.54s | `greedy_20f` | 1.60s | 887ms | 1318ms | `This is a short deterministic.` |
| `cu128_wheel` | installed CUDA 12.8 wheel | 7.54s | `sampled_seed42` | 6.40s | 281ms | 2770ms | `Hello from the Quent's TP by Python wheel. This sample compares the same Quen 3 custom voice setting.` |
| `cu130_wheel` | installed CUDA 13.0 wheel | 7.18s | `greedy_20f` | 1.60s | 779ms | 1199ms | `This is a short determination.` |
| `cu130_wheel` | installed CUDA 13.0 wheel | 7.18s | `sampled_seed42` | 6.40s | 266ms | 2704ms | `Hello from the Quint GPP Python wheel. This sample compares the same Quen 3 custom voice settings.` |

## Files

| file | bytes | sha256 |
| --- | ---: | --- |
| `samples/cpu_reset_before_local_greedy_20f_customvoice_bf16.wav` | 76844 | `699c509822f045cb46c7443ba0c2ad6a72f104da2e77332ec4281a467254a109` |
| `samples/cpu_reset_before_local_sampled_seed42_customvoice_bf16.wav` | 307244 | `6092ae027ac9f8d515a5ac371ae28b53de2bd7ec88e752df64d042f608879456` |
| `samples/cuda13_reset_before_local_greedy_20f_customvoice_bf16.wav` | 76844 | `22670dc959dab8a0df1b83d7ccc1e4c5eb6d8bec4336dab63223f30a21138f53` |
| `samples/cuda13_reset_before_local_sampled_seed42_customvoice_bf16.wav` | 307244 | `578efded0607e0ab8b61d7ff5db476ef11102adf50e7f0406af597aab3a66cea` |
| `samples/cu128_wheel_greedy_20f_customvoice_bf16.wav` | 76844 | `f4391cb4c6eb892daf563aaf2751b4fd66de3fadcbc6779bd45ca1fe3c472702` |
| `samples/cu128_wheel_sampled_seed42_customvoice_bf16.wav` | 307244 | `cd5649fc32cb2348fe20a92d8dd2c7eb0f2818f6fc6a40303012422b5812b62a` |
| `samples/cu130_wheel_greedy_20f_customvoice_bf16.wav` | 76844 | `22670dc959dab8a0df1b83d7ccc1e4c5eb6d8bec4336dab63223f30a21138f53` |
| `samples/cu130_wheel_sampled_seed42_customvoice_bf16.wav` | 307244 | `578efded0607e0ab8b61d7ff5db476ef11102adf50e7f0406af597aab3a66cea` |

## Prompts

- `greedy_20f`: `This is a short deterministic backend comparison.`
- `sampled_seed42`: `Hello from the qwentts cpp Python wheel. This sample compares the same Qwen three custom voice settings across backends.`
