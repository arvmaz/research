# AI Game Music Generation Research

*Research date: May 23, 2026 — free/offline-capable tools focus*

---

## 1. Free/Open-Source Local AI Music Tools

### MusicGen (Meta)
- **What**: Transformer language model for music generation from text prompts
- **Offline**: ✅ Fully offline — run locally via PyTorch
- **License**: CC-BY-NC 4.0 — **⚠️ NON-COMMERCIAL** — commercial use requires Meta license
- **Quality**: Good for 30s–2min loops; struggles with longer compositions
- **Model sizes**: Small (300M params), Medium (1.5B), Large (3.3B)
- **Link**: https://github.com/meta/musicgen, https://huggingface.co/meta/musicgen

### Riffusion
- **What**: Generates music via stable diffusion image-space interpolation
- **Offline**: ✅ Fully offline — self-hostable via Docker
- **License**: **MIT** — commercial-friendly, permissive
- **Quality**: Excellent for short loops (5–30s); less coherent for longer pieces
- **Speed**: ~10–20s generation on GPU
- **Link**: https://github.com/riffusion/riffusion

### AudioCraft (Meta) — Full Suite
- **What**: Unified audio generation — MusicGen + SoundGen + MaDi
- **Offline**: ✅ Fully offline
- **License**: CC-BY-NC 4.0 (same as MusicGen — non-commercial)
- **Use**: Procedural music, ambient soundscapes, SFX generation
- **Link**: https://github.com/facebookresearch/audiocraft

### Bark (Suno open-source)
- **What**: Text-to-audio — generates voice + music + sound effects
- **Offline**: ✅ Fully offline — pip install, runs locally
- **License**: **MIT** — commercial OK
- **Quality**: Good for voice-heavy content, ambience; less structured as music
- **Link**: https://github.com/suno-ai/bark

### Jukebox (OpenAI)
- **What**: Long-form music generation (2–4 minutes)
- **Offline**: ✅ Fully offline
- **License**: Microsoft Research License — limited commercial use
- **Quality**: Decent but slow; older model (2020)
- **Note**: High resource requirements (GPU heavily recommended)
- **Link**: https://github.com/openai/jukebox

---

## 2. Cloud-Only Tools (NOT Offline-Capable)

| Tool | Offline | License | Commercial |
|------|---------|---------|------------|
| Stable Audio | ❌ | Proprietary | ❌ |
| Udio | ❌ | Proprietary | ❌ |
| Suno | ❌ | Proprietary | ❌ |
| Mubert | ❌ | Proprietary | ❌ |

---

## 3. Game Engine Integrations

All currently require **custom integration** — no native plugins exist.

### Unity
- No official MusicGen/AudioCraft plugin
- Workaround: Run MusicGen as local Python server, game calls localhost API
- ONNX export possible for some models

### Godot
- Can trigger AI-generated loops as audio streams
- Custom integration via Python backend (REST API)
- Godot 4.x Better Audio plugin for improved audio handling

### Unreal Engine
- MetaSound for procedural audio — can load AI-generated samples
- Audio Mixer triggers AI loops as sound cues
- Integration via Python backend bridge

### Recommended Workflow
```
1. Batch generate loops offline (MusicGen/Riffusion)
2. Edit loop points in Audacity/DAW
3. Import as audio files into engine
```
**Game jam workflow**: ~1–2 hours for full soundtrack using this approach

---

## 4. Output Quality & Licensing Summary

| Tool | Max Length | Loop-Friendly | License | Commercial Use |
|------|------------|---------------|---------|---------------|
| MusicGen Large | 30s–2min | Moderate | CC-BY-NC 4.0 | ❌ Needs Meta license |
| MusicGen Small | 30s | Good | CC-BY-NC 4.0 | ❌ Needs Meta license |
| Riffusion | 5–30s | Excellent | **MIT** | ✅ Yes |
| Bark | 30s | Poor | **MIT** | ✅ Yes |
| Jukebox | 2–4min | Moderate | MSR | ✅ Limited |
| AudioCraft | 30s–2min | Moderate | CC-BY-NC 4.0 | ❌ Needs Meta license |

### ⚠️ Critical Licensing Warning
**CC-BY-NC = NO commercial use** without a separate commercial license from Meta. Many indie devs assume "open source" = commercial OK, but the NC (non-commercial) clause explicitly restricts this.

**Safest for commercial indie games**: Riffusion (MIT), Bark (MIT)

---

## 5. Indie Dev Post-Mortems

### Reported Findings
- **Good for**: Moody ambient, atmospheric tracks, quick prototyping
- **Struggles with**: High-energy chiptune, structured songs with clear sections
- **Game jam use**: Multiple Ludum Dare teams used Riffusion/MusicGen — mostly positive for placeholders
- **Common issues**:
  - Generated music lacks clear loop points (requires manual editing)
  - Prompt sensitivity — getting desired genre/mood is hit-or-miss
  - Some tools add audible watermarks on free tier
  - GPU required for reasonable quality (6–8GB VRAM minimum)

### Watermarks
- Stable Audio: Hidden watermarks
- Udio: Watermarked free tier
- Suno: Watermarked free tier

---

## 6. References

- https://github.com/meta/musicgen
- https://github.com/riffusion/riffusion
- https://github.com/suno-ai/bark
- https://github.com/facebookresearch/audiocraft
- https://github.com/openai/jukebox
- https://huggingface.co/meta/musicgen

---

## Summary

- **Best for commercial use**: Riffusion (MIT) — loop-friendly, fast, no commercial restrictions
- **Best for prototyping**: MusicGen Small — fast, decent quality, free
- **AI+human workflow required**: Generated tracks need DAW editing for seamless loops
- **No native engine plugins**: All integrations require custom Python backend or batch-generate workflow
- **GPU strongly recommended**: 6–8GB VRAM for acceptable generation speed