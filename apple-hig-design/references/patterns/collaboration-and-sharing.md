---
title: Collaboration and sharing
url: https://developer.apple.com/design/human-interface-guidelines/collaboration-and-sharing
platforms: [iOS, iPadOS, macOS, visionOS, watchOS]
last_updated: 2023-12-05
---

# Collaboration and sharing

Great collaboration and sharing experiences are simple and responsive, letting people engage with the content while communicating effectively with others.

## Core guidance

System interfaces and the Messages app can help you provide consistent and convenient ways for people to collaborate and share. For example, people can share content or begin a collaboration by dropping a document into a Messages conversation or selecting a destination in the familiar share sheet.

After a collaboration begins, people can use the Collaboration button in your app to communicate with others, perform custom actions, and manage details. In addition, people can receive Messages notifications when collaborators mention them, make changes, join, or leave.

You can take advantage of Messages integration and the system-provided sharing interfaces whether you implement collaboration and sharing through CloudKit, iCloud Drive, or a custom solution. To offer these features when you use a custom collaboration infrastructure, make sure your app also supports universal links (for developer guidance, see Supporting universal links in your app).

In addition to helping people share and collaborate on documents, visionOS supports immersive sharing experiences through SharePlay. For guidance, see SharePlay.

### Best practices

**Place the Share button in a convenient location, like a toolbar, to make it easy for people to start sharing or collaborating.** In iOS 16, the system-provided share sheet includes ways to choose a file-sharing method and set permissions for a new collaboration; iPadOS 16 and macOS 13 introduce similar appearance and functionality in the sharing popover. In your SwiftUI app, you can also enable sharing by presenting a share link that opens the system-provided share sheet when people choose it; for developer guidance, see `ShareLink`.

**If necessary, customize the share sheet or sharing popover to offer the types of file sharing your app supports.** If you use CloudKit, you can add support for sending a copy of a file by passing both the file and your collaboration object to the share sheet. Because the share sheet has built-in support for multiple items, it automatically detects the file and makes the "send copy" functionality available. With iCloud Drive, your collaboration object supports "send copy" functionality by default. For custom collaboration, you can support "send copy" functionality in the share sheet by including a file — or a plain text representation of it — in your collaboration object.

**Write succinct phrases that summarize the sharing permissions you support.** For example, you might write phrases like "Only invited people can edit" or "Everyone can make changes." The system uses your permission summary in a button that reveals a set of sharing options that people use to define the collaboration.

**Provide a set of simple sharing options that streamline collaboration setup.** You can customize the view that appears when people choose the permission summary button to provide choices that reflect your collaboration functionality. For example, you might offer options that let people specify who can access the content and whether they can edit it or just read it, and whether collaborators can add new participants. Keep the number of custom choices to a minimum and group them in ways that help people understand them at a glance.

**Prominently display the Collaboration button as soon as collaboration starts.** The system-provided Collaboration button reminds people that the content is shared and identifies who's sharing it. Because the Collaboration button typically appears after people interact with the share sheet or sharing popover, it works well to place it next to the Share button.

**Provide custom actions in the collaboration popover only if needed.** Choosing the Collaboration button in your app reveals a popover that consists of three sections. The top section lists collaborators and provides communication buttons that can open Messages or FaceTime, the middle section contains your custom items, and the bottom section displays a button people use to manage the shared file. You don't want to overwhelm people with too much information, so it's crucial to offer only the most essential items that people need while they use your app to collaborate. For example, Notes summarizes the most recent updates and provides buttons that let people get more information about the updates or view more activities.

**If it makes sense in your app, customize the title of the modal view's collaboration-management button.** People choose this button — titled "Manage Shared File" by default — to reveal the collaboration-management view where they can change settings and add or remove collaborators. If you use CloudKit sharing, the system provides a management view for you; otherwise, you create your own.

**Consider posting collaboration event notifications in Messages.** Choose the type of event that occurred — such as a change in the content or the collaboration membership, or the mention of a participant — and include a universal link people can use to open the relevant view in your app. For developer guidance, see `SWHighlightEvent`.

