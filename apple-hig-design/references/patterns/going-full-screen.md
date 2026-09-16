---
title: Going full screen
url: https://developer.apple.com/design/human-interface-guidelines/going-full-screen
platforms: [iOS, iPadOS, macOS]
last_updated: 2025-06-09
---

# Going full screen

iPhone, iPad, and Mac offer full-screen modes that let people expand a window to fill the screen, hiding system controls and providing a distraction-free environment.

## Core guidance

Apple TV and Apple Watch don't offer full-screen modes because apps and games already fill the screen by default. Apple Vision Pro doesn't offer a full-screen mode because people can expand a window to fill more of their view or use the Digital Crown to hide passthrough and transition to a more immersive experience (for guidance, see Immersive experiences).

### Best practices

**Support full-screen mode when it makes sense for your experience.** People appreciate full-screen mode when they want to concentrate on a task or be immersed in content. Consider offering a full-screen mode if your experience lets people play a game; view media like videos or photo slideshows; or perform an in-depth task that benefits from a distraction-free environment.

**If necessary, adjust your layout in full-screen mode, but don't programmatically resize your window.** When a window is larger in full-screen mode than in non-full-screen mode, you want to keep essential content prominent while making good use of the extra space. For example, it might make sense to adjust the proportions of your interface without changing which items appear. If you make such adjustments, be sure they're subtle enough to maintain a consistent interface and avoid causing visually jarring transitions between modes.

**Continue to provide access to essential features and controls so people can complete their task without exiting full-screen mode.** For example, a full-screen media experience needs to make playback controls persistently available or easy to reveal when people need them.

**Except in games, let people reveal the Dock while your iPadOS or macOS app is in full-screen mode.** In iPadOS and macOS, it's important to preserve access to the Dock so people can quickly open other apps and Dock items. To help prevent people from accidentally revealing the Dock while they're playing your full-screen game, you can ask iPadOS to ignore an initial swipe up from the screen's bottom edge or hide the Dock entirely in macOS. For developer guidance, see `preferredScreenEdgesDeferringSystemGestures` (SwiftUI), `preferredScreenEdgesDeferringSystemGestures` (UIKit), and `hideDock` (AppKit).

**After people switch away from your full-screen experience, help them resume where they left off when they return.** For example, a game or a slideshow needs to pause automatically when people leave the experience so they don't miss anything.

**Let people choose when to exit full-screen mode.** People generally don't expect full-screen mode to end automatically when they switch to a different experience or finish an absorbing activity, like playing a game or viewing a movie.

**Prioritize content by temporarily hiding toolbars and navigation controls.** You can offer a distraction-free environment by hiding elements when content is the primary focus, such as when viewing full-screen photos or reading a document. If you implement such behavior, let people restore the hidden elements with a familiar gesture or action like tapping, swiping down, or moving the cursor to the top of the screen. Be sure to keep controls visible when they're essential for navigation or performing tasks. Although a visionOS window can hide its toolbars or navigation controls, people generally expect different types of immersive experiences while wearing Apple Vision Pro; for guidance, see Immersive experiences.

## Platform considerations

Not supported in tvOS, visionOS, or watchOS.

### iOS, iPadOS

**Consider deferring system gestures to prevent accidental exits in a full-screen app or game.** By default, the Home Screen indicator automatically hides shortly after someone switches to your app or game. It reappears when someone interacts with the bottom portion of the screen, allowing them to swipe once to exit. Whenever possible, retain this behavior because it's familiar and what people expect. If supporting this results in unexpected exits, you can enable two swipes rather than one to exit. For developer guidance, see `preferredScreenEdgesDeferringSystemGestures`.

### macOS

**Use the system-provided full-screen experience.** Using the system's full-screen support ensures that your full-screen window works well in all contexts. For example, some Mac models include a camera housing that occupies an area at the top-center of the screen. Using the system's full-screen support automatically accommodates this area. For developer guidance, see `toggleFullScreen(_:)`.

**In a game, don't change the display mode when players go full screen.** People expect to be in control of their display mode, and changing it automatically doesn't improve performance.

For additional developer guidance, see Managing your game window for Metal in macOS.

