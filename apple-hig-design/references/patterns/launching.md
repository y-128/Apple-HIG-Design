---
title: Launching
url: https://developer.apple.com/design/human-interface-guidelines/launching
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2024-06-10
---

# Launching

A streamlined launch experience helps people start using your app or game immediately.

## Core guidance

Launching begins when someone opens your app or game, includes an initial download, and ends when the first screen is ready. After launching completes, you might offer an onboarding experience, which can give people a high-level view of your app or game.

### Best practices

**Launch instantly.** People want to start interacting with your app or game right away, and sometimes they don't want to wait more than a couple of seconds.

**If the platform requires it, provide a launch screen.** In iOS, iPadOS, and tvOS, the system displays your launch screen the moment your app or game starts and quickly replaces it with your first screen, giving people the impression that your experience is fast and responsive. For guidance, see Launch screens, below. macOS, visionOS, and watchOS don't require launch screens.

**If you need a splash screen, consider displaying it at the beginning of your onboarding flow.** A splash screen is a beautiful graphic that succinctly communicates branding and other information you need to provide. If you don't provide an onboarding experience, you might display your splash screen as soon as launching completes.

**Restore the previous state when your app restarts so people can continue where they left off.** Avoid making people retrace steps to reach their previous location in your app or game. Restore granular details of the previous state as much as possible — for example, scroll the view to people's most recent position, and display windows in the same state and location in which people left them.

### Launch screens

Not applicable for macOS, visionOS, or watchOS.

**Downplay the launch experience.** A launch screen isn't part of an onboarding experience or a splash screen, and it isn't an opportunity for artistic expression. A launch screen's sole function is to enhance the perception of your experience as quick to launch and immediately ready to use.

**Design a launch screen that's nearly identical to the first screen of your app or game.** If you include elements that look different when launching completes, people may experience an unpleasant flash between the launch screen and your first screen. If your app or game displays a solid color before transitioning to the first screen, create a launch screen that displays only that solid color. Also make sure your launch screen matches the device's current orientation and appearance mode.

**Avoid including text on your launch screen, even if your first screen displays text.** Because the content in a launch screen doesn't change, any text you display won't be localized.

**Don't advertise.** The launch screen isn't a branding opportunity. Avoid creating a screen that looks like a splash screen or an "About" window, and don't include logos or other branding elements unless they're a fixed part of your app's first screen.

## Platform considerations

No additional considerations for macOS or watchOS.

### iOS, iPadOS

**Launch in the appropriate orientation.** If your app or game supports both portrait and landscape modes, launch using the device's current orientation. If your interface only runs in one orientation, launch in that orientation and let people rotate the device if necessary. Ensure a landscape-only interface responds correctly, regardless of whether people enter landscape orientation by rotating the device left or right. For guidance, see Layout.

### tvOS

> **Note (Apple):** Unlike the layered images throughout much of a tvOS app, the launch screen is static.

**In a live-viewing app, consider automatically starting playback soon after people start the app.** People come to your app to watch TV, so you might want to start playing new or recently viewed live content after a few seconds of inactivity. For guidance, see Live-viewing apps.

### visionOS

**Consider launching in the Shared Space even if your app is fully immersive.** Opening a window in the Shared Space lets you provide more context about your app or game while giving it time to load, and it also lets you present a control that people can use to open your fully immersive experience. In general, people appreciate being able to choose when to transition to a Full Space, especially if they're currently running other apps in the Shared Space. For guidance, see Immersive experiences.

## Native implementation

**Related**
- Onboarding
- Loading

**Developer documentation**
- Specifying your app's launch screen — Xcode
- Responding to the launch of your app — UIKit

**Videos:** Optimizing App Launch · Love at First Launch

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**"Launch instantly... don't wait more than a couple of seconds" → this is a Core Web Vitals conversation, not a design-copy exercise.** Apple's launch-time expectation maps almost one-to-one onto Largest Contentful Paint and Time to Interactive. The web's version of "a couple of seconds" has an actual measured threshold: Google's guidance treats an LCP under 2.5 seconds as good, which lines up closely with what Apple is describing in prose. Where a native app controls its own startup path end-to-end, a web page is also at the mercy of network conditions and third-party scripts, so hitting this bar usually means more engineering discipline (critical CSS, deferred non-essential JS, image sizing) than it does for a native launch screen.

**Launch screen → the browser gives you this almost for free if you don't fight it.** A blank white flash before your app's real UI is the web equivalent of a launch screen that doesn't match the first screen — exactly what Apple's "design a launch screen nearly identical to the first screen" rule warns against. The nearest deliberate web tool is a static HTML/CSS shell (skeleton or matching background) that paints before your JS framework hydrates, plus a `theme-color` meta tag and manifest background color so the browser's own chrome doesn't clash during the gap.

**"Avoid including text on your launch screen... it won't be localized" → the same trap exists in a web app shell.** A static pre-render shell is, structurally, unlocalized content — if you bake a language-specific string into it, users whose locale differs from your default will see the wrong language for a frame or two. Keep the pre-hydration shell to layout and brand marks, exactly as Apple recommends, and let localized text arrive only once the real app renders.

**"Restore the previous state on restart" → maps directly to persisted client state and URL-addressable views.** Scroll position, form contents, and window/pane arrangement are all things a web app can restore from `sessionStorage`/`localStorage` or from the URL itself (a route with a query parameter for scroll anchor or selected item). The web has an advantage here Apple's platforms don't: a URL can encode state directly, so a shared or reloaded link can restore someone else's — or your own past — position without any client-side storage at all.

**"Don't advertise on the launch screen" → applies to the pre-hydration shell and to install prompts alike.** Don't use the earliest paint people see as a marketing surface; save persuasion for after the product has proven itself, which is the same ordering principle as Onboarding's ratings-prompt guidance.

**Where the mapping is thinner: there is no OS-enforced launch-screen contract.** iOS and tvOS display your launch screen *for* you, on a schedule the system controls, which guarantees the transition happens with system-level consistency. On the web, you are entirely responsible for building and timing your own shell — nothing forces a "first paint" to look intentional the way the OS forces an app's launch screen to appear. Sloppy web launches are the default; a deliberate shell is something you have to build.

## Do / Don't

| Do | Don't |
|---|---|
| Get to a usable first screen as fast as possible | Add artificial delay or unnecessary intro animation |
| Make a launch screen nearly identical to the first screen | Include elements that flash or change once loading completes |
| Match the device's current orientation and appearance mode | Ignore orientation or Dark Mode on the launch screen |
| Restore the previous state on restart | Force people to retrace their steps after relaunching |
| Keep the launch screen free of text and branding | Use the launch screen as a branding or "About" opportunity |
| Provide a launch screen only where the platform requires it | Add a launch screen to macOS, visionOS, or watchOS |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
