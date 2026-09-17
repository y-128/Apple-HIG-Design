---
title: Feedback
url: https://developer.apple.com/design/human-interface-guidelines/feedback
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Feedback

Feedback helps people know what's happening, discover what they can do next, understand the results of actions, and avoid mistakes.

## Core guidance

Providing clear, consistent feedback as people interact with your app or game can make it feel intuitive and encourage deeper exploration. Feedback can communicate several different things, such as:

- The current status of something
- The success or failure of an important task or action
- A warning about an action that can have negative consequences
- An opportunity to correct a mistake or problematic situation

The most effective feedback tends to match the significance of the information to the way it's delivered. For example, it often works well to display status information in a passive way so that people can view it when they need it. In contrast, a warning about possible data loss needs to interrupt people so they have a chance to avoid the problem.

### Best practices

**Make sure all feedback is accessible.** When you use multiple ways to provide feedback, you reach more people and give them the opportunity to receive the feedback in ways that work for them. For example, when you provide feedback using color, text, sound, and haptics, people can receive it whether they silence their device, look away from the screen, or use VoiceOver. (For guidance on providing haptic feedback, see Playing haptics.)

**Consider integrating status feedback into your interface.** When status feedback is available near the items it describes, people get important information without having to take action or leave their current context. For example, Mail in iOS and iPadOS describes the most recent update and displays the number of unread messages in the toolbar of the mailbox screen, making the information unobtrusive but easy for people to check when they're interested.

**Use alerts to deliver critical — and ideally actionable — information.** By design, alerts disrupt the current context, so you need to match the importance of the information to the level of interruption. Alerts can lose their impact if you use them too often or to deliver unimportant information. For guidance, see Alerts.

**Warn people when they initiate a task that can cause data loss that's unexpected and irreversible.** In contrast, don't warn people when data loss is the expected result of their action. For example, the Finder doesn't warn people every time they throw away a file because deleting the file is the expected result.

**When it makes sense, confirm that a significant action or task has completed.** For example, people appreciate getting feedback that confirms a successful Apple Pay transaction. It's generally best to reserve this type of confirmation for activities that are sufficiently important — because people typically expect their action or task to succeed, they only need to know when it doesn't.

**Show people when a command can't be carried out and help them understand why.** For example, if people request directions without specifying a destination, Maps tells them that it can't provide directions to and from the same location.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, tvOS, or visionOS.

### watchOS

**Avoid displaying an indeterminate progress indicator — such as a loading indicator — in a watchOS app.** An animated indicator can make people think they need to continue paying attention to the display, which isn't a good user experience. To provide a better experience, reassure people that they'll receive a notification when the process completes.

## Native implementation

**Related**
- Playing audio
- Playing haptics
- Motion

**Developer documentation**
- Animation and haptics — UIKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**"Match the significance of information to how it's delivered" → this is the single most important web-accessibility-of-feedback rule, and it maps to ARIA live-region politeness.** Apple's core distinction — passive status information versus interruptive warnings — has an almost literal web analogue in `aria-live="polite"` versus `aria-live="assertive"` (or a native `role="alert"`, which is implicitly assertive). Politely announced feedback waits for a pause in whatever the screen reader is already saying; assertive feedback interrupts immediately. Using assertive for routine status updates is the accessibility-tree version of over-using alerts, and it produces the same fatigue Apple warns about — people start tuning it out, or in the screen-reader case, get interrupted so often the experience becomes unusable.

**"Make sure all feedback is accessible" → don't encode feedback in color alone, and don't encode it in a toast alone either.** Apple's example — color, text, sound, haptics together — generalizes on the web to: never let color be the only signal (fails colorblind users and anyone in bright sunlight), and never let a transient visual toast be the only signal (fails screen-reader users if it isn't wired into a live region, and fails anyone who glanced away when it appeared, since most toasts vanish and leave no trace). A toast paired with a live-region announcement and a persistent state change in the UI covers the same bases Apple's multi-channel example does.

**"Integrate status feedback into your interface" near the item it describes → inline, contextual state beats a global notification center for routine status.** A badge count or inline "saved" indicator next to the thing it describes is calmer than routing every status update through a corner toast stack, for the same reason Apple's Mail example works: the person checks it when they're already looking at the relevant area, rather than being pulled toward a notification tray.

**"Use alerts for critical, actionable information — don't overuse them" → `window.confirm()`/`alert()` are the wrong implementation even when the judgment to interrupt is right.** Browser-native alert dialogs are unstyled, block the entire tab, and provide no room for the actionable framing Apple asks for ("ideally actionable"). A custom modal dialog (see Modality's web translation for the accessibility requirements that come with it) is the right vehicle; native `alert()` should be treated as a debugging tool, not a production feedback pattern.

**"Warn only when data loss is unexpected and irreversible" → the `beforeunload` confirmation is the textbook case of getting this backwards.** Browsers historically let sites throw a "leave site?" warning on every navigation, and the pattern became so abused that browsers now suppress the custom message entirely. Apple's Finder example — don't warn when the loss is the expected, intended result of the action — is exactly the discipline that was missing from the sites that trained users to reflexively dismiss `beforeunload` dialogs. Reserve any exit-confirmation for genuinely surprising, irreversible loss (an unsaved multi-paragraph draft), never for routine navigation.

**"Confirm significant completed actions, but don't confirm the expected case" → applies directly to optimistic UI.** A web app that optimistically updates the UI before the server confirms should still surface an unambiguous success or rollback signal for consequential actions (a payment, an irreversible delete-confirmation), while routine successful actions (a saved form field) can stay passive or silent, matching Apple's "they only need to know when it doesn't" succeed framing.

**"Explain why a command can't be carried out" → error messages should name the specific problem, not report a generic failure state.** Apple's Maps example (same origin and destination) is a model for web form validation and API-error handling alike: surface the actual constraint that was violated in plain language near the control that violated it, rather than a blanket "something went wrong" banner that leaves the person guessing what to fix.

**watchOS's "don't show an indeterminate spinner, reassure with a notification instead" → the nearest web parallel is background-task feedback via the Notifications API or a persistent status area, not a page you keep open and staring at.** For a task the person doesn't need to actively watch, prefer a completion notification (browser push, in-app toast on return) over a spinner that implies continuous attention is required — the same logic Apple applies to the watch's small, glance-oriented screen applies to any workflow where staring at a spinner is a worse experience than being told when it's done.

## Do / Don't

| Do | Don't |
|---|---|
| Deliver feedback through more than one channel | Rely on color alone to convey status |
| Place status feedback near what it describes | Force people to leave context to check routine status |
| Reserve alerts for critical, actionable information | Overuse alerts for unimportant information |
| Warn before unexpected, irreversible data loss | Warn when data loss is the intended, expected result |
| Confirm important actions, especially failures | Confirm every routine, expected success |
| Explain specifically why a command failed | Show a generic failure message with no explanation |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
