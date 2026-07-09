# AI Sound Effects Generation Research

*Research date: May 23, 2026 — free/offline-capable tools focus*

---

## 1. Free/Open-Source Local AI SFX Tools

### Bark (Suno)
- **What**: Text-to-audio — generates speech, music, and various sound effects via text prompts
- **Offline**: ✅ Fully offline — pip install, runs locally
- **License**: **MIT** — commercial-friendly
- **Use cases**: Footsteps, UI clicks, combat sounds, ambient loops, voice lines
- **Requirements**: GPU for reasonable speed; CPU possible but slow
- **Link**: https://github.com/suno-ai/bark

### AudioGen (Meta)
- **What**: Text-to-audio model specifically for sound effect generation
- **Offline**: ✅ Fully offline — open-source release from Meta
- **License**: Research license — check for commercial use terms
- **Use cases**: Footsteps, UI sounds, combat effects, environmental sounds
- **Note**: Relatively new; promising open-source SFX option
- **Link**: https://github.com/facebookresearch/audiocraft

### Tortoise TTS
- **What**: High-quality text-to-speech for voice lines
- **Offline**: ✅ Fully offline
- **License**: GNU GPL v3 — **⚠️ Caution: GPL linking issues for game engines**
- **Use cases**: NPC voice lines, dialogue systems, in-game announcements
- **Quality**: Excellent voice quality
- **Speed**: Very slow without GPU
- **Link**: https://github.com/neonbjb/tortoise-tts

### Riffusion
- **What**: Music generation via image-space interpolation — can be prompted for SFX-like loops
- **Offline**: ✅ Fully offline — self-hostable via Docker
- **License**: **MIT** — commercial-friendly
- **Use cases**: Ambient loops, atmospheric textures, short musical SFX
- **Link**: https://github.com/riffusion/riffusion

### Jukebox (OpenAI)
- **What**: Long-form music/audio generation
- **Offline**: ✅ Fully offline
- **License**: Microsoft Research License
- **Use cases**: Background ambience, cinematic score elements
- **Note**: Older model; high resource requirements
- **Link**: https://github.com/openai/jukebox

---

## 2. Cloud-Only Tools (Not Offline)

| Tool | Free Tier | SFX Focus | Offline | Commercial |
|------|-----------|-----------|---------|------------|
| **Bleep** (bleeep.com) | ✅ Limited | ✅ Yes | ❌ | ❌ (check terms) |
| **ElevenLabs** | ✅ Limited | Voice only | ❌ | ✅ Paid |
| **Soundraw** | ✅ Limited | Music focus | ❌ | ✅ Paid |
| **Mubert** | ✅ Limited | Music focus | ❌ | ✅ Paid |

### Bleep (bleeep.com)
- Browser-based AI SFX generator
- Quick prototyping for: UI clicks, basic combat sounds
- No offline capability — cloud-dependent
- Freemium model

### ElevenLabs
- Primarily a voice/Speech synthesis tool
- Free tier: limited credits
- SFX generation not main focus; cloud-only
- Excellent for voice lines, not general SFX

---

## 3. Local/Offline Tools Summary

| Tool | Type | Offline | License | Best For |
|------|------|---------|---------|----------|
| **Bark** | TTA | ✅ | **MIT** | Multi-purpose SFX, voice, ambience |
| **AudioGen** | TTA | ✅ | Research | SFX generation (Meta) |
| **Tortoise TTS** | TTS | ✅ | GPLv3 | Voice lines only (GPL caution) |
| **Riffusion** | TTA | ✅ | **MIT** | Ambient loops, textures |
| **Jukebox** | TTA | ✅ | MSR | Cinematic ambience |

---

## 4. Game Engine Integrations

All AI SFX tools require custom pipelines — no native engine plugins.

### Unity
- Bark and Tortoise TTS: unofficial integrations via Python scripting
- General approach: Python backend → WAV output → Unity AudioSource

### Godot
- Open-source tools easier to integrate
- Custom REST API bridge to local Python server
- Godot 4.x Better Audio for improved audio handling

### Unreal Engine
- Limited native support
- Python plugin bridges for AI SFX tools
- MetaSound can trigger AI-generated WAV files

### Recommended Workflow
```
1. Generate SFX via Bark/AudioGen locally
2. Export as WAV/MP3
3. Import to engine as standard audio assets
4. Assign to AudioSource/SoundCue
```

---

## 5. Commercial Licensing

| Tool | Free | Commercial Use |
|------|------|---------------|
| Bark | ✅ | ✅ (MIT) |
| AudioGen | ✅ | ✅ (Research license — verify) |
| Tortoise TTS | ✅ | ⚠️ (GPLv3 — linking concerns) |
| Riffusion | ✅ | ✅ (MIT) |
| Jukebox | ✅ | ✅ (MSR limited) |
| Bleep | ✅ Limited | ❓ (Check terms) |
| ElevenLabs | ✅ Limited | ✅ (Paid subscription) |

### ⚠️ GPL Caution for Tortoise TTS
If you link GPL-licensed code into a game engine (especially proprietary engines like Unity/Unreal), you may be required to release your game under GPL. Use MIT-licensed alternatives (Bark, Riffusion) for safer commercial paths.

---

## 6. Indie Dev Documentation

- Limited publicly documented cases of AI SFX in shipped commercial games
- Most indie devs using AI SFX:
  - Use cloud APIs during prototyping
  - Replace with traditional recording for final production
  - Document via Discord/blog posts rather than formal post-mortems
- No major commercial indie titles prominently advertising AI SFX use

---

## 7. References

- https://github.com/suno-ai/bark
- https://github.com/facebookresearch/audiocraft
- https://github.com/neonbjb/tortoise-tts
- https://github.com/riffusion/riffusion
- https://github.com/openai/jukebox
- https://bleeep.com

---

## Summary

- **Best all-purpose SFX**: Bark (MIT, multi-purpose, can generate footsteps/UI/combat)
- **Best for commercial**: Bark or Riffusion (both MIT license)
- **Voice lines**: Bark (MIT) or ElevenLabs (paid, cloud-only)
- **No native engine plugins** — all require Python backend or manual WAV import
- **GPU recommended** for generation speed on all local tools
- **GPL licensing concern** with Tortoise TTS — avoid for proprietary game engines