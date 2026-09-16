---
title: ShazamKit
url: https://developer.apple.com/design/human-interface-guidelines/shazamkit
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# ShazamKit

ShazamKit supports audio recognition by matching an audio sample against the ShazamKit catalog or a custom audio catalog.

## Core guidance

You can use ShazamKit to provide features like:

- Enhancing experiences with graphics that correspond with the genre of currently playing music
- Making media content accessible to people with hearing disabilities by providing closed captions or sign language that syncs with the audio
- Synchronizing in-app experiences with virtual content in contexts like online learning and retail

If you need the device microphone to get audio samples for your app to recognize, you must request access to it. As with all types of permission requests, it's important to help people understand why you're asking for access. For guidance, see Privacy.

### Best practices

After you receive permission to access the microphone for features that use ShazamKit, follow these guidelines.

**Stop recording as soon as possible.** When people allow your app to record audio for recognition, they don't expect the microphone to stay on. To help preserve privacy, only record for as long as it takes to get the sample you need.

**Let people opt in to storing your app's recognized songs to their iCloud library.** If your app can store recognized songs to iCloud, give people a way to first approve this action. Even though both the Music Recognition control and the Shazam app show your app as the source of the recognized song, people appreciate having control over which apps can store content in their library.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, tvOS, visionOS, or watchOS.

## Native implementation

**Developer documentation**
- ShazamKit

**Videos:** Explore ShazamKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

ShazamKit itself — matching a captured audio sample against Apple's proprietary Shazam catalog, or against a developer's own catalog built with ShazamKit's fingerprinting tools — has no web equivalent. There is no browser-exposed audio-recognition catalog comparable to Shazam's, and the fingerprinting and matching happen against a proprietary Apple service that a web page cannot call into the way a native app can through the framework. A web app wanting equivalent functionality would need a third-party audio-recognition API reached over the network, which is a different architecture with different privacy and latency properties, not a drop-in substitute.

What transfers cleanly is the microphone-privacy reasoning, because that reasoning is about permission-gated hardware access in general, not about ShazamKit specifically. **"Stop recording as soon as possible"** maps directly to the web's `getUserMedia` microphone permission: a web app that requests microphone access for a recognition or transcription feature should stop the media stream's tracks the moment it has what it needs, rather than holding the microphone open, for the same reason Apple states — people who grant access for one recognition task don't expect it to stay live. **"Let people opt in before storing recognized content"** generalizes to any web feature that persists data derived from a sensitive input (audio, camera, location): storing something to a personal library or account should be a separate, explicit choice from the act of capturing it, not a default that piggybacks on the original permission grant.

Where the mapping stops: Apple's guidance assumes iCloud as the storage destination and the Music Recognition control as a system-level surface showing provenance. Neither has a web counterpart — a web app must build its own equivalent of "show the person where this data is going and let them decide," since there's no OS-level control doing that work for it.

## Do / Don't

| Do | Don't |
|---|---|
| Explain why you need microphone access before requesting it | Request microphone access without context |
| Stop recording as soon as you have the audio sample you need | Leave the microphone recording after the sample is captured |
| Ask people to opt in before storing recognized songs to iCloud | Store recognized content to iCloud without explicit approval |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
