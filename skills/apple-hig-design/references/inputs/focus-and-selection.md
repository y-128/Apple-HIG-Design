---
title: Focus and selection
url: https://developer.apple.com/design/human-interface-guidelines/focus-and-selection
platforms: [iPadOS, macOS, tvOS, visionOS]
last_updated: 2023-10-24
---

# Focus and selection

Focus helps people visually confirm the object that their interaction targets.

## Core guidance

Focus supports simplified, component-based navigation. Using inputs like a remote, game controller, or keyboard, people bring focus to the components they want to interact with.

In many cases, focusing an item also selects it. The exception is when automatic selection might cause a distracting context shift, like opening a new view. In tvOS, for example, people use the remote to move focus from item to item as they seek the one they want, but because selecting a focused item opens or activates it, selection requires a separate gesture.

Different platforms communicate focus in different ways. For example, iPadOS and macOS show focus by drawing a ring around an item or highlighting it; tvOS generally uses the parallax effect to give the focused item an appearance of depth and liveliness. The combination of focus effects and interactions is sometimes called a **focus system** or **focus model**.

### Best practices

**Rely on system-provided focus effects.** System-defined focus effects are precisely tuned to complement interactions with Apple devices, providing experiences that feel responsive, fluid, and lifelike. Incorporating system-provided focus behaviors gives your app consistency and predictability, helping people understand it quickly. Consider creating custom focus effects only if it's absolutely necessary.

**Avoid changing focus without people's interaction.** People rely on the focus system to help them know where they are in your app. If you change focus without their interaction, people have to spend time finding the newly focused item, delaying their current task. The exception is when people are moving focus using an input device that lets them make discrete, directional movements — like a keyboard, remote, or game controller — and a previously focused item disappears. In this scenario, there are only a small number of items within one discrete step of the previously focused item, so moving focus to one of these remaining items ensures that the focus indicator is in a location people can easily find. When people aren't moving focus by using such an input device, you can't predict the item they'll target next, so it's generally best to simply hide the focus indicator when the focused object disappears.

**Be consistent with the platform as you help people bring focus to items in your app.** For example, in iPadOS and macOS, a full keyboard access mode helps people use the keyboard to reach every control, so you only need to support focus for content elements like list items, text fields, and search fields, and not for controls like buttons, sliders, and toggles. In contrast, tvOS users rely on using directional gestures on a remote or game controller (or pressing the arrow keys on an attached keyboard) to reach every onscreen element, so you need to make sure that people can bring focus to every element in your app.

**Indicate focus using visual appearances that are consistent with the platform.** For example, consider a window that contains a list of items. In iPadOS and macOS, the system draws focused list items using white text and a background highlight that matches the app's accent color, drawing unfocused items using the standard text color and a gray background highlight.

**In general, use a focus ring for a text or search field, but use a highlight in a list or collection.** Although you can use a focus ring to draw attention to an item that fills a cell, like a photo, it's usually easier for people to view lists and collections when an entire row is highlighted.

## Platform considerations

Not supported in iOS or watchOS.

### iPadOS

iPadOS 15 and later defines a focus system that supports keyboard interactions for navigating text fields, text views, and sidebars, in addition to various types of collection views and other custom views in your app.

The iPadOS and tvOS focus systems are similar. People perform actions by moving a focus indicator to an item and then selecting it. Although the underlying system is the same, the user experiences are a little different. tvOS uses **directional focus**, which means people can use the same interaction — that is, swiping the Siri Remote or using only the arrow keys on a connected keyboard — to navigate to every onscreen component. In contrast, iPadOS defines **focus groups**, which represent specific areas within an app, like a sidebar, grid, or list. Using focus groups, iPadOS can support two different keyboard interactions:

- Pressing the Tab key moves focus among focus groups, letting people navigate to sidebars, grids, and other app areas.
- Pressing an arrow key supports a directional focus interaction that's similar to tvOS, but limited to navigation among items in the same focus group. For example, people can use an arrow key to move through the items in a list or a sidebar.

