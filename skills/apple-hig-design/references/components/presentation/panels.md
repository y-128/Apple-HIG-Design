---
title: Panels
url: https://developer.apple.com/design/human-interface-guidelines/panels
platforms: [macOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Panels

In a macOS app, a panel typically floats above other open windows providing supplementary controls, options, or information related to the active window or current selection.

## Core guidance

In general, a panel has a less prominent appearance than an app's main window. When the situation calls for it, a panel can also use a dark, translucent style to support a heads-up display (or HUD) experience.

When your app runs in other platforms, consider using a modal view to present supplementary content that's relevant to the current task or selection.

### Best practices

**Use a panel to give people quick access to important controls or information related to the content they're working with.** For example, you might use a panel to provide controls or settings that affect the selected item in the active document or window.

**Consider using a panel to present inspector functionality.** An inspector displays the details of the currently selected item, automatically updating its contents when the item changes or when people select a new item. In contrast, if you need to present an Info window — which always maintains the same contents, even when the selected item changes — use a regular window, not a panel. Depending on the layout of your app, you might also consider using a split view pane to present an inspector.

**Prefer simple adjustment controls in a panel.** As much as possible, avoid including controls that require typing text or selecting items to act upon because these actions can require multiple steps. Instead, consider using controls like sliders and steppers because these components can give people more direct control.

**Write a brief title that describes the panel's purpose.** Because a panel often floats above other open windows in your app, it needs a title bar so people can position it where they want. Create a short title using a noun — or a noun phrase with title-style capitalization — that can help people recognize the panel onscreen. For example, macOS provides familiar panels titled "Fonts" and "Colors," and many apps use the title "Inspector."

**Show and hide panels appropriately.** When your app becomes active, bring all of its open panels to the front, regardless of which window was active when the panel opened. When your app is inactive, hide all of its panels.

**Avoid including panels in the Window menu's documents list.** It's fine to include commands for showing or hiding panels in the Window menu, but panels aren't documents or standard app windows, and they don't belong in the Window menu's list.

**In general, avoid making a panel's minimize button available.** People don't usually need to minimize a panel, because it displays only when needed and disappears when the app is inactive.

**Refer to panels by title in your interface and in help documentation.** In menus, use the panel's title without including the term panel: for example, "Show Fonts," "Show Colors," and "Show Inspector." In help documentation, it can be confusing to introduce "panel" as a different type of window, so it's generally best to refer to a panel by its title or — when it adds clarity — by appending "window" to the title. For example, the title "Inspector" often supplies enough context to stand on its own, whereas it can be clearer to use "Fonts window" and "Colors window" instead of just "Fonts" and "Colors."

### HUD-style panels

A HUD-style panel serves the same function as a standard panel, but its appearance is darker and translucent. HUDs work well in apps that present highly visual content or that provide an immersive experience, such as media editing or a full-screen slide show. For example, QuickTime Player uses a HUD to display inspector information without obstructing too much content.

**Prefer standard panels.** People can be distracted or confused by a HUD when there's no logical reason for its presence. Also, a HUD might not match the current appearance setting. In general, use a HUD only:

- In a media-oriented app that presents movies, photos, or slides
- When a standard panel would obscure essential content
- When you don't need to include controls — with the exception of the disclosure triangle, most system-provided controls don't match a HUD's appearance

**Maintain one panel style when your app switches modes.** For example, if you use a HUD when your app is in full-screen mode, prefer maintaining the HUD style when people take your app out of full-screen mode.

**Use color sparingly in HUDs.** Too much color in the dark appearance of a HUD can be distracting. Often, you need only small amounts of high-contrast color to highlight important information in a HUD.

**Keep HUDs small.** HUDs are designed to be unobtrusively useful, so letting them grow too large defeats their primary purpose. Don't let a HUD obscure the content it adjusts, and make sure it doesn't compete with the content for people's attention.

## Platform considerations

Not supported in iOS, iPadOS, tvOS, visionOS, or watchOS. This guidance applies to macOS only.

## Native implementation

**Related**
- Windows
- Modality

**Developer documentation**
- `NSPanel` — AppKit
- `hudWindow` — AppKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Panel → a floating, non-modal auxiliary panel component, built by hand.** Nothing in the web platform models "a lightweight window that floats above the document, stays out of the way, and shows or hides with the parent's activation state" — this is a desktop multi-window concept, and the web's execution context is a single document, not a set of coordinated OS-level windows. The nearest approximable pattern is a `position: fixed` panel using the Popover API's non-auto (`manual`) mode for top-layer stacking without light-dismiss, since a panel — unlike a popover — should not vanish on outside click.

**Inspector pattern → maps more naturally as a persistent sidebar than as a floating panel.** Apple's inspector idea (contents follow the current selection) is a UI pattern the web already handles well without needing a floating window: a docked side panel that re-renders on selection change. Skip the floating-window part of the metaphor unless your app genuinely needs multiple independent, movable inspector surfaces — in a browser tab, that adds real complexity (z-index management, drag bounds, focus order) for a benefit desktop users get for free from the OS window manager.

**Show/hide tied to app activation → has no equivalent, because the web has no "app-inactive" state.** A browser tab is either visible/focused or it isn't; there's no analogue to "another native app became frontmost, so hide my panels." The closest available signal is the Page Visibility API (`document.visibilityState`), which tells you the tab itself lost visibility — not that some other panel-owning context took focus. Don't try to replicate this behavior faithfully; it doesn't have a home on the web.

**HUD styling → pure visual language, transfers as CSS.** "Dark, translucent, minimal controls" is just a color and material choice — a low-opacity dark background with `backdrop-filter: blur()` reproduces the look. The *judgment* behind it (use sparingly, only for media-heavy contexts, keep small) is content-agnostic advice that applies to any web overlay just as much as to a native HUD: a translucent dark overlay is a stronger visual statement than a standard panel, so reserve it for genuinely visual, chrome-light contexts rather than defaulting to it.

**Title-bar-as-drag-handle → replicable, but is a bespoke build.** A panel's title bar in macOS is both a label and the surface you drag to reposition the panel. On the web this means pairing a labelled header element with pointer-event-based drag logic; there's no native "draggable window chrome" primitive to lean on, unlike `<dialog>` or the Popover API for the modal/nonmodal cases elsewhere in this component family.

## Do / Don't

| Do | Don't |
|---|---|
| Use a panel for controls tied to the active selection | Use a panel for content unrelated to the current context |
| Give a panel a short, noun-based title | Title a panel with a full sentence or vague label |
| Bring all panels forward when the app activates | Leave panels visible when the app is inactive |
| Prefer sliders and steppers over text entry in a panel | Require multi-step text entry for simple adjustments |
| Reserve HUD styling for media-heavy, immersive contexts | Use a HUD by default with no logical reason for it |
| Keep a HUD small and out of the way | Let a HUD grow large enough to obscure the content it adjusts |
| Refer to panels by their title, not "panel," in UI text | Introduce "panel" as a separate window concept in help docs |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
