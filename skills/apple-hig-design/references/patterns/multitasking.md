---
title: Multitasking
url: https://developer.apple.com/design/human-interface-guidelines/multitasking
platforms: [iOS, iPadOS, macOS, tvOS, visionOS]
last_updated: 2025-06-09
---

# Multitasking

Multitasking lets people switch quickly from one app to another, performing tasks in each.

## Core guidance

People expect to use multitasking on their devices, and they may think something is wrong if your app doesn't allow it. With rare exceptions — such as some games, and Apple Vision Pro apps running in a Full Space — every app needs to work well with multitasking.

In addition to app switching, multitasking can present different experiences on different devices; see Platform considerations.

### Best practices

A great multitasking experience helps people accomplish tasks in multiple apps by managing content in a variety of simultaneous contexts. Because you don't know when people will initiate multitasking, your app or game always needs to be prepared to save and restore their context.

**Pause activities that require people's attention or active participation when they switch away.** If your app is a game or a media-viewing app, for example, make sure people don't miss anything when they switch to another app. When they switch back, let them continue as if they never left.

**Respond smoothly to audio interruptions.** Occasionally, audio from another app or the system itself may interrupt your app's audio. For example, an incoming phone call or a music playlist initiated by Siri might interrupt your app's audio. When situations like these occur, people expect your app to respond in the following ways:

- Pause audio indefinitely for primary audio interruptions, such as playing music, podcasts, or audiobooks.
- Temporarily lower the volume or pause the audio for shorter interruptions, such as GPS directional notifications, and resume the original volume or playback when the interruption ends.

For guidance, see Playing audio.

**Finish user-initiated tasks in the background.** When someone starts a task like downloading assets or processing a video file, they expect it to finish even if they switch away from your app. If your app is in the middle of performing a task that doesn't need additional input, complete it in the background before suspending.

**Use notifications sparingly.** Your app can send notifications when it's suspended or running in the background. If people start an important or time-sensitive task in your app, and then switch away from it, they might appreciate receiving a notification when the task completes so they can switch back to your app and take the next step. In contrast, people don't generally need to know the moment a routine or secondary task completes. In this scenario, avoid sending an unnecessary notification; instead, let people check on the task when they return to your app. For guidance, see Managing notifications.

## Platform considerations

Not supported in watchOS.

### iOS

On iPhone, multitasking lets people use FaceTime or watch a video in Picture in Picture while they also use a different app. The app switcher displays all currently open apps, and a current FaceTime call can continue while people use another app.

### iPadOS

On iPad, people can view and interact with the windows of several different apps at the same time. An individual app can also support multiple open windows, which lets people view and interact with more than one window in the same app at one time.

People can use iPad with either full-screen or windowed apps. When full screen, apps occupy the full screen, and people can switch between individual app windows using the app switcher.

When using windowed apps, app windows are resizable, and people can arrange them to suit their needs with behavior similar to macOS. The system provides window controls for common tiling configurations, entering full screen, minimizing, and closing windows. The system identifies the frontmost window by coloring its window controls and casting a drop shadow on windows behind it. For guidance, see Windows > iPadOS.

Additionally, videos and FaceTime calls can also play in a Picture in Picture overlay above other content regardless of whether apps are full screen or windowed.

> **Note (Apple):** Apps don't control multitasking configurations or receive any indication of the ones that people choose.

To help your app respond correctly when people open it while windowed, make sure it adapts gracefully to different screen sizes. For guidance, see Layout and Windows; for developer guidance, see Multitasking on iPad, Mac, and Apple Vision Pro. To learn more about how people use iPad multitasking features, see Use multitasking on your iPad.

### macOS

On Mac, multitasking is the default experience because people typically run more than one app at a time, switching between windows and tasks as they work. When multiple app windows are open, macOS applies drop shadows that make the windows appear layered on the desktop, and applies other visual effects to help people distinguish different window states; for guidance, see macOS window states.

### tvOS

On Apple TV, people can play or browse content while also playing movies or TV shows in Picture in Picture (where supported).

### visionOS

