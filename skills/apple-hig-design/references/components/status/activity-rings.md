---
title: Activity rings
url: https://developer.apple.com/design/human-interface-guidelines/activity-rings
platforms: [iOS, iPadOS, watchOS]
last_updated: 2024-03-29
---

# Activity rings

Activity rings show an individual's daily progress toward Move, Exercise, and Stand goals.

## Core guidance

In watchOS, the Activity ring element always contains three rings, whose colors and meanings match those the Activity app provides. In iOS, the Activity ring element contains either a single Move ring representing an approximation of activity, or all three rings if an Apple Watch is paired.

### Best practices

**Display Activity rings when they're relevant to the purpose of your app.** If your app is related to health or fitness, and especially if it contributes information to HealthKit, people generally expect to find Activity rings in your interface. For example, if you structure a workout or health session around the completion of Activity rings, consider displaying the element on a workout metrics screen so that people can track their progress during their session. Similarly, if you provide a summary screen that appears at the conclusion of a workout, you could display Activity rings to help people check on their progress toward their daily goals.

**Use Activity rings only to show Move, Exercise, and Stand information.** Activity rings are designed to consistently represent progress in these specific areas. Don't replicate or modify Activity rings for other purposes. Never use Activity rings to display other types of data. Never show Move, Exercise, and Stand progress in another ring-like element.

**Use Activity rings to show progress for a single person.** Never use Activity rings to represent data for more than one person, and make sure it's obvious whose progress you're showing by using a label, a photo, or an avatar.

**Always keep the visual appearance of Activity rings the same, regardless of where you display them.** Follow these guidelines to provide a consistent experience:

- Never change the colors of the rings; for example, don't use filters or modify opacity.
- Always display Activity rings on a black background.
- Prefer enclosing the rings and background within a circle. To do this, adjust the corner radius of the enclosing view rather than applying a circular mask.
- Ensure that the black background remains visible around the outermost ring. If necessary, add a thin, black stroke around the outer edge of the ring, and avoid including a gradient, shadow, or any other visual effect.
- Always scale the rings appropriately so they don't seem disconnected or out of place.
- When necessary, design the surrounding interface to blend with the rings; never change the rings to blend with the surrounding interface.

**To display a label or value that's directly associated with an Activity ring, use the colors that match it.** To display the ring-specific labels Move, Exercise, and Stand, or to display a person's current and goal values for each ring, use the colors specified for each ring, given as RGB values.

> **Source limitation:** The source page specifies the Move, Exercise, and Stand ring colors as RGB values shown in a color-swatch graphic. That graphic did not extract as text in the captured PDF — only the labels "Move," "Exercise," and "Stand" survived, with no numeric RGB values attached to any of them. Rather than invent plausible-looking numbers, this file omits them. Look up the current RGB values directly on the Apple Developer Documentation page linked above before implementing ring-specific label or value colors.

**Maintain Activity ring margins.** An Activity ring element must include a minimum outer margin of no less than the distance between rings. Never allow other elements to crop, obstruct, or encroach upon this margin or the rings themselves.

**Differentiate other ring-like elements from Activity rings.** Mixing different ring styles can lead to a visually confusing interface. If you must include other rings, use padding, lines, or labels to separate them from Activity rings. Color and scale can also help provide visual separation.

**Don't send notifications that repeat the same information the Activity app sends.** The system already delivers Move, Exercise, and Stand progress updates, so it's confusing for people to receive redundant information from your app. Also, don't show an Activity ring element in your app's notifications. It's fine to reference Activity progress in a notification, but do so in a way that's unique to your app and doesn't replicate the same information the system provides.

**Don't use Activity rings for decoration.** Activity rings provide information to people; they don't just embellish your app's design. Never display Activity rings in labels or background graphics.

**Don't use Activity rings for branding.** Use Activity rings strictly to display Activity progress in your app. Never use Activity rings in your app's icon or marketing materials.

## Platform considerations

