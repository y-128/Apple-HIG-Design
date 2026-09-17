English | [日本語](README.ja.md)

# apple-hig-design

A Claude Code skill that turns Apple's Human Interface Guidelines (HIG) into a reference Claude can use when it makes UI design decisions.

## What is this?

Apple's Human Interface Guidelines (HIG) are Apple's official rulebook for how apps on iOS, iPadOS, macOS, tvOS, visionOS, and watchOS should look and behave: button sizes, spacing, when to use a modal, how dark mode should work, and so on.

A Claude Code "skill" is a folder of instructions and reference files that Claude Code loads automatically when it decides the folder is relevant to what you asked. You don't run a command to activate it — Claude reads a short description of each installed skill, and pulls in the full content only when the task matches.

This skill gives Claude 158 reference files, one per HIG topic, each containing Apple's actual wording and actual numbers. Instead of guessing "a tap target is probably 44 points" from memory, Claude opens the relevant file and quotes the number Apple actually publishes — including platform-specific exceptions (for example, tap targets are 44pt on iOS but 60pt on visionOS). Each topic also includes a "Web translation" section: this project's own interpretation of how the native principle might apply to web UI. Apple never wrote guidance for the web, so this section is clearly marked as derived, not sourced from Apple.

## Who is this for?

Anyone who asks Claude Code to design, implement, or review UI, whether for a native Apple platform app or a web app, and wants answers grounded in Apple's actual documentation instead of Claude's memory.

Example questions this skill lets Claude answer accurately:

- "Is this iOS sheet presentation correct per the HIG?"
- "How should this web modal behave if I want it to follow Apple's design thinking?"
- "What's the minimum tap target size on visionOS?"
- "Should this be a sheet or an alert?"
- "How deep can a sidebar's hierarchy go?"
- "Is this accessible enough?"

## What's inside

```
Apple-HIG-Design/                     # Repository root
├── README.md / README.ja.md          # This file (English / Japanese)
├── NOTICE.md / NOTICE.ja.md          # Rights and licensing. Read before forking or redistributing.
├── LICENSE                           # MIT license for the original work
├── .claude-plugin/
│   ├── marketplace.json              # Lets Claude Code add this repository as a plugin marketplace
│   └── plugin.json                   # Plugin manifest
└── skills/
    └── apple-hig-design/             # The skill itself
        ├── SKILL.md                  # Router file. Claude reads this first.
        └── references/
            ├── INDEX.md            # Index of all 158 topics
            ├── getting-started/    #   9 files  Platform-specific starting points
            ├── foundations/        #  18 files  Typography, color, layout, accessibility, etc.
            ├── patterns/           #  25 files  Design patterns: modals, search, onboarding, etc.
            ├── inputs/             #  13 files  Gestures, keyboard, Digital Crown, and other input
            ├── technologies/       #  29 files  Apple Pay, HealthKit, SharePlay, and other integrations
            └── components/         #  64 files  UI components, split into 8 subfolders
                ├── content/                       #  4
                ├── layout-and-organization/       # 10
                ├── menus-and-actions/             # 12
                ├── navigation-and-search/         #  5
                ├── presentation/                  #  8
                ├── selection-and-input/           # 11
                ├── status/                        #  4
                └── system-experiences/            # 10
```

That's 9 + 18 + 25 + 13 + 29 + 64 = 158 topics in total.

Each reference file follows the same structure:

| Section | Content |
|---|---|
| `Core guidance` | Apple's instructions and the reasoning behind them. Numbers are never rounded or omitted. |
| `Platform considerations` | Differences across iOS / iPadOS / macOS / tvOS / visionOS / watchOS |
| `Specifications` | A spec table, only included when Apple's original page has one |
| `Native implementation` | SwiftUI / UIKit / AppKit API names, linked to Apple's official docs |
| `Web translation *(derived — not from Apple)*` | This project's own reading of how the native principle maps to web UI. This is **not** Apple's guidance. |
| `Do / Don't` | A side-by-side comparison table |

Note on language: the reference files under `references/` are written in English so that they match Apple's terminology and API names. This README and NOTICE also have Japanese versions (`README.ja.md`, `NOTICE.ja.md`).

## Requirements

- Claude Code installed and working.
- `git`, only if you use the manual installation. Not required for the plugin installation.

## Installation

### Option 1: Plugin marketplace (recommended)

This repository is a Claude Code plugin marketplace. Run these two commands inside Claude Code:

```
/plugin marketplace add y-128/Apple-HIG-Design
/plugin install apple-hig-design@apple-hig-design
```

The first command registers this repository as a marketplace. The second installs the `apple-hig-design` plugin from it (the format is `plugin-name@marketplace-name`, and both happen to be `apple-hig-design`).

The same can be done from a terminal:

```bash
claude plugin marketplace add y-128/Apple-HIG-Design
claude plugin install apple-hig-design@apple-hig-design
```

Restart Claude Code, or start a new session, after installing.

To get later updates:

```
/plugin marketplace update apple-hig-design
```

To uninstall:

```
/plugin uninstall apple-hig-design@apple-hig-design
```

