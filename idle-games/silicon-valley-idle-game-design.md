# Silicon Valley Idle — Game Design Document

## Setting
You are a nobody engineer in Silicon Valley, early 2000s. No name, no connections, no funding. Just a laptop and an internet connection. Your goal: build a name for yourself through the evolving internet platforms of the 2000s–2020s.

**Tone**: Satirical, nerdy, referential to real tech culture. Think HBO's *Silicon Valley* meets Cookie Clicker.

---

## Platforms (in chronological order of the game)

| Era | Platform | What it represents |
|-----|----------|---------------------|
| 2003 | **MySpace** | The starting platform — everyone is here, nobody is special |
| 2006 | **YouTube** | Video era begins — first viral potential |
| 2006 | **Twitter** | Microblogging — spread ideas fast |
| 2009 | **Mastodon** (real 2016, fictional earlier) | Open-source alternative — the purist path |
| 2010 | **Instagram** | Image-first — aesthetics matter now |
| 2012 | **Snapchat** | Ephemeral content — the young crowd |
| 2013 | **Medium** | Long-form writing — substance over brevity |
| 2015 | **Podcast** | Audio era — build a voice brand |
| 2018 | **Tech Talk / TED-style** | Main stage — mass recognition |
| 2020 | **Newsletter / Substack** | Direct audience — no algorithm dependency |
| 2022 | **Mastodon Refounded** (fictional event) | Second chance at the open web |
| 2024+ | **Your Own Company** | The endgame — build something real |

---

## Core Currency

**Influence Points (IP)** — your measure of fame/impact in Silicon Valley.

Earning IP feels like: followers gained, articles shared, deals closed, products shipped.

---

## Progression — First 5 Minutes (Tutorial Stage)

### Stage 1: MySpace Engineer (0:00 – 1:00)
**State**: Living in a studio apartment, debugging code at 2am.

You start with:
- A broken personal website (serves as your click target)
- A MySpace profile (auto-generated, nobody knows you)
- 0 followers

**Actions available:**
1. **Post on MySpace** — Click to publish a short blog update. +1 IP, +1 MySpace follower.
2. **Add a MySpace song** — Costs IP. Increases click value by 10%.
3. **Customize MySpace profile** — Unlocks upgrade tree.

**Milestone**: First 10 followers → unlocks YouTube.

---

### Stage 2: YouTube Awakening (1:00 – 2:30)
**State**: Someone told you videos are the future.

New mechanic: **Videos** — auto-generate IP over time (idle mechanic kick-in)

You unlock:
- **Record Video** — Click action. Higher IP gain than MySpace posts.
- **YouTube Channel** — Shows subscriber count (idle income multiplier)
- **SEO Trick** — Reduces cost of future upgrades

**Milestone**: 100 subscribers → unlocks Twitter.

---

### Stage 3: Twitter Velocity (2:30 – 4:00)
**State**: You're posting constantly. Your phone won't stop buzzing.

New mechanic: **Retweets** — follower count grows faster, but so does the pace.

You unlock:
- **Tweet** — Click action. Very fast IP gain.
- **Viral Thread** — Passive multiplier, activates randomly
- **Blue Check** — One-time purchase. Boosts all IP gain by 25%. Costs real-world time (game mechanic).

**Milestone**: 1,000 followers → unlocks blog/Medium.

---

### Stage 4: The Blogging Arc (4:00 – 5:00)
**State**: Words matter again. Long-form substance.

New mechanic: **Articles** — high IP per action, slower pace.

You unlock:
- **Write Article** — Click action. Large IP burst.
- **Medium Publication** — Passive income from article backlog
- **Substack** (pre-release teaser) — Shows as locked future upgrade

**Milestone**: Article hits 100 claps → unlocks Company founding screen.

---

### Stage 5: Founder Mode (5:00+)
**State**: You have an email list, followers, and a reputation.

The game transforms:
- Platforms become **buildings** you can buy and upgrade
- Each platform contributes IP/sec (idle income)
- Click actions become less dominant — strategic upgrades take over

