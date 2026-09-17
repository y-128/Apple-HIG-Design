---
title: Sheets
url: https://developer.apple.com/design/human-interface-guidelines/sheets
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2026-03-24
---

# Sheets

A sheet helps people perform a scoped task that's closely related to their current context.

## Core guidance

A sheet is useful for requesting specific information from people or presenting a simple task that they can complete before returning to the parent view. For example, a sheet might let people supply information needed to complete an action, such as attaching a file or choosing a location to save it.

### Anatomy

In macOS, tvOS, visionOS, and watchOS, a sheet is always modal. A modal sheet presents a targeted experience that prevents people from interacting with the parent view until they dismiss the sheet.

In iOS and iPadOS, a sheet can be either modal or nonmodal. When a nonmodal sheet is onscreen, people use its functionality to affect the parent view without dismissing the sheet. For example, Notes on iPhone and iPad uses a nonmodal sheet to let people format various text selections as they edit a note.

> *Image caption:* The Notes format sheet lets people apply formatting to selected text in the editing view.
> *Image caption:* Because the sheet is nonmodal, people can make additional text selections without dismissing the sheet.

There are several common buttons that help people navigate through and dismiss sheets.

- The **Cancel** (or **Close**) button dismisses a sheet without saving any changes. This type of button is common in most sheets.
- The **Done** button dismisses a sheet after completing a task or explicitly saving changes.
- The **Back** button lets people navigate to a previous step in a multi-step flow or to a parent view in a hierarchy. It isn't intended to dismiss a sheet.

The placement of these buttons varies between platforms; see Platform considerations.

### Best practices

**For complex or prolonged user flows, consider alternatives to sheets.** For example, iOS and iPadOS offer a full-screen style of modal view that can work well to display content like videos, photos, or camera views or to help people perform multistep tasks like document or photo editing (for developer guidance, see `UIModalPresentationStyle.fullScreen`). In a macOS experience, you might want to open a new window or let people enter full-screen mode instead of using a sheet. For example, a self-contained task like editing a document tends to work well in a separate window, whereas going full screen can help people view media. In visionOS, you can give people a way to transition your app to a Full Space where they can dive into content or a task.

**Display only one sheet at a time from the main interface.** When people close a sheet, they expect to return to the parent view or window. If closing a sheet takes people back to another sheet, they can lose track of where they are in your app. If something people do within a sheet results in another sheet appearing, close the first sheet before displaying the new one. If necessary, you can display the first sheet again after people dismiss the second one.

**Use a nonmodal view when you want to present supplementary items that affect the main task in the parent view.** To give people access to information and actions they need while continuing to interact with the main window, consider using a split view in visionOS or a panel in macOS; in iOS and iPadOS, you can use a nonmodal sheet for this workflow.

**Provide an alternative to the Done button.** If you provide a Done button, always pair it with a Cancel button to give people a clear way to dismiss the sheet without confirming or saving their changes, or a Back button to move to a previous step in the sheet. Relying solely on the Done button implies that completing the task is the only way to exit the sheet, which can feel restrictive or misleading.

**Avoid showing all three buttons — Cancel, Done, and Back — together.**

## Platform considerations

No additional considerations for tvOS.

### iOS, iPadOS

In iOS and iPadOS, for sheets with a single view, the Cancel button belongs on the leading edge of the top toolbar. When present, the Done button belongs on the trailing edge.

For sheets with a multi-step flow, the placement of buttons can vary across steps: on the first step, where there isn't a Back button, the Cancel button belongs on the leading edge; when present, the Done button belongs on the trailing edge, in an inactive state to indicate that the task isn't complete yet.

**A resizable sheet expands when people scroll its contents or drag the grabber**, which is a small horizontal indicator that can appear at the top edge of a sheet. Sheets resize according to their detents, which are particular heights at which a sheet naturally rests. Designed for iPhone, the system defines two detents: **large** is the height of a fully expanded sheet and **medium** is about half of the fully expanded height. Sheets can have one or more custom detent values.

Sheets automatically support the large detent. Adding the medium detent allows the sheet to rest at both heights, whereas specifying only medium prevents the sheet from expanding to full height.

**In an iPhone app, consider supporting the medium detent to allow progressive disclosure of the sheet's content.** For example, a share sheet displays the most relevant items within the medium detent, where they're visible without resizing. To view more items, people can scroll or expand the sheet. In contrast, you might not want to support the medium detent if a sheet's content is more useful when it displays at full height. For example, the compose sheets in Messages and Mail display only at full height to give people enough room to create content.

**Include a grabber in a resizable sheet.** A grabber shows people that they can drag the sheet to resize it; they can also tap it to cycle through the detents. In addition to providing a visual indicator of resizability, a grabber also works with VoiceOver so people can resize the sheet without seeing the screen.

**Support swiping to dismiss a sheet.** People expect to swipe vertically to dismiss a sheet instead of tapping a dismiss button. If people have unsaved changes in the sheet when they begin swiping to dismiss it, use an action sheet to let them confirm their action.

**Prefer using the page or form sheet presentation styles in an iPadOS app.** Each style uses a default size for the sheet, centering its content on top of a dimmed background view and providing a consistent experience.

### macOS

In macOS, a sheet is a cardlike view with rounded corners that floats on top of its parent window. The parent window is dimmed while the sheet is onscreen, signaling that people can't interact with it until they dismiss the sheet. However, people expect to interact with other app windows before dismissing a sheet.