Onscreen components can indicate focus by using the **halo effect** or the **highlighted appearance**.

The halo focus effect — also known as the **focus ring** — displays a customizable outline around the component. You can apply the halo effect to custom views and to fully opaque content within a collection or list cell, such as an image.

**Customize the halo focus effect when necessary.** By default, the system uses an item's shape to infer the shape of its halo. If the system-provided halo doesn't give you the appearance you want, you can refine it to match contours like rounded corners or shapes defined by Bézier paths. You can also adjust a halo's position if another component occludes or clips it. For example, you might need to ensure that a badge appears above the halo or that a parent view doesn't clip it.

The highlighted appearance — in which the component's text uses the app's accent color — also indicates focus, but **it's not a focus effect**. The highlight appearance occurs automatically when people select a collection view cell on which you've set content configurations.

**Ensure that focus moves through your custom views in ways that make sense.** As people continue pressing the Tab key, focus moves through focus groups in reading order: leading to trailing, and top to bottom. Although focus moves through system-provided views in ways that people expect, you might need to adjust the order in which the focus system visits your custom views. For example, if you want focus to move down through a vertical stack of custom views before it moves in the trailing direction to the next view, you need to identify the stack container as a single focus group.

**Adjust the priority of an item to reflect its importance within a focus group.** When a group receives focus, its primary item automatically receives focus too, making it easy for people to select the item they're most likely to want. You can make an item primary by increasing its priority.

### tvOS

**In a full-screen experience, let people use gestures to interact with the content, not to move focus.** When an item displays in full screen, it doesn't show focus, so people naturally assume that their gestures will affect the object, and not its focus state.

**Avoid displaying a pointer.** People expect to navigate a fixed number of items by changing focus, not by trying to drag a tiny pointer around a huge screen. While free-form movement might make sense during gameplay, such as when looking for a hidden object or flying a plane, use the focus model when people navigate menus and other interface elements. If your app requires a pointer, make sure it's highly visible and feels integrated with your experience.

**Design your interface to accommodate components in various focus states.** In tvOS, focusable items can have up to five different states, each of which is visually distinct. Because focusing an item often increases its scale, you need to supply assets for the larger, focused size to ensure they always look sharp, and you need to make sure the larger item doesn't crowd the surrounding interface.

| State | Description |
|---|---|
| Unfocused | The viewer hasn't brought focus to the item. Unfocused items appear less prominent than focused items. |
| Focused | The viewer brings focus to the item. A focused item visually stands out from the other onscreen content through elevation to the foreground, illumination, and animation. |
| Selecting | The viewer chooses the focused item. A focused item provides instant visual feedback when people choose it. For example, a button might briefly invert its colors and animate before it transitions to its selected appearance. |
| Selected | The viewer has chosen or activated the item in some way. For example, a heart-shaped button that people can use to favorite a photo might appear filled in the selected state and empty in the deselected state. |
| Unavailable | The viewer can't bring focus to the item or choose it. An unavailable item appears inactive. |

### visionOS

visionOS supports the same focus system as in iPadOS and tvOS, letting people use a connected input device like a keyboard or game controller to interact with apps and the system.

> **Note (Apple):** When people look at a virtual object to identify it as the object they want to interact with, the system uses the hover effect, not a focus effect, to provide visual feedback (for guidance, see Eyes). The hover effect isn't related to the focus system.

## Native implementation

**Related**
- Eyes
- Keyboards

**Developer documentation**
- Focus Attributes — TVML
- Focus-based navigation — UIKit
- About focus interactions for Apple TV — UIKit
- `UIFocusHaloEffect`
- `UICollectionView` / `NSTableView`
- `UICollectionViewCell`
- `focusGroupIdentifier`
- `UIFocusGroupPriority`

**Videos:** Design for spatial input · Design for spatial user interfaces · Design for the iPadOS pointer

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**"Rely on system-provided focus effects" → don't remove the browser's default `:focus` outline.** Apple's platforms tune focus rings at the system level so every app inherits a consistent, well-tested appearance. The web's nearest equivalent is the user-agent default focus outline, which browsers have already invested in making visible and legible. Stripping it with `outline: none` for aesthetic reasons throws away exactly what Apple is telling native developers to lean on, and it is the single most common accessibility regression on the web. If a custom focus style is genuinely needed, it should look at least as visible as the native ring, not less.