**Unlocked Buildings:**
| Building | Icon | What it represents | Effect |
|----------|------|--------------------|--------|
| MySpace HQ | Social network icon | Your blogging past | +1 IP/sec |
| YouTube Studio | Video play button | Video content | +5 IP/sec |
| Twitter Firehouse | Bird logo | Real-time influence | +10 IP/sec |
| Mastodon Server | Elephant | Open-source purism | +15 IP/sec, immune to algorithm changes |

---

## Core Upgrade Trees

### Platform Upgrades (per platform)
1. **Visibility** — More people see your posts (+IP per click)
2. **Automation** — Posts happen on a timer (unlocks idle income for that platform)
3. **Virality Boost** — Random chance of 10x multiplier
4. **Sponsorship** — Brands pay you (real money appears as IP multiplier)

### Meta Upgrades
- **Better Laptop** — +10% all IP gain
- **Coffee Subscription** — +5% click speed
- **Social Network** — Follower gain +25%
- **VC Meeting** — Unlock funding system
- **TED Talk** — Mass exposure event

---

## Prestige Mechanic: "The Flop"

When you feel stuck, you can "flop" — declare your current project a failure and start fresh with a **Legacy Bonus**:
- All future IP gains +10% per previous run
- Some upgrades carry over as "reputation"
- Story snippets unlock based on how far you got

This mirrors real startup culture — your failure becomes a line on your resume.

---

## UI Design Direction

**Layout**: 
- Left panel: Current platform with click target (large, central)
- Right panel: Stats (followers, IP, IP/sec)
- Bottom panel: Building/platform icons — each is a clickable upgrade

**Aesthetic**: 
- Early game: Craigslist grey, early-web energy
- Later game: Sleek dark mode, neon accents
- Platform icons evolve: MySpace is blue gradient, Twitter is bird silhouette, etc.

**Click feedback**:
- Numbers fly up (+1 IP, +10 IP)
- Platform icon bounces slightly
- Sound effect: subtle cash register cha-ching

---

## Monetization (optional/late)
No real-money purchases in this idle game — it's a single-purchase or free experience. The monetization is in-world: fake "sponsorships" that boost IP temporarily.

---

## Story Snippets (unlock on milestones)

These appear as overlay cards between stages:

> **Stage 1 Complete: "First Post"**
> "Your MySpace post went live at 3:47 AM. Your mom was your only friend on the platform. She liked it anyway."

> **Stage 2 Complete: "First Viral"**
> "A video of your cat explaining recursion got 47 views. You're famous in your apartment."

> **Stage 3 Complete: "Verified"**
> "The blue check appeared. Nobody told you what it actually did, but it feels important."

---

## Art Style Direction

**Pixel art / retro-modern hybrid** — nostalgic for the 2000s web but clean enough to read as "Silicon Valley chic".

Early game uses blocky, low-res pixel aesthetic (32x32 icons, 8-bit color).
Late game transitions to crisper pixel art (64x64, 16-bit color depth).

Platform logos are simplified pixel renditions — not photorealistic.

Font: Monospace / code aesthetic for numbers and stats; clean sans-serif for story text.

---

## Technical Notes (for implementation)

- **Engine**: Browser-based (single HTML file with JS) or Godot
- **Save system**: localStorage for persistence
- **Offline progress**: Calculate elapsed time on load, grant IP/sec × seconds away (capped at 8 hours)
- **Number formatting**: Use suffixes (1.2K, 3.4M, 1.1B) as numbers grow large
- **Idle balance**: IP/sec should roughly equal 10x what a click generates per second at the current stage

---

## File Structure
```
/opt/data/silicon-valley-idle/
  index.html       — game entry point
  style.css        — UI styling
  game.js          — core game logic
  /assets/
    /icons/        — platform icons (PNG, 64x64)
    /sprites/      — character sprite sheets
    /audio/        — click sounds, notifications
  /data/
    upgrades.json   — all upgrade definitions
    platforms.json  — platform definitions
    milestones.json — story unlocks
```