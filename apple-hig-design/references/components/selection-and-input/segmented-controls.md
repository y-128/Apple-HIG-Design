---
title: Segmented controls
url: https://developer.apple.com/design/human-interface-guidelines/segmented-controls
platforms: [iOS, iPadOS, macOS, tvOS, visionOS]
last_updated: 2023-06-21
---

# Segmented controls

A segmented control is a linear set of two or more segments, each of which functions as a button.

## Core guidance

### Selection models

Within a segmented control, all segments are usually equal in width. Like buttons, segments can contain text or images. Segments can also have text labels beneath them (or beneath the control as a whole).

A segmented control offers a single choice from among a set of options, or in macOS, either a single choice or multiple choices. For example, in macOS Keynote people can select only one segment in the alignment options control to align selected text. In contrast, people can choose multiple segments in the font attributes control to combine styles like bold, italics, and underline. The toolbar of a Keynote window also uses a segmented control to let people show and hide various editing panes within the main window area.

> *Image caption:* Single choice versus multiple choices in a segmented control.

In addition to representing the state of a single or multiple-choice selection, a segmented control can function as a set of buttons that perform actions without showing a selection state. For example, the Reply, Reply all, and Forward buttons in macOS Mail. For developer guidance, see `isMomentary` and `NSSegmentedControl.SwitchTracking.momentary`.

### Best practices

**Use a segmented control to provide closely related choices that affect an object, state, or view.** For example, a segmented control in an inspector could let people choose one or more attributes to apply to a selection, or a segmented control in a toolbar could offer a set of actions to perform on the current view.

> *Image caption:* In the iOS Health app, a segmented control provides a choice of time ranges for the activity graphs to display.

**Consider a segmented control when it's important to group functions together, or to clearly show their selection state.** Unlike other button styles, segmented controls preserve their grouping regardless of the view size or where they appear. This grouping can also help people understand at a glance which controls are currently selected.

**Keep control types consistent within a single segmented control.** Don't assign actions to segments in a control that otherwise represents selection state, and don't show a selection state for segments in a control that otherwise performs actions.

**Limit the number of segments in a control.** Too many segments can be hard to parse and time-consuming to navigate. Aim for no more than about five to seven segments in a wide interface and no more than about five segments on iPhone.

**In general, keep segment size consistent.** When all segments have equal width, a segmented control feels balanced. To the extent possible, it's best to keep icon and title widths consistent too.

### Content

**Prefer using either text or images — not a mix of both — in a single segmented control.** Although individual segments can contain text labels or images, mixing the two in a single control can lead to a disconnected and confusing interface.

**As much as possible, use content with a similar size in each segment.** Because all segments typically have equal width, it doesn't look good if content fills some segments but not others.

**Use nouns or noun phrases for segment labels.** Write text that describes each segment and uses title-style capitalization. A segmented control that displays text labels doesn't need introductory text.

## Platform considerations

Not supported in watchOS.

### iOS, iPadOS

**Consider a segmented control to switch between closely related subviews.** A segmented control can be useful as a way to quickly switch between related subviews. For example, the segmented control in Calendar's New Event sheet switches between the subviews for creating a new event and a new reminder. For switching between completely separate sections of an app, use a tab bar instead.

### macOS

**Consider using introductory text to clarify the purpose of a segmented control.** When the control uses symbols or interface icons, you could also add a label below each segment to clarify its meaning. If your app includes tooltips, provide one for each segment in a segmented control.

**Use a tab view in the main window area — instead of a segmented control — for view switching.** A tab view supports efficient view switching and is similar in appearance to a box combined with a segmented control. Consider using a segmented control to help people switch views in a toolbar or inspector pane.

**Consider supporting spring loading.** On a Mac equipped with a Magic Trackpad, spring loading lets people activate a segment by dragging selected items over it and force clicking without dropping the selected items. People can also continue dragging the items after a segment activates.

### tvOS

**Consider using a split view instead of a segmented control on screens that perform content filtering.** People generally find it easy to navigate back and forth between content and filtering options using a split view. Depending on its placement, a segmented control may not be as easy to access.

**Avoid putting other focusable elements close to segmented controls.** Segments become selected when focus moves to them, not when people click them. Carefully consider where you position a segmented control relative to other interface elements. If other focusable elements are too close, people might accidentally focus on them when attempting to switch between segments.

### visionOS

When people look at a segmented control that uses icons, the system displays a tooltip that contains the descriptive text you supply.

## Native implementation

