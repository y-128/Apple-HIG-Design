---
title: Offering help
url: https://developer.apple.com/design/human-interface-guidelines/offering-help
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2023-12-05
---

# Offering help

Although the most effective experiences are approachable and intuitive, you can provide contextual help when necessary.

## Core guidance

### Best practices

**Let your app's tasks inform the types of help people might need.** For example, you might help people perform simple, one- or two-step tasks by displaying an inline view that succinctly describes the task. In contrast, if your app or game supports complex or multistep tasks you might want to provide a tutorial that teaches people how to accomplish larger goals. In general, directly relate the help you provide to the precise action or task people are doing right now and make it easy for people to dismiss or avoid the help if they don't need it.

**Use relevant and consistent language and images in your help content.** Always make sure guidance is appropriate for the current context. For example, if someone's using the Siri Remote with your tvOS experience, don't show tips or images that feature a game controller. Also be sure the terms and descriptions you use are consistent with the platform — for example, don't write copy that tells people to click a button on an iPhone or tap a menu item on a Mac.

**Make sure all help content is inclusive.** For guidance, see Inclusion.

**Avoid bloating your help content by explaining how standard components or patterns work.** Instead, describe the specific action or task that a standard element performs in your app or game. If your experience introduces a unique control or expects people to use an input device in a nonstandard way — such as holding the Siri Remote rotated 90 degrees — orient people quickly, preferring animation or graphics to educate instead of a lengthy description.

### Creating tips

A tip is a small, transient view that briefly describes how to use a feature in your app. Tips are a great way to teach people about new or less obvious features in your app, or help them discover faster ways to accomplish a task. For developer guidance, see TipKit.

**Use the most appropriate tip type for your app's user interface.** Display a popover tip when you want to preserve the content flow, or an inline tip when you want to ensure that surrounding information is visible. You can use an annotation-style inline tip when pointing to a specific UI element, or a hint-style tip when it's not related to a specific piece of UI.

> *Image caption:* Three tip types shown side by side — Popover, Annotation, and Hint.

**Use tips for simple features.** Tips work best on features that are easy to describe and that people can complete with a few simple steps. **If a feature requires more than three actions, it's probably too complicated for a tip.**

**Make tips short, actionable, and engaging.** A tip's goal is to encourage people to try new features. Use direct, action-oriented language to describe what the feature does and explain how to use it. **Keep your tips to one or two sentences** and avoid including content that's promotional or related to a different feature or user flow. Promotional content is anything that advertises, sells, or isn't aligned with the current context of what the person is doing.

**Define rules to help ensure your tips reach the intended audience.** Not everyone benefits from every tip — for example, people who've already used a feature won't appreciate viewing a tip that describes it. Use parameter-based or event-based eligibility rules to control when a tip appears, and only display a tip if someone might benefit from its use. When your app has more than one tip, set the display frequency so tips display at a reasonable cadence — **for example, once every 24 hours.**

**If there's an image or symbol that people associate with the feature, consider including it in the tip, and prefer the filled variant.** For example, a tip with a star can help people understand that the tip is related to favorites.

> *Image caption:* A tip using a filled star symbol to indicate its connection to a favorites feature.

**If the feature is represented by an image that the tip connects to directly, avoid repeating the same image in both the tip and the UI.**

**Use buttons to direct people to information or options.** If your feature has settings people can customize, or you want to redirect people to an area where they can learn more about a feature, consider adding a button. Buttons can take people directly to the settings where they make adjustments, or if there's more information people might find useful, add a button to take them to additional resources, such as a setup flow.

## Platform considerations

No additional considerations for iOS, iPadOS, tvOS, or watchOS.

### macOS, visionOS

A tooltip (called a help tag in user documentation) displays a small, transient view that briefly describes how to use a component in the interface. In apps that run on a Mac — including iPhone and iPad apps — tooltips can appear when a person holds the pointer over an element; in visionOS apps, a tooltip can appear when a person looks at an element or holds the pointer over it. For developer guidance, see `help(_:)`.

**Describe only the control that people indicate interest in.** When people want to know how to use a specific control, they don't want to learn how to use nearby controls or how to perform a larger task.

**Explain the action or task the control initiates.** It often works well to begin the description with a verb — for example, "Restore default settings" or "Add or remove a language from the list."

**In general, avoid repeating a control's name in its tooltip.** Repeating the name takes up space in the tooltip and rarely adds value to the description.

