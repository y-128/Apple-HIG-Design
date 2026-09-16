---
title: Progress indicators
url: https://developer.apple.com/design/human-interface-guidelines/progress-indicators
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2023-09-12
---

# Progress indicators

Progress indicators let people know that your app isn't stalled while it loads content or performs lengthy operations.

## Core guidance

Some progress indicators also give people a way to estimate how long they have to wait for something to complete. All progress indicators are transient, appearing only while an operation is ongoing and disappearing after it completes.

Because the duration of an operation is either known or unknown, there are two types of progress indicators:

- **Determinate**, for a task with a well-defined duration, such as a file conversion
- **Indeterminate**, for unquantifiable tasks, such as loading or synchronizing complex data

Both determinate and indeterminate progress indicators can have different appearances depending on the platform. A determinate progress indicator shows the progress of a task by filling a linear or circular track as the task completes. Progress bars include a track that fills from the leading side to the trailing side. Circular progress indicators have a track that fills in a clockwise direction.

> *Image caption:* Progress bar.
> *Image caption:* Circular progress indicator.

An indeterminate progress indicator — also called an activity indicator — uses an animated image to indicate progress. All platforms support a circular image that appears to spin; however, macOS also supports an indeterminate progress bar.

> *Image caption:* An indeterminate progress indicator on macOS.
> *Image caption:* An indeterminate progress indicator on watchOS.

### Best practices

**When possible, use a determinate progress indicator.** An indeterminate progress indicator shows that a process is occurring, but it doesn't help people estimate how long a task will take. A determinate progress indicator can help people decide whether to do something else while waiting for the task to complete, restart the task at a different time, or abandon the task.

**Be as accurate as possible when reporting advancement in a determinate progress indicator.** Consider evening out the pace of advancement to help people feel confident about the time needed for the task to complete. Showing 90 percent completion in five seconds and the last 10 percent in 5 minutes can make people wonder if your app is still working and can even feel deceptive.

**Keep progress indicators moving so people know something is continuing to happen.** People tend to associate a stationary indicator with a stalled process or a frozen app. If a process stalls for some reason, provide feedback that helps people understand the problem and what they can do about it.

**When possible, switch a progress bar from indeterminate to determinate.** If an indeterminate process reaches a point where you can determine its duration, switch to a determinate progress bar. People generally prefer a determinate progress indicator, because it helps them gauge what's happening and how long it will take.

**Don't switch from the circular style to the bar style.** Activity indicators (also called spinners) and progress bars are different shapes and sizes, so transitioning between them can disrupt your interface and confuse people.

**If it's helpful, display a description that provides additional context for the task.** Be accurate and succinct. Avoid vague terms like loading or authenticating because they seldom add value.

**Display a progress indicator in a consistent location.** Choosing a consistent location for a progress indicator helps people reliably find the status of an operation across platforms or within or between apps.

**When it's feasible, let people halt processing.** If people can interrupt a process without causing negative side effects, include a Cancel button. If interrupting the process might cause negative side effects — such as losing the downloaded portion of a file — it can be useful to provide a Pause button in addition to a Cancel button.

**Let people know when halting a process has a negative consequence.** When canceling a process results in lost progress, it's helpful to provide an alert that includes an option to confirm the cancellation or resume the process.

## Platform considerations

No additional considerations for tvOS or visionOS.

### iOS, iPadOS

#### Refresh content controls

A refresh control lets people immediately reload content, typically in a table view, without waiting for the next automatic content update to occur. A refresh control is a specialized type of activity indicator that's hidden by default, becoming visible when people drag down the view they want to reload. In Mail, for example, people can drag down the list of Inbox messages to check for new messages.

**Perform automatic content updates.** Although people appreciate being able to do an immediate content refresh, they also expect automatic refreshes to occur periodically. Don't make people responsible for initiating every update. Keep data fresh by updating it regularly.

**Supply a short title only if it adds value.** Optionally, a refresh control can include a title. In most cases, this is unnecessary, as the animation of the control indicates that content is loading. If you do include a title, don't use it to explain how to perform a refresh. Instead, provide information of value about the content being refreshed. A refresh control in Podcasts, for example, uses a title to tell people when the last podcast update occurred.

### macOS

In macOS, an indeterminate progress indicator can have a bar or circular appearance. Both versions use an animated image to indicate that the app is performing a task.

> *Image caption:* Indeterminate progress bar.
> *Image caption:* Indeterminate circular progress indicator.

**Prefer an activity indicator (spinner) to communicate the status of a background operation or when space is constrained.** Spinners are small and unobtrusive, so they're useful for asynchronous background tasks, like retrieving messages from a server. Spinners are also good for communicating progress within a small area, such as within a text field or next to a specific control, such as a button.

**Avoid labeling a spinning progress indicator.** Because a spinner typically appears when people initiate a process, a label is usually unnecessary.

### watchOS

By default the system displays the progress indicators in white over the scene's background color. You can change the color of the progress indicator by setting its tint color.

> *Image caption:* Progress bar.
> *Image caption:* Circular progress indicator.
> *Image caption:* Activity indicator.

