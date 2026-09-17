---
title: Writing
url: https://developer.apple.com/design/human-interface-guidelines/writing
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2025-12-16
---

# Writing

The words you choose within your app are an essential part of its user experience.

## Core guidance

Whether you're building an onboarding experience, writing an alert, or describing an image for accessibility, designing through the lens of language will help people get the most from your app or game.

### Getting started

**Determine your app's voice.** Think about who you're talking to, so you can figure out the type of vocabulary you'll use. What types of words are familiar to people using your app? How do you want people to feel? The words for a banking app might convey trust and stability, for example, while the words in a game might convey excitement and fun. Create a list of common terms, and reference that list to keep your language consistent. Consistent language, along with a voice that reflects your app's values, helps everything feel more cohesive.

**Match your tone to the context.** Once you've established your app's voice, vary your tone based on the situation. Consider what people are doing while they're using your app — both in the physical world and within the app itself. Are they exercising and reached a goal? Or are they trying to make a payment and received an error? Situational factors affect both what you say and how you display the text on the screen. Apple's own example compares two Apple Watch messages: one straightforward and direct, reflecting the seriousness of the situation, and one light and congratulatory, reflecting an achievement.

**Be clear.** Choose words that are easily understood and convey the right thing. Check each word to be sure it needs to be there. If you can use fewer words, do so. When in doubt, read your writing out loud.

**Write for everyone.** For your app to be useful for as many people as possible, it needs to speak to as many people as possible. Choose simple, plain language and write with accessibility and localization in mind, avoiding jargon and gendered terminology. For guidance, see Writing inclusively and VoiceOver; for developer guidance, see Localization.

### Best practices

**Consider each screen's purpose.** Pay attention to the order of elements on a screen, and put the most important information first. Format your text to make it easy to read. If you're trying to convey more than one idea, consider breaking up the text onto multiple screens, and think about the flow of information across those screens.

**Be action oriented.** Active voice and clear labels help people navigate through your app from one step to the next, or from one screen to another. When labeling buttons and links, it's almost always best to use a verb. Prioritize clarity and avoid the temptation to be too cute or clever with your labels. For example, just saying "Send" often works better than "Let's do it!" For links, avoid using "Click here" in favor of more descriptive words or phrases, such as "Learn more about UX Writing." This is especially important for people using screen readers to access your app.

**Build language patterns.** Consistency builds familiarity, helping your app feel cohesive, intuitive, and thoughtfully designed. It also makes writing for your app easier, as you can return to these patterns again and again.

**Adopt capitalization rules that align with your app's style, then apply them consistently.** While certain components, like button labels, have specific guidelines, how you format text reflects your app's voice. Title case is generally considered formal, while sentence case is more casual. Choose a style for each UI element type and use it consistently throughout your app — for example, title case for all alerts or sentence case for all headlines.

**Give clear guidance and use consistent language throughout processes with multiple steps.** If your app has a flow that spans multiple screens, decide how you want to label the actions that take people from one step to the next. Begin with language like "Get Started" to indicate you're starting a flow. You can use the button label to hint at the next step, or use terms like "Continue" or "Next," but be consistent with what you choose. Make it clear when a flow is complete by using language like "Done."

**Use possessive pronouns sparingly.** Possessive pronouns like *my* and *your* are often unnecessary to establish context. For example, "Favorites" conveys the same message as "Your Favorites," and is more succinct. If you do use possessive pronouns, use them consistently throughout your app, and try not to switch perspectives. Avoid using *we* altogether because it may be unclear who the "we" in question refers to. This is particularly problematic in error messages like "We're having trouble loading this content." Something like "Unable to load content" is much clearer.