No additional considerations for iPadOS or watchOS. Not supported in macOS, tvOS, or visionOS.

### iOS

Activity rings are available in iOS with `HKActivityRingView`. The appearance of the Activity ring element changes automatically depending on whether an Apple Watch is paired:

- With an Apple Watch paired, iOS shows all three Activity rings.
- Without an Apple Watch paired, iOS shows the Move ring only, which represents an approximation of a person's activity based on their steps and workout information from other apps.

> *Image caption:* Apple Watch paired — iOS shows all three Activity rings.
> *Image caption:* No Apple Watch paired — iOS shows the Move ring only.

Because iOS shows Activity rings whether or not an Apple Watch is paired, activity history can include a combination of both styles. For example, Activity rings in Fitness have three rings when a person exercises with their Apple Watch paired, and only the Move ring when they exercise without their Apple Watch.

## Native implementation

**Related**
- Workouts

**Developer documentation**
- `HKActivityRingView` — HealthKit

**Key APIs**
- `HKActivityRingView` — renders the Activity ring element in iOS and iPadOS

**Videos:** Track workouts with HealthKit on iOS and iPadOS · Build a workout app for Apple Watch · Build custom workouts with WorkoutKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**This component barely transfers, and it's worth saying so plainly.** Activity rings are not a generic "radial progress" widget — they are a fixed, three-metric, single-person visualization tied to Apple's own HealthKit data model and Watch/Fitness ecosystem. There is no web platform, no health-data standard, and no user hardware (a wrist-worn accelerometer plus a paired phone) that this maps onto. A web app has no Move/Exercise/Stand goal triad to visualize, and inventing one to look like Apple's rings would be recreating branding, not solving a UX problem.

**The one principle that does transfer: don't borrow a recognizable system visual and repurpose it.** Apple's strongest rules here aren't about layout — they're "never use Activity rings for other data," "never use them for branding," "never use them for decoration." The underlying idea generalizes: if you build a distinctive, brand-associated visualization (a specific ring arrangement, a specific icon system, a specific chart signature), don't let it drift into contexts where it no longer means what it originally meant. A three-ring circular progress motif on the web that visually echoes Apple's Activity rings risks implying an Apple/HealthKit affiliation your app doesn't have — treat it as a trademark-adjacent risk, not just a design choice.

**If you actually need a "multiple related metrics, one glance" widget, design a new one.** A generic multi-ring or multi-arc radial chart is a legitimate, well-covered web charting pattern (nested `<svg>` arcs or `<canvas>`, each ring independently labeled and colored for its own metric) — but it belongs to the general vocabulary already covered under progress indicators and gauges on this platform, not to this page. Give it your own visual identity — different proportions, different color logic, a different number of rings — rather than reproducing three rings on black.

**Accessibility parity, if you do build something ring-shaped.** Apple's underlying accessibility expectation — that a VoiceOver user gets the same information a sighted user gets from the rings — maps directly: expose each ring's label and current/goal values as text (ARIA `role="img"` with a full `aria-label`, or adjacent visually-hidden text), never rely on ring fill percentage alone to carry the information.

## Do / Don't

| Do | Don't |
|---|---|
| Show Activity rings only when your app is genuinely health- or fitness-related | Use Activity rings to display unrelated data |
| Show progress for exactly one person, identified by label, photo, or avatar | Represent more than one person's data in a single Activity ring element |
| Keep ring colors, background, and scale exactly as Apple defines them | Recolor, filter, or reshape the rings to match your app's theme |
| Enclose the rings in a circle by adjusting corner radius | Apply a circular mask over rectangular rings |
| Preserve the minimum outer margin between rings and other elements | Let other UI crop, obstruct, or encroach on the rings or their margin |
| Reference Activity progress in a notification in your app's own voice | Show an Activity ring element inside a notification |
| Use Activity rings strictly to show Activity progress | Use Activity rings for decoration, branding, icons, or marketing materials |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
