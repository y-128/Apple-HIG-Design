---
title: Designing for iPadOS
url: https://developer.apple.com/design/human-interface-guidelines/designing-for-ipados
platforms: [iPadOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Designing for iPadOS

People value the power, mobility, and flexibility of iPad as they enjoy media, play games, perform detailed productivity tasks, and bring their creations to life.

## Core guidance

As you begin designing your app or game for iPad, start by understanding the following fundamental device characteristics and patterns that distinguish the iPadOS experience. Using these characteristics and patterns to inform your design decisions can help you provide an app or game that iPad users appreciate.

### Device characteristics

**Display.** iPad has a large, high-resolution display.

**Ergonomics.** People often hold their iPad while using it, but they might also set it on a surface or place it on a stand. Positioning the device in different ways can change the viewing distance, although people are typically within about 3 feet of the device as they interact with it.

**Inputs.** People can interact with iPad using Multi-Touch gestures and virtual keyboards, an attached keyboard or pointing device, Apple Pencil, or voice, and they often combine multiple input modes.

**App interactions.** Sometimes, people perform a few quick actions on their iPad. At other times, they spend hours immersed in games, media, content creation, or productivity tasks. People frequently have multiple apps open at the same time, and they appreciate viewing more than one app onscreen at once and taking advantage of inter-app capabilities like drag and drop.

**System features.** iPadOS provides several features that help people interact with the system and their apps in familiar, consistent ways.

- Multitasking
- Widgets
- Drag and drop

### Best practices

Great iPad experiences integrate the platform and device capabilities that people value most. To help your experience feel at home in iPadOS, prioritize the following ways to incorporate these features and capabilities.

**Take advantage of the large display to elevate the content people care about**, minimizing modal interfaces and full-screen transitions, and positioning onscreen controls where they're easy to reach, but not in the way.

**Use viewing distance and input mode to help you determine the size and density of the onscreen content you display.**

**Let people use Multi-Touch gestures, a physical keyboard or trackpad, or Apple Pencil**, and consider supporting unique interactions that combine multiple input modes.

**Adapt seamlessly to appearance changes** — like device orientation, multitasking modes, Dark Mode, and Dynamic Type — and transition effortlessly to running in macOS, letting people choose the configurations that work best for them.

## Platform considerations

This guidance is specific to iPadOS and iPad. It does not generalize to iOS, macOS, or the other Apple platforms — each has its own dedicated overview page in this guide, reflecting a different display, ergonomics, and set of system features. Note that iPadOS is the one platform in this set whose own overview explicitly names a transition point to another platform: apps can also run in macOS, and the guidance calls out adapting to that transition as part of "appearance changes."

## Native implementation

**Related**
- Apple Design Resources

**Developer documentation**
- iPadOS Pathway

**Videos:** Elevate the design of your iPad app · Meet Liquid Glass · Get to know the new design system

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance, and this page is built around iPad's specific display size, its wider range of input modes (touch, physical keyboard, trackpad, Apple Pencil, voice), and system features — Multitasking, Widgets, drag and drop between apps — that are operating-system integrations without a browser equivalent. Most of it does not transfer.

**What doesn't transfer.** There is no web analogue to iPadOS multitasking (Split View, Slide Over) or to system-level Widgets. Drag and drop between two separate native apps has no reliable web counterpart either; the HTML Drag and Drop API exists, but it operates within or between pages you control, not across arbitrary installed software the way iPadOS drag and drop does. "Positioning the device in different ways can change the viewing distance" describes a physical flexibility (handheld, propped on a stand) that a page cannot detect or respond to.

**What transfers narrowly.** "Use viewing distance and input mode to help you determine size and density" does generalize into responsive design's core instinct: a layout should size content and touch targets based on the input capabilities and viewport it's actually running with (touch versus pointer, coarse versus fine), rather than assuming one input model for every visitor. "Let people use multiple input modes" maps to not building an interface that silently breaks for keyboard-only or trackpad-only visitors just because touch is the primary target. Beyond that narrow overlap, treat this page as background for why iPad apps look the way they do, not as a source of web layout patterns.

## Do / Don't

| Do | Don't |
|---|---|
| Use the large display to elevate the content people care about | Force modal interfaces and full-screen transitions where the display has room to avoid them |
| Size and lay out onscreen content based on viewing distance and input mode | Use one fixed density regardless of how far away or how the device is being used |
| Support Multi-Touch, physical keyboard or trackpad, and Apple Pencil | Design for touch alone and let other input modes degrade |
| Adapt to orientation, multitasking modes, Dark Mode, and Dynamic Type | Assume a single fixed window size or appearance |
| Position onscreen controls where they're easy to reach without being in the way | Place controls so they either crowd content or require reaching across the display |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