On Apple Vision Pro, people can run multiple apps at the same time in the Shared Space, viewing and switching between windows and volumes throughout the space.

Only one window is active at a time in the Shared Space. When people look from one window to another, the window they're currently looking at becomes active while the previous window becomes more translucent and appears to recede along the z-axis. Closing an app window in the Shared Space transitions the app to the background without quitting it.

> **Note (Apple):** When an app is the Now Playing app, closing its window automatically pauses audio playback; if people want to resume playback, they can do so in Control Center without opening the window.

**Avoid interfering with the system-provided multitasking behavior.** When people look from one window to another, visionOS applies a feathered mask to the window they look away from to clarify its changed state. To avoid interfering with this visual feedback, don't change the appearance of a window's edges.

**Don't pause a window's video playback when people look away from it.** In visionOS, as in macOS, people expect the playback they start in one window to continue while they view or perform a task in another window.

**Be prepared for situations where your audio can duck.** Unless an app is currently the Now Playing app, its audio can duck when people look away from it to another app.

## Native implementation

**Related**
- Layout
- Windows
- Playing video

**Developer documentation**
- Responding to the launch of your app — UIKit
- Multitasking on iPad, Mac, and Apple Vision Pro — UIKit

**Videos:** Elevate the design of your iPad app · Make your UIKit app more flexible

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance, and this topic is substantially platform-bound: it describes OS-level window and process management — app switchers, Picture in Picture overlays, Shared Space window states — that a browser tab does not control. Where a narrow principle does transfer, it's about how a single page behaves when it loses and regains attention, not about managing multiple apps.

**"Pause activities that require attention when people switch away" → the Page Visibility API.** A web page can detect `document.visibilityState` changing to `"hidden"` and pause a game loop, a video, or an animation accordingly, then resume on `"visible"`. This is the one piece of Apple's guidance that maps almost directly: a tab losing focus is the closest web equivalent to an app being backgrounded, and the same UX expectation — resume as if nothing happened — applies.

**"Respond smoothly to audio interruptions" → the Media Session API covers some of this, imperfectly.** A browser can be told about your media's play/pause/seek actions via `navigator.mediaSession`, which lets OS-level media keys and interruptions (an incoming call notification sound, another tab's audio) interact with your playback more gracefully. But the two-tier distinction Apple draws — indefinite pause for primary audio versus a temporary duck for short interruptions — isn't something the browser negotiates for you; if you want that behavior, you have to detect the interruption yourself (visibility changes, other-tab audio via the Audio Session-like signals aren't exposed) and implement the response.

**"Finish user-initiated tasks in the background" → the web can do this, but only within Service Worker and Background Sync limits, and never indefinitely.** A page that's fully closed cannot keep running; a long download or upload continuing after a tab loses focus is possible while the tab stays open, and a Service Worker with Background Sync can retry a deferred network task after the fact, but there's no equivalent of an OS granting your process extra background execution time the way iOS or macOS does for a suspended app.

**Multiple simultaneous windows, tiling, app switchers, Picture in Picture as an OS overlay → largely out of scope for a single web page.** A page can request Picture in Picture for a `<video>` element specifically (the Document Picture-in-Picture API extends this to arbitrary content in some browsers), which is the narrowest possible slice of what Apple describes — everything else (app switcher UI, window tiling controls, Shared Space translucency states) belongs to the browser chrome, not to the page, and no web API hands that control to page authors. State this plainly rather than stretching an analogy: multi-window and multitasking presentation is the browser's job, not the app's.

## Do / Don't

| Do | Don't |
|---|---|
| Pause attention-requiring activities when the app loses focus, and resume cleanly on return | Let a background game or video continue advancing unseen |
| Distinguish primary audio interruptions (pause indefinitely) from brief ones (duck and resume) | Treat every interruption the same way |
| Finish an in-progress user-initiated task in the background | Abandon a download or a processing task the moment focus is lost |
| Send a notification only for important or time-sensitive completions | Notify people every time a routine background task finishes |
| Adapt gracefully to windowed and resized presentations | Assume your app always has the full screen to itself |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
