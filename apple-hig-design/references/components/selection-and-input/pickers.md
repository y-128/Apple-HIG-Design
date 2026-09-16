---
title: Pickers
url: https://developer.apple.com/design/human-interface-guidelines/pickers
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2023-06-05
---

# Pickers

A picker displays one or more scrollable lists of distinct values that people can choose from.

## Core guidance

The system provides several styles of pickers, each of which offers different types of selectable values and has a different appearance. The exact values shown in a picker, and their order, depend on the device language.

Pickers help people enter information by letting them choose single or multipart values. Date pickers specifically offer additional ways to choose values, like selecting a day in a calendar view or entering dates and times using a numeric keypad.

### Best practices

**Consider using a picker to offer medium-to-long lists of items.** If you need to display a fairly short list of choices, consider using a pull-down button instead of a picker. Although a picker makes it easy to scroll quickly through many items, it may add too much visual weight to a short list of items. On the other hand, if you need to present a very large set of items, consider using a list or table. Lists and tables can adjust in height, and tables can include an index, which makes it much faster to target a section of the list.

**Use predictable and logically ordered values.** Before people interact with a picker, many of its values can be hidden. It's best when people can predict what the hidden values are, such as with an alphabetized list of countries, so they can move through the items quickly.

**Avoid switching views to show a picker.** A picker works well when displayed in context, below or in proximity to the field people are editing. A picker typically appears at the bottom of a window or in a popover.

**Consider providing less granularity when specifying minutes in a date picker.** By default, a minute list includes 60 values (0 to 59). You can optionally increase the minute interval as long as it divides evenly into 60. For example, you might want quarter-hour intervals (0, 15, 30, and 45).

## Platform considerations

No additional considerations for visionOS.

### iOS, iPadOS

A date picker is an efficient interface for selecting a specific date, time, or both, using touch, a keyboard, or a pointing device. You can display a date picker in one of the following styles:

- **Compact** — A button that displays editable date and time content in a modal view.
- **Inline** — For time only, a button that displays wheels of values; for dates and times, an inline calendar view.
- **Wheels** — A set of scrolling wheels that also supports data entry through built-in or external keyboards.
- **Automatic** — A system-determined style based on the current platform and date picker mode.

A date picker has four modes, each of which presents a different set of selectable values.

- **Date** — Displays months, days of the month, and years.
- **Time** — Displays hours, minutes, and (optionally) an AM/PM designation.
- **Date and time** — Displays dates, hours, minutes, and (optionally) an AM/PM designation.
- **Countdown timer** — Displays hours and minutes, up to a maximum of 23 hours and 59 minutes. This mode isn't available in the inline or compact styles.

The exact values shown in a date picker, and their order, depend on the device location.

> *Image caption:* Several examples of date pickers showing different combinations of style and mode: Compact, Inline, Wheels.
> *Image caption:* In a compact layout, a picker opens as a popover over your content.

**Use a compact date picker when space is constrained.** The compact style displays a button that shows the current value in your app's accent color. When people tap the button, the date picker opens a modal view, providing access to a familiar calendar-style editor and time picker. Within the modal view, people can make multiple edits to dates and times before tapping outside the view to confirm their choices.

### macOS

**Choose a date picker style that suits your app.** There are two styles of date pickers in macOS: textual and graphical. The textual style is useful when you're working with limited space and you expect people to make specific date and time selections. The graphical style is useful when you want to give people the option of browsing through days in a calendar or selecting a range of dates, or when the look of a clock face is appropriate for your app.

For developer guidance, see `NSDatePicker`.

### tvOS

Pickers are available in tvOS with SwiftUI. For developer guidance, see `Picker`.

### watchOS

Pickers display lists of items that people navigate using the Digital Crown, which helps people manage selections in a precise and engaging way.

A picker can display a list of items using the wheels style. watchOS can also display date and time pickers using the wheels style. For developer guidance, see `Picker` and `DatePicker`.

You can configure a picker to display an outline, caption, and scrolling indicator.

For longer lists, the navigation link displays the picker as a button. When someone taps the button, the system shows the list of options. The person can also scrub through the options using the Digital Crown without tapping the button. For developer guidance, see `NavigationLink`.

## Native implementation

