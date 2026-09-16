---
title: AirPlay
url: https://developer.apple.com/design/human-interface-guidelines/airplay
platforms: [iOS, iPadOS, macOS, tvOS]
last_updated: 2023-05-02
---

# AirPlay

AirPlay lets people stream media content wirelessly from iOS, iPadOS, macOS, and tvOS devices to Apple TV, HomePod, and TVs and speakers that support AirPlay.

## Core guidance

### Best practices

**Prefer the system-provided media player.** The built-in media player offers a standard set of controls and supports features like chapter navigation, subtitles, closed captioning, and AirPlay streaming. It's also easy to implement, provides a consistent and familiar playback experience across the system, and accommodates the needs of most media apps. Consider designing a custom video player only if the system-provided player doesn't meet your app's needs.

**Provide content in the highest possible resolution.** Your HTTP Live Streaming (HLS) playlist needs to include the full range of available resolutions so that people can experience your content in the resolution that's appropriate for the device they're using (AVFoundation automatically selects the resolution based on the device). If you don't include a range of resolutions, your content looks low quality when people stream it to a device that can play at higher resolutions. For example, content that looks great on iPhone at 720p will look low quality when people use AirPlay to stream it to a 4K TV.

**Stream only the content people expect.** Avoid streaming content like background loops and short video experiences that make sense only within the context of the app itself.

**Support both AirPlay streaming and mirroring.** Supporting both features gives people the most flexibility.

**Support remote control events.** When you do, people can choose actions like play, pause, and fast forward on the lock screen, and through interaction with Siri or HomePod.

**Don't stop playback when your app enters the background or when the device locks.** For example, people expect the TV show they started streaming from your app to continue while they check their mail or put their device to sleep. In this type of scenario, it's also crucial to avoid automatic mirroring because people don't want to stream other content on their device without explicitly choosing to do so.

**Don't interrupt another app's playback unless your app is starting to play immersive content.** For example, if your app plays a video when it launches or auto-plays inline videos, play this content on only the local device, while allowing current playback to continue.

**Let people use other parts of your app during playback.** When AirPlay is active, your app needs to remain functional. If people navigate away from the playback screen, make sure other in-app videos don't begin playing and interrupt the streaming content.

**If necessary, provide a custom interface for controlling media playback.** If you can't use the system-provided media player, you can create a custom media player that gives people an intuitive way to enter AirPlay. If you need to do this, be sure to provide custom buttons that match the appearance and behavior of the system-provided ones, including distinct visual states that indicate when playback starts, is occurring, or is unavailable. Use only Apple-provided symbols in custom controls that initiate AirPlay, and position the AirPlay icon correctly in your custom player — that is, in the lower-right corner (in iOS 16 and iPadOS 16 and later).

### Using AirPlay icons

You can download AirPlay icons in Resources. You have the following options for displaying the AirPlay icon in your app.

**Black AirPlay icon.** Use the black AirPlay icon on white or light backgrounds when other technology icons also appear in black.

**White AirPlay icon.** Use the white AirPlay icon on black or dark backgrounds when other technology icons also appear in white.

**Custom color AirPlay icon.** Use a custom color when other technology icons also appear in the same color.

**Position the AirPlay icon consistently with other technology icons.** If you display other technology icons within shapes, you can display the AirPlay icon in the same manner.

**Don't use the AirPlay icon or name in custom buttons or interactive elements.** Use the icon and the name AirPlay only in noninteractive ways.

**Pair the icon with the name AirPlay correctly.** You can show the name below or beside the icon if you also reference other technologies in this way. Use the same font you use in the rest of your layout. Avoid using the AirPlay icon within text or as a replacement for the name AirPlay.

**Emphasize your app over AirPlay.** Make references to AirPlay less prominent than your app name or main identity.

### Referring to AirPlay

**Use correct capitalization when using the term AirPlay.** AirPlay is one word, with an uppercase A and uppercase P, each followed by lowercase letters. If your layout displays only all-uppercase designations, you can typeset AirPlay in all uppercase to match the style of the rest of the layout.

**Always use AirPlay as a noun.** Example usage:

