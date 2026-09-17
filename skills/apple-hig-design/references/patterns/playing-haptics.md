---
title: Playing haptics
url: https://developer.apple.com/design/human-interface-guidelines/playing-haptics
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2024-05-07
---

# Playing haptics

Playing haptics can engage people's sense of touch and bring their familiarity with the physical world into your app or game.

## Core guidance

Depending on the platform and the device people are using, the system can play haptics in addition to visual and auditory feedback. For example, components like switches, sliders, and pickers automatically play haptic feedback on supported iPhone models; on Apple Watch, the Taptic Engine generates haptics for a number of built-in feedback patterns, which watchOS combines with an audible tone. On a Mac that's equipped with a Force Touch trackpad, an app can play haptics while people drag content or when they force click to change the speed of media controls.

In addition to built-in haptic capabilities, some external input devices can also play haptics. For example:

- In an iPadOS, macOS, tvOS, or visionOS app or game, game controllers can provide haptic feedback (for developer guidance, see Playing Haptics on Game Controllers).
- Apple Pencil Pro and some trackpads can provide haptic feedback when connected to certain iPad models. (For details on Apple Pencil features and compatibility, see Apple Pencil.)

### Best practices

**Use system-provided haptic patterns according to their documented meanings.** People recognize standard haptics because the system plays them consistently on interactions with standard controls. If the documented use case for a pattern doesn't make sense in your app or game, avoid using the pattern to mean something else. Instead, use a generic pattern or create your own, where supported. For guidance, see Custom haptics.

**Use haptics consistently throughout your app or game.** It's important to build a clear, causal relationship between each haptic and the action that causes it so people learn to associate certain haptic patterns with certain experiences. If a haptic doesn't reinforce a cause-and-effect relationship, it can be confusing and seem gratuitous. For example, if your game plays a specific haptic pattern when a character fails to finish a mission, people associate that pattern with a negative outcome. If you use the same haptic pattern for a positive outcome like a level completion, people will be confused.

**Prefer using haptics to complement other feedback in your app or game.** When visual, auditory, and tactile feedback are in harmony — as they generally are in the physical world — the user experience is more coherent and can seem more natural. For example, you generally want to match the intensity and sharpness of a haptic with the intensity and sharpness of the animation it accompanies. You can also synchronize sound with haptics; for developer guidance, see Delivering Rich App Experiences with Haptics.

**Avoid overusing haptics.** Sometimes a haptic can feel just right when it happens occasionally, but become tiresome when it plays frequently. Doing user testing can help you discover a balance that most people appreciate. Often, the best haptic experience is one that people may not be conscious of, but miss when it's turned off.

**In most apps, prefer playing short haptics that complement discrete events.** Although long-running haptics that accompany a gameplay flow can enhance the experience, long-running haptics in an app can dilute the meaning of the feedback and distract people from their task. On Apple Pencil Pro, for example, continuous or long-lasting haptics don't tend to clarify the writing or drawing experience and can even make holding the pencil less pleasant.

**Make haptics optional.** Let people turn off or mute haptics, and make sure people can still enjoy your app or game without them.

**Be aware that playing haptics might impact other user experiences.** By design, haptics produce enough physical force for people to feel the vibration. Ensure that haptic vibrations don't disrupt experiences involving device features like the camera, gyroscope, or microphone.

### Custom haptics

Games often use custom haptics to enhance gameplay. Although it's less common, nongame apps might also use custom haptics to provide a richer, more delightful experience.

You can design custom haptic patterns that vary dynamically, based on user input or context. For example, the impact players feel when a game character jumps from a tree can be stronger than when the character jumps in place, and substantial experiences — like a collision or a hit — can feel very different from subtle experiences like the approach of footsteps or a looming danger.

There are two basic building blocks you can use to generate custom haptic patterns:

- **Transient events** are brief and compact, often feeling like taps or impulses. The experience of tapping the Flashlight button on the Home Screen is an example of a transient event.
- **Continuous events** feel like sustained vibrations, such as the experience of the lasers effect in a message.

Regardless of the type of haptic event you use to generate a custom haptic, you can also control its sharpness and intensity. You can think of sharpness as a way to abstract a haptic experience into the waveform that produces the corresponding physical sensations. Specifying sharpness lets you relay to the system your intent for the experience. For example, you might use sharpness values to convey an experience that's soft, rounded, or organic, or one that's crisp, precise, or mechanical. As the term implies, intensity means the strength of the haptic.

By combining transient and continuous events, varying sharpness and intensity, and including optional audio content, you can create a wide range of different haptic experiences. For developer guidance, see Core Haptics.

## Platform considerations

### iOS

On supported iPhone models, you can add haptics to your experience in the following ways:

- Use standard UI components — like toggles, sliders, and pickers — that play Apple-designed system haptics by default.
- When it makes sense, use a feedback generator to play one of several predefined haptic patterns in the categories of notification, impact, and selection (for developer guidance, see `UIFeedbackGenerator`).

**Notification** haptics provide feedback about the outcome of a task or action, such as depositing a check or unlocking a vehicle:

| Pattern | Meaning |
|---|---|
| Success | Indicates that a task or action has completed. |
| Warning | Indicates that a task or action has produced a warning of some kind. |
| Error | Indicates that an error has occurred. |

**Impact** haptics provide a physical metaphor you can use to complement a visual experience. For example, people might feel a tap when a view snaps into place or a thud when two heavy objects collide:

