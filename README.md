# discipline_tracker

<div align="center">

<pre><code>
    ____  _       _ _ _           _             _             _
   |  _ \(_) __ _(_) (_) __ _  __| | __ _ _ __ | |_ _ __ __ _| |_ ___  _ __
   | | | | |/ _` | | | |/ _` |/ _` |/ _` | '_ \| __| '__/ _` | __/ _ \| '__|
   | |_| | | (_| | | | | (_| | (_| | (_| | | | | |_| | | (_| | || (_) | |
   |____/|_|\__, |_| |_|\__,_|\__,_|\__,_|_| |_|\__|_|  \__,_|\__\___/|_|
            |___/
</code></pre>

**A local-first, terminal-inspired recovery and deep-work operating system.**

[![License: MIT](https://img.shields.io/badge/License-MIT-orange.svg?style=flat-square)](LICENSE)
[![Status: Stable](https://img.shields.io/badge/Status-Stable-success.svg?style=flat-square)]()
[![Dependencies: Zero](https://img.shields.io/badge/Dependencies-None-8A2BE2.svg?style=flat-square)]()

</div>

---

## Table of Contents

- [Purpose](#purpose)
- [Mission](#mission)
- [Vision](#vision)
- [Why This Exists](#why-this-exists)
- [Features](#features)
- [Site Architecture & Layout](#site-architecture--layout)
- [Getting Started](#getting-started)
- [Recovery Methodology](#recovery-methodology)
- [Philosophy](#philosophy)
- [Keyboard Shortcuts](#keyboard-shortcuts)
- [Data & Privacy](#data--privacy)
- [Tech Stack](#tech-stack)
- [Roadmap](#roadmap)
- [License](#license)

---

## Purpose

`discipline_tracker` exists to solve one problem: **reclaiming attention from algorithmic feeds and redirecting it toward meaningful work.**

In an ecosystem engineered to maximize engagement through infinite scroll, variable reward schedules, and dopamine hijacking, willpower alone is insufficient. This tool treats recovery not as a matter of "trying harder," but as a **systems design problem** — replacing destructive loops with structured, measurable, and rewarding alternatives.

The purpose is to provide a **self-contained, zero-dependency, offline-capable command center** for:
- Tracking and constraining screen time (especially short-form video)
- Building atomic habits that compound over time
- Logging deep work and study sessions
- Documenting emotional states and urges without judgment
- Setting and achieving long-term self-improvement quests

---

## Mission

> **To make deep work the default state and mindless consumption the exception.**

Our mission is to give individuals a practical, beautiful, and private toolset to:

1. **Measure** what currently goes unmeasured — reel exposure, focus time, habit streaks, study hours.
2. **Constrain** digital consumption through explicit budgets and real-time progress bars.
3. **Replace** the void left by removed apps with structured, rewarding activities.
4. **Reflect** daily on progress, setbacks, and emotional patterns without shame.
5. **Persist** entirely in the user's browser — no accounts, no tracking, no servers, no friction.

We believe that **attention is the scarcest resource of the 21st century**, and that protecting it is an act of self-respect.

---

## Vision

We envision a world where:

- **Technology serves the user**, not the other way around. The default interaction with a smartphone is intentional, not compulsive.
- **Deep work is culturally celebrated** the way "hustle culture" currently celebrates constant connectivity.
- **Recovery from algorithmic addiction** is treated with the same seriousness and tooling as physical fitness or financial planning.
- **Local-first software** becomes the norm — your data lives on your device, under your control, forever.
- **Self-improvement is gamified** not through external rewards, but through streaks, quests, and the intrinsic satisfaction of mastery.

`discipline_tracker` is the first step toward that world: a single-file, open-source, terminal-aesthetic dashboard that proves you don't need a corporation's permission to build a better relationship with technology.

---

## Why This Exists

Short-form video platforms are not neutral tools. They are **attention extraction engines** optimized by thousands of engineers to:

- Trigger dopamine spikes through variable reward schedules
- Eliminate stopping cues via infinite scroll
- Personalize content to exploit individual psychological vulnerabilities
- Create withdrawal symptoms (boredom, anxiety) when removed

Willpower is a depleting resource. **Environment design is not.**

This tracker treats your daily routine like an operating system:
- Reels are a `kill -9` process
- Deep work is a `systemctl enable` service
- Habits are cron jobs that run automatically
- Reflection is the log file you review to debug your behavior

---

## Features

### Dashboard — `dashboard.rs`
Your daily command center. At a glance:
- Habits completed today
- Total deep focus time
- Screen time vs. budget
- Reel exposure vs. limit
- Recent study sessions
- Quick-access protocol checklist

### Habit Tracker — `habits.rs`
- **Atomic habits** with streak counters
- **One-click completion** with visual feedback
- **28-day heatmap** showing completion intensity
- **Add / delete** custom habits
- Streak preservation logic (breaks reset, progress compounds)

### Focus Timer — `focus.rs`
- **Pomodoro (25m)**, Deep (50m), and Ultra (90m) presets
- **Live countdown** with pause/resume
- **Auto-logging** of completed sessions to history
- Session archive with date, duration, and type

### Screen Time Monitor — `screentime.rs`
- **Dual budgets**: total screen time + reel-specific exposure
- **Visual progress bars** with color-coded warnings (green to yellow to red)
- **Reel-free day counter** — your most important metric
- **Urge logger** — every time you resist, it gets recorded
- **Recovery actions** — pre-loaded alternatives when cravings hit

### Study Log — `study.rs`
- Log sessions by **topic** and **duration**
- **Running totals** (all-time, this week)
- **Top topic identification**
- Optional notes for each session
- Auto-integration with the "100 Hours of Deep Work" quest

### Goals & Quests — `goals.rs`
- RPG-style **quest system** with progress bars
- Pre-loaded quests:
  - Reel-free streak (30 days)
  - 100 Hours of Deep Work
  - Read 10 Books
- **+/- increment buttons** for manual progress updates
- Custom quest creation

### Journal — `journal.rs`
- **Mood-tagged entries** (Focused, Calm, Tired, Urge, Relapsed)
- **Chronological archive** with date stamps
- Free-form reflection space
- Pattern spotting over time

### Command Palette — `Ctrl+K`
- **Vim-inspired navigation** — jump to any module instantly
- **Quick actions** — start a timer, log an urge, export data
- Fuzzy search through all commands

### Settings — `settings.rs`
- **Export to JSON** — backup your entire history
- **Import from JSON** — restore on any device
- **Reset all data** — nuclear option with confirmation
- No cloud, no lock-in, no vendor dependency

---

## Site Architecture & Layout

```
+-------------------------------------------------------------+
|  SIDEBAR (260px)              |  MAIN CONTENT (flex)        |
|  --------------------------     |  -------------------------  |
|  > discipline                 |  crate / module / file.rs   |
|  v1.0.0 - stable              |                             |
|                               |  [DOCBLOCK]                 |
|  Overview                     |  Description of module      |
|  |-- Dashboard                |                             |
|  |-- Habit Tracker            |  [STATS GRID]               |
|  |-- Focus Timer [run]        |  +----+ +----+ +----+     |
|                               |  | 04 | | 2h | | 90m|     |
|  Recovery                     |  +----+ +----+ +----+     |
|  |-- Screen Time [warn]       |                             |
|  |-- Journal                  |  [CARD]                     |
|                               |  +---------------------+  |
|  Growth                       |  | Module content        |  |
|  |-- Study Log                |  | Forms, tables, etc.  |  |
|  |-- Goals & Quests           |  +---------------------+  |
|                               |                             |
|  System                       |  [TERMINAL BLOCK]           |
|  |-- Settings                 |  $ sudo killall reels       |
|                               |                             |
|  // Press Ctrl+K for palette  |                             |
+-------------------------------------------------------------+
```

### Design Tokens

| Token | Value | Usage |
|-------|-------|-------|
| `--bg` | `#0d0d0d` | Page background |
| `--surface` | `#141414` | Cards, sidebar |
| `--surface-2` | `#1a1a1a` | Hover states, inputs |
| `--surface-3` | `#222222` | Buttons, elevated elements |
| `--border` | `#2a2a2a` | Dividers, outlines |
| `--text` | `#e0e0e0` | Primary text |
| `--text-muted` | `#888888` | Secondary text |
| `--accent` | `#d65d0e` | Links, active states, highlights |
| `--success` | `#2ea043` | Positive metrics, completed states |
| `--warning` | `#e3b341` | Caution, streak warnings |
| `--danger` | `#f85149` | Over-budget, relapses, destructive actions |
| `--info` | `#58a6ff` | Links, hints |
| `--font` | `Fira Code` | All typography (monospace) |

