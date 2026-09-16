---
title: Modality
url: https://developer.apple.com/design/human-interface-guidelines/modality
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2023-12-05
---

# Modality

Modality is a design technique that presents content in a separate, dedicated mode that prevents interaction with the parent view and requires an explicit action to dismiss.

## Core guidance

Presenting content modally can:

- Ensure that people receive critical information and, if necessary, act on it
- Provide options that let people confirm or modify their most recent action
- Help people perform a distinct, narrowly scoped task without losing track of their previous context
- Give people an immersive experience or help them concentrate on a complex task

Depending on the platform, different components present these modal experiences. All platforms can present an **alert**, a modal view that delivers important information related to your app or game. Each platform may also define other types of modal views for context-specific options, such as activity views, sheets, and confirmation dialogs or action sheets. To help people perform a distinct task, iOS, iPadOS, and macOS apps tend to use sheets or popovers, but iPadOS, macOS, and visionOS apps might also just use a separate window.

To provide a temporary experience, like viewing media, or to help people perform a distinct, multistep task, like editing content, apps can offer a full-screen modal experience. Apps may also offer nonmodal types of full-screen experiences — see Going full screen. visionOS apps can offer a range of immersive experiences — see Immersive experiences.

### Best practices

**Present content modally only when there's a clear benefit.** A modal experience takes people out of their current context and requires an action to dismiss, so use modality only when it helps people focus or make choices that affect their content or device.

**Aim to keep modal tasks simple, short, and streamlined.** If a modal task is too complicated, people can lose track of the task they suspended when they entered the modal view, especially if the modal view obscures their previous context.

**Take care to avoid creating a modal experience that feels like an app within your app.** In particular, presenting a hierarchy of views within a modal task can make people forget how to retrace their steps. If a modal task must contain subviews, provide a single path through the hierarchy and avoid including buttons that people might mistake for the button that dismisses the modal view.

**Consider using a full-screen modal style for in-depth content or a complex task.** A modal experience that fills a window or the device display minimizes distractions, so it can work well for presenting videos, photos, or camera views, or to support a multistep task like marking up a document or editing a photo. When a visionOS app runs alongside other apps in the Shared Space, a full-screen modal presentation fills a window; if people transition the app to a Full Space, the full-screen modal presentation can become a more immersive experience.

**Always give people an obvious way to dismiss a modal view.** In general, it works well to follow the platform conventions people already know. In iOS, iPadOS, and watchOS apps, people typically expect to find a button in the top toolbar or swipe down; in macOS and tvOS apps, people expect to find a button in the main content view.

**When necessary, help people avoid data loss by getting confirmation before closing a modal view.** Regardless of whether people use a dismiss gesture or a button, if closing the view could result in the loss of user-generated content, explain the situation and give people ways to resolve it. For example, in iOS you might present an action sheet that includes a save option.

**Make it easy to identify a modal view's task.** When people enter a modal view, they switch away from their previous context and might not return to it right away. A title that names the modal view's task — or additional text that describes the task or provides guidance — helps people keep their place in your app.

**Let people dismiss a modal view before presenting another one.** Allowing multiple modal views to be visible at the same time tends to create visual clutter and can make your app seem scattered and disorganized. People need to remember the context they were in before a modal view appears, so presenting multiple views adds to people's cognitive load, especially when a modal view hides another one by appearing on top of it. Although an alert can appear on top of all other content — including other modal views — never display more than one alert at the same time.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, tvOS, visionOS, or watchOS.

## Native implementation

**Related**
- Sheets
- Alerts
- Popovers
- Action sheets
- Activity views

**Developer documentation**
- Presentation modifiers — SwiftUI
- `UIModalPresentationStyle` — UIKit
- Modal Windows and Panels — AppKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**"Prevents interaction with the parent view" → an actual focus trap, not just a visual overlay.** Apple's definition of modality is behavioral, not visual: the parent view stops receiving interaction. A web dialog that merely sits on top of a dimmed backdrop but leaves the page's tab order intact is not modal in Apple's sense — a keyboard or screen-reader user can still tab into content behind it. The `<dialog>` element's `showModal()` method is the closest native match: it removes everything outside the dialog from the accessibility tree and tab order automatically, which is exactly the guarantee Apple is describing. A hand-rolled modal built from a positioned `<div>` must reproduce this by trapping focus (cycling Tab and Shift+Tab within the dialog), setting `aria-modal="true"`, and inert-ing (or removing from the tab order) everything behind it — the `inert` attribute on the background content does this declaratively.

**"Requires an explicit action to dismiss" → decide deliberately whether backdrop-click and Escape count.** Native `<dialog>` closes on Escape by default, which matches Apple's iOS/watchOS convention of a dismiss control plus a swipe gesture. Whether a click outside the dialog also dismisses it is a judgment call the web makes per-component; Apple's own platforms are inconsistent here too (sheets rubber-band on background tap in some contexts, alerts never dismiss that way). The rule that transfers cleanly is Apple's own: the dismissal method must be obvious, not just discoverable by accident.

**"Give people an obvious way to dismiss" → a visible, labeled close affordance, not reliance on Escape alone.** Keyboard-only dismissal fails anyone unaware of the shortcut or using touch. Pair Escape-to-close with a visible close button placed where Apple places it — top of the modal, consistent across your app — so the affordance doesn't depend on the input method.

**"Never display more than one alert at the same time" → queue, don't stack.** The web has no system-level alert queue the way iOS does, so this discipline has to be built into your own state management: a single alert-hosting root that renders at most one alert and queues the rest, rather than letting independent components each summon their own dialog and risking two stacking.

**Full-screen modal → view transitions can substitute for the "fills the display" cue.** Apple's full-screen modal signals importance partly through occupying the entire display, minimizing distraction. On the web, a full-viewport overlay (rather than a centered card) reproduces the same signal, and the View Transitions API can supply the animated hand-off that makes the transition feel like entering a distinct mode rather than a layer popping up.

**Restoring focus on dismiss transfers directly.** Whichever element opened the modal should reliably receive focus back when it closes — this is uncontested best practice in both native and web modality, and is one of the most commonly missed steps in hand-built web dialogs.

**Where the mapping breaks down: platform-level modal stacking.** iOS and macOS have a system-wide notion of "the current modal presentation," enforced by the OS regardless of which app or view controller is asking. On the web, every dialog is just DOM inside your own page — there is no browser-level guarantee that a third-party widget or ad iframe won't spawn its own competing "modal." You own the entire discipline yourself; the platform will not enforce it for you.

## Do / Don't

| Do | Don't |
|---|---|
| Use modality only when it gives a clear benefit | Present content modally out of habit or for routine navigation |
| Keep modal tasks simple, short, and streamlined | Build a complex multi-view hierarchy inside a modal |
| Provide a single path through a modal task's subviews | Include buttons people could mistake for the dismiss control |
| Give an obvious, platform-conventional dismiss action | Hide the dismissal method or rely on an undiscoverable gesture |
| Confirm before closing a modal that would lose user content | Silently discard user-generated content on dismiss |
| Name the modal view's task in its title | Leave people unsure what task the modal view is for |
| Let one modal close before presenting the next | Stack multiple modal views on top of each other |
| Show at most one alert at a time | Display more than one alert simultaneously |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
