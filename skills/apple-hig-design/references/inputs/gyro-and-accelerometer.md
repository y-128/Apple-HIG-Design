---
title: Gyroscope and accelerometer
url: https://developer.apple.com/design/human-interface-guidelines/gyro-and-accelerometer
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Gyroscope and accelerometer

On-device gyroscopes and accelerometers can supply data about a device's movement in the physical world.

## Core guidance

You can use accelerometer and gyroscope data to provide experiences based on real-time, motion-based information in apps and games that run in iOS, iPadOS, and watchOS. tvOS apps can use gyroscope data from the Siri Remote. For developer guidance, see Core Motion.

### Best practices

**Use motion data only to offer a tangible benefit to people.** For example, a fitness app might use the data to provide feedback about people's activity and general health, and a game might use the data to enhance gameplay. Avoid gathering data simply to have the data.

> **Note (Apple):** If your experience needs to access motion data from a device, you must provide copy that explains why. The first time your app or game tries to access this type of data, the system includes your copy in a permission request, where people can grant or deny access.

**Outside of active gameplay, avoid using accelerometers or gyroscopes for the direct manipulation of your interface.** Some motion-based gestures may be difficult to replicate precisely, may be physically challenging for some people to perform, and may affect battery usage.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, tvOS, visionOS, or watchOS. Direct on-device accelerometer and gyroscope data is available to apps and games on iOS, iPadOS, and watchOS; tvOS apps can read gyroscope data from the Siri Remote rather than from Apple TV hardware itself.

## Native implementation

**Related**
- Feedback

**Developer documentation**
- Getting processed device-motion data — Core Motion

**Key APIs**
- Core Motion — read raw and processed accelerometer, gyroscope, and device-motion data

**Videos:** Measure health with motion

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance, but this is one of the few hardware topics with a genuine, permission-gated web analogue: the `DeviceOrientationEvent` and `DeviceMotionEvent` APIs. They expose device tilt, rotation rate, and acceleration in roughly the same shape Core Motion does for native apps, and — critically — the same trust model applies. Safari on iOS requires an explicit `requestPermission()` call, triggered by a user gesture, before a page can receive motion or orientation events at all; this maps almost exactly onto Apple's own rule that accessing motion data requires a system permission prompt with app-supplied justification copy. The parallel is strong enough that Apple's underlying reasoning — ask only when there's a tangible benefit, and explain why — transfers as direct, practical advice for the web permission prompt too, since a vague or missing justification is just as likely to make someone decline on the web as on iOS.

Where the mapping breaks down: browser support and behavior are inconsistent across platforms. Non-Safari browsers on iOS inherit WebKit's permission requirement, but Android browsers historically granted motion access without a gesture-gated prompt (behavior has shifted over time and by browser), so the same code produces a materially different trust experience depending on where it runs. There's also no browser equivalent to reading gyroscope data from a paired remote the way tvOS reads the Siri Remote — that pairing-specific data source has no web parallel at all.

**"Avoid using motion data for direct interface manipulation outside gameplay" → this principle transfers unchanged.** The reasoning is platform-agnostic: motion gestures are hard to replicate precisely, exclude people who can't perform them, and cost battery. A web game using the Generic Sensor API's `Accelerometer`/`Gyroscope` interfaces (a lower-level alternative to the Device Motion/Orientation events, with narrower browser support) or the Device Motion events for gameplay should follow the same restraint, and should likewise never make motion input the only way to operate non-game UI.

## Do / Don't

| Do | Don't |
|---|---|
| Use motion data for a specific, tangible benefit (fitness feedback, gameplay) | Collect motion data with no defined use for it |
| Explain, in your permission-request copy, why you need motion data | Present the system permission prompt with no justification |
| Use motion data inside active gameplay | Use motion data to directly manipulate ordinary interface elements |
| Offer a non-motion way to perform any task, outside gameplay | Make a motion gesture the only way to complete a task |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
