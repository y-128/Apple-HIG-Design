---
title: Live-viewing apps
url: https://developer.apple.com/design/human-interface-guidelines/live-viewing-apps
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Live-viewing apps

As you design a live-viewing app, prioritize the content and create fun, fluid interactions that encourage immersion in the live-viewing experience.

## Core guidance

Live-viewing apps need to elevate and prioritize live content. In every screen, draw people's attention to live content and make sure they can distinguish it from video-on-demand (VOD) content at a glance.

### Best practices

**Feature live content prominently and make it easy to access.** People come to your app to watch content, so you want to minimize the interval between starting your app and playing content. When live content is in the first tab, people don't have to tap more than once to start viewing it.

**Let people tap once — or not at all — to start playback.** For example, you might display a Watch Now button on top of featured or recently viewed live content. When people tap this button, it immediately disappears and playback begins, replacing your app's UI with a full-screen, immersive viewing experience.

**Make sure live content looks live.** People need to be able to distinguish live content from VOD content. Although simply playing live content is the best way to make it feel live, you can also help people recognize live content by marking it in some way. For example, you might display other channels in a collection row titled "Live" and give each item a visual indicator — such as a badge, symbol, or sash — that identifies it as live.

**Consider indicating the progress of currently playing live content.** People appreciate knowing where they'll land when they jump into in-progress live content. You can use a progress bar or other indicator to show people how much content remains.

**Give people additional actions and viewing alternatives.** In addition to playback, which always needs to be the primary action, make it easy for people to record, restart, download, and perform other actions that you support. Display these actions in the same order throughout your app — for example, Watch, Start Over, Record, and Favorite. Also, if the currently playing content is playing again at other times, show this information so that people can schedule their viewing.

**Consider using a content footer for browsing channels during playback.** A content footer lets people browse without taking them out of the live playback experience. If you decide to use a content footer, be sure to:

- Give it a subtle treatment, such as a darkening, to keep text legible and help all items remain visually distinct from the content playing behind it.
- Make it easy for people to identify the thumbnail that represents the currently playing content by, for example, badging the thumbnail or tinting its progress bar.
- Match the categories in the content footer to those in your electronic program guide (for related guidance, see EPG experience).
- Design a simple, predictable way for people to invoke and dismiss the content footer — for example, if swiping up invokes the footer, people would expect swiping down to dismiss it.

**Provide instant visual feedback when people change channels.** This is essential for two reasons: people need confirmation that they've arrived at the channel they want, and providing feedback can give the streaming content some time to load.

**Match audio to the current context.** When people start playing live content, they expect the audio to match even if they switch to browsing while the content plays in the background. However, when people navigate away from the live tab in your app, they leave the live-viewing context, so audio needs to stop.

### EPG experience

Live-viewing apps typically provide an electronic program guide (EPG) that contains information about scheduled programming. Follow these guidelines to give people a streamlined EPG experience that feels designed specifically for your live-viewing app.

**Prominently display current information and make it easy to return to playback.** When people first open the EPG, the current program, channel, and time needs to be easy to spot so they can instantly return to the current channel.

**Make browsing the EPG effortless.** A typical EPG contains a lot of information, so it's important to help people page, scroll, or jump through it easily. Also consider providing a My Channels group or a Favorites group that gives people quick access to the content they view most often.

**Group content into familiar categories to help people find it more easily.** For example, you might use categories like Movies, TV Shows, Kids, Sports, and Popular. If your app includes a content footer, organize content thumbnails using the same categories as in the EPG.

**Let people browse the EPG without leaving their current content.** For example, you can continue playing content in a picture-in-picture (PiP) mode or in the background while people browse the EPG.

### Cloud DVR

If you support digital video recording (DVR) in the cloud, follow these guidelines to provide a great recording experience in your live-viewing app.

**Let people start and stop recording from the info panel.** While live-streaming, people want to reveal the info panel to start recording immediately.