- "Use AirPlay to listen on your speaker"
- "AirPlay to your speaker"
- "You can AirPlay with [App Name]"

**Use terms like works with, use, supports, and compatible.** Example usage:

- "[App Name] is compatible with AirPlay"
- "AirPlay-enabled speaker"
- "You can use AirPlay with [App Name]"
- "[App Name] has AirPlay"

**Use the name Apple with the name AirPlay if desired.** Example: "Compatible with Apple AirPlay"

**Refer to AirPlay if appropriate and to add clarity.** If your content is specific to AirPlay, you can use Airplay to make that clear. You can also refer to AirPlay in technical specifications. Example: "[App Name] now supports AirPlay"

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, or tvOS. Not supported in watchOS.

## Native implementation

**Related**
- Apple Design Resources
- Apple Trademark List
- Guidelines for Using Apple Trademarks and Copyrights

**Developer documentation**
- AVFoundation
- AVKit
- `AVPlayerViewController`
- `usesExternalPlaybackWhileExternalScreenIsActive`
- Remote command center events
- `ambient`

**Videos:** Reaching the Big Screen with AirPlay 2

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. AirPlay is a proprietary wireless streaming protocol between Apple devices and AirPlay-certified receivers — there is no web API that discovers or drives an AirPlay target, and a browser cannot initiate AirPlay streaming or mirroring on its own. This page is honestly platform-specific in its mechanism.

The closest web equivalent for casting media to an external screen is the Remote Playback API (used for AirPlay and Google Cast target selection in Safari and Chrome respectively) combined with the `<video>` element's native `x-webkit-airplay` / `disableRemotePlayback` attributes — but even there, the actual protocol and receiver ecosystem are outside the web's control, and Safari on macOS/iOS exposes AirPlay through this route specifically because it's an Apple-controlled surface, not a generic web capability. A web app can opt in or out of showing the AirPlay/casting affordance in the native video controls, but it cannot build a fully custom cross-browser equivalent the way it could for other UI.

What transfers is the design reasoning around **trademark and brand-boundary hygiene**, which is the real substance of this page beyond the streaming mechanics itself:

**"Prefer the system-provided player over a custom one" → prefer the browser's native media controls over a custom player.** The reasoning is identical: native controls are free, consistent with what people already know, and come with accessibility and remote-control behavior built in. A custom `<video>` skin should be justified by a real design need, not built by default — exactly Apple's framing.

**"Don't stop playback when backgrounded" → respect Media Session API and Picture-in-Picture expectations.** The web analogue of "don't interrupt the TV show when the app backgrounds" is supporting the Media Session API so playback state, metadata, and controls surface correctly in the OS-level media control center, and not pausing video simply because the tab lost focus.

**"Use official artwork and terminology, don't imply endorsement, emphasize your product over the technology's brand" → this is a general trademark-usage principle that applies to any licensed or certified third-party technology mark a web product references** (a payment network's logo, a certification badge, a hardware partner's name). Use the mark unmodified, in an approved color scheme, and keep it visually subordinate to your own brand — the same rule Apple states for AirPlay applies to referencing any other company's trademark on a web page.

Beyond these principles, the specific guidance about icon corner-positioning, resolution-adaptive HLS playlists for 4K AirPlay targets, and remote-control event handling describes native platform mechanics with no meaningful web parallel.

## Do / Don't

| Do | Don't |
|---|---|
| Use the system-provided media player when possible | Build a custom player without a real design need |
| Provide the full range of resolutions in your HLS playlist | Ship only one low resolution and let it upscale on a 4K TV |
| Support both streaming and mirroring | Support only one AirPlay mode |
| Continue playback when the app backgrounds or the device locks | Stop playback just because the app isn't in the foreground |
| Use official AirPlay icon color variants matched to your other tech icons | Recolor or restyle the AirPlay icon arbitrarily |
| Use AirPlay only as a noun, correctly capitalized | Use AirPlay as a verb form like "AirPlaying" or "SharePlayed" |
| Keep the AirPlay icon and name noninteractive | Use the AirPlay icon or name as a custom button |
| Emphasize your app's identity over the AirPlay reference | Let the AirPlay name or icon dominate your app's branding |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