**Write for how people use each device.** People may use your app on several types of devices. While your language needs to be consistent across them, think about where it would be helpful to adjust your text to make it suitable for different devices. Make sure you describe gestures correctly on each device — for example, not saying "click" for a touch device like iPhone or iPad where you mean "tap." Where and how people use a device, its screen size, and its location all affect how you write for your app. iPhone and Apple Watch, for example, offer opportunities for personalization, but their small screens require brevity. TVs, on the other hand, are often in common living spaces, and several people are likely to see anything on the screen, so consider who you're addressing. Bigger screens also require brevity, as the text must be large for people to see it from a distance.

**Provide clear next steps on any blank screens.** An empty state, like a completed to-do list or bookmarks folder with nothing in it, can provide a good opportunity to make people feel welcome and educate them about your app. Empty states can also showcase your app's voice, but make sure that the content is useful and fits the context. An empty screen can be daunting if it isn't obvious what to do next, so guide people on actions they can take, and give them a button or link to do so if possible. Remember that empty states are usually temporary, so don't show crucial information that could then disappear.

**Write clear error messages.** It's always best to help people avoid errors. When an error message is necessary, display it as close to the problem as possible, avoid blame, and be clear about what someone can do to fix it. For example, "That password is too short" isn't as helpful as "Choose a password with at least 8 characters." Remember that errors can be frustrating. Interjections like "oops!" or "uh-oh" are typically unnecessary and can sound insincere. If you find that language alone can't address an error that's likely to affect many people, use that as an opportunity to rethink the interaction.

**Choose the right delivery method.** There are many ways to get people's attention, whether or not they are actively using your app. When there's something you want to communicate, consider the urgency and importance of the message. Think about the context in which someone might see the message, whether it requires immediate action, and how much supporting information someone might need. Choose the correct delivery method, and use a tone appropriate for the situation. For guidance, see Notifications, Alerts, and Action sheets.

**Keep settings labels clear and simple.** Help people easily find the settings they need by labeling them as practically as possible. If the setting label isn't enough, add an explanation. Describe what it does when turned on, and people can infer the opposite. In the Handwashing Timer setting for Apple Watch, for example, the description explains that a timer can start when you're washing your hands. It isn't necessary to tell you that a timer won't start when this setting is off. If you need to direct someone to a setting, provide a direct link or button, rather than trying to describe its location. For guidance, see Settings.

**Show hints in text fields.** If your app allows people to enter their own text, like account or contact information, label all fields clearly, and use hint or placeholder text so people know how to format the information. You can give an example in hint text, like "name@example.com," or describe the information, such as "Your name." Show errors right next to the field, and instruct people how to enter the information correctly, rather than scolding them for not following the rules. "Use only letters for your name" is better than "Don't use numbers or symbols." Avoid robotic error messages with no helpful information, like "Invalid name." For guidance, see Text fields.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, tvOS, visionOS, or watchOS — the guidance above applies uniformly across all six platforms.

## Native implementation

**Related**
- Apple Style Guide
- Writing inclusively
- Inclusion
- Accessibility
- Color

**Referenced elsewhere in this guidance**
- VoiceOver — cited alongside Writing inclusively when choosing accessible, jargon-free language
- Localization — cited as the developer-facing counterpart to writing for everyone
- Notifications, Alerts, and Action sheets — cited when choosing the right delivery method for a message
- Settings — cited for linking directly to a setting instead of describing its location in prose
- Text fields — cited for hint text, placeholder text, and inline field-error patterns

**Videos**
- Craft clear names for features and labels in your app
- Make a big impact with small writing changes
- Writing for interfaces

This page names no concrete APIs (no localization or accessibility-label API calls appear in the source); its guidance is entirely about word choice and content strategy, implemented through whatever text and localization APIs your platform already uses (see Localization for the developer-facing implementation path).

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy. Because this page is about word choice and content strategy rather than rendering mechanics, almost all of it transfers to the web unchanged — voice and tone, plain language, action-oriented labels, avoiding "we," clear error messages, empty-state guidance, and settings-label clarity are platform-agnostic writing advice. The few points below are where the web genuinely diverges.

