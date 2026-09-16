---
title: iMessage apps and stickers
url: https://developer.apple.com/design/human-interface-guidelines/imessage-apps-and-stickers
platforms: [iOS, iPadOS]
last_updated: 2023-05-02
---

# iMessage apps and stickers

An iMessage app can help people share content, collaborate, and even play games with others in a conversation; stickers are images that people can use to decorate a conversation.

## Core guidance

An iMessage app or sticker pack is available within the context of a Messages conversation and also in effects in both Messages and FaceTime. You can create an iMessage app or sticker pack as a standalone app or as an app extension within your iOS or iPadOS app.

### Best practices

**Prefer providing one primary experience in your iMessage app.** People are in a conversational flow when they choose your app, so your functionality or content needs to be easy to understand and immediately available. If you want to provide multiple types of functionality or different collections of content, consider creating a separate iMessage app for each one.

**Consider surfacing content from your iOS or iPadOS app.** For example, your iMessage app could offer app-specific information that people might want to share — such as a shopping list or a trip itinerary — or support a simple, collaborative task, like deciding where to go for a meal or which movie to watch.

**Present essential features in the compact view.** People can experience your iMessage app in a compact view that appears below the message transcript, or they can expand the view to occupy most of the window. Make sure the most frequently used items are available in the compact view, reserving additional content and features for the expanded view.

**In general, let people edit text only in the expanded view.** The compact view occupies roughly the same space as the keyboard. To ensure that the iMessage app's content remains visible while people edit, display the keyboard in the expanded view.

**Create stickers that are expressive, inclusive, and versatile.** Whether your stickers are rich, static images or short animations, make sure that each one remains legible against a wide range of backgrounds and when rotated or scaled. You can also use transparency to help people visually integrate a sticker with text, photos, and other stickers.

**For each sticker, provide a localized alternative description.** VoiceOver can help people use your sticker pack by speaking a sticker's alternative description.

## Platform considerations

No additional considerations for iOS or iPadOS. Not supported in macOS, tvOS, visionOS, or watchOS.

## Specifications

### Icon sizes

The icon for an iMessage app or sticker pack can appear in Messages, the App Store, notifications, and Settings. After people install your iMessage app or sticker pack, its icon also appears in the app drawer in the Messages app.

You supply a square-cornered icon for each extension you offer, and the system automatically applies a mask that rounds the corners.

To ensure that your icon looks great in any context and on various devices, create a square-cornered icon in the following sizes:

| Usage | @2x (pixels) | @3x (pixels) |
|---|---|---|
| Messages, notifications | 148x110 | - |
| | 143x100 | - |
| | 120x90 | 180x135 |
| | 64x48 | 96x72 |
| | 54x40 | 81x60 |
| Settings | 58x58 | 87x87 |
| App Store | 1024x1024 | 1024x1024 |

> **Source limitation:** the source table's "Usage" column left several rows unlabeled — only the "Messages, notifications" and "Settings" / "App Store" rows carry a usage label in the captured PDF. The rows are reproduced above exactly as they appear, including the blank usage cells, rather than guessing which context each unlabeled size row belongs to.

### Sticker sizes

Messages supports small, regular, and large stickers. Pick the size that works best for your content and prepare all of your stickers at that size; don't mix sizes within a single sticker pack. Messages displays stickers in a grid, organized differently for different sizes.

Create your sticker images using the following @3x dimensions for the sticker size you chose. If necessary, the system generates @2x and @1x versions by downscaling the images at runtime.

| Sticker size | @3x dimensions (pixels) |
|---|---|
| Small | 300x300 |
| Regular | 408x408 |
| Large | 618x618 |

A sticker file must be 500 KB or smaller in size. For each supported format, the table below provides guidance for using transparency and animation.

| Format | Transparency | Animation |
|---|---|---|
| PNG | 8-bit | No |
| APNG | 8-bit | Yes |
| GIF | Single-color | Yes |
| JPEG | No | No |

## Native implementation

**Related**
- iMessage Apps and Stickers

**Developer documentation**
- Messages
- Adding Sticker packs and iMessage apps to the system Stickers app, Messages camera, and FaceTime — Messages

**Key APIs**
- `MSStickerSize` — the sticker size enumeration referenced for the @3x dimension table above

**Videos:** Express Yourself!

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

There is no web platform equivalent to an iMessage app or sticker extension — Messages, its compact/expanded view model, and its sticker drawer are iOS-and-iPadOS-specific surfaces with no browser or web-standard analogue. A web chat widget embedded in a page is architecturally closer to a website than to an OS-level messaging extension, so nothing here transfers as an API or integration point.

What does transfer is the underlying interaction principle, independent of the platform it was written for. "Prefer one primary experience" and "present essential features in the compact view first" describe a general truth about any UI that must work in a small, collapsed surface before an expanded one: identify the single most-used action and make it reachable without requiring the user to open anything further. This is the same reasoning behind mobile-first responsive design and behind collapsed-vs-expanded widget patterns on the web (a chat bubble that expands to a full panel, a notification tray that expands from an icon). The reasoning — small surfaces demand ruthless prioritization — holds regardless of platform; the specific compact/expanded mechanics and icon-size specifications do not.

The alternative-description guidance for stickers maps directly and without qualification: any image conveying meaning on the web needs an `alt` text equivalent, for exactly the same reason Apple states here — a screen reader needs something to say. That principle is platform-agnostic because it is really a statement about assistive technology, not about Messages.

## Do / Don't

| Do | Don't |
|---|---|
| Provide one primary experience per iMessage app | Cram multiple unrelated functions into a single app |
| Put the most frequently used items in the compact view | Bury essential features only in the expanded view |
| Let people edit text in the expanded view with the keyboard visible | Let the keyboard obscure content while editing in the compact view |
| Make stickers legible against varied backgrounds, rotated and scaled | Ship stickers that only look correct at one size or on one background |
| Provide a localized alternative description for every sticker | Leave stickers without VoiceOver-readable descriptions |
| Prepare all stickers in a pack at one consistent size | Mix small, regular, and large stickers within a single pack |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
