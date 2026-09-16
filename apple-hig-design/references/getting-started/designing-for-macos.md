---
title: Designing for macOS
url: https://developer.apple.com/design/human-interface-guidelines/designing-for-macos
platforms: [macOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Designing for macOS

People rely on the power, spaciousness, and flexibility of a Mac as they perform in-depth productivity tasks, view media or content, and play games, often using several apps at once.

## Core guidance

As you begin designing your app or game for macOS, start by understanding the fundamental device characteristics and patterns that distinguish the macOS experience. Using these characteristics and patterns to inform your design decisions can help you provide an app or game that Mac users appreciate.

### Device characteristics

**Display.** A Mac typically has a large, high-resolution display, and people can extend their workspace by connecting additional displays, including their iPad.

**Ergonomics.** People generally use a Mac while they're stationary, often placing the device on a desk or table. In the typical use case, the viewing distance can range from about 1 to 3 feet.

**Inputs.** People expect to enter data and control the interface using any combination of input modes, such as physical keyboards, pointing devices, game controls, and Siri.

**App interactions.** Interactions can last anywhere from a few minutes of performing some quick tasks to several hours of deep concentration. People frequently have multiple apps open at the same time, and they expect smooth transitions between active and inactive states as they switch from one app to another.

**System features.** macOS provides several features that help people interact with the system and their apps in familiar, consistent ways.

- The menu bar
- File management
- Going full screen
- Dock menus

### Best practices

Great Mac experiences integrate the platform and device capabilities that people value most. To help your design feel at home in macOS, prioritize the following ways to incorporate these features and capabilities.

**Leverage large displays to present more content in fewer nested levels and with less need for modality**, while maintaining a comfortable information density that doesn't make people strain to view the content they want.

**Let people resize, hide, show, and move your windows** to fit their work style and device configuration, and support full-screen mode to offer a distraction-free context.

**Use the menu bar to give people easy access to all the commands they need to do things in your app.**

**Help people take advantage of high-precision input modes to perform pixel-perfect selections and edits.**

**Handle keyboard shortcuts to help people accelerate actions and use keyboard-only work styles.**

**Support personalization**, letting people customize toolbars, configure windows to display the views they use most, and choose the colors and fonts they want to see in the interface.

## Platform considerations

This guidance is specific to macOS and Mac. It does not generalize to iOS, iPadOS, or the other Apple platforms — each has its own dedicated overview page in this guide, reflecting a different display, ergonomics, and set of system features. macOS is also the one platform here defined by stationary use, high-precision pointing input, and windowing conventions (the menu bar, Dock menus, resizable windows) that the touch-first platforms don't share.

## Native implementation

**Related**
- Apple Design Resources

**Developer documentation**
- macOS Pathway

**Videos:** Meet Liquid Glass · Get to know the new design system · Build an AppKit app with the new design

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance, and this page is built around desktop-specific conventions — a persistent menu bar, Dock menus, freely resizable and repositionable windows, and high-precision pointing input — that a browser tab does not have access to or control over. Most of it does not transfer.

**What doesn't transfer.** A web page cannot offer a system menu bar, cannot manage its own window chrome (resize, minimize, full screen), and has no equivalent to Dock menus. "People can extend their workspace by connecting additional displays" describes an OS-level window-management capability a page has no visibility into.

**What transfers narrowly.** "Handle keyboard shortcuts to help people accelerate actions and use keyboard-only work styles" generalizes directly: a web app used for sustained productivity work benefits from the same discipline, keeping in mind that browsers reserve many chords for their own use, so the available shortcut space is smaller than native macOS gives you. "Support personalization" maps loosely to remembering a user's layout, view, and appearance choices across sessions, though a web page has far less latitude to change than a native app does. "Maintain a comfortable information density" is the one instruction that transfers almost unchanged — a wide viewport inflates line length and information density the same way a large Mac display does, and the fix (constrain line length, use whitespace deliberately) is the same fix on both platforms.

## Do / Don't

| Do | Don't |
|---|---|
| Use large displays to present more content with fewer nested levels | Nest content deeply just because a phone-sized layout would have required it |
| Let people resize, hide, show, and move windows, and support full screen | Lock window size or force a single fixed layout |
| Put every command people need in the menu bar | Bury frequently needed commands where only a mouse-driven search can find them |
| Support high-precision pointing for pixel-perfect selection and editing | Design controls only for the coarser precision of touch |
| Provide keyboard shortcuts for keyboard-only work styles | Require the pointer for actions a keyboard-only person needs to perform |
| Let people personalize toolbars, views, colors, and fonts | Ship one fixed configuration with no customization |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
