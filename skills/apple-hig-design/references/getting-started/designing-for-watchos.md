---
title: Designing for watchOS
url: https://developer.apple.com/design/human-interface-guidelines/designing-for-watchos
platforms: [watchOS]
last_updated: 2023-06-05
---

# Designing for watchOS

When people glance at their Apple Watch, they know they can access essential information and perform simple, timely tasks whether they're stationary or in motion.

## Core guidance

As you begin designing your app for Apple Watch, start by understanding the following fundamental device characteristics and patterns that distinguish the watchOS experience. Using these characteristics and patterns to inform your design decisions can help you provide an app that Apple Watch users appreciate.

### Fundamental device characteristics

**Display.** The small Apple Watch display fits on the wrist while delivering an easy-to-read, high-resolution experience.

**Ergonomics.** Because people wear Apple Watch, they're usually no more than a foot away from the display as they raise their wrist to view it and use their opposite hand to interact with the device. In addition, the Always On display lets people view information on the watch face when they drop their wrist.

**Inputs.** People can navigate vertically or inspect data by turning the Digital Crown, which offers consistent control on the watch face, the Home Screen, and within apps. They can provide input even while they're in motion with standard gestures like tap, swipe, and drag. Pressing the Action button initiates an essential action without looking at the screen, and using shortcuts helps people perform their routine tasks quickly and easily. People can also take advantage of data that device features provide, such as GPS, sensors for blood oxygen and heart function, and the altimeter, accelerometer, and gyroscope.

**App interactions.** People glance at the Always On display many times throughout the day, performing concise app interactions that can last for less than a minute each. People frequently use a watchOS app's related experiences — like complications, notifications, and Siri interactions — more than they use the app itself.

**System features.** watchOS provides several features that help people interact with the system and their apps in familiar, consistent ways.

- Complications
- Notifications
- Always On
- Watch faces

### Best practices

Great Apple Watch experiences are streamlined and specialized, and integrate the platform and device capabilities that people value most. To help your experience feel at home in watchOS, prioritize the following ways to incorporate these features and capabilities.

**Support quick, glanceable, single-screen interactions** that deliver critical information succinctly and help people perform targeted actions with a simple gesture or two.

**Minimize the depth of hierarchy in your app's navigation**, and use the Digital Crown to provide vertical navigation for scrolling or switching between screens.

**Personalize the experience** by proactively anticipating people's needs and using on-device data to provide actionable content that's relevant in the moment or very soon.

**Use complications to provide relevant, potentially dynamic data and graphics** right on the watch face where people can view them on every wrist raise and tap them to dive straight into your app.

**Use notifications to deliver timely, high-value information** and let people perform important actions without opening your app.

**Use background content such as color to convey useful supporting information**, and use materials to illustrate hierarchy and a sense of place.

**Design your app to function independently**, complementing your notifications and complications by providing additional details and functionality.

## Platform considerations

This page is specific to watchOS. The wrist-worn form factor, the Digital Crown, and the Always On display have no counterpart on other Apple platforms. See the corresponding "Designing for" page for iOS, iPadOS, macOS, tvOS, and visionOS.

## Native implementation

**Related**
- Apple Design Resources

**Developer documentation**
- watchOS Pathway

**Videos:** What's new in watchOS 26

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

Most of this page describes hardware — a wrist-worn display viewed from no more than a foot away, a physical Digital Crown, an Always On display — that has no web equivalent. There is no browser context that replicates glancing at a wrist for a few seconds while in motion.

**Glanceable, single-screen interactions → the same discipline applies to small-viewport and notification-surface content.** Apple's reasoning is that an interaction under a minute has to deliver its point without requiring navigation. The same reasoning applies to a web push notification, a PWA home-screen badge, or content rendered in a narrow viewport: state the one piece of information that matters first, and don't require scrolling or drilling down to get it.

**Minimize navigation depth → keep critical actions within one or two taps of entry.** This is a general small-surface UX principle that transfers cleanly: the smaller and more transient the context, the fewer layers of navigation a person should have to cross to act.

**Complications, notifications, Always On, and the Digital Crown → platform services with no direct web equivalent.** A complication depends on watch-face placement and system-level always-visible rendering; a web notification can deliver timely information but can't live persistently on a home screen the way a complication does. The Digital Crown is a physical input mechanism with no browser analogue — don't stretch scroll-wheel or trackpad gestures into a substitute.

## Do / Don't

| Do | Don't |
|---|---|
| Deliver critical information in a quick, single-screen glance | Require multiple screens to convey one piece of information |
| Keep navigation hierarchy shallow | Nest actions behind several levels of navigation |
| Use on-device data to personalize what's shown right now | Show the same generic content regardless of context |
| Surface relevant, potentially dynamic data through complications | Rely on the app alone to deliver time-sensitive information |
| Let notifications carry timely, high-value actions | Force people to open the app for every important action |
| Design the app to work independently of notifications and complications | Make the app depend entirely on its complications and notifications |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
