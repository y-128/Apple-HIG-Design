---
title: Watch faces
url: https://developer.apple.com/design/human-interface-guidelines/watch-faces
platforms: [watchOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Watch faces

A watch face is a view that people choose as their primary view in watchOS.

## Core guidance

The watch face is at the heart of the watchOS experience. People choose a watch face they want to see every time they raise their wrist, and they customize it with their favorite complications. People can even customize different watch faces for different activities, so they can switch to the watch face that fits their current context.

In watchOS 7 and later, people can share the watch faces they configure. For example, a fitness instructor might configure a watch face to share with their students by choosing the Gradient watch face, customizing the color, and adding their favorite health and fitness complications. When the students add the shared watch face to their Apple Watch or the Watch app on their iPhone, they get a custom experience without having to configure it themselves.

You can also configure a watch face to share from within your app, on your website, or through Messages, Mail, or social media. Offering shareable watch faces can help you introduce more people to your complications and your app.

### Best practices

**Help people discover your app by sharing watch faces that feature your complications.** Ideally, you support multiple complications so that you can showcase them in a shareable watch face and provide a curated experience. For some watch faces, you can also specify a system accent color, images, or styles. If people add your watch face but haven't installed your app, the system prompts them to install it.

**Display a preview of each watch face you share.** Displaying a preview that highlights the advantages of your watch face can help people visualize its benefits. You can get a preview by using the iOS Watch app to email the watch face to yourself. The preview includes an illustrated device bezel that frames the face and is suitable for display on websites and in watchOS and iOS apps. Alternatively, you can replace the illustrated bezel with a high-fidelity hardware bezel that you can download from Apple Design Resources and composite onto the preview.

**Aim to offer shareable watch faces for all Apple Watch devices.** Some watch faces are available on Series 4 and later — such as California, Chronograph Pro, Gradient, Infograph, Infograph Modular, Meridian, Modular Compact, and Solar Dial — and Explorer is available on Series 3 (with cellular) and later. If you use one of these faces in your configuration, consider offering a similar configuration using a face that's available on Series 3 and earlier. To help people make a choice, you can clearly label each shareable watch face with the devices it supports.

**Respond gracefully if people choose an incompatible watch face.** The system sends your app an error when people try to use an incompatible watch face on Series 3 or earlier. In this scenario, consider immediately offering an alternative configuration that uses a compatible face instead of displaying an error. Along with the previews you provide, help people understand that they might receive an alternative watch face if they choose a face that isn't compatible with their Apple Watch.

## Platform considerations

Not supported in iOS, iPadOS, macOS, tvOS, or visionOS. Watch face selection and configuration is exclusive to watchOS, even though sharing a configured face can happen from an iOS app, a website, Messages, Mail, or social media.

## Native implementation

**Related**
- Apple Design Resources — Product Bezels

**Developer documentation**
- Sharing an Apple Watch face — ClockKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance, and a watch face is a hardware- and OS-bound personalization surface — the primary view of a wearable device, built around complications and physical device bezels — that has no equivalent on the web. A web page cannot become a device's home screen the way a watch face does.

Two narrow principles transfer independent of the surface. First, **preview before commit**: Apple's requirement that a shareable watch face include a visual preview (framed in a device bezel) before someone adds it restates the general UX principle that any personalization or theme-configuration flow should let people see the result before applying it — the same reasoning behind a theme picker or avatar customizer showing a live preview on the web. Second, **respond gracefully to an incompatible configuration** restates as a general graceful-degradation principle: when a piece of personalization can't run on the current device or browser, offer a compatible fallback rather than surfacing a bare error, the same posture a web app should take when a requested feature isn't supported in the visitor's browser.

Everything else — complications, device-specific face availability by Apple Watch series, and sharing through the iOS Watch app — is watchOS hardware and ecosystem detail with nothing on the web to map to.

## Do / Don't

| Do | Don't |
|---|---|
| Feature your complications in a shareable watch face | Share a watch face that doesn't showcase your app |
| Provide a preview framed in a device bezel before sharing | Share a watch face with no preview of how it will look |
| Offer a compatible alternative for older Apple Watch models | Only support faces limited to Series 4 and later |
| Clearly label which devices each shareable face supports | Leave device compatibility unstated |
| Offer an alternative configuration when a face is incompatible | Show a bare error when someone picks an incompatible face |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