## Platform considerations

No additional considerations for iOS, iPadOS, or macOS. Not available in tvOS.

### visionOS

By default, the system supports screen sharing for an app running in the Shared Space by streaming the current window to other collaborators. If one person transitions the app to a Full Space while sharing is in progress, the system pauses the stream for other people until the app returns to the Shared Space. For guidance, see Immersive experiences.

### watchOS

In your SwiftUI app running in watchOS, use `ShareLink` to present the system-provided share sheet.

## Native implementation

**Related**
- Activity views

**Developer documentation**
- Shared with You
- `ShareLink` — SwiftUI

**Key APIs**
- `ShareLink` — SwiftUI control that presents the system-provided share sheet
- `SWHighlightEvent` — used to post collaboration event notifications into Messages

**Videos:** Design for Collaboration with Messages · Enhance collaboration experiences with Messages · Integrate your custom collaboration app with Messages

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**The Share button and system share sheet → the Web Share API, with a much narrower feature set.** `navigator.share()` opens the OS-level share sheet on supporting browsers (Safari, Chrome on mobile; desktop support is inconsistent) and covers Apple's baseline instruction — place a convenient share action, let the system present destinations. What it does not give you is Apple's collaboration layer: there's no web-native concept of a "collaboration object" that carries both a file and live-editing permissions through the share sheet, so a real-time collaboration invite has to be built as your own link-based flow (generate a URL, send it via `navigator.share()` or copy-to-clipboard) rather than handed to a system API that understands collaboration semantics.

**Permission summaries and sharing options ("Only invited people can edit") → this is pure product design on the web, with no platform default to inherit.** Apple's system renders your permission summary inside a system-managed button and popover; on the web you own the entire surface — the invite dialog, the role picker (viewer/editor), the phrasing — because there's no OS-level sharing popover to plug into. The transferable discipline is the writing guidance itself: keep the permission summary to a short, plain phrase, and keep the number of role choices small.

**The Collaboration button and its three-section popover → build the equivalent as an in-app affordance; nothing comparable ships with the platform.** A "who's here" indicator with avatars, a communication entry point, and a manage-access action is a well-established pattern in web collaborative editors (Google Docs, Figma, Notion all converged on something like it independently), which suggests the underlying need is real — but you're implementing product UI, not calling a system component the way `ShareLink` does.

**Real-time presence and live co-editing → this is the part of "collaboration" the web has to build entirely from scratch, and it's the hardest part.** Apple's guidance assumes CloudKit or iCloud Drive supply conflict resolution and live sync underneath the UI it describes. The web has no equivalent managed backend; you either bring your own real-time sync layer (CRDTs, operational transforms, a WebSocket-backed service) or fall back to simpler asynchronous sharing (a link with view/comment permissions, no live co-editing). Be explicit with stakeholders about which tier you're building — "sharing a link" and "simultaneous collaborative editing" are different engineering problems that Apple's guidance treats as a continuum but the web does not hand you for free.

**Collaboration notifications posted into Messages → no web equivalent; use web push or in-app notification instead.** Apple's `SWHighlightEvent` integration with the Messages app is iMessage-specific system integration a web app cannot reach. The nearest transferable behavior is the Notifications API / Push API for the same underlying goal (tell someone their collaborator made a change), understanding it's a different, less-integrated channel with its own permission prompt and no guarantee of delivery the way a system-level Messages integration has.

## Do / Don't

| Do | Don't |
|---|---|
| Place Share in a convenient, consistent location like a toolbar | Bury sharing behind an unexpected menu |
| Write short, plain-language permission summaries | Use vague or technical language for who can access what |
| Keep sharing-option choices to a minimum, grouped clearly | Present a long list of granular permission toggles |
| Show a persistent, prominent indicator once collaboration starts | Leave people unsure whether content is currently shared |
| Offer only the most essential custom actions in a collaboration surface | Overload a collaboration popover with every possible action |
| Notify people of collaboration events sparingly and meaningfully | Send a notification for every minor change a collaborator makes |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
