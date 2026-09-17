---
title: Loading
url: https://developer.apple.com/design/human-interface-guidelines/loading
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2025-06-09
---

# Loading

The best content-loading experience finishes before people become aware of it.

## Core guidance

If your app or game loads assets, levels, or other content, design the behavior so it doesn't disrupt or negatively impact the user experience.

### Best practices

**Show something as soon as possible.** If you make people wait for loading to complete before displaying anything, they can interpret the lack of content as a problem with your app or game. Instead, consider showing placeholder text, graphics, or animations as content loads, replacing these elements as content becomes available.

**Let people do other things in your app or game while they wait for content to load.** Loading content in the background helps give people access to other actions. For example, a game could load content in the background while players learn about the next level or view an in-game menu. For developer guidance, see Improving the player experience for games with large downloads.

**If loading takes an unavoidably long time, give people something interesting to view while they wait.** For example, you might provide gameplay hints, display tips, or introduce people to new features. Gauge the remaining loading time as accurately as possible to help you avoid giving people too little time to enjoy your placeholder content or having so much time that you need to repeat it.

**Improve installation and launch time by downloading large assets in the background.** Consider using the Background Assets framework to schedule asset downloads — like game level packs, 3D character models, and textures — to occur immediately after installation, during updates, or at other nondisruptive times.

### Showing progress

**Clearly communicate that content is loading and how long it might take to complete.** Ideally, content displays instantly, but for situations where loading takes more than a moment or two, you can use system-provided components — called progress indicators — to show that loading is ongoing. In general, use a determinate progress indicator when you know how long loading will take, and an indeterminate progress indicator when you don't. For guidance, see Progress indicators.

**For games, consider creating a custom loading view.** Standard progress indicators work well in most apps, but can sometimes feel out of place in a game. Consider designing a more engaging experience by using custom animations and elements that match the style of your game.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, tvOS, or visionOS.

### watchOS

**As much as possible, avoid showing a loading indicator in your watchOS experience.** People expect quick interactions with their Apple Watch, so aim to display content immediately. In situations where content needs a second or two to load, it's better to display a loading indicator than a blank screen.

## Native implementation

**Related**
- Launching
- Progress indicators

**Developer documentation**
- Background Assets
- Improving the player experience for games with large downloads

**Videos:** Discover Apple-Hosted Background Assets

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**"The best loading experience finishes before people become aware of it" → this is a performance-budget statement, not a spinner-design statement.** Apple's framing puts the emphasis in the right place: the goal is for loading to not need a UI at all. On the web that means treating this section's guidance as secondary to reducing payload size, deferring non-critical requests, and prioritizing above-the-fold content — the same discipline Launching's Core Web Vitals mapping describes. A beautifully designed progress indicator is a fallback for when you've failed to make loading invisible, not the target outcome.

**"Show something as soon as possible" → render a skeleton or partial UI immediately, then stream in content.** This is one of the most direct translations in the whole pattern set. A blank white page while data fetches reads, to a user, exactly like Apple describes: a possible problem, not a system doing work. Skeleton screens, optimistic UI, and streaming server-rendered HTML (so the shell paints before data resolves) all implement this rule. The mechanism differs by framework, but the goal — never show nothing — is identical to Apple's.

**"Let people do other things while they wait" → don't block interaction on an in-flight request unless you truly must.** If a page fetch is loading a secondary panel, the rest of the page should stay interactive. This argues against full-page loading overlays for partial updates — reserve a blocking loading state for the cases where the content being fetched genuinely gates everything else, mirroring Apple's own distinction between background loading and disruptive loading.

**Determinate vs. indeterminate progress indicators → the same choice, made the same way.** If you can compute percent-complete (a known file size, a known number of steps), show it — a determinate progress bar sets accurate expectations and reduces perceived wait, exactly as Apple's guidance implies. If you can't compute it, an indeterminate spinner is honest about that uncertainty; don't fake a percentage you don't actually know, which is a trap some web loading libraries fall into with animated "progress" that isn't tied to anything real.

**"Gauge the remaining time accurately... avoid repeating placeholder content" → applies to loading-state copy and skeleton animations too.** A skeleton screen that loops for far longer than expected starts to read as broken, the web equivalent of Apple's placeholder-content-repeats problem. If a fetch is known to be slow, say so and give a real estimate rather than looping an indefinite shimmer past the point where it stops reading as "in progress" and starts reading as "stuck."

**Background asset downloading → service workers and prefetching are the nearest web equivalent, with weaker guarantees.** The Background Assets framework can schedule downloads at OS-managed, power-aware times even when the app isn't running. The web's closest tools — Background Fetch, service-worker prefetching, `<link rel="prefetch">` — exist, but browser support and the guarantees around them are considerably less reliable than a first-party OS framework, and iOS Safari in particular restricts background execution tightly. Treat aggressive background prefetching as an enhancement you verify works in your actual target browsers, not a dependable baseline the way Background Assets is on Apple platforms.

**watchOS's "avoid a loading indicator, prefer immediate content" → the general web lesson is that a spinner is a design failure for anything users expect to be instant.** The specific hardware reasoning (a tiny always-glanced-at screen) doesn't transfer, but the underlying principle does: for interactions users expect to be effectively instant (opening a menu, toggling a filter), don't reach for a spinner as the default response to any latency — fix the latency, or make the UI update optimistically before the network confirms it.

## Do / Don't

| Do | Don't |
|---|---|
| Show placeholder content the moment loading begins | Display a blank screen while content loads |
| Let people keep interacting while background content loads | Block the entire experience for a non-blocking fetch |
| Use a determinate indicator when you know the duration | Fake a percentage you can't actually measure |
| Use an indeterminate indicator when duration is unknown | Show a determinate bar with a guessed value |
| Give people something engaging during unavoidable long waits | Let placeholder content loop long enough to feel broken |
| Schedule large downloads in the background at nondisruptive times | Force people to wait through a large download before starting |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