**Let people record a future program in a view that provides details about the content.** Also, give people the option to record only that program or all future episodes.

**Help people adapt the recording experience to their needs.** Let people specify precisely what they want to record, such as only the current episode, only new episodes, or only games that involve specific teams.

**Allow playback and other content-specific actions within your cloud DVR area.** When people open a view that displays content details in your cloud DVR section, let them play or delete content and, if applicable, adjust recording settings.

**Consider offering a control that lets people manage cloud DVR settings.** For example, you might let people delete recordings they've already watched or content that's older than a certain number of days. Ideally, help people avoid running out of space by letting them set up automatic storage management, which overwrites the oldest or already viewed content.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, tvOS, visionOS, or watchOS.

## Native implementation

**Related**
- Remotes
- Playing video

> **Source limitation:** This page's Resources section lists only Related links in the captured source; no Developer documentation or Videos entries were present.

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**"Minimize the interval between opening the app and playing content" → treat time-to-first-frame as the core performance budget.** Apple's "tap once, or not at all" standard is a statement about perceived latency, and the web equivalent is largely a loading-and-caching problem: prefetching the live stream manifest, avoiding a client-side routing waterfall before the player mounts, and treating the live stream URL as something resolvable before any other page chrome finishes rendering. A live-viewing web page that shows a full app shell, then a spinner, then a video element defeats the same expectation Apple is describing.

**"Make sure live content looks live" → the badge/indicator pattern transfers directly, the ambient cue does not.** A "Live" badge, a red dot, or a pulsing indicator is straightforward HTML/CSS. What doesn't transfer is Apple's implicit assumption of a persistent system clock and consistent progress-bar semantics across apps; on the web, you have to build the "how much of this live window remains" indicator yourself with no shared platform convention to lean on, so be more explicit in labeling than a native app would need to be.

**Picture-in-Picture for EPG browsing → Document Picture-in-Picture makes this genuinely buildable, with the same caveat as `playing-video.md`: browser support is uneven.** Letting people keep watching in a small window while browsing an electronic program guide in the same tab is close to exactly what the Document PiP API and the plain `<video>` PiP request exist for, in Chromium-based browsers; Safari's PiP support is more limited for arbitrary page content and Firefox lacks the Document PiP API outright, so this pattern degrades to "switch away and lose video" on a meaningful share of browsers.

**"Audio needs to stop when people navigate away from the live tab" → this is close to automatic on the web, for the wrong reason.** A single-page app that unmounts its video element on navigation naturally stops audio; the risk is the opposite of Apple's platform, where background audio persistence takes deliberate work to build. On the web, background audio persistence across a route change takes deliberate work to build (keeping the underlying media element alive across a client-side navigation), so if a product wants live audio to survive backgrounding the tab, that has to be engineered on top of the default rather than suppressed.

**Cloud DVR, content footer channel-browsing during playback, and EPG paging → these transfer as UI patterns but not as platform capability.** None of this depends on anything TV/Apple-specific; a content footer overlay, a channel guide grid, and a "record this episode / all episodes" choice are ordinary web UI problems. The place the mapping thins out is input: Apple's guidance assumes a remote-control or touch interaction model with well-understood swipe-to-invoke/swipe-to-dismiss gestures; a web implementation needs to support keyboard and pointer interaction as first-class, not translate remote-control gestures literally.

## Do / Don't

| Do | Don't |
|---|---|
| Put live content in the first tab so it's reachable in one tap | Bury live content behind multiple navigation steps |
| Visually distinguish live content from VOD content | Make people guess whether something is live or on-demand |
| Show a progress indicator for in-progress live content | Drop people into live content with no sense of how much remains |
| Keep primary, secondary, and additional actions in a consistent order across the app | Reorder actions like Watch, Record, and Favorite inconsistently between screens |
| Give instant visual feedback on channel change | Leave people uncertain whether a channel switch registered |
| Stop audio when people leave the live-viewing context | Let live audio keep playing after people navigate away from the live tab |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
