---
title: Always On
url: https://developer.apple.com/design/human-interface-guidelines/always-on
platforms: [iOS, watchOS]
last_updated: 2023-09-12
---

# Always On

On devices that include the Always On display, the system can continue to display an app's interface when people suspend their interactions with the device.

## Core guidance

In the Always On state, a device can continue to give people useful, glanceable information in a low-power, privacy-preserving way by dimming the display and minimizing onscreen motion. The system can display different items depending on the device.

- On iPhone 14 Pro and iPhone 14 Pro Max, the system displays Lock Screen items like Widgets and Live Activities when people set aside their device face up and stop interacting with it.
- When people drop their wrist while wearing Apple Watch, the system dims the watch face, continuing to display the interface of the app as long as it's either frontmost or running a background session.

On both devices, the system displays notifications while in Always On, and people can tap the display to exit Always On and resume interactions.

### Best practices

**Hide sensitive information.** It's crucial to redact personal information that people wouldn't want casual observers to view, like bank balances or health data. You also need to hide personal information that might be visible in a notification.

**Keep other types of personal information glanceable when it makes sense.** On Apple Watch, for example, people typically appreciate getting pace and heart rate updates while they're working out; on iPhone, people appreciate getting a glanceable update on a flight arrival or a notification when a ride-sharing service arrives. If people don't want any information to be visible, they can turn off Always On.

**Keep important content legible and dim nonessential content.** You can increase dimming on secondary text, images, and color fills to give more prominence to the information that's important to people. For example, a to-do list app might remove row backgrounds and dim each item's additional details to highlight its title. Also, if you display rich images or large areas of color, consider removing the images and using dimmed colors.

**Maintain a consistent layout.** Avoid making distracting interface changes when Always On begins or ends and throughout the Always On experience. For example, when Always On begins, prefer transitioning an interactive component to an unavailable appearance — don't just remove it. Within the Always On context, aim to make infrequent, subtle updates to the interface. For example, a sports app might pause granular play-by-play updates while in Always On, only updating the score when it changes. Note that unnecessary changes during Always On can be especially distracting on iPhone, because people often put their device face up on a surface, making motion on the screen visible even when they're not looking directly at it.

**Gracefully transition motion to a resting state; don't stop it instantly.** Smoothly finishing the current motion helps communicate the transition and avoids making people think that something went wrong.

## Platform considerations

No additional considerations for iOS or watchOS. Not supported in iPadOS, macOS, tvOS, or visionOS.

## Native implementation

**Related**
- Designing for watchOS

**Developer documentation**
- Designing your app for the Always On state — watchOS apps

**Videos:** What's new in watchOS 8 · Build a workout app for Apple Watch · What's new in SwiftUI

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy — and here the mapping is thin, because Always On describes behavior of a specific class of hardware display (iPhone 14 Pro's LTPO screen, Apple Watch's always-on OLED) that the system drives while the app is suspended or backgrounded. A browser tab has no equivalent low-power display state, and the web has no API that lets a page request "dim and keep rendering while the device is idle" the way a watchOS complication or Live Activity can.

What transfers is not the mechanism but a couple of the underlying content-design principles, applied to a different problem: how a web page should present glanceable, low-attention, or ambient-viewing content.

**"Hide sensitive information in a low-attention state" → applies to any public or ambient display context.** A web dashboard meant to run on an office TV, a kiosk, or a shared screen should redact the same categories of data Apple names — balances, health data, anything a passerby shouldn't casually read — the same way a lock-screen widget does. This is a general public-display design principle that Always On happens to state clearly, not something unique to watchOS or iPhone hardware.

**"Dim nonessential content, keep the essential legible" → informs ambient/idle UI states, not Always On itself.** If a web app has its own concept of an idle or ambient view (a kiosk screensaver mode, a dashboard that dims after inactivity via `prefers-reduced-motion` and a CSS opacity transition), the same hierarchy principle applies: reduce secondary text and imagery before touching the primary value someone glances at.

**"Transition motion to a resting state rather than stopping it instantly" → maps to any animation that must yield to a reduced-motion or idle context on the web.** When a page detects `prefers-reduced-motion` or its own idle timer and needs to stop an animation, finishing the current cycle rather than freezing mid-motion is the same courtesy — abrupt stops read as broken regardless of platform.

Beyond these narrow principles, this page is honestly platform-bound: the actual Always On display, its dimming behavior, its interaction with Live Activities and complications, and the system's role in driving it have no web analogue.

## Do / Don't

| Do | Don't |
|---|---|
| Redact bank balances, health data, and other sensitive content | Leave sensitive information visible in the dimmed state |
| Keep genuinely useful glanceable info visible (pace, heart rate, flight status) | Show every detail at full prominence regardless of relevance |
| Dim secondary text, images, and color fills | Dim or hide the primary content people came to check |
| Transition interactive elements to an unavailable appearance | Remove interactive elements abruptly when Always On begins |
| Make infrequent, subtle interface updates while in Always On | Continue granular real-time updates that cause visible motion |
| Let in-progress motion finish smoothly | Stop animation instantly when Always On begins |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
