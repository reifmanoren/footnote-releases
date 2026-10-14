# Footnote releases

Downloads for Footnote, a desktop app that searches your videos by what was said, shown and written on screen. Everything runs on your computer.

This repository holds only release files: app installers, the auto-update manifest, and optional model files the app downloads. The app verifies every file it downloads against a SHA-256 checksum built into the app.

## Model files (release `models-v1`)

These are downloaded by the app when **Hebrew support** is turned on. They are redistributed under their original licenses.

| File | What it is | License |
|---|---|---|
| `ivrit-ai-whisper-large-v3-turbo-q8_0.bin` | Hebrew speech recognition model by [ivrit.ai](https://huggingface.co/ivrit-ai/whisper-large-v3-turbo-ggml), 8-bit quantized with whisper.cpp | Apache-2.0 (see `LICENSE-Apache-2.0.txt`) |
| `opus-mt-tc-big-he-en-*` | Hebrew→English translation model [OPUS-MT](https://huggingface.co/Helsinki-NLP/opus-mt-tc-big-he-en) by Helsinki-NLP (Jörg Tiedemann et al.), used to translate visual search queries | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) |

**Changes from the originals**

- ivrit.ai model: quantized from 16-bit to 8-bit (`q8_0`) with `whisper-quantize`. Source revision `2130c78e4a9cb4914cc4df91a1c3031407789705`.
- OPUS-MT model: converted from PyTorch to ONNX (encoder, and decoder with output layer), weights quantized to 8 bits per channel, tokenizer converted to `tokenizer.json`. Source revision `134c5a850dcaa763eec85bd1f4eb25112fecedbb`. Translations match the original model on our test set.

Checksums are in `SHA256SUMS.txt` on each release.

## Attribution

- ivrit.ai: *ivrit-ai/whisper-large-v3-turbo-ggml*, Apache License 2.0.
- OPUS-MT: Tiedemann, J. and Thottingal, S. (2020). *OPUS-MT: Building open translation services for the World.* EAMT 2020. Model *Helsinki-NLP/opus-mt-tc-big-he-en*, CC BY 4.0.
- Whisper by OpenAI (MIT); whisper.cpp by ggml-org (MIT).
