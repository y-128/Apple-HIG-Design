---
title: Ornaments
url: https://developer.apple.com/design/human-interface-guidelines/ornaments
platforms: [visionOS]
last_updated: 2024-02-02
---

# Ornaments

In visionOS, an ornament presents controls and information related to a window, without crowding or obscuring the window's contents.

## Core guidance

An ornament floats in a plane that's parallel to its associated window and slightly in front of it along the z-axis. If the associated window moves, the ornament moves with it, maintaining its relative position; if the window's contents scroll, the controls or information in the ornament remain unchanged.

Ornaments can appear on any edge of a window and can contain UI components like buttons, segmented controls, and other views. The system uses ornaments to create and manage components like toolbars, tab bars, and video playback controls; you can use an ornament to create a custom component.

### Best practices

**Consider using an ornament to present frequently needed controls or information in a consistent location that doesn't clutter the window.** Because an ornament stays close to its window, people always know where to find it. For example, Music uses an ornament to offer Now Playing controls, ensuring that these controls remain in a predictable location that's easy to find.

**In general, keep an ornament visible.** It can make sense to hide an ornament when people dive into a window's content — for example, when they watch a video or view a photo — but in most cases, people appreciate having consistent access to an ornament's controls.

**If you need to display multiple ornaments, prioritize the overall visual balance of the window.** Ornaments help elevate important actions, but they can sometimes distract from your content. When necessary, consider constraining the total number of ornaments to avoid increasing a window's visual weight and making your app feel more complicated. If you decide to remove an ornament, you can relocate its elements into the main window.

**Aim to keep an ornament's width the same or narrower than the width of the associated window.** If an ornament is wider than its window, it can interfere with a tab bar or other vertical content on the window's side.

**Consider using borderless buttons in an ornament.** By default, an ornament's background is glass, so if you place a button directly on the background, it may not need a visible border. When people look at a borderless button in an ornament, the system automatically applies the hover affect to it (for guidance, see Eyes).

**Use system-provided toolbars and tab bars unless you need to create custom components.** In visionOS, toolbars and tab bars automatically appear as ornaments, so you don't need to use an ornament to create these components. For developer guidance, see Toolbars and TabView.

## Platform considerations

Not supported in iOS, iPadOS, macOS, tvOS, or watchOS. Ornaments are exclusive to visionOS.

## Native implementation

**Related**
- Layout
- Toolbars

**Developer documentation**
- `ornament(visibility:attachmentAnchor:contentAlignment:ornament:)` — SwiftUI

**Key APIs**
- `ornament(visibility:attachmentAnchor:contentAlignment:ornament:)` — SwiftUI, attaches a custom ornament to a window
- Toolbars — SwiftUI, automatically rendered as an ornament in visionOS
- `TabView` — SwiftUI, automatically rendered as an ornament (tab bar) in visionOS

**Videos:** Design for spatial user interfaces

## Web translation *(derived — not from Apple)*

This topic is platform-bound and has no meaningful web analogue. An ornament is a spatially-anchored, z-axis-offset UI surface that tracks a window through 3D space while staying detached from its content's scroll position — a concept the two-dimensional, DOM-flow-based web layout model has no native concept of. The closest visual cousin on the web is a `position: fixed` or `position: sticky` toolbar that stays pinned to a viewport edge while page content scrolls beneath it, but that comparison only holds at the surface level: a sticky toolbar has no independent depth, doesn't float in front of its container along a third axis, and doesn't move as a physically anchored sibling the way an ornament tracks a visionOS window through space.

What does transfer is the underlying design principle, independent of the 3D mechanism: keep frequently needed controls in a stable, predictable location outside the content's own scroll flow, don't let a persistent control surface grow wide enough to crowd adjacent content, and prefer using a framework's built-in persistent-toolbar or sticky-header component over hand-rolling one, for the same reason Apple gives — the system-provided version already handles the surrounding behavior correctly. Beyond that principle, nothing about ornaments' spatial anchoring, glass background material, or z-axis offset has a meaningful web equivalent.

## Do / Don't

| Do | Don't |
|---|---|
| Use an ornament for frequently needed, consistently located controls | Bury frequently needed controls inside scrolling window content |
| Keep an ornament visible except when content genuinely demands full focus | Hide an ornament by default without a strong content-immersion reason |
| Keep multiple ornaments visually balanced against the window | Add ornaments without limit, increasing visual weight |
| Keep an ornament's width at or below the window's width | Let an ornament grow wider than its associated window |
| Use borderless buttons on an ornament's glass background | Add unnecessary visible borders to ornament buttons |
| Use system-provided toolbars and tab bars, which auto-render as ornaments | Build a custom ornament to replicate what a system toolbar already does |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
