---
title: Buttons
url: https://developer.apple.com/design/human-interface-guidelines/buttons
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2025-12-16
---

# Buttons

A button initiates an instantaneous action.

## Core guidance

Versatile and highly customizable, buttons give people simple, familiar ways to do tasks in your app. In general, a button combines three attributes to clearly communicate its function:

- **Style.** A visual style based on size, color, and shape.
- **Content.** A symbol (or icon), text label, or both that a button displays to convey its purpose.
- **Role.** A system-defined role that identifies a button's semantic meaning and can affect its appearance.

There are also many button-like components that have distinct appearances and behaviors for specific use cases, like toggles, pop-up buttons, and segmented controls.

### Best practices

When buttons are instantly recognizable and easy to understand, an app tends to feel intuitive and well designed.

**Make buttons easy for people to use.** It's essential to include enough space around a button so that people can visually distinguish it from surrounding components and content. Giving a button enough space is also critical for helping people select or activate it, regardless of the method of input they use. As a general rule, a button needs a **hit region of at least 44x44 pt** — in **visionOS, 60x60 pt** — to ensure that people can select it easily, whether they use a fingertip, a pointer, their eyes, or a remote.

**Always include a press state for a custom button.** Without a press state, a button can feel unresponsive, making people wonder if it's accepting their input.

### Style

System buttons offer a range of styles that support customization while providing built-in interaction states, accessibility support, and appearance adaptation. Different platforms define different styles that help you communicate hierarchies of actions in your app.

**In general, use a button that has a prominent visual style for the most likely action in a view.** To draw people's attention to a specific button, use a prominent button style so the system can apply an accent color to the button's background. Buttons that use color tend to be the most visually distinctive, helping people quickly identify the actions they're most likely to use. **Keep the number of prominent buttons to one or two per view.** Presenting too many prominent buttons increases cognitive load, requiring people to spend more time considering options before making a choice.

**Use style — not size — to visually distinguish the preferred choice among multiple options.** When you use buttons of the same size to offer two or more options, you signal that the options form a coherent set of choices. By contrast, placing two buttons of different sizes near each other can make the interface look confusing and inconsistent. If you want to highlight the preferred or most likely option in a set, use a more prominent button style for that option and a less prominent style for the remaining ones.

**Avoid applying a similar color to button labels and content layer backgrounds.** If your app already has bright, colorful content in the content layer, prefer using the default monochromatic appearance of button labels. For more guidance, see Liquid Glass color.

### Content

Ensure that each button clearly communicates its purpose. Depending on the platform, a button can contain a symbol (or icon), a text label, or both to help people understand what it does.

> **Note (Apple):** In macOS and visionOS, the system displays a tooltip after people hover over a button for a moment. A tooltip displays a brief phrase that explains what a button does; for guidance, see Offering help.

**Try to associate familiar actions with familiar icons.** For example, people can predict that a button containing the `square.and.arrow.up` symbol will help them perform share-related activities. If it makes sense to use an icon in your button, consider using an existing or customized symbol. For a list of symbols that represent common actions, see Standard icons.

**Consider using text when a short label communicates more clearly than an icon.** To use text, write a few words that succinctly describe what the button does. Using title-style capitalization, consider starting the label with a verb to help convey the button's action — for example, a button that lets people add items to their shopping cart might use the label "Add to Cart."

### Role

A system button can have one of the following roles:

- **Normal.** No specific meaning.
- **Primary.** The button is the default button — the button people are most likely to choose.
- **Cancel.** The button cancels the current action.
- **Destructive.** The button performs an action that can result in data destruction.

A button's role can have additional effects on its appearance. For example, a primary button uses an app's accent color, whereas a destructive button uses the system red color.

**Assign the primary role to the button people are most likely to choose.** When a primary button responds to the Return key, it makes it easy for people to quickly confirm their choice. In addition, when the button is in a temporary view — like a sheet, an editable view, or an alert — assigning it the primary role means that the view can automatically close when people press Return.

**Don't assign the primary role to a button that performs a destructive action, even if that action is the most likely choice.** Because of its visual prominence, people sometimes choose a primary button without reading it first. Help people avoid losing content by assigning the primary role to nondestructive buttons.

## Platform considerations

No additional considerations for tvOS.

### iOS, iPadOS

**Configure a button to display an activity indicator when you need to provide feedback about an action that doesn't instantly complete.** Displaying an activity indicator within a button can save space in your user interface while clearly communicating the reason for the delay. To help clarify what's happening, you can also configure the button to display a different label alongside the activity indicator. For example, the label "Checkout" could change to "Checking out…" while the activity indicator is visible. When a delay occurs after people click or tap your configured button, the system displays the activity indicator next to the original or alternative label, hiding the button image, if there is one.