**Be brief.** As much as possible, **limit tooltip content to a maximum of 60 to 75 characters** (note that localization often changes the length of text). To make a description brief and direct, consider using a sentence fragment and omitting articles. If you need a lot of text to describe a control, consider simplifying your interface design.

**Use sentence case.** Sentence case tends to appear more casual and approachable. If you write complete sentences, omit ending punctuation unless it's required to be consistent with your app's style.

**Consider offering context-sensitive tooltips.** For example, you could provide different text for a control's different states.

## Native implementation

**Related**
- Onboarding
- Feedback
- Writing
- Help menu

**Developer documentation**
- TipKit
- `NSHelpManager` — AppKit
- `help(_:)`

**Videos:** Make features discoverable with TipKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**"Directly relate help to the precise task, make it easy to dismiss" → contextual, dismissible help beats a help center link.** A support-site link that opens in a new tab breaks flow entirely — the person leaves the task to go read about it, then has to find their way back. Inline, contextual help (a tooltip, an inline hint, a small popover anchored to the control in question) keeps the person in place, which is the same reasoning Apple gives for preferring inline views on simple tasks and reserving tutorials for complex ones.

**"Use relevant and consistent language for the current platform" → don't say 'click' on a touch device or 'tap' on a mouse-and-keyboard device.** This maps directly and is worth taking literally on the web: input-method-aware copy (detecting touch vs. pointer via `matchMedia('(pointer: coarse)')` or similar) is one of the few places where Apple's platform-specific wording advice has a clean web equivalent, since a responsive site genuinely serves both input types to different people.

**"Avoid explaining how standard components work" → don't write a tooltip for a component the platform already makes self-evident.** A native `<select>`, a standard button, a text input — these carry enough convention that explaining "click here to submit" is noise. Reserve help content for genuinely nonstandard interactions your app introduces, exactly as Apple advises against explaining standard iOS/macOS controls.

**Tips → TipKit's closest web shape is a small library-backed component, but the eligibility-rules discipline is the part worth copying even without the library.** Web onboarding-tooltip libraries exist, but most default to the sequential-tour anti-pattern this same skill's Onboarding entry warns against. What transfers cleanly from Apple's TipKit guidance is the *policy*, independent of any library: gate a tip on whether the person has already used the feature, cap the frequency (Apple's own example is once every 24 hours), and never show more than one tip competing for attention at a time. Implement that with a stored per-user "seen" and "last-shown" timestamp regardless of which UI library renders the tip itself.

**"Keep tips to one or two sentences, avoid promotional content" → applies word-for-word to web tooltip and coach-mark copy.** This is pure content guidance and needs no platform translation — a web tooltip that reads like ad copy fails the same way a native one does, and for the same reason: it breaks the trust that the interruption was worth having.

**Tooltips (macOS/visionOS section) → the native `title` attribute is not sufficient; use a proper tooltip pattern with keyboard and touch support.** The browser's built-in `title` attribute tooltip is slow to appear, invisible to keyboard-only users, and unavailable on touch devices entirely — none of which match Apple's tooltip behavior of appearing promptly on hover or gaze. A custom tooltip component needs `aria-describedby` linking the trigger to the tooltip text, a visible-on-focus trigger (not hover-only, so keyboard users get it too), and — per Apple's brevity rule — a hard cap on length, since the 60–75 character guidance is a genuinely good target for any tooltip, web or native, that has to render as a small floating label without wrapping unpredictably.

**"Avoid repeating the control's name in its tooltip" and "use sentence case, drop ending punctuation" → straightforward copy rules that transfer unchanged.** Nothing about the web changes why these are good tooltip-writing rules; treat them as house style for any web tooltip content.

## Do / Don't

| Do | Don't |
|---|---|
| Relate help directly to the task at hand | Explain how standard components already work |
| Make help easy to dismiss or avoid | Force people through help they didn't ask for |
| Use platform-appropriate language ("tap" vs. "click") | Use touch-specific copy on a pointer-driven platform |
| Reserve tips for simple, few-step features | Use a tip to explain a feature that needs more than three actions |
| Keep tip copy to one or two sentences | Include promotional content in a tip |
| Gate tips with eligibility rules and a display cadence | Show a tip to someone who's already used the feature |
| Keep tooltips to roughly 60–75 characters | Write a long paragraph inside a tooltip |
| Begin a tooltip description with a verb | Repeat the control's own name in its tooltip |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
