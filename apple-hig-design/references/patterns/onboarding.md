---
title: Onboarding
url: https://developer.apple.com/design/human-interface-guidelines/onboarding
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2024-06-10
---

# Onboarding

Onboarding can help people get a quick start using your app or game.

## Core guidance

Ideally, people can understand your app or game simply by experiencing it, but if onboarding is necessary, design a flow that's fast, fun, and optional. When available, onboarding occurs after launching is complete — it isn't part of the launch experience.

### Best practices

**Teach through interactivity.** People tend to grasp and retain information better when they can actually perform the task they're learning about instead of just viewing instructional material. As much as possible, provide an interactive onboarding experience where people can safely test an action, discover a feature, or try out a game mechanic.

**Consider providing a collection of context-specific tips instead of a single onboarding flow.** Integrating contextually relevant tips into your experience can help people learn about their current task while they make progress in your app or game. A context-specific tip can also help people learn better because it lets them concentrate on a single action or task before encountering new information. When you have instructional content that refers to a specific area of the interface, display these instructions near that area. For developer guidance, see TipKit.

**If you need to present a prerequisite onboarding flow, design a brief, enjoyable experience that doesn't require people to memorize a lot of information.** When onboarding is quick and entertaining, people are more likely to complete it. In contrast, if you try to teach too much, people can feel overwhelmed and may be less likely to remember what they learned.

**If it makes sense to offer a separate tutorial, consider making it optional.** If you let people skip the tutorial when they first launch your app or game, don't present it again on subsequent launches, but make sure it's easy for people to find if they want to view it later — for example, in a help, account, or settings area within your app or game.

**Keep onboarding content focused on the experience you provide.** People enter your onboarding flow to learn about your app or game; they don't need to learn how to use the system or the device.

### Additional content

**Briefly display a splash screen if necessary.** If you need to include a splash screen, design a beautiful graphic that communicates succinctly. Aim to display your splash screen just long enough for people to absorb the information at a glance without feeling that it's delaying their experience.

**Don't let large downloads hinder onboarding.** People want to start using your app or game immediately after first launching it, whether they participate in an onboarding flow or skip it. Consider including enough media and other content in your software package to prevent people from having to wait for downloads to complete before they can start interacting with your app or game. For guidance, see Launching.

**Avoid displaying licensing details within your onboarding flow.** Let the App Store display agreements and disclaimers so people can read them before downloading your app or game. If you must include these items within the onboarding flow, integrate them in a balanced way that doesn't disrupt the experience.

### Additional requests

**Postpone nonessential setup flows or customization steps.** Provide reasonable default settings so most people can immediately start interacting with your app or game without performing additional configuration.

**If your app or game needs access to private data or resources before it can function, consider integrating the permission request into your onboarding flow.** Making the request during your onboarding flow gives you the opportunity to show people why your app or game needs their permission and the benefits of granting it. Otherwise, present a permission request when people first access the specific function that relies on private data or resources. For guidance, see Requesting permission.

**Prefer letting people experience your app or game before prompting them for ratings or purchases.** People can be more likely to respond positively to such requests when they've had a chance to become engaged with your app or game.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, tvOS, visionOS, or watchOS.

## Native implementation

**Related**
- Launching
- Feedback
- Offering help

**Developer documentation**
- TipKit
- Requesting permission

**Videos:** Discoverable design · Designing Award Winning Apps and Games · Love at First Launch

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**"Onboarding occurs after launching is complete" → don't gate the first render on an onboarding decision.** Apple draws a hard line between launching (getting the app usable) and onboarding (teaching it). On the web the equivalent mistake is a splash-then-tour sequence that blocks time-to-interactive behind a modal carousel before the person can even see the product. Render the real interface first; layer onboarding on top of, or after, a usable page — not in front of it.

**"Teach through interactivity" → progressive disclosure inside the real UI beats a slideshow.** A multi-screen "here's what you can do" carousel is the web-native version of the single onboarding flow Apple is steering you away from in the very next rule. Coach marks, empty states with a first action pre-highlighted, and inline hints that appear the first time a person reaches a feature all teach through doing rather than watching, which is what this rule is actually asking for regardless of platform.

**"Context-specific tips instead of a single onboarding flow" → TipKit's nearest web analogue is a small, dismissible, rules-gated tooltip system, not a tour library.** Most web "product tour" libraries default to exactly the pattern Apple recommends against: a sequential, modal walkthrough of the whole interface. The better mapping is a lightweight tip component that appears near the relevant control, fires once per feature, respects a dismissed/seen state in storage, and never blocks interaction with the page underneath it.

**"Make the tutorial easy to find later, don't force it again" → persist a per-user 'has seen onboarding' flag, and surface a manual re-entry point.** This is a straightforward state-management problem on the web: store completion in account state (or `localStorage` for anonymous sessions) and expose "Show me how this works again" from a help or settings menu, exactly as Apple describes.

**"Don't let large downloads hinder onboarding" → doesn't map to app-package weight, but does map to bundle size and lazy-loading.** The mechanism differs — there's no equivalent to shipping media inside an installed binary — but the underlying principle is the same: don't make people wait on a network fetch before they can start interacting. Route-based code-splitting and lazy-loading non-critical assets after first paint achieves the same "immediately interactive" outcome Apple wants from bundling media in the package.

**"Avoid licensing details in onboarding" → keep terms-of-service acceptance out of the product tour.** A checkbox for terms belongs at account creation or checkout, not woven into a feature walkthrough — the reasoning transfers exactly: legal content and a persuasive first-run experience have different jobs and reading someone's terms of service is not itself onboarding.

**Permission requests → the browser's own permission prompt is even less recoverable than a native one, so timing matters more, not less.** iOS lets an app re-prompt via Settings if a person changes their mind. Many browsers make a denied permission (camera, location, notifications) far harder to reverse — often requiring the person to find a per-site settings icon in the address bar. This raises the stakes on Apple's advice to ask in context, with an explanation, at the moment the benefit is obvious, rather than issuing a blanket request during onboarding when the payoff is still abstract.

**Ratings/purchase prompts → equally applicable, with the browser's own "add to home screen" and notification-permission prompts as siblings.** The same patience Apple asks for before an App Store rating prompt applies to a web app's install prompt or push-notification opt-in: ask after a person has had a genuine win, not on page load.

## Do / Don't

| Do | Don't |
|---|---|
| Let onboarding be fast, fun, and optional | Make onboarding a precondition for using the app |
| Teach through an interactive, hands-on flow | Present a passive slideshow of instructional screens |
| Use context-specific tips near the relevant UI | Front-load every feature into one long onboarding flow |
| Let people skip a tutorial and find it again later | Force a skipped tutorial to reappear on every launch |
| Ship enough content to avoid blocking on downloads | Make people wait for downloads before they can start |
| Request permissions in context, with a clear reason | Bundle a blanket permission request into onboarding |
| Let people experience the app before asking for a rating | Prompt for ratings or purchases before any engagement |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
