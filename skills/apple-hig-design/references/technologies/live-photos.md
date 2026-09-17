---
title: Live Photos
url: https://developer.apple.com/design/human-interface-guidelines/live-photos
platforms: [iOS, iPadOS, macOS, tvOS, visionOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Live Photos

Live Photos lets people capture favorite memories in a sound- and motion-rich interactive experience that adds vitality to traditional still photos.

## Core guidance

When Live Photos is available, the Camera app captures additional content — including audio and extra frames — before and after people take a photo. People press a Live Photo to see it spring to life.

### Best practices

**Apply adjustments to all frames.** If your app lets people apply effects or adjustments to a Live Photo, make sure those changes are applied to the entire photo. If you don't support this, give people the option of converting it to a still photo.

**Keep Live Photo content intact.** It's important for people to experience Live Photos in a consistent way that uses the same visual treatment and interaction model across all apps. Don't disassemble a Live Photo and present its frames or audio separately.

**Implement a great photo sharing experience.** If your app supports photo sharing, let people preview the entire contents of Live Photos before deciding to share. Always offer the option to share Live Photos as traditional photos.

**Clearly indicate when a Live Photo is downloading and when the photo is playable.** Show a progress indicator during the download process and provide some indication when the download is complete.

**Display Live Photos as traditional photos in environments that don't support Live Photos.** Don't attempt to replicate the Live Photos experience provided in a supported environment. Instead, show a traditional, still representation of the photo.

**Make Live Photos easily distinguishable from still photos.** The best way to identify a Live Photo is through a hint of movement. Because there are no built-in Live Photo motion effects, like the one that appears as you swipe through photos in the full-screen browser of Photos app, you need to design and implement custom motion effects.

In cases where movement isn't possible, show a system-provided badge above the photo, either with or without text. **Never include a playback button that a viewer can interpret as a video playback button** — a Live Photo is not a video, and a playback-button affordance would set the wrong expectation about what pressing it does.

**Keep badge placement consistent.** If you show a badge, put it in the same location on every photo. Typically, a badge looks best in a corner of a photo.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, or tvOS. Not supported in watchOS.

### visionOS

In visionOS, people can view a Live Photo, but they can't capture one.

## Native implementation

**Developer documentation**
- `PHLivePhoto` — PhotoKit
- LivePhotosKit JS

**Videos:** What's new in camera capture

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

Live Photos itself has no web analogue. It depends on hardware that only exists on the capture device: a camera pipeline that continuously buffers frames and audio around the shutter press, plus a file format (paired still image and short video/audio clip) that ties the two together. A web page has no way to reach into a device's camera buffer before or after a photo is taken — the closest a browser gets is `getUserMedia`, which starts recording only after the user grants access and the code runs, well after any "before the shutter" window has closed. There is no way to construct the underlying asset from the web side, so nothing here transfers as an implementation technique.

What does transfer, narrowly, is the interaction reasoning around *displaying* an already-existing Live Photo asset (for example one fetched from an API that stores such assets). "Keep Live Photo content intact" and "don't disassemble the frames or audio" restate a general principle about composite media: if a format bundles related pieces into one meaningful unit, a UI that unbundles them silently misrepresents what the person captured. That reasoning applies to any rich-media object handled on the web (e.g., a video with a synchronized caption track), even though the specific case of Live Photos won't occur there. Likewise, "show a badge rather than a playback button when movement can't be shown" is really an instruction about not implying an interaction affordance you can't deliver — the same logic that applies to any static-preview-of-dynamic-content pattern on the web, such as a GIF thumbnail that shouldn't look like a video player if tapping it doesn't play a video.

Everything else — the capture pipeline, the frame-and-audio bundling, the platform-provided motion effect, the download/playable state tied to iCloud sync — is genuinely platform-bound and does not map to a web equivalent.

## Do / Don't

| Do | Don't |
|---|---|
| Apply adjustments to the entire Live Photo, or offer to convert it to a still photo | Apply an edit to only some frames of a Live Photo |
| Keep a Live Photo's frames and audio bundled together | Disassemble a Live Photo and present its parts separately |
| Let people preview the full Live Photo before sharing, and offer a still-photo sharing option | Share a Live Photo without letting people preview it first |
| Show progress and completion state while a Live Photo downloads | Leave people guessing whether a Live Photo has finished downloading |
| Show a traditional still photo where Live Photos isn't supported | Try to fake the Live Photos experience in an unsupported environment |
| Use a hint of movement or a system-provided badge to signal a Live Photo | Include a playback button that looks like a video control |
| Keep badge placement consistent across every photo | Move the badge around from photo to photo |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
