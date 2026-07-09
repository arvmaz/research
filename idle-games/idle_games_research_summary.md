# Idle Games Research — Summary Report

*Generated: May 23, 2026*

---

## Project Goal
Learn everything about incremental/idle games (Cookie Clicker-like) to design and build one from scratch. Focus areas: game mechanics, similar games, implementation details, and progression systems.

Additional investigation: AI tooling for graphics, music, and sound effects.

---

## Part 1: Game Genre Overview

### What is Cookie Clicker?
An **incremental/idle game** (also called "clicker game" or "AFK game") released in 2013 by Julien "Orteil" Thiennot. It is the archetype of its genre.

**Core mechanics:**
- Click/tap to earn a currency
- Spend currency on buildings/upgrades that auto-generate more currency
- Numbers grow exponentially
- No real end state — the loop continues indefinitely

### Genre: Incremental / Idle Games

| Trait | Description |
|-------|-------------|
| Exponential scaling | Costs and rewards grow by fixed multipliers |
| No failure state | You can't lose, only slow down |
| Idle propagation | Gains continue even when not actively playing |
| Meta-progression | Upgrades unlock new tiers of content |

**Notable games**: Adventure Capitalist, Idle Miner, Anti-Idle, Tap Titans, Egg, Inc.

**Why notable**: Masterclass in variable ratio reinforcement schedules — the same psychology as slot machines.

---

## Part 2: AI Tools Research

### AI Graphics — Key Findings

**Game Jams with AI Graphics:**
- Stable Diffusion Game Jam (Aug 2023) — 1,000+ participants
- AI Game Jam (2023) — disclosure required
- Ludum Dare 54 (2024) — AI allowed with disclosure
- GMTK, Brackey's — neutral/disclosure policy

**Top Tools:**
| Tool | Type | License | Commercial |
|------|------|---------|------------|
| Stable Diffusion | Open-source | Apache 2.0 | ✅ |
| Midjourney | Cloud | Proprietary | ❌ |
| Leonardo.ai | Cloud | Freemium | ❌ |
| ComfyUI | Workflow UI | MIT | ✅ |
| Flux.1 | Open-source | Open | ✅ |

**Key Finding**: Hybrid AI+hand-edit workflows outperform pure AI. ~40-60% time savings on asset creation.

### AI Music — Key Findings

**Free/Offline-Capable Tools:**
| Tool | License | Commercial | Notes |
|------|---------|------------|-------|
| **Riffusion** | **MIT** | ✅ | Best for commercial use, loop-friendly |
| **Bark** | **MIT** | ✅ | Voice + music + SFX |
| MusicGen | CC-BY-NC 4.0 | ❌ | Non-commercial only |
| AudioCraft | CC-BY-NC 4.0 | ❌ | Non-commercial only |
| Jukebox | MSR | ✅ Limited | Older model |

**⚠️ Critical**: MusicGen and AudioCraft are CC-BY-NC — **no commercial use** without a separate Meta license.

**Best commercial path**: Riffusion (MIT, fast, loop-friendly)

### AI Sound Effects — Key Findings

**Free/Offline-Capable Tools:**
| Tool | License | Commercial | Best For |
|------|---------|------------|----------|
| **Bark** | **MIT** | ✅ | Multi-purpose SFX, footsteps, UI, combat |
| AudioGen | Research | ✅ (verify) | Meta SFX generation |
| Tortoise TTS | GPLv3 | ⚠️ | Voice lines only — GPL linking concerns |
| Riffusion | **MIT** | ✅ | Ambient loops, textures |

**⚠️ GPL Warning**: Tortoise TTS is GPLv3 — linking to proprietary engines (Unity/Unreal) may require GPL licensing of your game.

**Recommendation**: Bark (MIT) for all SFX needs — generates footsteps, UI clicks, combat sounds, ambient loops, and voice lines.

---

## Part 3: Cross-Cutting Findings

### No Native Engine Plugins
All AI tools (graphics, music, SFX) require **custom pipelines** to integrate with game engines:
- **Best workflow**: Batch generate offline → import as audio/sprite files → engine handles playback
- **Real-time**: Run local Python server (MusicGen/Bark) → game calls localhost API → stream audio

### Tool Recommendations Summary

| Category | Recommended Tool | Why |
|----------|-----------------|-----|
| Game Graphics | Stable Diffusion + ComfyUI | Open-source, LoRA/ControlNet, commercial OK |
| Game Music | Riffusion | MIT license, loop-friendly, fast |
| Game SFX | Bark | MIT license, multi-purpose, voice included |
| Narrative | GPT-4/Claude (API) | No dedicated game narrative tool; LLMs for dialogue/quests |

### Game Engine Support
- **Unity**: No native AI plugins; custom Python server integration
- **Godot**: Custom integration; open-source tools easier to bridge
- **Unreal**: MetaSound for procedural audio; Python bridge for AI

### Common Denominator
All AI tooling research points to the same conclusion: **local Python servers + batch generation workflow** is the most reliable architecture for indie game AI integration.

---

## Part 4: Next Steps

Pending research (from kanban board):
1. Core game mechanics research
2. Similar games analysis
3. Implementation details research
4. Progression systems research
5. Master research document synthesis

---

## References

### Research Documents
- `ai_game_graphics_research.md`
- `ai_game_music_tools_research.md`
- `ai_game_sfx_tools_research.md`

### Game Jams
- https://itch.io/jams/search?q=ai+game+jam
- https://gmtk.itch.io/
- https://ldjam.com/
- https://brackeys.com/

### AI Graphics Tools
- https://github.com/AUTOMATIC1111/stable-diffusion-webui
- https://github.com/comfyanonymous/ComfyUI
- https://github.com/lllyasviel/ControlNet
- https://leonardo.ai/

### AI Music/SFX Tools
- https://github.com/riffusion/riffusion (MIT — commercial-safe)
- https://github.com/suno-ai/bark (MIT — commercial-safe)
- https://github.com/meta/musicgen (CC-BY-NC — non-commercial)
- https://github.com/facebookresearch/audiocraft

### Communities
- r/GameDev
- GameDev.tv Discord