| Pattern | Meaning |
|---|---|
| Light | Indicates a collision between small or lightweight UI objects. |
| Medium | Indicates a collision between medium-sized or medium-weight UI objects. |
| Heavy | Indicates a collision between large or heavyweight UI objects. |
| Rigid | Indicates a collision between hard or inflexible UI objects. |
| Soft | Indicates a collision between soft or flexible UI objects. |

**Selection** haptics provide feedback while the values of a UI element are changing:

| Pattern | Meaning |
|---|---|
| Selection | Indicates that a UI element's values are changing. |

### macOS

When a Magic Trackpad is available, your app can provide one of the three following haptic patterns in response to a drag operation or force click.

| Haptic feedback pattern | Description |
|---|---|
| Alignment | Indicates the alignment of a dragged item. For example, this pattern could be used in a drawing app when people drag a shape into alignment with another shape. Other scenarios could include scaling an object to fit within specific dimensions, positioning an object at a preferred location, or reaching the beginning/end or minimum/maximum of something like a scrubber in a video app. |
| Level change | Indicates movement between discrete levels of pressure. For example, as people press a fast-forward button on a video player, playback could increase or decrease and haptic feedback could be provided as different levels of pressure are reached. |
| Generic | Intended for providing general feedback when the other patterns don't apply. |

For developer guidance, see `NSHapticFeedbackPerformer`.

### watchOS

Apple Watch Series 4 and later provides haptic feedback for the Digital Crown, which gives people a more tactile experience as they scroll through content. By default, the system provides linear haptic detents that people can feel as they rotate the Digital Crown. Some system controls, like table views, provide detents as new items scroll onto the screen. For developer guidance, see `WKHapticType`.

watchOS defines a **Notification** haptic that tells the person that something significant or out of the ordinary has happened and requires their attention. The system plays this same haptic when a local or remote notification arrives. watchOS also defines the following additional haptic types: Up, Down, Success, Failure, Retry, Start, Stop, Click.

> **Source limitation:** The source presents the watchOS haptic list as a widget with "Notification" as the described, playable pattern and a sidebar list of eight further type names (Up, Down, Success, Failure, Retry, Start, Stop, Click) with no individual descriptions captured in the PDF. Only "Notification" has prose explaining its meaning in the source; the other eight are listed by name only.

## Native implementation

**Related**
- Feedback
- Gestures

**Developer documentation**
- Core Haptics

**Key APIs**
- `UIFeedbackGenerator` — iOS predefined haptic patterns (notification, impact, selection)
- `NSHapticFeedbackPerformer` — macOS trackpad haptic patterns (alignment, level change, generic)
- `WKHapticType` — watchOS haptic types
- Playing Haptics on Game Controllers — game controller haptic feedback on iPadOS, macOS, tvOS, visionOS
- Core Haptics — custom transient/continuous haptic pattern design

**Videos:** Practice audio haptic design · Introducing Core Haptics

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance, and for this topic the honest answer is that the web analogue is narrow. The Vibration API (`navigator.vibrate()`) is the only web primitive that touches the same hardware category as this document, and it falls far short of what Apple describes here.

**What the Vibration API can do.** It triggers a single undifferentiated buzz, or a pattern of on/off durations in milliseconds, on devices with a vibration motor. That is the entire surface area. There is no sharpness parameter, no intensity parameter, no library of documented system patterns with agreed meanings, no synchronized-audio API, and no distinction between "transient" and "continuous" events beyond what you build yourself out of timed pulses.

**Where the mapping breaks down entirely.** Apple's model rests on *shared vocabulary*: a Success notification haptic means the same thing across every app because the system defines and plays it consistently, and people learn that vocabulary once. The web has no equivalent system-level haptic language, so even if `navigator.vibrate()` were universally supported, a pattern a web app invents would carry no pre-existing meaning to the person feeling it — every site would be teaching its own private vocabulary, which is precisely the failure mode Apple's guidance is designed to prevent ("use system-provided patterns according to their documented meanings").

**Platform support is also badly fragmented.** `navigator.vibrate()` works on Chrome for Android but is unsupported in Safari on iOS and unsupported in desktop browsers generally — meaning the API is unavailable on the exact devices (iPhone, Apple Watch, iPad, Mac trackpads) this HIG page is written for. A web app cannot produce a haptic on an iPhone through the browser at all; only a native app can call into the system's haptic APIs.

**What does transfer as a principle, not an API.** Apple's higher-level rules — make it optional, don't overuse it, keep it short and tied to a discrete event, make sure it doesn't fight with a device sensor — are sound guidance for the rare case where `navigator.vibrate()` is available and appropriate (a supported Android browser, typically for a game or a discrete confirmation). Treat vibration on the web as an occasional, gracefully-degrading enhancement, never as a feedback channel any interaction depends on, since most of your audience's devices and browsers will silently do nothing when you call it.

## Do / Don't

| Do | Don't |
|---|---|
| Use system-provided haptic patterns for their documented meaning | Repurpose a standard pattern (e.g., Success) to mean something else |
| Build a consistent, causal link between each haptic and the action that triggers it | Use the same haptic for both positive and negative outcomes |
| Match haptic intensity and sharpness to the accompanying animation | Let haptics feel disconnected from the visual feedback they accompany |
| Keep most app haptics short and tied to discrete events | Use long-running haptics in a non-game app where they dilute meaning |
| Let people turn off or mute haptics entirely | Make haptics mandatory for using the app or game |
| Consider whether a haptic could disrupt camera, gyroscope, or microphone use | Ignore the physical side effects of a vibration on other active sensors |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
