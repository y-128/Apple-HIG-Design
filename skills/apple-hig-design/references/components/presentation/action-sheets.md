---
title: Action sheets
url: https://developer.apple.com/design/human-interface-guidelines/action-sheets
platforms: [iOS, iPadOS, macOS, tvOS, watchOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Action sheets

An action sheet is a modal view that presents choices related to an action people initiate.

## Core guidance

> **Developer note (Apple):** When you use SwiftUI, you can offer action sheet functionality in all platforms by specifying a presentation modifier for a confirmation dialog. If you use UIKit, you use `UIAlertController.Style.actionSheet` to display an action sheet in iOS, iPadOS, and tvOS.

### Best practices

**Use an action sheet — not an alert — to offer choices related to an intentional action.** For example, when people cancel the message they're editing in Mail on iPhone, an action sheet provides two choices: delete the draft, or save the draft. Although an alert can also help people confirm or cancel an action that has destructive consequences, it doesn't provide additional choices related to the action. More importantly, an alert is usually unexpected, generally telling people about a problem or a change in the current situation that might require them to act.

**Use action sheets sparingly.** Action sheets give people important information and choices, but they interrupt the current task to do so. To encourage people to pay attention to action sheets, avoid using them more than necessary.

**Aim to keep titles short enough to display on a single line.** A long title is difficult to read quickly and might get truncated or require people to scroll.

**Provide a message only if necessary.** In general, the title — combined with the context of the current action — provides enough information to help people understand their choices.

**If necessary, provide a Cancel button that lets people reject an action that might destroy data.** Place the Cancel button at the bottom of the action sheet (or in the upper-left corner of the sheet in watchOS). A SwiftUI confirmation dialog includes a Cancel button by default.

**Make destructive choices visually prominent.** Use the destructive style for buttons that perform destructive actions, and place these buttons at the top of the action sheet where they tend to be most noticeable.

## Platform considerations

No additional considerations for macOS or tvOS. Not supported in visionOS.

### iOS, iPadOS

**Use an action sheet — not a menu — to provide choices related to an action.** People are accustomed to having an action sheet appear when they perform an action that might require clarifying choices. In contrast, people expect a menu to appear when they choose to reveal it.

**Avoid letting an action sheet scroll.** The more buttons an action sheet has, the more time and effort it takes for people to make a choice. Also, scrolling an action sheet can be hard to do without inadvertently tapping a button.

### watchOS

The system-defined style for action sheets includes a title, an optional message, a Cancel button, and one or more additional buttons. The appearance of this interface is different depending on the device.

Each button has an associated style that conveys information about the button's effect. There are three system-defined button styles:

| Style | Meaning |
|---|---|
| Default | The button has no special meaning. |
| Destructive | The button destroys user data or performs a destructive action in the app. |
| Cancel | The button dismisses the view without taking any action. |

**Avoid displaying more than four buttons in an action sheet, including the Cancel button.** When there are fewer buttons onscreen, it's easier for people to view all their options at once. Because the Cancel button is required, aim to provide no more than three additional choices.

## Native implementation

**Related**
- Modality
- Sheets
- Alerts

**Developer documentation**
- `confirmationDialog(_:isPresented:titleVisibility:actions:)` — SwiftUI
- `UIAlertController.Style.actionSheet` — UIKit
- `destructive` — SwiftUI (destructive button role)
- `UIAlertAction.Style.destructive` — UIKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Action sheet → a `<dialog>` styled and positioned as a choice list, not a native browser primitive.** There's no HTML element that natively renders as an anchored, bottom-sliding action sheet. Build it as a modal `<dialog>` (for the same focus-trapping reasons as Alerts and Sheets) styled to slide from the bottom edge on narrow viewports, with its buttons laid out as a vertical list rather than the row-of-buttons an alert uses. On wider viewports where the "sheet" affordance stops making sense, the same content is usually better served as a plain confirmation dialog.

**"Use an action sheet — not a menu" → the same distinction exists on the web, and it is worth keeping.** Apple's line is that an action sheet appears because of something the person just did, while a menu appears because the person asked to see it. The web equivalent is: don't repurpose a `<select>`, a dropdown menu, or the Popover API's disclosure pattern for a set of choices tied to a destructive or committing action — those affordances read as "browse options," not "confirm what just happened." Reserve the modal-dialog treatment for the latter.

**Destructive-style prominence → applies directly.** Placing the destructive choice first and giving it distinct (commonly red) styling transfers unchanged; it's a visual-hierarchy rule independent of platform.

**Four-button ceiling (watchOS) → a general small-screen principle, not a watch-specific one.** The reasoning — fewer onscreen choices are faster to scan — applies to any narrow viewport. A mobile web action sheet with six or seven options is exactly as hard to use as Apple's hypothetical five-button watch sheet; if you have that many choices, that's a sign the interaction belongs in a full page or a searchable list, not a sheet.

**Cancel placement → keep it, and keep it dismissible by Escape too.** Whether Cancel sits at the bottom of a vertical list (mobile pattern) or the corner (Apple's watchOS convention), the web addition is that `<dialog>` already closes on `Escape` — don't let a custom Cancel button be the *only* way out.

## Do / Don't

| Do | Don't |
|---|---|
| Use an action sheet for choices tied to an action just taken | Use an action sheet for an unexpected system message |
| Keep titles to one line | Write a long title that wraps or truncates |
| Place the destructive button at the top, styled distinctly | Bury a destructive choice among neutral ones |
| Include Cancel only when data could be lost | Add Cancel to every action sheet regardless of stakes |
| Limit to four buttons total on watchOS | Offer five or more choices in a watchOS action sheet |
| Use a menu when people choose to reveal options | Use an action sheet for browsable, non-action-triggered choices |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