**Labeling form fields → the `<label>` element and `aria-label` are the direct equivalent of "label all fields clearly," with one added constraint.** Apple says to label fields clearly and allows hint or placeholder text to carry formatting guidance. On the web, a visible, programmatically associated `<label>` (or an `aria-label`/`aria-labelledby` when no visible label is feasible) is the accessibility-tree equivalent of a field label read aloud by VoiceOver. The added constraint is that placeholder text alone is not a substitute for a label on the web: it disappears once someone starts typing and often fails contrast requirements, so a person who loses their place mid-form has no label left to read. Apple's page doesn't need to make this distinction because native text fields keep a persistent label by default; web forms need the label and the hint to be two separate, both-persistent elements.

**ARIA label and live-region text → parallels Apple's accessibility-label advice, plus a dynamic-announcement layer Apple's page doesn't address.** The same "be clear, be concise, avoid jargon" standard Apple applies to VoiceOver labels applies directly to `aria-label` and `alt` text. The genuine addition on the web is `aria-live` regions: when an error or status message appears without a page reload (the direct web analogue of Apple's "display an error as close to the problem as possible"), it must also be exposed to assistive technology as it appears, not just positioned near the field visually — a concern this page doesn't need to raise because native error UI is automatically exposed to VoiceOver when it appears.

**Title case vs. sentence case → the same choice, but web convention leans further toward sentence case.** Apple frames this as a style decision with title case reading as more formal and sentence case as more casual, applied consistently per UI element type. Web UI — buttons, form labels, navigation — has converged more heavily on sentence case than native app chrome has, partly because sentence case is cheaper to localize (it doesn't require per-language title-casing rules) and reads faster in body-dense layouts like responsive web pages. The underlying instruction is identical: pick one rule per element type and hold it everywhere.

**Brevity for small screens vs. big screens → responsive breakpoints replace Apple's fixed device categories.** Apple's advice to keep iPhone and Apple Watch copy brief, and to keep TV copy brief for legibility at a distance, maps on the web to writing shorter link and button text at narrow viewport widths and larger, shorter strings for TV-scale or projected web experiences. The difference is that Apple can write once per named device; a responsive layout has to hold up across a continuous range of widths, so copy-length rules need to be tied to container or viewport breakpoints rather than to a fixed set of device targets.

**Character-limit constraints → native UI chrome enforces limits the browser won't.** Apple's own page states no numeric character limits — its constraint is qualitative ("must be large for people to see it from a distance," "small screens require brevity") because native components like buttons and tab bars truncate predictably and consistently across an OS. A `<button>` or a flex item on the web won't truncate the same way by default, and behavior varies by browser and layout, so web copy needs either an explicit line-clamp/truncation rule or a length budget decided in advance — a design decision Apple's platforms make for you and the web does not.

## Do / Don't

| Do | Don't |
|---|---|
| Use a verb for button and link labels ("Send") | Use vague or overly clever labels ("Let's do it!") |
| Use descriptive link text ("Learn more about UX Writing") | Use "Click here" as link text |
| Say "Unable to load content" | Say "We're having trouble loading this content" |
| Say "tap" for touch devices like iPhone or iPad | Say "click" for a touch-device gesture |
| Say "Choose a password with at least 8 characters" | Say "That password is too short" |
| Write matter-of-fact error copy | Open errors with interjections like "oops!" or "uh-oh" |
| Say "Use only letters for your name" | Say "Don't use numbers or symbols" |
| Give a specific, actionable field error | Show a robotic error with no useful information ("Invalid name") |
| Describe only what a setting does when turned on | Explain both the on and off states of a setting |
| Provide a direct link or button to a setting | Describe a setting's location in prose |
| Pick one capitalization style per UI element type and hold it | Mix title case and sentence case within the same element type |
| Use possessive pronouns sparingly and consistently | Switch between "my," "your," and "we" within the same app |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