### macOS

Several specific button types are unique to macOS.

**Push buttons.** The standard button type in macOS is known as a push button. You can configure a push button to display text, a symbol, an icon, or an image, or a combination of text and image content. Push buttons can act as the default button in a view and you can tint them.

- **Use a flexible-height push button only when you need to display tall or variable height content.** Flexible-height buttons support the same configurations as regular push buttons — and they use the same corner radius and content padding — so they look consistent with other buttons in your interface. If you need to present a button that contains two lines of text or a tall icon, use a flexible-height button; otherwise, use a standard push button. For developer guidance, see `NSButton.BezelStyle.flexiblePush`.
- **Append a trailing ellipsis to the title when a push button opens another window, view, or app.** Throughout the system, an ellipsis in a control title signals that people can provide additional input. For example, the Edit buttons in the AutoFill pane of Safari Settings include ellipses because they open other views that let people modify autofill values.
- **Consider supporting spring loading.** On systems with a Magic Trackpad, spring loading lets people activate a button by dragging selected items over it and force clicking — that is, pressing harder — without dropping the selected items. After force clicking, people can continue dragging the items, possibly to perform additional actions.

**Square buttons.** A square button (also known as a gradient button) initiates an action related to a view, like adding or removing rows in a table. Square buttons contain symbols or icons — not text — and you can configure them to behave like push buttons, toggles, or pop-up buttons. The buttons appear in close proximity to their associated view — usually within or beneath it — so people know which view the buttons affect.

- **Use square buttons in a view, not in the window frame.** Square buttons aren't intended for use in toolbars or status bars. If you need a button in a toolbar, use a toolbar item.
- **Prefer using a symbol in a square button.** SF Symbols provides a wide range of symbols that automatically receive appropriate coloring in their default state and in response to user interaction.
- **Avoid using labels to introduce square buttons.** Because square buttons are closely connected with a specific view, their purpose is generally clear without the need for descriptive text.
- For developer guidance, see `NSButton.BezelStyle.smallSquare`.

**Help buttons.** A help button appears within a view and opens app-specific help documentation. Help buttons are circular, consistently sized buttons that contain a question mark. For guidance on creating help documentation, see Offering help.

- **Use the system-provided help button to display your help documentation.** People are familiar with the appearance of the standard help button and know that choosing it opens help content.
- **When possible, open the help topic that's related to the current context.** For example, the help button in the Rules pane of Mail settings opens the Mail User Guide to a help topic that explains how to change these settings. If no specific help topic applies directly to the current context, open the top level of your app's help documentation when people choose a help button.
- **Include no more than one help button per window.** Multiple help buttons in the same context make it hard for people to predict the result of clicking one.
- **Position help buttons where people expect to find them.** Use the following locations for guidance.

| View style | Help button location |
|---|---|
| Dialog with dismissal buttons (like OK and Cancel) | Lower corner, opposite to the dismissal buttons and vertically aligned with them |
| Dialog without dismissal buttons | Lower-left or lower-right corner |
| Settings window or pane | Lower-left or lower-right corner |

- **Use a help button within a view, not in the window frame.** For example, avoid placing a help button in a toolbar or status bar.
- **Avoid displaying text that introduces a help button.** People know what a help button does, so they don't need additional descriptive text.

**Image buttons.** An image button appears in a view and displays an image, symbol, or icon. You can configure an image button to behave like a push button, toggle, or pop-up button.

- **Use an image button in a view, not in the window frame.** For example, avoid placing an image button in a toolbar or status bar. If you need to use an image as a button in a toolbar, use a toolbar item. See Toolbars.
- **Include about 10 pixels of padding between the edges of the image and the button edges.** An image button's edges define its clickable area even when they aren't visible. Including padding ensures that a click registers correctly even if it's not precisely within the image. In general, avoid including a system-provided border in an image button; for developer guidance, see `isBordered`.
- **If you need to include a label, position it below the image button.** For related guidance, see Labels.

### visionOS

A visionOS button typically includes a visible background that can help people see it, and the button plays sound to provide feedback when people interact with it.

There are three standard button shapes in visionOS. Typically, an icon-only button uses a circle shape, a text-only button uses a `roundedRectangle` or `capsule` shape, and a button that includes both an icon and text uses the capsule shape.

visionOS buttons use different visual styles to communicate four different interaction states: **Idle, Hover, Selected, Unavailable.**

> **Note (Apple):** In visionOS, buttons don't support custom hover effects.

In addition to the four states, a button can also reveal a tooltip when people look at it for a brief time. In general, buttons that contain text don't need to display a tooltip because the button's descriptive label communicates what it does.

