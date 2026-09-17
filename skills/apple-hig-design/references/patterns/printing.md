---
title: Printing
url: https://developer.apple.com/design/human-interface-guidelines/printing
platforms: [iOS, iPadOS, macOS, visionOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Printing

An iOS, iPadOS, macOS, or visionOS app can integrate system-provided print functionality when it makes sense, presenting custom printer- and document-specific options if necessary.

## Core guidance

### Best practices

**Make printing discoverable.** Help people find your print action by placing it in standard system locations. For example, include a Print item in your macOS app's File menu; in your iOS or iPadOS app, add a toolbar button that opens an action sheet. If your macOS app has a toolbar, you might want to put a Print button there, too, but consider making it an optional button that people can add when they customize the toolbar.

**Present a printing option only when it's possible.** If there's nothing onscreen to print, or no printers are available, dim the Print item in a macOS app's File menu and remove the Print action from the Action sheet in an iOS or iPadOS app. If you implement a custom print button, dim or hide it when printing isn't possible.

**Present relevant printing options.** If it makes sense to offer options like selecting a page range, requesting multiple copies, or printing on both sides — and the printer supports the options — use the system-provided view to present them.

## Platform considerations

No additional considerations for iOS, iPadOS, or visionOS. Not supported in tvOS or watchOS.

### macOS

**If your macOS app offers app-specific print options that the system doesn't offer, consider creating a custom category for the print panel.** By default, the print panel offers several categories of settings, such as Layout, Paper Handling, and Media & Quality. Give your custom category a unique name, such as your app name, and include options that help people have a great print experience in your app. For example, Keynote offers presentation-specific options, like the ability to print presenter notes, slide backgrounds, and skipped slides.

**If your app supports document-specific page settings, consider presenting a page setup dialog.** A page setup dialog includes rarely changed settings for page size, orientation, and scaling that apply to printing a particular document. If this makes sense in your app, avoid implementing features the system already provides. For example, you don't need to include options like changing the page orientation or printing in reverse order because the system implements these options.

**Make sure interdependencies between options are clear.** For example, if double-sided printing is available, an option to print on transparencies becomes unavailable.

**Separate advanced features from frequently used features.** Consider using a disclosure control to hide advanced options until they're needed. Label advanced options as Advanced Options.

**Consider letting people preview the effect of a setting.** For example, you could update a thumbnail image to show the effect of changing a tone control.

**Consider storing modified settings with the document.** At minimum, it makes sense to store print settings until the document is closed in case people want to print it again.

## Native implementation

**Related**
- File management
- File menu

**Developer documentation**
- `UIPrintInteractionController` — UIKit
- `NSDocument` — AppKit

**Key APIs**
- `UIPrintInteractionController` — presents the system print panel and interaction on iOS and iPadOS
- `NSDocument` — AppKit's document base class, the natural place to store per-document print settings

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**The whole system-provided print panel Apple describes has one web equivalent: `window.print()`, and it's far less controllable.** Calling `window.print()` opens the browser's own print dialog, which handles page range, copies, duplex, and paper size the same way Apple's system panel does — but a web app cannot add a custom settings category to it, cannot show a live settings preview inside it, and cannot store print settings with "the document" the way `NSDocument` can, because the dialog is entirely the browser's, not the page's. Any customization has to happen *before* the dialog opens, via CSS.

**"Make printing discoverable" → a visible print action, plus print styles that don't depend on someone finding it.** Placing a Print button in an obvious location (a toolbar, a menu) mirrors Apple's guidance directly. The web-specific half of this principle is that people also print via the browser's own menu or Ctrl/Cmd-P with no in-page action at all, so a print stylesheet (`@media print`) that produces a reasonable result unprompted matters as much as the visible button — unlike native apps, the web can't gate printing behind app-defined discoverability alone.

**"Present printing options only when possible" → the browser already suppresses the dialog when nothing can be printed**, so this specific rule mostly transfers itself: there's no printer-detection step for a web page to gate on, since the browser's dialog handles that. Where it still applies is your own print *button* — hide or disable it if the current view genuinely has nothing worth printing (an empty state, a loading screen), same reasoning as Apple's.

**Print-specific layout ("relevant printing options," page setup, custom categories) → CSS `@media print` is the whole toolkit, and it's presentational only.** You can hide non-printable chrome (`display: none` in a print stylesheet), force page breaks (`break-before`/`break-after`), and set expected margins (`@page`), but you cannot inject an app-specific settings panel into the browser's print dialog the way a macOS app can extend the print panel with a custom category. If your app needs settings like "include presenter notes" the way Keynote does, those have to be **in-page controls that regenerate the printable content** before `window.print()` is called — the customization happens upstream of the dialog, not inside it.

**Storing print settings with the document → there's no per-document print-settings persistence primitive on the web.** Apple's `NSDocument`-backed storage of print settings has no browser equivalent; if you want "remember the last print settings for this document," you build it yourself against your own storage (localStorage keyed by document ID, or a backend field), because the browser's print dialog doesn't expose its chosen settings back to the page in a way you could persist.

## Do / Don't

| Do | Don't |
|---|---|
| Put the print action in a standard, discoverable location | Bury printing somewhere people wouldn't expect to find it |
| Hide or disable the print action when there's nothing to print | Present a print action that fails once chosen |
| Offer page range, copies, and duplex options only when the printer supports them | Show settings the current printer can't act on |
| Group advanced print options behind a disclosure control | Clutter the default print view with rarely used settings |
| Store the print settings people chose with the document | Reset print settings every time the print dialog reopens |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
