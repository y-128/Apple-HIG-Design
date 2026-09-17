---
title: Designing for iOS
url: https://developer.apple.com/design/human-interface-guidelines/designing-for-ios
platforms: [iOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Designing for iOS

People depend on their iPhone to help them stay connected, play games, view media, accomplish tasks, and track personal data in any location and while on the go.

## Core guidance

As you begin designing your app or game for iOS, start by understanding the following fundamental device characteristics and patterns that distinguish the iOS experience. Using these characteristics and patterns to inform your design decisions can help you provide an app or game that iPhone users appreciate.

### Device characteristics

**Display.** iPhone has a medium-size, high-resolution display.

**Ergonomics.** People generally hold their iPhone in one or both hands as they interact with it, switching between landscape and portrait orientations as needed. While people are interacting with the device, their viewing distance tends to be no more than a foot or two.

**Inputs.** Multi-Touch gestures, virtual keyboards, and voice control let people perform actions and accomplish meaningful tasks while they're on the go. In addition, people often want apps to use their personal data and input from the device's gyroscope and accelerometer, and they may also want to participate in spatial interactions.

**App interactions.** Sometimes, people spend just a minute or two checking on event or social media updates, tracking data, or sending messages. At other times, people can spend an hour or more browsing the web, playing games, or enjoying media. People typically have multiple apps open at the same time, and they appreciate switching frequently among them.

**System features.** iOS provides several features that help people interact with the system and their apps in familiar, consistent ways.

- Widgets
- Home Screen quick actions
- Spotlight
- Shortcuts
- Activity views

### Best practices

Great iPhone experiences integrate the platform and device capabilities that people value most. To help your design feel at home in iOS, prioritize the following ways to incorporate these features and capabilities.

**Help people concentrate on primary tasks and content** by limiting the number of onscreen controls while making secondary details and actions discoverable with minimal interaction.

**Adapt seamlessly to appearance changes** — like device orientation, Dark Mode, and Dynamic Type — letting people choose the configurations that work best for them.

**Support interactions that accommodate the way people usually hold their device.** For example, it tends to be easier and more comfortable for people to reach a control when it's located in the middle or bottom area of the display, so it's especially important to let people swipe to navigate back or initiate actions in a list row.

**With people's permission, integrate information available through platform capabilities** in ways that enhance the experience without asking people to enter data. For example, you might accept payments, provide security through biometric authentication, or offer features that use the device's location.

## Platform considerations

This guidance is specific to iOS and iPhone. It does not generalize to iPadOS, macOS, or the other Apple platforms — each has its own dedicated overview page in this guide, reflecting a different display, ergonomics, and set of system features.

## Native implementation

**Related**
- Apple Design Resources

**Developer documentation**
- iOS Pathway

**Videos:** Meet Liquid Glass · Get to know the new design system

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance, and this page is unusually hardware-bound: it's built around iPhone's specific display size, one- or two-handed grip, foot-or-two viewing distance, and system features like Widgets, Spotlight, and Shortcuts that have no browser equivalent. Most of it does not transfer.

**What doesn't transfer.** There is no web analogue to Home Screen quick actions, Spotlight indexing, or Activity views — these are operating-system integrations, not page-level concerns. "Viewing distance of a foot or two" and "held in one or both hands" describe a physical relationship to a device that a responsive layout can approximate (via viewport width and touch-target sizing) but never truly knows; a browser has no reliable signal for how far away or how the page is being held.

**What transfers narrowly.** The underlying instinct behind "support interactions that accommodate the way people usually hold their device" does generalize: place primary actions within comfortable thumb reach on a phone-width viewport, and don't assume every visitor has a mouse hovering as a discovery mechanism. "Adapt seamlessly to appearance changes" maps to respecting the operating system's Dark Mode preference and the browser's text-size preference, which is the closest web equivalent to Dynamic Type. Beyond that, treat this page as background context for understanding *why* iOS apps look the way they do, not as a source of web patterns.

## Do / Don't

| Do | Don't |
|---|---|
| Limit onscreen controls and keep secondary actions minimally discoverable | Crowd the primary task with every possible control at once |
| Adapt to orientation, Dark Mode, and Dynamic Type changes | Force a single fixed appearance regardless of the person's settings |
| Place frequently used controls within comfortable one-handed reach | Put primary actions where a one-handed grip can't easily reach them |
| Use platform capabilities (location, biometrics, payments) to reduce manual data entry, with permission | Ask people to type in data the device could supply with their permission |
| Support swipe gestures for back-navigation and row actions | Rely solely on buttons for actions people expect to reach by gesture |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