**Button sizes in visionOS:**

| Shape | Mini | Small | Regular | Large | Extra large |
|---|---|---|---|---|---|
| Circular | 28 pt | 32 pt | 44 pt | 52 pt | 64 pt |
| Capsule (text only) | 28 pt | 32 pt | 44 pt | 52 pt | 64 pt |
| Capsule (text and icon) | 28 pt | 32 pt | 44 pt | 52 pt | 64 pt |
| Rounded rectangle | 28 pt | 32 pt | 44 pt | 52 pt | 64 pt |

> **Source limitation:** Apple presents these sizes as a matrix (Shape × Mini/Small/Regular/Large/Extra large) with visual shape swatches in each cell rather than repeated numeric values. The PDF capture preserves only the column headers (Mini 28 pt, Small 32 pt, Regular 44 pt, Large 52 pt, Extra large 64 pt) and the row labels (Circular, Capsule (text only), Capsule (text and icon), Rounded rectangle); it does not indicate any per-shape numeric variation. The table above applies the shared size scale to every shape, which is the most defensible reading of the source, but if any shape uses a different pt value at a given size, that distinction did not survive the PDF capture.

**Prefer buttons that have a discernible background shape and fill.** It tends to be easier for people to see a button when it's enclosed in a shape that uses a contrasting background fill. The exception is a button in a toolbar, context menu, alert, or ornament where the shape and material of the larger component make the button comfortably visible. The following guidelines can help you ensure that a button looks good in different contexts:

- When a button appears on top of a glass window, use the thin material as the button's background.
- When a button appears floating in space, use the glass material for its background.

**Avoid creating a custom button that uses a white background fill and black text or icons.** The system reserves this visual style to convey the toggled state.

**In general, prefer circular or capsule-shape buttons.** People's eyes tend to be drawn toward the corners in a shape, making it difficult to keep looking at the shape's center. The more rounded a button's shape, the easier it is for people to look steadily at it. When you need to display a button by itself, prefer a capsule-shape button.

**Provide enough space around a button to make it easy for people to look at it.** Aim to place buttons so their centers are always **at least 60 pts apart**. If your buttons measure **60 pts or larger, add 4 pts of padding** around them to keep the hover effect from overlapping. Also, it's usually best to avoid displaying small or mini buttons in a vertical stack or horizontal row.

**Choose the right shape if you need to display text-labeled buttons in a stack or row.** Specifically, prefer the rounded-rectangle shape in a vertical stack of buttons and prefer the capsule shape in a horizontal row of buttons.

**Use standard controls to take advantage of the audible feedback sounds people already know.** Audible feedback is especially important in visionOS, because the system doesn't play haptics.

### watchOS

watchOS displays all inline buttons using the capsule button shape. When you place a button inline with content, it gains a material effect that contrasts with the background to ensure legibility.

**Use a toolbar to place buttons in the corners.** The system automatically moves the time and title to accommodate toolbar buttons. The system also applies the Liquid Glass appearance to toolbar buttons, providing a clear visual distinction from the content beneath them.

**Prefer buttons that span the width of the screen for primary actions in your app.** Full-width buttons look better and are easier for people to tap. If two buttons must share the same horizontal space, use the same height for both, and use images or short text titles for each button's content.

**Use toolbar buttons to provide either navigation to related areas or contextual actions for the view's content.** These buttons provide access to additional information or secondary actions for the view's content.

**Use the same height for vertical stacks of one- and two-line text buttons.** As much as possible, use identical button heights for visual consistency.

## Specifications

| Item | Value |
|---|---|
| Minimum hit region (most platforms) | 44x44 pt |
| Minimum hit region (visionOS) | 60x60 pt |
| Image button padding (macOS) | ~10 px between image edges and button edges |
| Minimum spacing between visionOS button centers | ≥60 pt apart |
| Extra padding when visionOS buttons are ≥60 pt | +4 pt padding |
| visionOS button size — Mini | 28 pt |
| visionOS button size — Small | 32 pt |
| visionOS button size — Regular | 44 pt |
| visionOS button size — Large | 52 pt |
| visionOS button size — Extra large | 64 pt |

## Native implementation

**Related**
- Pop-up buttons
- Pull-down buttons
- Toggles
- Segmented controls
- Location button

**Developer documentation**
- Button — SwiftUI
- UIButton — UIKit
- NSButton — AppKit