**Always let people choose when to enter full-screen mode.** Prefer letting people use your window's Enter Full Screen button, View menu item, or the Control-Command-F keyboard shortcut. Avoid offering a custom menu of window modes. In a game, you might also provide a custom toggle that turns full-screen mode on and off.

## Native implementation

**Related**
- Layout
- Multitasking
- Windows
- The menu bar

**Developer documentation**
- `fullScreenCover(item:onDismiss:content:)` — SwiftUI
- `NSScreen` — AppKit
- `NSWindow.CollectionBehavior` — AppKit
- Managing your game window for Metal in macOS — Swift, Objective-C

**Key APIs**
- `preferredScreenEdgesDeferringSystemGestures` — SwiftUI/UIKit, defers system gesture recognition at screen edges
- `hideDock` — AppKit, hides the Dock entirely while in full-screen mode
- `toggleFullScreen(_:)` — AppKit, invokes the system-provided full-screen transition
- `NSWindow.CollectionBehavior` — AppKit, declares a window's full-screen participation

**Videos:** Elevate the design of your iPad app

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web where a genuine analogue exists; several parts of this topic are OS-window-management concerns with no web equivalent, and are called out as such below.

**Full-screen mode itself → the Fullscreen API, with one structural difference from Apple's model.** `element.requestFullscreen()` and the `fullscreenchange` event give a page the same category of experience Apple describes: content expands to fill the display, hiding browser chrome. The difference is who initiates it — Apple's window-level full screen is triggered by the person (a button, a shortcut, a system gesture), and the Fullscreen API requires a user gesture too, so that expectation transfers cleanly. What doesn't transfer is persistence across navigation: a full-screen web page drops out of full screen on most browser-level events (a new tab, an alert, in some cases a permission prompt) that wouldn't touch a native full-screen window at all, so treat full screen as more fragile on the web than Apple's guidance assumes.

**"Adjust your layout, don't programmatically resize your window" → the analogous rule for the web is to reflow content, not resize the browser window.** A web page cannot resize its own browser window in full screen (nor should it try — `window.resizeTo` is heavily restricted and ignored in most contexts anyway). The transferable instruction is Apple's underlying one: use the extra screen real estate by adjusting proportions and information density, not by fundamentally rearranging what's present, so the transition in and out of full screen doesn't feel like loading a different page.

**"Let people choose when to exit" → don't force an exit from full screen for reasons unrelated to their action.** The Fullscreen API already respects this in one direction (nothing forces the *browser* out without a user or browser-security event), but app-level code should mirror the same restraint Apple describes — don't script an automatic `document.exitFullscreen()` on a timer or on an unrelated state change, since people expect fullscreen to persist until they choose to leave it.

**"Prioritize content by temporarily hiding toolbars and navigation" → this maps directly and is common web practice already.** Auto-hiding a video player's controls after a period of inactivity, or hiding a reading view's chrome until the pointer moves to the top of the viewport, is the same UX contract Apple describes for native full-screen apps, and the implementation (a mousemove/touchstart listener resetting a hide timer) is straightforward and already widely adopted on video sites and reading apps.

**Preserving access to the Dock, deferring system edge gestures, avoiding display-mode changes in games → no web equivalent.** These are OS-level window-manager concerns (macOS's Dock, iPadOS's Home Screen indicator, a game changing display resolution) that a web page has no access to and no comparable surface for. State this plainly: a browser tab in full screen doesn't participate in a Dock or an OS gesture-deferral system at all, so there's nothing to translate here beyond the general Fullscreen API exit path (typically Escape), which the browser — not the page — controls.

## Do / Don't

| Do | Don't |
|---|---|
| Offer full screen for immersive tasks: games, media, focused reading | Force full screen on people who haven't asked for it |
| Adjust proportions and density to use extra space well | Programmatically resize the window, or make full screen feel like a different app |
| Keep essential controls reachable, even if hidden until needed | Remove access to features people need mid-task |
| Let people exit full screen on their own initiative | End full-screen mode automatically when it isn't the person's choice |
| Pause and let people resume where they left off after switching away | Let a slideshow or game silently advance while unattended |
| Use the system's full-screen transition on macOS | Build a custom full-screen mode when the system-provided one would do |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