**Related**
- Split views

**Developer documentation**
- `segmented` — SwiftUI
- `UISegmentedControl` — UIKit
- `NSSegmentedControl` — AppKit

**Key APIs**
- `isMomentary` — configure a control as a set of momentary buttons instead of a selection state
- `NSSegmentedControl.SwitchTracking.momentary` — AppKit equivalent for momentary tracking

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Selection-state segmented control → a radio group, not a `<select>` or a tab list.** When a segmented control shows a single choice from a set (Apple's default macOS Keynote alignment example), its behavior is a mutually-exclusive selection with a persistent visual state — exactly what a native radio group already does. A group of visually-connected `<input type="radio">` elements sharing a `name`, styled to look like segments, gives you roving-tabindex arrow-key navigation, screen-reader group announcement, and label association for free. A `role="radiogroup"` built from `<button>` elements only reproduces this correctly if you also hand-implement the arrow-key roving-tabindex pattern from the WAI-ARIA Authoring Practices — easy to get subtly wrong (Tab moving between every segment instead of just into and out of the group, for instance).

**Multiple-choice segmented control (macOS) → a group of toggle buttons, not checkboxes styled as buttons.** When several segments can be active at once (Apple's font-attributes example: bold, italic, underline together), the web analogue is a `role="group"` containing buttons with `aria-pressed`, each toggled independently. This is a different ARIA pattern from the radio group above, and conflating the two — for instance building every segmented control as an `aria-pressed` button group regardless of whether the underlying choice is exclusive — silently breaks the single-choice case for screen-reader and keyboard users, even though it might look identical sighted.

**Momentary segmented control (Reply / Reply all / Forward) → a plain button toolbar.** Apple is explicit that this variant carries no selection state at all — it is a set of action buttons that happen to share a segmented visual container. The correct web equivalent is unstyled `<button>` elements in a `role="toolbar"` or plain grouping, not radio inputs or `aria-pressed`; adding either state semantic here would tell assistive technology the buttons remember a choice, which they don't.

**"Switch between closely related subviews" vs. "switch between separate sections" → segmented control vs. tabs, and the web has a real answer for the distinction.** Apple's own rule — segmented control for related subviews within one screen, tab bar for separate app sections — maps cleanly onto two different ARIA patterns that already exist for exactly this split. `role="tablist"` / `role="tab"` / `role="tabpanel"` is built for the tab-bar case, where selecting an item swaps the panel of content shown and only one tab is ever active. The radiogroup-of-buttons pattern above is built for the segmented-control case, where the "choice" more often changes a filter, a mode, or an attribute rather than replacing an entire content region. If a supposed segmented control is actually swapping full views, it should probably be built as tabs; if it's filtering or setting an attribute in place, the tablist pattern is the wrong tool because it implies exactly one visible panel exists, which a filter control doesn't guarantee.

**Segment count limits → the same crowding logic, worse on narrow viewports.** Apple's five-to-seven ceiling (five on iPhone) exists because segments compress equally regardless of content length; on the web, where viewport width is far less predictable than a known device catalog, the same crowding happens sooner and less predictably. Treat the five-segment iPhone number as a reasonable mobile-web ceiling too, and prefer wrapping to a different control (a `<select>` or a disclosure menu) over letting segment labels truncate.

**Spring loading (macOS drag-and-drop activation) → no direct web equivalent.** HTML drag-and-drop has `dragenter`/`dragover` events that can be used to build a similar hover-to-activate behavior, but there is no built-in browser affordance for it, and force click has no web analogue at all on non-Apple hardware. Treat this as a nice-to-have custom interaction rather than something to expect parity on.

## Do / Don't

| Do | Don't |
|---|---|
| Use a segmented control for closely related choices affecting one object, state, or view | Mix action segments and selection-state segments in the same control |
| Keep segment count to about five to seven (five on iPhone) | Overload a control with more segments than fit comfortably |
| Keep segment widths and content sizes consistent | Let some segments fill with content while others stay empty |
| Use nouns or noun phrases with title-style capitalization for labels | Mix text and images within a single control |
| Use a segmented control to switch between closely related subviews (iOS, iPadOS) | Use a segmented control to switch between completely separate app sections — use a tab bar |
| Use a tab view for view switching in the main window area (macOS) | Place segmented controls, switches, or radio buttons in a toolbar or status bar |
| Keep other focusable elements away from segmented controls (tvOS) | Let focus accidentally land on nearby elements when navigating segments |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