## Native implementation

**Developer documentation**
- `ProgressView` — SwiftUI
- `UIProgressView` — UIKit
- `UIActivityIndicatorView` — UIKit
- `UIRefreshControl` — UIKit
- `NSProgressIndicator` — AppKit

**Key APIs**
- `ProgressView` — SwiftUI view for both determinate and indeterminate progress
- `UIProgressView` — UIKit determinate progress bar
- `UIActivityIndicatorView` — UIKit indeterminate spinner
- `UIRefreshControl` — UIKit pull-to-refresh control
- `NSProgressIndicator` — AppKit progress bar or spinner, determinate or indeterminate

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy. This is one of the cleanest translations in this skill — the web has near-exact native equivalents for both progress-indicator types.

**Determinate → `<progress value="…" max="…">` or `role="progressbar"` with `aria-valuenow`/`aria-valuemin`/`aria-valuemax`.** This is a direct, one-to-one mapping. The `<progress>` element already encodes Apple's semantic distinction: give it a `value` and it's determinate; omit `value` and it's indeterminate, matching Apple's own determinate/indeterminate split exactly. If you build a custom progress bar instead of using `<progress>`, replicate that same state distinction in ARIA rather than inventing a third, ambiguous state.

**"When possible, use a determinate progress indicator" → the same reasoning holds, and it's stronger on the web.** Apple's argument — determinate lets people decide whether to wait, multitask, or abandon the task — applies without modification. On the web there's an additional reason: an indeterminate spinner gives search engines, monitoring tools, and users on slow connections no signal about whether a request is almost done or hung, which matters more when network latency (not local computation) is the dominant source of wait time.

**"Be accurate; even out the pace" → don't fake progress, and be wary of skeleton screens as a substitute.** Apple's warning against a progress bar that jumps to 90% and stalls maps directly to the web anti-pattern of client-side progress bars that animate on a fixed timer disconnected from the actual request. If you can't get real progress events (e.g., from `fetch`'s `ReadableStream` or `XMLHttpRequest.onprogress`), an honest indeterminate indicator is better than a fabricated determinate one. Skeleton screens are a legitimate web-native technique for perceived performance, but they answer a different question ("what will this look like") than a progress indicator ("how much longer") — don't present one as if it were the other.

**"Keep progress indicators moving" → this is where the mapping genuinely breaks down, and it's worth naming explicitly.** Apple's rule assumes continuous animation is free and universally acceptable. On the web, `prefers-reduced-motion: reduce` means a meaningful share of users have asked for exactly the opposite — no continuously spinning or pulsing UI. Apple's own guidance doesn't have to reconcile this because iOS's Reduce Motion setting targets a narrower set of effects than a full spinning-indicator ban. On the web, honor `prefers-reduced-motion` by keeping a static or minimally-animated fallback (a pulsing opacity at a slow, non-vestibular-triggering rate, or a text status like "Loading…") that still signals "not stalled" without continuous motion — don't just disable the indicator entirely, or you reintroduce the exact ambiguity Apple's rule exists to prevent.

**"Don't switch from circular to bar style" → don't swap indicator shape mid-flight, and don't swap loading strategy mid-flight either.** The web-specific version of this same instinct: don't render a spinner, then replace it with a skeleton screen, then replace that with a different placeholder before the real content arrives. Pick one loading representation per operation and commit to it.

**"Let people halt processing" → wire Cancel/Pause buttons to `AbortController`.** The direct implementation of Apple's cancel guidance is an `AbortController` passed into `fetch`, with the Cancel button calling `.abort()`. Apple's Pause-in-addition-to-Cancel case (avoiding loss of a partially downloaded file) maps to the web's `Range` header / resumable-upload patterns — pausing without discarding already-transferred bytes, rather than aborting the whole request.

**Refresh content controls → pull-to-refresh has no native browser element, and PWA/mobile-web implementations should treat that as a signal, not a gap to fill unquestioningly.** There's no HTML equivalent to `UIRefreshControl`; on the mobile web, pull-to-refresh is typically hand-built with touch event listeners and `overscroll-behavior: contain` to prevent the browser's native overscroll from interfering. Apple's own advice to also perform automatic content updates regardless applies just as strongly on the web — don't make pull-to-refresh the only way content gets current, since it's a discoverability-poor gesture that a meaningful fraction of users will never find.

## Do / Don't

| Do | Don't |
|---|---|
| Use a determinate indicator whenever the task's duration is knowable | Default to an indeterminate spinner when real progress data is available |
| Report advancement accurately, evening out an uneven pace | Let a determinate indicator race to 90% and stall on the last stretch |
| Keep the indicator animating for the full duration of the operation | Let an indicator go stationary while work is still happening |
| Switch from indeterminate to determinate once duration becomes knowable | Stay indeterminate after you can measure real progress |
| Keep one indicator shape (circular or bar) for the life of an operation | Switch between circular and bar styles mid-operation |
| Offer Cancel (and Pause, when losing partial progress matters) | Trap people in a process they can't interrupt |
| Warn people when canceling will discard progress | Silently discard progress on cancellation with no confirmation |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