**Key APIs**
- `NSButton.BezelStyle.flexiblePush` — macOS flexible-height push button
- `NSButton.BezelStyle.smallSquare` — macOS square (gradient) button
- `isBordered` — suppress the system-provided border on an image button
- `preferredElementSize` — control iOS/iPadOS menu layout (referenced from the related Menus page)

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**A button is a semantic commitment, not a visual one.** Apple defines a button by what it does — it "initiates an instantaneous action" — and layers style, content, and role on top of that meaning. On the web the equivalent commitment is the `<button>` element (or an `<a>` when the action is really navigation to a new URL). A `<div>` with a click handler discards everything the platform gives a real button for free: keyboard focusability, Space/Enter activation, the accessibility tree exposing it with the `button` role, and forced-colors/high-contrast support. Recreating all of that by hand with ARIA (`role="button"`, `tabindex="0"`, manual key handlers) is possible but is strictly worse than using the native element, and it's easy to miss a case — this is the single most common accessibility failure on the web, and it is exactly the failure Apple's "role" concept is designed to prevent by construction.

**The 44x44 pt hit region → a real minimum target size, not just visual padding.** Apple's number isn't arbitrary — it's sized to a fingertip, and the guidance explicitly separates the *visual* button from its *hit region*, which can be larger than what's drawn. WCAG 2.5.8 (Target Size, Minimum) sets essentially the same floor at 24x24 CSS px, and the widely adopted better practice is 44x44 CSS px, matching Apple's pt value almost exactly (a CSS px and an iOS pt are both ~1/96 inch-ish reference units at 1x, so the numbers transfer directly). The practical technique is the same as Apple's own advice: keep a small visual button but expand the clickable area with padding or an invisible pseudo-element, rather than growing the artwork. Mobile web has no visionOS-scale exception; 44px is the floor across form factors.

**Prominent style, one or two per view → one primary action, marked as such.** Apple's rule that only one or two buttons per view should carry the prominent (accent-colored) treatment maps to the long-standing web pattern of exactly one `.primary` (or `type="submit"`) button per form or view, with the rest styled as secondary or tertiary. The reasoning transfers exactly: color is the strongest visual signal a screen has, and spending it on multiple competing buttons erodes its meaning back to zero, which is Apple's own "cognitive load" argument stated in interface terms.

**Role (Normal/Primary/Cancel/Destructive) → doesn't have a native HTML equivalent, but should still be modeled.** HTML has no `role="destructive"` for buttons the way SwiftUI does. The visual part (red/danger color) is trivial to reproduce in CSS, but Apple's *behavioral* rule — never assign primary to a destructive action, because prominence invites unread confirmation — is the part worth keeping even without platform support. It argues against a common web anti-pattern: a bright, prominent "Delete" button that's easiest to click precisely because it's destructive.

**Press states → `:active`, but don't stop there.** Apple's warning that a button without a press state "can feel unresponsive" applies directly; CSS's `:active` pseudo-class is the direct equivalent. But the web also needs `:hover` (pointer-only, so gate it behind `@media (hover: hover)` to avoid sticky hover on touch) and `:focus-visible` for keyboard users — a dimension Apple's guidance doesn't need to call out because the platform supplies focus rings automatically for native controls; on the web you must not remove them without replacing them.

**Icon-only buttons → the tooltip Apple gets for free must be built, and an accessible name must exist independently of it.** Apple notes that macOS and visionOS show a tooltip on hover automatically. The web's `title` attribute is the closest native equivalent, but it's mouse-only, delayed, and not reliably read by screen readers — so an icon-only web button still needs an explicit `aria-label` (or visually-hidden text) carrying the same content a sighted mouse user gets from the tooltip. This is a case where the web gives you less for free than Apple's platform does, and the gap has to be closed by hand every time.

**Ellipsis-suffix convention for buttons that open a "further input" view → carries over as a genuine UX convention, not just typography.** Apple's rule that a trailing "…" signals "this needs more information from you before it completes" is a convention English-speaking web users already share (it's inherited from desktop OS conventions generally), so it's safe to reuse verbatim in button labels that open a modal or a multi-step flow.

## Do / Don't

| Do | Don't |
|---|---|
| Give every button a hit region of at least 44x44 pt (60x60 pt in visionOS) | Rely on a button's visible size alone to define its tap target |
| Include a press state for custom buttons | Ship a custom button with no visual feedback on press |
| Use a prominent style for one or two buttons per view | Make every button in a view prominent |
| Distinguish preferred options with style, not size | Place two differently sized buttons of the same set next to each other |
| Assign the primary role to the most likely, nondestructive choice | Assign the primary role to a destructive action |
| Use standard help-button placement (lower corner, opposite dismissal buttons) | Add more than one help button per window |
| In macOS, append an ellipsis when a push button opens another view | Omit the ellipsis on a button that requires more input before completing |
| In visionOS, prefer circular or capsule shapes with a discernible fill | Use a white-fill, black-content button style outside the system's toggled state |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
