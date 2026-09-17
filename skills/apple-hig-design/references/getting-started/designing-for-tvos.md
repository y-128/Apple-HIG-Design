---
title: Designing for tvOS
url: https://developer.apple.com/design/human-interface-guidelines/designing-for-tvos
platforms: [tvOS]
last_updated: 2022-09-14
---

# Designing for tvOS

People enjoy the vibrant content, immersive experiences, and streamlined interactions that tvOS delivers in media and games, as well as in fitness, education, and home utility apps.

## Core guidance

As you begin designing your app or game for tvOS, start by understanding the following fundamental device characteristics and patterns that distinguish the tvOS experience. Using these characteristics and patterns to inform your design decisions can help you provide an app or game that tvOS users appreciate.

### Fundamental device characteristics

**Display.** A TV typically has a very large, high-resolution display.

**Ergonomics.** Although people generally remain many feet away from their stationary TV — often 8 feet or more — they sometimes continue to interact with content as they move around the room.

**Inputs.** People can use a remote, a game controller, their voice, and apps running on their other devices to interact with Apple TV.

**App interactions.** People can get deeply immersed in a single experience — often lasting hours — but they also appreciate using a picture-in-picture view to simultaneously follow an alternative app or video.

**System features.** Apple TV users expect their apps and games to integrate well with the following system experiences.

- Integrating with the TV app
- SharePlay
- Top Shelf
- TV provider accounts

### Best practices

Great tvOS experiences integrate the platform and device capabilities that people value most. To help your experience feel at home in tvOS, prioritize the following ways to incorporate these features and capabilities.

**Support powerful, delightful interactions through the fluid, familiar gestures people make with the Siri Remote.**

**Embrace the tvOS focus system.** Let it gently highlight and expand onscreen items as people move among them, helping them know what to do and where they are at all times.

**Deliver beautiful, edge-to-edge artwork, subtle and fluid animations, and engaging audio.** Wrap people in a rich, cinematic experience that's clear, legible, and captivating from across the room.

**Enhance multiuser support.** Make sign-in easy and infrequent, handle shared sign-in, and automatically switch profiles when people change the current viewer.

## Platform considerations

This page is specific to tvOS; the device characteristics and best practices above describe the living-room, remote-driven experience and don't generalize to other Apple platforms. See the corresponding "Designing for" page for iOS, iPadOS, macOS, visionOS, and watchOS.

## Native implementation

**Related**
- Apple Design Resources

**Developer documentation**
- tvOS Pathway

**Videos:** Build SwiftUI apps for tvOS

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

This page is mostly a description of a piece of hardware — a large, distant, remote-controlled display — and most of that doesn't transfer to the web. There is no direct web equivalent to a Siri Remote, the tvOS focus system, or a stationary TV viewing distance of 8 feet or more.

**The focus system → visible `:focus-visible` states.** The reasoning behind Apple's focus system is the same reasoning behind requiring visible keyboard-focus styles on the web: when a person can't point directly at what they want, the interface has to show, unambiguously, where they currently are. A web page navigated by remote, game controller, or keyboard needs the same clear, high-contrast focus indicator tvOS provides automatically — nothing in CSS gives you this by default the way the focus system does.

**"Legible and captivating from across the room" → treat 10-foot viewing as an extreme, not a default.** If you're building a web app meant to run on a smart-TV browser or a set-top box, the same distance-driven legibility rules apply: larger type, higher contrast, and simpler layouts than you'd use for a phone or laptop screen. For anything else, this doesn't apply — most web content is read at arm's length, and designing for TV-scale legibility everywhere would only hurt readability at normal distances.

**Multiuser sign-in, Top Shelf, SharePlay, TV provider accounts → platform services with no web counterpart.** These depend on tvOS system integration and Apple TV hardware. A web app can approximate shared-session ideas (e.g., a persisted login shared across a household), but there is no meaningful mapping for Top Shelf's home-screen content preview or SharePlay's synchronized playback.

## Do / Don't

| Do | Don't |
|---|---|
| Support fluid, familiar Siri Remote gestures | Design interactions that assume a mouse or touch pointer |
| Let the tvOS focus system highlight and expand onscreen items | Build UI that ignores or fights the focus system |
| Deliver edge-to-edge artwork legible from across the room | Design fine detail meant only for close-up viewing |
| Make sign-in easy, infrequent, and shared across viewers | Force repeated per-app sign-in for every household member |
| Automatically switch profiles when the viewer changes | Assume the same person is always watching |
| Support picture-in-picture for a secondary experience | Assume every session is a single, uninterrupted focus |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