### Module Navigation Pattern

Every page follows the Rust documentation convention:
- **Breadcrumb**: `crate / discipline_tracker / module.rs`
- **Docblock**: Orange left-border info box explaining the module's purpose
- **Code blocks**: Styled with `--bg` background and `--border` outline
- **Terminal windows**: Bash-style blocks with colored dots and command prompts
- **Stability badges**: `run`, `warn`, `stable` tags on sidebar links

---

## Getting Started

### Installation

Zero dependencies. Zero build step.

```bash
# 1. Save the file
curl -O https://your-domain.com/discipline_tracker.html

# 2. Open it
open discipline_tracker.html        # macOS
xdg-open discipline_tracker.html    # Linux
start discipline_tracker.html       # Windows
```

Or simply save the HTML file to your desktop and double-click it.

### First Run

1. Open the file in any modern browser (Chrome, Firefox, Safari, Edge)
2. Set your **Screen Time Limits** in Settings
3. Check off today's habits on the Dashboard
4. Start your first **Focus Timer** session
5. Log your first **Study Session**

All data persists automatically in your browser's `localStorage`.

### Backup Strategy

```bash
# Export your data weekly
# Settings -> Export JSON -> discipline_backup_2026-07-01.json

# Store in a secure location (encrypted drive, password manager)
```

