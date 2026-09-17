---
title: App Shortcuts
url: https://developer.apple.com/design/human-interface-guidelines/app-shortcuts
platforms: [iOS, iPadOS, visionOS, watchOS]
last_updated: 2026-06-08
---

# App Shortcuts

An App Shortcut gives people access to your app's key functions or content throughout the system.

## Core guidance

People can initiate App Shortcuts using features like Siri, Spotlight, and the Shortcuts app; using hardware features like the Action button on iPhone or Apple Watch; or by squeezing Apple Pencil.

Because App Shortcuts are part of your app, they are available immediately when installation finishes. For example, a journaling app could offer an App Shortcut for making a new journal entry that's available before a person opens the app for the first time. Once someone starts using your app, its App Shortcuts can reflect their choices, like those from FaceTime for calling recent contacts.

App Shortcuts use App Intents to define actions within your app to make available to the system. Each App Shortcut includes one or more actions that represent a set of steps people might want to perform to accomplish a task. For example, a home security app might combine the two common actions of turning off the lights and locking exterior doors when a person goes to sleep at night into a single App Shortcut. **Each app can include up to 10 App Shortcuts.**

> **Note (Apple):** When you use App Intents to make your app's actions available to the system, in addition to the App Shortcuts that your app provides, people can also make their own custom shortcuts by combining actions in the Shortcuts app. Custom shortcuts give people flexibility to configure the behavior of actions, and enable workflows that perform tasks across multiple apps. For additional guidance, see the Shortcuts User Guide.

### Best practices

**To surface common types of app functionality throughout the system, consider adopting app schemas instead.** Apps in common domain areas can adopt app schemas to make their actions and content available to Apple Intelligence. On supported devices, this lets Siri and other system experiences surface app features contextually without the need to adopt individual App Shortcuts. App Shortcuts are useful for exposing unique features or custom content to the system in areas not covered by app schemas.

**Offer App Shortcuts for your app's most common and important tasks.** Straightforward tasks that people can complete without leaving their current context work best, but you can also open your app if it helps people complete multistep tasks more easily.

**Add flexibility by letting people choose from a set of options.** An App Shortcut can include a single optional value, or parameter, if it makes sense. For example, a meditation app could offer an App Shortcut that lets someone begin a specific type of meditation: "Start [morning, daily, sleep] meditation." Include predictable and familiar values as options, because people won't have the list in front of them for reference.

**Ask for clarification in response to a request that's missing optional information.** For example, someone might say "Start meditation" without specifying the type (morning, daily, or sleep); you could follow up by suggesting the one they used most recently, or one based on the current time of day. If one option is most likely, consider presenting it as the default, and provide a short list of alternatives to choose from if a person doesn't want the default choice.

**Keep voice interactions simple.** If your phrase feels too complicated when you say it aloud, it's probably too difficult to remember or say correctly. For example, "Start [sleep] meditation with nature sounds" appears to have two possible parameters: the meditation type, and the accompanying sound. If additional information is absolutely required, ask for it in a subsequent step.

**Make App Shortcuts discoverable in your app.** People are most likely to remember and use App Shortcuts for tasks they do often, once they know the shortcut is available. Consider showing occasional tips in your app when people perform common actions to let them know an App Shortcut exists.

### Responding to App Shortcuts

As a person engages with an App Shortcut, your app can respond in a variety of ways, including with dialogue that Siri speaks aloud and custom visuals like snippets and Live Activities.

- **Snippets** are great for custom views that display static information or dialog options, like showing the weather at a person's location or confirming an order.
- **Live Activities** offer continuous access to information that's likely to remain relevant and change over a period of time, and are great for timers and countdowns that appear until an event is complete.

**Provide enough detail for interaction on audio-only devices.** People can receive responses on audio-only devices such as AirPods and HomePod too, and may not always be able to see content onscreen. Include all critical information in the full dialogue text of your App Shortcuts.

### Editorial guidelines

