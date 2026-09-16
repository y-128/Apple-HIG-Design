---
title: Ratings and reviews
url: https://developer.apple.com/design/human-interface-guidelines/ratings-and-reviews
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2023-09-12
---

# Ratings and reviews

People often view the ratings and reviews for an app or game before they download it.

## Core guidance

Delivering a great overall experience is the best way to encourage positive ratings and reviews, but it's also crucial to choose the right time to ask people for feedback. Although every app is different, some possible ways to do this involve looking at how many times or how frequently people launch your app, the number of features someone explores, or the number of tasks they complete.

People can always rate your app within the App Store.

### Best practices

**Ask for a rating only after people have demonstrated engagement with your app or game.** For example, you might prompt people when they complete a game level or a significant task. Avoid asking for a rating on first launch or during onboarding, because people haven't had enough time to gain a clear understanding of your app's value or form an opinion. People may even be more likely to leave negative feedback if they feel an app is asking for a rating before they get a chance to use it.

**Avoid interrupting people while they're performing a task or playing a game.** Asking for feedback can disrupt the user experience and feel like a burden. Look for natural breaks or stopping points in your app or game where a rating request is less likely to be bothersome.

**Avoid pestering people.** Repeated rating requests can be irritating, and may even negatively influence people's opinion of your app. Consider allowing at least a week or two between requests, prompting again after people demonstrate additional engagement with your experience.

**Prefer the system-provided prompt.** iOS, iPadOS, and macOS offer a consistent, nonintrusive way for apps and games to request ratings and reviews. When you identify places in your experience where it makes sense to ask for feedback, the system checks for previous feedback and — if there isn't any — displays an in-app prompt that asks for a rating and an optional written review. People can supply feedback or dismiss the prompt with a single tap or click; they can also opt out of receiving these prompts for all apps they have installed. The system automatically limits the display of the prompt to **three occurrences per app within a 365-day period**. For developer guidance, see `RequestReviewAction`.

**Weigh the benefits of resetting your summary rating against the potential disadvantage of showing fewer ratings.** When you release a new version of your app or game, you can reset the summary of individual ratings you received since the last reset. Although resetting means that the ratings reflect the current version, it also tends to result in having fewer ratings overall, which can discourage some people from downloading your app. For developer guidance, see Reset app summary rating.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, tvOS, visionOS, or watchOS.

> **Source limitation:** Although the Platform considerations section states there are no additional per-platform considerations, the Best practices text notes that the system-provided rating prompt is specifically an iOS, iPadOS, and macOS capability (`RequestReviewAction`). The source doesn't clarify whether or how the system prompt is available on tvOS, visionOS, or watchOS.

## Specifications

| Attribute | Value |
|---|---|
| Maximum system-prompt occurrences | 3 per app within a 365-day period |

## Native implementation

**Related**
- Ratings, reviews, and responses

**Developer documentation**
- `RequestReviewAction` — StoreKit

**Key APIs**
- `RequestReviewAction` — trigger the system-provided rating and review prompt

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**The core timing principle transfers completely, independent of platform.** "Ask after demonstrated engagement, not on first contact" and "avoid interrupting an active task" are behavioral psychology, not App Store mechanics — they apply identically to a web app asking for a testimonial, a review, an NPS score, or a feedback survey. The reasoning Apple gives (people haven't formed an opinion yet; interrupting a task reads as a burden) doesn't reference any platform-specific capability, so it needs no translation at all.

**The system-provided prompt → there is no web equivalent, and this is where the mapping genuinely breaks.** `RequestReviewAction`'s value isn't just its UI, it's that the *operating system* owns the rate limiting (three prompts per 365 days, automatic suppression if the person already responded, a global opt-out that covers every app at once) and that the resulting rating posts to a review surface — the App Store — that has independent trust with the reader. A web app has no OS-level actor to delegate to. Any "leave a review" prompt on the web is entirely the site's own UI, the site has to build and enforce its own frequency cap in application logic, and the destination (Trustpilot, Google reviews, an app's own testimonial system) is a third party the site doesn't control either. Where Apple's guidance says "prefer the system prompt," the honest web instruction is "you have to be your own rate limiter, because nothing else will be."

**"Avoid pestering people" → build the suppression state yourself, since the browser won't.** Without an OS tracking prompt history across every site a person visits, a web app needs to persist its own record (a cookie, local storage, or a server-side flag tied to the account) of when it last asked and what the person answered, and needs to honor a real cooldown and a real "don't ask again" the way Apple's system does automatically. Skipping this because "the browser doesn't provide it" is not a valid excuse — it just means the discipline shifts from relying on the platform to writing the equivalent logic explicitly.

**"Weigh resetting your summary rating against showing fewer ratings" → the same trade-off applies to third-party review widgets that support review resets or version-scoping**, but the specific mechanic (App Store version-based rating resets) is a StoreKit feature with no direct web equivalent; a website generally can't selectively reset only some reviews the way an app version reset does, so this piece of guidance doesn't transfer as a concrete action, only as a reminder that suppressing old feedback trades authenticity for currency.

## Do / Don't

| Do | Don't |
|---|---|
| Ask for a rating after people show real engagement | Ask for a rating on first launch or during onboarding |
| Time the request for a natural break or stopping point | Interrupt an active task or gameplay to ask for a rating |
| Space repeated requests at least a week or two apart | Prompt again immediately after a dismissal |
| Prefer the system-provided rating and review prompt | Build a custom prompt when the system one is available and sufficient |
| Weigh the trade-off before resetting your summary rating | Reset ratings reflexively on every release without considering the cost |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
