---
title: Status bars
url: https://developer.apple.com/design/human-interface-guidelines/status-bars
platforms: [iOS, iPadOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Status bars

A status bar appears along the upper edge of the screen and displays information about the device's current state, like the time, cellular carrier, and battery level.

## Core guidance

### Best practices

**Obscure content under the status bar.** By default, the background of the status bar is transparent, allowing content beneath to show through. This transparency can make it difficult to see information presented in the status bar. If controls are visible behind the status bar, people may attempt to interact with them and be unable to do so. Be sure to keep the status bar readable, and don't imply that content behind it is interactive. Prefer using a scroll edge effect to place a blurred view behind the status bar.

**Consider temporarily hiding the status bar when displaying full-screen media.** A status bar can be distracting when people are paying attention to media. Temporarily hide these elements to provide a more immersive experience. The Photos app, for example, hides the status bar and other interface elements when people browse full-screen photos.

> *Image caption:* The Photos app with the status bar visible
> *Image caption:* The Photos app with the status bar hidden

**Avoid permanently hiding the status bar.** Without a status bar, people have to leave your app to check the time or see if they have a Wi-Fi connection. Let people redisplay a hidden status bar with a simple, discoverable gesture. For example, when browsing full-screen photos in the Photos app, a single tap shows the status bar again.

## Platform considerations

No additional considerations for iOS or iPadOS. Not supported in macOS, tvOS, visionOS, or watchOS.

## Native implementation

**Developer documentation**
- `UIStatusBarStyle` — UIKit
- `preferredStatusBarStyle` — UIKit

**Key APIs**
- `ScrollEdgeEffectStyle` — apply a scroll edge effect to place a blurred view behind the status bar
- `UIScrollEdgeEffect` — UIKit equivalent for the same blurred scroll-edge treatment
- `UIStatusBarStyle` — set the status bar's content style (light/dark)
- `preferredStatusBarStyle` — override the status bar style for a view controller

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance, and the browser's own status bar / address bar is chrome the page cannot draw into or control the way a native app owns its status bar — that distinction is the starting point for what does and doesn't transfer.

Two things genuinely carry over. First, a page installed as a PWA in standalone or fullscreen display mode can set `theme-color` to tint the OS status bar area, and can request `viewport-fit=cover` with `env(safe-area-inset-top)` to lay content correctly around a device's status bar or notch — the closest web equivalent of "obscure content under the status bar" is giving fixed headers a translucent, blurred background (`backdrop-filter`) so scrolling content doesn't collide with bar content, mirroring Apple's scroll-edge-effect advice. Second, "avoid permanently hiding the status bar" restates as a caution against fullscreen/standalone web experiences that remove all navigation chrome without a clear, discoverable way back to it — the underlying risk (stranding someone with no way to check basic system state or escape) is the same even though what's being hidden differs.

Everything else on this page is native chrome management with no web analogue: an ordinary browser tab never lets a page hide or restyle the browser's own status bar at all.

## Do / Don't

| Do | Don't |
|---|---|
| Use a scroll edge effect to blur content behind the status bar | Let scrolling content collide unreadably with the status bar |
| Temporarily hide the status bar for full-screen, immersive media | Permanently hide the status bar with no way to bring it back |
| Provide a simple, discoverable gesture to redisplay a hidden status bar | Force people to leave your app to check the time or connectivity |
| Keep the status bar readable in both light and dark content | Imply that content behind the status bar is interactive |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