---

## Recovery Methodology

This tool implements a **four-phase recovery protocol**:

### Phase 1: Awareness (Measure)
- Log all screen time honestly
- Track every reel minute without judgment
- Document urges when they occur

### Phase 2: Constraint (Budget)
- Set hard limits (e.g., 15 min reels/day)
- Use the visual progress bar as a speedometer
- Treat over-budget as a system failure, not a moral one

### Phase 3: Replacement (Rebuild)
- When you delete a behavior, you must insert a replacement:
  - Reels -> Pomodoro sessions
  - Doom-scrolling -> Reading log entries
  - Phone-in-bed -> Journal entries
- The Focus Timer and Study Log are your replacement behaviors

### Phase 4: Reflection (Optimize)
- Weekly journal review: what triggered urges?
- Monthly goal assessment: are quests progressing?
- Quarterly data export: long-term trend analysis

---

## Philosophy

### Local-First
Your data never leaves your device. There is no server, no API, no database, no analytics. You own your attention data the same way you own your thoughts.

### Terminal Aesthetic
The Rust docs design language was chosen deliberately:
- **Monospace fonts** evoke precision and engineering
- **Dark themes** reduce eye strain during long sessions
- **Module trees** make navigation feel like exploring a codebase
- **Terminal blocks** reframe self-discipline as system administration

### No Gamification
Unlike apps that sell your attention back to you with coins and leaderboards, this tracker uses **intrinsic motivation**:
- Streaks are for you, not for a social graph
- Quests are private, not performative
- The only competition is yesterday's version of yourself

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl + K` | Open Command Palette |
| `Esc` | Close Command Palette / Modals |
| `D` | Navigate to Dashboard |
| `H` | Navigate to Habits |
| `F` | Navigate to Focus Timer |
| `J` | Navigate to Journal |
| `G D` | Go to Dashboard (from palette) |
| `G H` | Go to Habits (from palette) |
| `G F` | Go to Focus (from palette) |
| `T 2` | Start 25-min timer (from palette) |
| `U` | Log urge resisted (from palette) |

---

## Data & Privacy

```rust
// Your data lifecycle
let data = localStorage::get("discipline_tracker_v1");
assert_eq!(data.owner, You);
assert_eq!(data.servers, 0);
assert_eq!(data.trackers, 0);
assert_eq!(data.third_parties, 0);
```

- **Storage**: Browser `localStorage` only
- **Lifetime**: Persists until you clear browser data or click "Reset All"
- **Portability**: Export anytime as JSON
- **Encryption**: At-rest security depends on your device encryption
- **Sharing**: None. We cannot see your data even if we wanted to.

---

## Tech Stack

| Layer | Technology | Rationale |
|-------|-----------|-----------|
| **Markup** | HTML5 | Universal, eternal, inspectable |
| **Styling** | CSS3 (custom properties) | Zero build tools, themable via `:root` |
| **Typography** | Fira Code (Google Fonts) | Monospace readability, coding aesthetic |
| **Logic** | Vanilla JavaScript (ES6+) | No frameworks, no dependencies, loads instantly |
| **Storage** | Browser localStorage | Offline, private, zero infrastructure |
| **Build** | None | Single file, copy-paste portable |

---

## Roadmap

- [ ] **Weekly Report Generator** — auto-summarize habits, focus, and screen time
- [ ] **Book Tracker** — dedicated reading log with page counts and reviews
- [ ] **Phone Jail Mode** — fullscreen lockout overlay during focus sessions
- [ ] **Data Visualization** — canvas-based charts for long-term trends
- [ ] **PWA Support** — install as standalone app on mobile/desktop
- [ ] **Import from Screen Time APIs** — iOS/Android native data ingestion
- [ ] **Streak Freeze** — one "sick day" per month without breaking streaks
- [ ] **Custom Themes** — light mode, high-contrast, solarized variants

---

## License

MIT License — see [LICENSE](LICENSE) for details.

You are free to use, modify, distribute, and even sell this tool. Your attention is yours. Your code is yours.

---

<div align="center">

<pre><code>
$ sudo systemctl enable discipline --now
# Active and running.
</code></pre>

**Built for humans. Designed for focus. Owned by you.**

</div>
