---
title: HealthKit
url: https://developer.apple.com/design/human-interface-guidelines/healthkit
platforms: [iOS, iPadOS, watchOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# HealthKit

HealthKit is the central repository for health and fitness data in iOS, iPadOS, and watchOS.

## Core guidance

When you support HealthKit in your app, you can ask people for permission to access and update their health information.

> **Note (Apple):** If your app doesn't provide health and fitness functionality, don't request access to people's private health data.

For example, a nutrition app might ask for permission to retrieve people's weight and activity data, so it can define calorie consumption goals and make dietary recommendations. In this scenario, the nutrition app could also send data — such as the calories that people log — to HealthKit, which can include the data in its global progress metrics.

### Privacy protection

You must request permission to access people's data, and you must take all necessary steps to protect that data. After you receive permission, it's essential to maintain people's trust by clearly showing them how you use their data.

**Provide a coherent privacy policy.** During the app submission process, you must provide a URL to a clearly stated privacy policy, so that people can view the policy when they click the link in the App Store page for your app.

**Request access to health data only when you need it.** It makes sense to request access to weight information when people log their weight, for example, but not immediately after your app launches. When your request is clearly related to the current context, you help people understand your app's intentions. Also, people can change the permissions they grant, so your app needs to make a request every time it needs access.

**Clarify your app's intent by adding descriptive messages to the standard permission screen.** People expect to see the system-provided permission screen when asked to approve access to health data. Write a few succinct sentences that explain why you need the information and how people can benefit from sharing it with your app. Avoid adding custom screens that replicate the standard permission screen's behavior or content.

**Manage health data sharing solely through the system's privacy settings.** People expect to globally manage access to their health information in Settings > Privacy. Don't confuse people by building additional screens in your app that affect the flow of health data.

### Activity rings

You can enhance your app's health and wellness offerings by displaying the Activity ring element to show people's progress toward their Move, Exercise, and Stand goals. The Activity app defines the position and color of each ring, so people are familiar with the element and understand what it means.

**Use Activity rings for Move, Exercise, and Stand information only.** Activity rings consistently represent progress in these specific areas. Don't attempt to replicate or modify Activity rings for other purposes or to display other types of data. Never show Move, Exercise, and Stand progress in another ring-like element.

**Use Activity rings to show progress for a single person.** Never use Activity rings to represent data for more than one person, and make sure it's obvious whose progress is shown, such as by using a label, a photo, or an avatar.

**Don't use Activity rings for ornamentation.** Activity rings provide information to people; they don't merely embellish your app's design. Never display Activity rings in labels or background graphics.

**Don't use Activity rings for branding.** Use Activity rings strictly to display Activity progress in your app. Never use Activity rings in your app's icon or marketing materials.

**Maintain Activity ring and background colors.** For a consistent user experience, the visual appearance of Activity rings must always be the same, regardless of the context in which they appear. Never change the look of the rings or background by using filters, changing colors, or modifying opacity. Instead, design the surrounding interface to blend with the rings. For example, enclose the rings within a circle. Always scale the rings appropriately so they don't seem disconnected or out of place.

**Maintain Activity ring margins.** An Activity ring element must include a minimum outer margin of no less than the distance between rings. Never allow other elements to crop, obstruct, or encroach upon this margin or the rings themselves. To display an Activity ring element within a circle, adjust the corner radius of the enclosing view rather than applying a circular mask.

**Differentiate other ring-like elements from Activity rings.** Mixing different ring styles can lead to a visually confusing interface. If you must include other rings, use padding, lines, or labels to separate them from Activity rings. Color and scale can also help provide visual separation.

**Provide app-specific information only in Activity notifications.** The system already delivers Move, Exercise, and Stand progress updates. Don't repeat this same information, and never show an Activity ring element in your app's notifications. It's fine to reference Activity progress in a notification, but do so in a way that's unique to your app and doesn't replicate the same information provided by the system.

For developer guidance, see `HKActivityRingView`.

### Apple Health icon

The Apple Health icon shows that an app works with HealthKit and the Health app.

**Use only the Apple-provided icon.** Don't create your own Apple Health icon design or attempt to mimic any Apple-provided designs. Download the Apple Health app icon from Apple Design Resources.

**Display the name Apple Health close to the Apple Health icon.** Displaying both elements near each other reminds people that the icon represents the Health app.

**Display the Apple Health icon consistently with other health-related app icons.** In a view that contains other app icons, make the Apple Health icon no smaller than other icons.

**Don't use the Apple Health icon as a button.** Use the icon only to indicate compatibility with the Health app.

**Don't alter the appearance of the Apple Health icon.** Don't mask the icon to change its corner radius or present it in a circular shape. Don't add embellishments like borders, color overlays, gradients, shadows, or other visual effects.

**Maintain a minimum clear space around the Apple Health icon of 1/10 of its height.** Don't composite the icon onto another graphic element.

**Don't use the Apple Health icon within text or as a replacement for the terms Health, Apple Health, or HealthKit.**

**Don't display Health app images or screenshots.** Like all Apple images, these designs are copyrighted and can't appear in your app or marketing materials. You can include an Activity ring element in your app to display Move, Exercise, and Stand progress.

### Editorial guidelines

**Refer to the Health app as Apple Health or the Apple Health app.** In your app and marketing text, using Apple Health adds clarity.

**Don't use the term HealthKit.** HealthKit is a developer-facing term that names the framework your app uses to access health data. If you need to explain to people how your app works with their data, use the term the Apple Health app. For example, you might say that your app "works with the Apple Health app" or "uses data from the Apple Health app."

**Use correct capitalization when using the term Apple Health.** Apple Health is two words, with an uppercase A and uppercase H, followed by lowercase letters. You can display Apple Health entirely in uppercase only when you need to conform to an established typographic interface style, such as in an app that capitalizes all text.

**Use the system-provided translation of Health to avoid confusing people.** It's best to refer to the Apple Health app using the translation that people view on their device.

## Platform considerations

No additional considerations for iOS, iPadOS, or watchOS. Not supported in macOS, tvOS, or visionOS.

## Specifications

| Element | Value |
|---|---|
| Apple Health icon minimum clear space | 1/10 of the icon's height |

## Native implementation

**Related**
- Works with Apple Health
- Activity rings
- Apple Design Resources

**Developer documentation**
- HealthKit
- Protecting user privacy — HealthKit

**Key APIs**
- `requestAuthorization(toShare:read:completion:)` — requests permission to read and write HealthKit data
- `HKActivityRingView` — displays the Activity ring element

**Videos:** Deliver workout insights with HealthKit workout zones · Meet the HealthKit Medications API · Track workouts with HealthKit on iOS and iPadOS

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance, and HealthKit itself has no web analogue: there is no browser-accessible, OS-level health-data repository with hardware-backed protections comparable to what HealthKit provides on iOS, iPadOS, and watchOS. A website cannot request HealthKit permissions or read from the Health app's store, and no web platform API offers an equivalent centralized, cross-app health datastore.

What transfers is the *consent and disclosure* discipline behind the guidance, because it addresses a problem every sensitive-data request shares, not something specific to HealthKit as a technology. Apple's rule to request access only when the request is contextually justified — not at launch, but at the moment the data is actually needed — maps directly onto the web's permission-prompt model for geolocation, camera, microphone, and notifications: fire the browser's native permission prompt from the exact interaction that needs it, never on page load. Apple's insistence on using the system-provided permission screen, and writing a plain-language justification rather than building a custom screen that mimics it, has a web parallel too: don't render a fake, in-page permission dialog that imitates the browser's own prompt to soften a "no," and don't gate the same feature behind a redundant custom consent screen before the real one appears. "Manage sharing solely through the system's privacy settings, not a shadow settings screen in your app" also transfers directly — direct people to the browser's own site-permissions panel rather than building a competing in-app toggle that doesn't actually revoke browser-level access.

The Activity ring and Apple Health icon guidance does not transfer at all. Both are Apple-owned visual assets governed by trademark and brand rules specific to Apple's ecosystem; there is no web equivalent to "download the official asset and never redraw it," because no browser vendor provides an analogous branded health-progress element for third-party sites to display. The general principle underneath — never imitate another platform's or company's proprietary UI element well enough that people mistake your rendering for the real thing — is a reasonable design ethic to keep, but it is not specific to health software.

## Do / Don't

| Do | Don't |
|---|---|
| Request health data access only at the moment it's needed | Request access immediately after app launch |
| Explain your intent with descriptive text on the standard permission screen | Build a custom screen that replicates the system permission screen |
| Let people manage health data sharing in Settings > Privacy | Build additional in-app screens that affect health data flow |
| Use Activity rings only for Move, Exercise, and Stand progress | Use Activity rings for other data types or as ornamentation |
| Use Activity rings for a single, clearly identified person | Represent more than one person's data in one Activity ring |
| Use the official, unmodified Apple Health icon | Redesign, recolor, or add effects to the Apple Health icon |
| Refer to "Apple Health" or "the Apple Health app" | Use the developer-facing term "HealthKit" in user-facing copy |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