**"Avoid changing focus without people's interaction" → don't move DOM focus programmatically without a clear input-driven reason.** Apple's exception — that focus may legitimately jump when a previously focused item disappears during discrete keyboard/remote navigation — maps to a narrow, well-understood web pattern: moving focus to the next logical element when the currently focused one is removed from the DOM (e.g., after deleting a list row, focus the next row or a sensible fallback), never moving focus on a timer, a background data refresh, or any event the user didn't directly cause.

**Focus ring versus highlight, by content type → this is where `:focus-visible` earns its keep.** Apple's distinction — a ring for a text or search field, a full-row highlight for a list or collection — has a rough web equivalent in choosing between an outline-style focus indicator (form inputs) and a background/color change (list items, menu items, table rows), matched to what reads clearly for that content shape. `:focus-visible` (as opposed to plain `:focus`) is the mechanism that lets a site show this indicator specifically for keyboard/switch input while suppressing it on mouse click, which is close in spirit to Apple's platform-level split between focus (keyboard/remote-driven) and simple pointer hover — though the web's version is a CSS heuristic guessing at input modality, not a first-class system concept the way Apple's focus model is.

**Focus versus selection as distinct concepts → this is the idea most worth carrying over deliberately.** Apple's core insight — that focusing an item and selecting/activating it are two different events, conflated only when doing so is safe — corrects a common web mistake, where `mouseover`/`:hover` handlers are wired to fire the same logic as `click`, or focus and click handlers are treated as interchangeable. ARIA's distinction between `aria-selected` (a value chosen within a set, as in a listbox or tab) and DOM focus (where keyboard input currently goes) is the structural equivalent, and getting it right is what makes composite widgets like listboxes, comboboxes, and tab panels operable by keyboard at all.

**tvOS directional focus and focus groups, halo effect, five-state focus model → largely platform-specific, but Tab order transfers.** The specific mechanics — a remote-driven parallax focus system, the halo effect's Bézier-path customization, and tvOS's five distinct visual focus states — depend on spatial navigation hardware the web doesn't have. What does transfer directly is the underlying idea behind iPadOS's "focus moves through focus groups in reading order, leading to trailing, top to bottom": DOM order should already reflect visual/reading order, so that natural Tab order needs no `tabindex` overrides. `tabindex="-1"` and roving `tabindex` patterns (as used in ARIA composite widgets) are the web's version of Apple's "identify the stack container as a single focus group" — grouping a set of related controls so Tab enters and exits the group once, while arrow keys move within it.

**visionOS hover-effect-versus-focus-effect distinction → conceptually close to CSS `:hover` versus `:focus-visible`, but the underlying input differs entirely.** Apple's note that gaze-driven hover is unrelated to the keyboard-driven focus system is a genuinely useful mental model — "the thing you're looking at" and "the thing that receives your next keystroke" are different questions — but the web has no gaze input to speak of, so this maps only at the level of the general principle, not the mechanism.

## Do / Don't

| Do | Don't |
|---|---|
| Rely on system-provided focus effects | Build custom focus effects unless absolutely necessary |
| Move focus only in response to direct user interaction | Change focus silently in the background |
| Use a focus ring for text/search fields, a highlight for list/collection rows | Use the same focus treatment for every content type regardless of shape |
| Treat focusing and selecting as distinct unless combining them is safe | Auto-select on focus when it would cause a distracting context shift |
| Support focus for every onscreen element in tvOS | Leave any onscreen element unreachable by directional focus in tvOS |
| Supply larger, sharp assets for a focused item's increased scale | Let a focused item's enlarged size crowd the surrounding interface |
| Avoid displaying a free-form pointer in tvOS menu navigation | Make people drag a tiny pointer around a large screen to navigate menus |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