### Option 2: Manual installation

1. Clone the repository somewhere on your machine:

   ```bash
   git clone https://github.com/y-128/Apple-HIG-Design.git
   cd Apple-HIG-Design
   mkdir -p ~/.claude/skills
   ```

   This creates a folder named `Apple-HIG-Design` (the repository root). Inside it, the `skills/apple-hig-design` folder is the skill itself and directly contains `SKILL.md`. The `cd` command moves you into the repository root, and `mkdir -p` creates the skills directory if it does not exist yet.

2. Link the skill into Claude Code's skills directory. Two options:

   **Option A: symlink** (keeps the skill in sync if you later `git pull`)

   ```bash
   ln -s "$(pwd)/skills/apple-hig-design" ~/.claude/skills/apple-hig-design
   ```

   **Option B: copy** (no symlink, but you won't get updates automatically)

   ```bash
   cp -R "$(pwd)/skills/apple-hig-design" ~/.claude/skills/apple-hig-design
   ```

   For a project-local install instead of a global one, use `.claude/skills/apple-hig-design` inside your project's own directory instead of `~/.claude/skills/apple-hig-design`.

3. Verify the link points at the right place:

   ```bash
   ls ~/.claude/skills/apple-hig-design/SKILL.md
   ```

   If this reports "No such file or directory," you linked one directory level too high or too low. Check whether `~/.claude/skills/apple-hig-design` itself contains `SKILL.md`, or whether you linked the repository root (`Apple-HIG-Design`) or the `skills` folder instead of `skills/apple-hig-design`.

4. Restart Claude Code, or start a new session. Skills are picked up at session start, so a running session won't see a skill you just installed.

Do not use both options at the same time; the skill would be loaded twice.

## Usage

You don't need to invoke this skill explicitly. Claude Code reads the short description of every installed skill and decides on its own when a task is relevant to UI design, so it will pull in this skill's content automatically during normal conversation.

Example prompts that will trigger it on their own:

- "Review this iOS sheet presentation against the HIG."
- "What's the minimum tap target size on visionOS?"
- "How should dark mode work for this screen?"

If you want to force it, name the skill directly: "Use the apple-hig-design skill to check this." When triggered, Claude first reads `references/INDEX.md` to find the relevant topic, then opens only the specific file(s) it needs. It does not read all 158 files for a single question.

## Known limitations

The reference files were generated from text extracted out of Apple's HIG pages. Some parts of the original pages could not be extracted. Wherever that happened, the file says so explicitly under a `Source limitation` note — nothing is filled in by guessing.

| Limitation | Example |
|---|---|
| Only the first tab of multi-tab JavaScript widgets was captured | The Dynamic Type size table: only the first size group is present, not the full Large-through-AX5 progression |
| Some topics have no published change log from Apple | 43 of the 158 files have `last_updated: unknown` in their frontmatter |
| Images and diagrams could not be extracted | The Standard icons table under Icons lists only labels and SF Symbol names, not the images |
| Interactive before/after widgets lost their content | The Spatial layout topic's before/after demonstration |

65 of the 158 files contain at least one `Source limitation` note.

## Updating and staleness

This skill is **not** automatically kept in sync with Apple's site. The content is a snapshot taken in July 2026, with one later update on 2026-09-09 that added "Designing for iPhone Duo" and refreshed the Layout, Branding, and SharePlay topics.

If a file's `last_updated` in its frontmatter is old or says `unknown`, or if you're making a decision that really matters, check the `url` field in that file's frontmatter and confirm against Apple's current page before relying on it.

## Glossary

- **HIG (Human Interface Guidelines)**: Apple's official design guidelines for its platforms.
- **Skill**: A folder of instructions and reference material that Claude Code loads automatically when relevant to the task at hand.
- **SwiftUI / UIKit / AppKit**: Apple's UI frameworks. SwiftUI is Apple's current cross-platform framework; UIKit is the older framework for iOS/iPadOS/tvOS; AppKit is the older framework for macOS.
- **Point (pt)**: Apple's unit for UI measurements. It is a logical unit that maps to a different number of physical pixels depending on screen density, unlike a fixed pixel measurement.
- **Dynamic Type**: Apple's system for letting users scale all text in an app up or down, for readability and accessibility.
- **SF Symbols**: Apple's built-in icon library, designed to match system fonts and scale with Dynamic Type.
- **Liquid Glass**: Apple's current translucent, light-refracting material design language, used across system UI.
- **Frontmatter**: The block of metadata (title, url, platforms, last_updated, etc.) at the top of each reference file, written in YAML.

## License

Original work in this project (the skill structure, the `Web translation` sections, this documentation) is licensed under MIT — see [LICENSE](LICENSE).

**Content derived from Apple's HIG is not covered by the MIT license.** It remains subject to `Human Interface Guidelines © Apple Inc. All rights reserved.` Read [NOTICE.md](NOTICE.md) before you fork or redistribute this repository. It explains which parts the MIT license covers and how this project handles Apple's rights.

This project has no affiliation with Apple Inc. and is not endorsed or sponsored by Apple.