**Present a sheet in a reasonable default size.** People don't generally expect to resize sheets, so it's important to use a size that's appropriate for the content you display. In some cases, however, people appreciate a resizable sheet — such as when they need to expand the contents for a clearer view — so it's a good idea to support resizing.

**Let people interact with other app windows without first dismissing a sheet.** When a sheet opens, you bring its parent window to the front — if the parent window is a document window, you also bring forward its modeless document-related panels. When people want to interact with other windows in your app, make sure they can bring those windows forward even if they haven't dismissed the sheet yet.

**Use a panel instead of a sheet if people need to repeatedly provide input and observe results.** A find and replace panel, for example, might let people initiate replacements individually, so they can observe the result of each search for correctness.

### visionOS

While a sheet is visible in a visionOS app, it floats in front of its parent window, dimming it, and becoming the target of people's interactions with the app.

**Avoid displaying a sheet that emerges from the bottom edge of a window.** To help people view the sheet, prefer centering it in their field of view.

**Present a sheet in a default size that helps people retain their context.** Avoid displaying a sheet that covers most or all of its window, but consider letting people resize the sheet if they want.

### watchOS

In watchOS, a sheet is a full-screen view that slides over your app's current content. The sheet is semitransparent to help maintain the current context, but the system applies a material to the background that blurs and desaturates the covered content.

**Use a sheet only when your modal task requires a custom title or custom content presentation.** If you need to give people important information or present a set of choices, consider using an alert or action sheet.

**Keep sheet interactions brief and occasional.** Use a sheet only as a temporary interruption to the current workflow, and only to facilitate an important task. Avoid using a sheet to help people navigate your app's content.

**If you change the default label, prefer using SF Symbols to represent the action.** Avoid using a label that might mislead people into thinking that the sheet is part of a hierarchical navigation interface. Also, if the text in the top-leading corner looks like a page or app title, people won't know how to dismiss the sheet.

## Native implementation

**Related**
- Modality
- Action sheets
- Popovers
- Panels

**Developer documentation**
- `sheet(item:onDismiss:content:)` — SwiftUI
- `UISheetPresentationController` — UIKit
- `presentAsSheet(_:)` — AppKit
- `detents` — UIKit (developer guidance for sheet detents)
- `prefersGrabberVisible` — UIKit
- `UIModalPresentationStyle` — UIKit (page/form sheet styles, full screen)

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Modal sheet → `<dialog>` opened with `showModal()`.** The same modal-focus reasoning from Alerts applies: `<dialog>` gives you the backdrop, top-layer stacking, and focus trap that a modal sheet needs without hand-building them. The web's closest visual match to Apple's cardlike, rounded, floating macOS sheet is a `<dialog>` sized to content rather than the viewport, centered or offset from a trigger, with `border-radius` and a drop shadow.

**Nonmodal sheet → this is where the web genuinely lacks a clean primitive.** Apple's iOS/iPadOS nonmodal sheet lets people interact with the parent view *and* the sheet at once — Notes' formatting sheet is the example. The Popover API (`popover` attribute, `showPopover()`) is the nearest native match: it renders in the top layer without a backdrop and doesn't trap focus, so background content stays interactive. It's a reasonable substitute, but it doesn't natively support the drag-to-resize, detent-snapping behavior Apple describes — that part has no web platform equivalent and has to be built by hand with pointer events.

**Detents (large / medium) → this is a mobile-native interaction with no direct CSS equivalent.** A bottom sheet that snaps to fixed heights and responds to drag gestures is commonly built today with a scroll-snap or a JavaScript gesture library (CSS `scroll-snap-type` on a container can approximate simple two-position snapping); there's no browser-native "detents" API. If you build one, mirror Apple's semantics: support the full-height state unconditionally, treat any intermediate height as an addition, not a replacement.

**Grabber → keep the affordance, keep the accessibility path.** Apple's grabber is both a visual drag handle and a VoiceOver-operable control that cycles detents on activation — meaning the resize behavior must be reachable without a drag gesture. On the web, a decorative drag handle alone fails this; pair it with a real, keyboard- and screen-reader-operable control (a button that cycles states) so resizing isn't gesture-only.

**"Avoid showing all three buttons together" → applies unchanged.** This is an information-architecture rule, not a platform one: Cancel discards, Done confirms, Back navigates a step. Offering all three simultaneously asks the user to disambiguate three different mental models of "leaving" at once, which is exactly as confusing in a web wizard as in a native one.

**Swipe-to-dismiss → supportable, but don't make it the only path.** `<dialog>` has no built-in swipe gesture; you'd add a pointer/touch handler that closes on a downward drag past a threshold. Because swipe gestures are easy to trigger accidentally and invisible to non-touch users, always keep an explicit Cancel/Close control alongside it, exactly as Apple pairs swipe-to-dismiss with a confirming action sheet when there are unsaved changes.

## Do / Don't

| Do | Don't |
|---|---|
| Show one sheet at a time from the main interface | Chain sheets so closing one reveals another |
| Pair a Done button with Cancel or Back | Rely on Done as the only way to exit a sheet |
| Support the large detent by default on iPhone | Specify only the medium detent and block full expansion |
| Include a grabber that also works with VoiceOver | Make resizing gesture-only with no accessible control |
| Use a panel in macOS for repeated input/observe cycles | Use a sheet for a task people repeat many times in a row |
| Center a visionOS sheet in the wearer's field of view | Let a visionOS sheet emerge from the bottom edge |
| Show Cancel, Done, and Back only as the flow needs them | Display all three buttons together |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