**Provide brief, memorable activation phrases and natural variants.** Because an App Shortcut phrase (or a variant you define) is what people say to run an App Shortcut with Siri, it's important to keep it brief to make it easier to remember. You have to include your app name, but you can be creative with it. For example, Keynote accepts both "Create a Keynote" and "Add a new presentation in Keynote" as App Shortcut phrases for creating a new document.

**When referring to App Shortcuts or the Shortcuts app, always use title case and make sure that Shortcuts is plural.** For example, "MyApp integrates with Shortcuts to provide a quick way to get things done with just a tap or by asking Siri, and offers App Shortcuts you can place on the Action button."

**When referring to individual shortcuts (not App Shortcuts or the Shortcuts app), use lowercase.** For example, "Run a shortcut by asking Siri or tapping a suggestion on the Lock Screen."

## Platform considerations

No additional considerations for visionOS or watchOS. Not supported in tvOS.

### iOS, iPadOS

App Shortcuts can appear in the Top Hit area of Spotlight when people search for your app, or in the Shortcuts area below. Each App Shortcut includes a symbol from SF Symbols that you choose to represent its functionality, or a preview image of an item that the shortcut links to directly.

**Order shortcuts based on importance.** The order you choose determines how App Shortcuts initially appear in both Spotlight and the Shortcuts app, so it's helpful to include the most generally useful ones first. Once people start using your App Shortcuts, the system updates to prioritize the ones they use most frequently.

### macOS

App Shortcuts aren't supported in macOS. However, actions you create for your app using App Intents are supported, and people can build custom shortcuts using them with the Shortcuts app on Mac.

## Native implementation

**Related**
- Siri
- Siri Style Guide
- Shortcuts User Guide

**Developer documentation**
- App Intents
- SiriKit
- Getting started with the App Intents framework — App Intents
- Defining app entities for your custom data types — App Intents
- Adding parameters to an app intent
- Displaying static and interactive snippets
- Making actions and content discoverable by Apple Intelligence

**Key APIs**
- App Intents framework — define actions your app exposes to the system
- `SiriTipUIView` — surface an in-app tip that an App Shortcut exists
- `AppShortcutPhrase` — define the activation phrase and variants for an App Shortcut
- `init(full:supporting:systemImageName:)` — provide full dialogue text for audio-only devices
- `LiveActivityIntent` — respond to an App Shortcut with a Live Activity

**Videos:** What's new in Shortcuts · Design interactive snippets · Get to know App Intents

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance, and App Shortcuts are a system-owned surface — they live in Siri, Spotlight, the Shortcuts app, and hardware buttons that have no web counterpart. Most of this page does not translate.

One narrow structural parallel exists: the Web App Manifest's `shortcuts` member lets an installed PWA declare a short list of jump-to actions that surface from the app's home-screen or taskbar icon (a long-press or right-click menu), the same way an App Shortcut surfaces from the Action button or Spotlight. The underlying principle — expose your app's few most common tasks as standalone entry points, reachable without opening the app to its default screen — carries over even though the surface, discovery mechanism, and voice layer do not. Keeping each declared shortcut's name short and unambiguous is good practice there for the same reason Apple asks for brief, memorable activation phrases: whatever surfaces the shortcut typically shows the name with little room and no context.

Beyond that, the guidance is Siri- and Shortcuts-specific — parameter prompting, voice phrase brevity, and audio-only dialogue have no meaningful web analogue, since the web has no equivalent voice assistant surface to design for.

## Do / Don't

| Do | Don't |
|---|---|
| Offer App Shortcuts for your most common, straightforward tasks | Add a shortcut for every possible action in your app |
| Keep activation phrases brief and memorable | Write a phrase that's awkward to say aloud |
| Ask a follow-up question when optional information is missing | Fail silently or guess wrong when a parameter is missing |
| Include all critical information in full dialogue text | Rely on-screen content that audio-only devices can't show |
| Use title case and "Shortcuts" (plural) for the app/feature | Use lowercase or singular "Shortcut" when referring to the app or feature |
| Use lowercase for an individual shortcut a person created | Capitalize an individual shortcut like a proper feature name |
| Order shortcuts in Spotlight and Shortcuts by importance | Leave shortcut order arbitrary or alphabetical only |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