**Related**
- Pull-down buttons
- Lists and tables

**Developer documentation**
- `Picker` — SwiftUI
- `UIDatePicker` — UIKit
- `UIPickerView` — UIKit
- `NSDatePicker` — AppKit
- `NavigationLink` — SwiftUI (watchOS)

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**The plain `<select>` is the closest native match, and it's a better default than most teams give it credit for.** A native `<select>` is keyboard-operable, screen-reader-supported, respects the OS's own text size and input method, and on mobile opens the platform's own wheel- or list-style picker automatically, which is functionally close to what Apple describes as the system providing "several styles of pickers" with a native appearance. Before building a custom picker component, weigh what you're giving up: a hand-rolled listbox has to reimplement typeahead, arrow-key navigation, `aria-activedescendant` or roving tabindex, and mobile-specific touch scrolling behavior that `<select>` gets for free from the browser and OS.

**"Consider a pull-down button for short lists, a picker for medium lists, a list or table for very long lists" → this length-based decision transfers directly.** The reasoning Apple gives is about matching visual weight and scan cost to list length, which isn't platform-specific. On the web the equivalent progression is a small set of visible radio buttons or a dropdown menu for a handful of options, a `<select>` (native or custom) for a medium list, and a searchable/filterable list or virtualized table for anything long enough that scrolling through it unaided is a poor experience. Apple's argument for adding a table index at large scale maps to adding a search/filter input once a list exceeds roughly a screenful.

**"Use predictable and logically ordered values" → this is an argument for `<select>`/`<datalist>` over a chip-cloud or unordered custom grid.** Apple's point is that people should be able to predict hidden values from position, alphabetical country lists being the example. On the web this argues against picker UIs that shuffle or group options in ways a person can't anticipate, and for keeping alphabetical or otherwise logical ordering even in a custom-styled dropdown, since predictability is what lets someone type ahead to jump to an item.

**"Avoid switching views to show a picker" → this is the strongest and most literal transfer.** Apple's reasoning is that a picker should stay in context, near the field it edits, not force a navigation change. On the web the equivalent failure is a picker that navigates to a new page or opens a disorienting full-screen modal for what should be an inline choice. An anchored dropdown, popover, or inline expansion preserves the surrounding context and scroll position the way Apple's bottom-sheet or popover placement does; a full page navigation to "select a value" does not.

**Date and time pickers are where the web genuinely falls short of the platform, and it's worth naming plainly.** `<input type="date">`, `type="time">`, and `type="datetime-local">` exist, but browser support for their built-in picker UI is inconsistent (notably, Safari and Firefox render these fields very differently from Chromium, and some browsers fall back to a plain text field with no picker affordance at all), and none of them offer anything resembling Apple's four distinct modes (Date, Time, Date and time, Countdown timer) or a duration-only countdown-timer input. A countdown-timer-style duration picker in particular has no native web equivalent at all — there is no `<input type="duration">`. If your product needs consistent cross-browser date/time or duration entry, expect to build a custom widget, and expect it to be one of the more accessibility-labor-intensive components in your app: correct keyboard interaction, localized formatting, and screen-reader announcement of the current value all have to be built by hand, whereas Apple gets all three from `UIDatePicker`/`NSDatePicker` for free.

**"Provide less granularity for minutes" → the underlying principle is about matching the input's precision to what people can usefully scroll through.** The web analogue isn't specific to minutes: any long enumerable range presented as a scrollable or steppable list (minutes, seconds, currency denominations, quantities) benefits from the same treatment, coarsening the interval when finer precision isn't meaningfully chooseable by a human scrolling a list.

## Do / Don't

| Do | Don't |
|---|---|
| Use a picker for medium-to-long lists of items | Use a picker for a short list better served by a pull-down button |
| Use a list or table with an index for very large sets | Force people to scroll a picker through hundreds of items |
| Order values predictably (e.g., alphabetized) | Hide values in an order people can't anticipate |
| Show a picker in context, near the field it edits | Navigate to a new view just to show a picker |
| Coarsen minute intervals when fine granularity isn't needed | Always default to 60 individual minute values without considering the use case |
| Choose a date picker style and mode that fit the available space | Use a wheels-style picker where a compact button would fit better |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
