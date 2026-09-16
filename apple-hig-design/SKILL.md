---
name: apple-hig-design
description: A reference covering all 158 topics in Apple's Human Interface Guidelines (HIG), including Apple's exact wording and exact numbers. Use this whenever designing, implementing, or reviewing UI, choosing a component, or deciding on typography, color, layout, motion, or accessibility. Applies to app development on all six Apple platforms (iOS, iPadOS, macOS, tvOS, visionOS, watchOS), to SwiftUI, UIKit, and AppKit component selection, and to web UI. Every topic includes guidance for translating native principles to the web, so use this even when the request doesn't mention "Apple" or "HIG" by name. Applies regardless of the language the question is asked in, including Japanese. Example questions this answers: "What's the natural way to present this modal?", "How big does a button's tap target need to be?", "I want to support dark mode", "Sheet or alert?", "How deep can a sidebar's hierarchy go?", "Is this accessible enough?". Look values up here before answering with numbers from memory.
---

# Apple HIG Reference

A reference collection covering all 158 topics of Apple's Human Interface Guidelines, structured for use in design decisions.

The purpose of this skill is to **not answer from memory**. You may remember that "a tap target is 44 points," but you likely can't accurately recall that it's 60 points on visionOS, how it changes across each Dynamic Type step, or that macOS has no Dynamic Type at all. This skill contains the values Apple actually publishes, verbatim.

## How to use this

1. **Read `references/INDEX.md`.** It lists all 158 topics with a one-line summary of each.
2. **Read only the `.md` file(s) for the relevant topic.** You do not need to, and should not, read all 158 files.
3. When citing a number, use exactly what's written in the file. Do not round or approximate it.

## Categories

| Folder | Count | What's in it |
|---|---|---|
| `getting-started/` | 9 | Each platform's character and the starting principles for designing on it |
| `foundations/` | 18 | Typography, color, layout, materials, motion, accessibility |
| `patterns/` | 25 | Design patterns: modals, search, onboarding, loading, etc. |
| `components/` | 64 | UI components, split into 8 subfolders (below) |
| `inputs/` | 13 | Gestures, keyboard, pointer, Digital Crown, gaze |
| `technologies/` | 29 | Integrations: Apple Pay, HealthKit, SharePlay, etc. |

`components/` breakdown: `content` (4), `layout-and-organization` (10), `menus-and-actions` (12), `navigation-and-search` (5), `presentation` (8), `selection-and-input` (11), `status` (4), `system-experiences` (10) — 8 subfolders in total.

## Frequently used topics

| What you're deciding | File to check |
|---|---|
| Minimum tap target size | `components/menus-and-actions/buttons.md` |
| Font size, Dynamic Type, line spacing | `foundations/typography.md` |
| Color usage, system colors | `foundations/color.md` |
| Dark mode | `foundations/dark-mode.md` |
| Spacing, safe areas, adaptive layout | `foundations/layout.md` |
| Foldables / dual-screen (iPhone Duo), vertical toolbars | `getting-started/designing-for-iphone-duo.md` |
| Liquid Glass, frosted/translucent materials | `foundations/materials.md` |
| Whether and how long to animate | `foundations/motion.md` |
| Contrast ratio, assistive technology | `foundations/accessibility.md` |
| Whether to use a modal | `patterns/modality.md` |
| Choosing between sheet / alert / popover | files under `components/presentation/` |
| Tab bar vs. sidebar | files under `components/navigation-and-search/` |
| Forms, text fields, toggles | files under `components/selection-and-input/` |
| How to show loading state | `patterns/loading.md`, `components/status/progress-indicators.md` |
| Writing UI copy | `foundations/writing.md` |
| Right-to-left language support | `foundations/right-to-left.md` |

## Structure of each reference file

| Section | Content |
|---|---|
| `Core guidance` | Apple's instructions and reasoning, numbers exactly as published |
| `Platform considerations` | Differences across platforms |
| `Specifications` | A spec table, only when the original page has one |
| `Native implementation` | SwiftUI / UIKit / AppKit API names and official docs |
| `Web translation` | Web-equivalent reading — **read the caution below before using this** |
| `Do / Don't` | A side-by-side comparison table |

## Caution when working on web projects

The `Web translation` section is **not from Apple**. The HIG contains no web guidance at all, so this section is a derived reading, extrapolated from native principles. Its heading is explicitly marked `*(derived — not from Apple)*`.

When you cite this section, do not present it as an Apple rule. Frame it in two steps: "Apple's principle is X; applied to the web, that suggests Y."

Many topics have no meaningful web translation. visionOS spatial layout, watchOS complications, Apple Pay's payment hardware, and similar topics honestly state that there is no web equivalent. **When a file says that, do not force a web implementation suggestion anyway.**

## Limits of the source material

The reference files were generated from text extracted out of Apple's HIG pages. Some parts of the original pages could not be extracted. Wherever that happened, the file states it explicitly under a `Source limitation` note. **Nothing is filled in by guessing.**

The main gaps:

- **Dynamic Type size tables** — Apple's pages switch between 7 size steps plus AX1–AX5 via tabs, but the source only printed the first tab of each group. There is no table for the default size (Large).
- **System color values** — colors are rendered as swatch images, so hex/RGB values could not be extracted. Only the color name and API identifier are present.
- **Change logs** — 43 of the 158 topics have no change log published by Apple. These are marked `last_updated: unknown`.

If asked for a specific value on a topic marked with `Source limitation`, **say plainly that the value isn't available here, and point to the file's frontmatter `url` to check Apple's primary source.** Never fabricate a plausible-sounding number.

## When this skill goes stale

Each file's `last_updated` is the date of the latest entry in Apple's change log for that page. The collection is a snapshot as of July 2026, with one additional update reflecting the 2026-09-09 revision (the new "Designing for iPhone Duo" topic, and updates to Layout, Branding, and SharePlay). Apple updates the HIG continuously, and **this skill does not automatically track those updates.**

When making an important decision on a topic where `last_updated` is old or `unknown`, check the current version via the `url` field. Liquid Glass-related topics in particular are an area of ongoing revision.
