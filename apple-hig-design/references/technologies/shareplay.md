---
title: SharePlay
url: https://developer.apple.com/design/human-interface-guidelines/shareplay
platforms: [iOS, iPadOS, macOS, tvOS, visionOS]
last_updated: 2026-09-09
---

# SharePlay

SharePlay lets people experience activities together from anywhere, whether they're watching a movie, playing a game, or sketching on a whiteboard.

With SharePlay, people take part in your app's activities together, from their own devices, even when they aren't in the same room. An **activity** is a shareable experience your app offers. The system keeps each activity in sync across everyone's devices and works alongside FaceTime or Messages so people can talk as they go.

An activity can start in different ways: from a control in your app, from a FaceTime call, or from a shared link. The system asks each participant to open your app on their own device, and invites anyone who doesn't have it to download it from the App Store.

> **Note (Apple):** If your activity involves content people buy or subscribe to, each participant needs their own copy or subscription. The system prompts anyone without access to download or subscribe.

## Core guidance

### Best practices

**Use SharePlay for real-time experiences.** SharePlay is designed for activities people do together at the same moment. To also support asynchronous collaboration, where people contribute on their own schedule, give them a way to share or save the activity after the session ends. For example, people can use SharePlay to view and edit a Freeform board together in real time, then share a link afterward to keep collaborating. For developer guidance, see Adding shared content collaboration to your app.

**Design an experience that best fits what people are doing together.** For many activities, like watching or browsing, it makes sense for everyone to share one view and see the same thing. Other activities feel richer when the view adapts to each person's role, like a game that gives every player their own perspective.

**Design activities that work across Apple platforms.** People may want to share with others on different devices, in different settings, and through different communication methods. Build adaptable experiences that work well across these differences so everyone can participate.

**Make it easy to start a shared activity.** Give people a clear, recognizable way to begin an activity in your app, like a button that includes the SharePlay symbol. People can also start from system-provided features like the share sheet. In visionOS, people can start an activity using the Share button next to the window bar. For developer guidance, see Presenting SharePlay activities from your app's UI.

**Let people join an activity without friction.** When someone joins, get them to the shared content quickly and avoid showing views unrelated to the activity. If they need to sign in, download content, or subscribe first, guide them through it in a view that dismisses as soon as they're done. For purchases or subscriptions, lower the barrier by offering provisional access to nonsubscribers or supporting Family Sharing. Defer nonessential steps to more natural moments. For example, a game might let people join a match right away and set up profiles once they're connected.

**Describe activities clearly and concisely.** When someone receives an invitation, a clear description helps them understand what they're about to join. For a movie, that might be the title, a short summary, and a poster image. Keep descriptions brief enough to avoid truncation.

**Keep people oriented as an activity changes.** When one person's action changes the activity for everyone, help people understand why. For media, the system can coordinate playback across devices, so pausing a movie for one person pauses it for everyone. For other changes, use in-app cues to show who's doing what. In Freeform, for example, a participant's initials appear next to their contribution, strengthening the sense of presence.

**Use the term SharePlay correctly.** You can use SharePlay as a noun, as in "Join SharePlay," or as a verb that describes an action in your interface, like a SharePlay Movie button. Don't pair SharePlay with an adjective. In a visionOS app, for instance, avoid adding terms like *virtual* or *spatial*. And don't alter the term itself with variations like *SharePlayed*, *SharePlays*, or *SharePlaying*.

## Platform considerations

No additional considerations for tvOS. Not supported in watchOS.

### iOS, iPadOS, macOS

**Support Picture in Picture for shared video.** Let people keep watching together even while they do other things on their device. On iPhone and iPad, a shared video can continue playing in a Picture in Picture window. On Mac, it can keep playing in a window people bring forward when they want to watch.

### visionOS

In visionOS, SharePlay brings an extra level of presence to shared activities, whether people are collaborating in the same room, playing a game with distant friends, or catching up over FaceTime. Standard windows are shareable through screen mirroring by default using the Share button, and you can adopt SharePlay to share volumetric windows and immersive content.

#### Designing shared activities

When people join a shared activity, the system creates a **shared context** so everyone experiences your content in the same relative location. People can discuss, point to, and interact with content as if it's really there in the room, which encourages authentic, intuitive interaction. Aligning your app's windows and volumes across everyone's devices gives people confidence they're looking at the same thing. Your app needs to position 3D objects, play sounds, and support interactions in ways that strengthen the feeling of being together. For developer guidance, see Synchronizing data during a SharePlay activity.

**Prefer starting your experience from a window.** An activity that starts in a window is easy to find, because people can share it by tapping the Share button next to the window bar. For an activity that begins in an immersive space, however, you need to design custom UI to help people start it. For developer guidance, see Implementing SharePlay for immersive spaces in visionOS.

**Resolve conflicts naturally.** When people share content, more than one person may try to act on the same thing at once. If only one person can use a tool or object at a time, avoid showing UI that lets someone else take control. Instead, let people speak or gesture to the group when they want a turn. Consider a simple rule, like *last change wins*, that keeps the environment collaborative and predictable.

**Reserve unique views for moments that call for them.** In general, keep views and immersion levels in sync so people feel connected. In some cases, though, a personalized view can enrich the experience. When someone enters an immersive view of their own, replace their spatial Persona with a contact photo so others know they've stepped away, and let everyone keep talking over FaceTime Audio.

**Let people opt in to immersion changes when they're mid-task.** When one person changes their level of immersion, your app can bring everyone along. First, check whether the change would interrupt what someone's doing. If it would, let them choose when to join rather than pulling them in automatically. For example, if people are watching a movie in the Apple TV app and someone switches to an immersive environment, anyone engaged in an activity in another window sees a prompt with an option to join when they're ready. Everyone else transitions right away. For guidance, see Immersive experiences.

**Let participants customize their experience for personal comfort and accessibility needs.** Settings like volume and subtitles help people stay comfortable. Keep these adjustments unique to each participant, so one person's changes don't affect anyone else.

**Make it easy to leave and rejoin.** People sometimes need to step away for another task or to engage with their surroundings. If someone exits, give them a clear control to rejoin quickly. If your app offers a windowed version of the activity, people can continue multitasking while staying connected to the shared activity and FaceTime Audio.

#### Personas

In a shared activity, how someone appears depends on their device and location:

- Someone joining remotely on Apple Vision Pro may appear as a **spatial Persona**, a representation that lets them make eye contact, gesture, move around, and interact with your content as if they were in the same room. If they haven't set up a Persona, they appear as a contact photo instead.
- Someone joining on iPhone, iPad, Mac, or Apple TV appears in a 2D window showing their video.
- When people wearing Apple Vision Pro devices are together in the same room, shared content appears in the same physical location for each of them, and they see each other naturally through passthrough.

**Support people who aren't represented by a spatial Persona.** Not everyone in a shared activity appears as a spatial Persona. People join from other devices, and someone on Apple Vision Pro might turn theirs off or join over windowed FaceTime. Make sure your activity works for all of them. If your experience relies on facial expressions or gestures, offer alternatives in your UI so these participants can take part fully.

For developer guidance, see Adding spatial Persona support to an activity and Configure your visionOS app for sharing with people nearby.

#### Spatial templates

A **spatial template** automatically arranges participants around your content in a way that suits what they're doing together. Each person has a **seat** that determines where they appear and which way they face, based on the content and the template you choose. Adopt the spatial template that best fits your activity, or create a custom template if none of the system ones fit.

| System template | Arrangement | Best for | Social effect |
|---|---|---|---|
| **Side-by-side** | Participants next to each other along a curve, all facing the shared content | Viewing or watching content together | People aren't facing one another, so it encourages less nonverbal interaction and keeps the focus on the content |
| **Surround** | Participants in a circle around the shared content | Tabletop games and other centralized experiences; especially when content is 3D or unique to each participant, since each viewer sees it from a different angle | Participants face each other as if grouped around a table, encouraging both verbal and nonverbal interaction |
| **Conversational** | Participants grouped around a center point, with your content along the edge of the circle rather than at its center | Experiences that are more about people being together while your app performs a task in the background, like playing music | Not everyone has the same view of the content, so it might not be convenient for everyone to interact with it |

**Divide a complex activity into stages.** Give each stage of an activity its own template that suits what people are doing at that point. In a game, for example, you might use one template for choosing teams and another for play. Because you can transition between templates, using a mix of system and custom templates is preferable to designing a single complex custom one.

**Let people initiate template transitions.** Unexpectedly swapping roles or moving seats can be disorienting, so tie template changes to a person's explicit action. In a game, for example, choosing a team can initiate the role and seat change that follows.

**Keep template transitions smooth.** Avoid frequent transitions or ones that require excessive movement. When you do move someone to a different seat or role, fade out and back in to ease the change, and provide visual cues to help them reorient afterward.

#### Custom templates

If none of the system templates suit your activity, you can create a custom template that defines your own seat arrangement. Seats apply only to people using a spatial Persona in visionOS, and an activity can also include people on other platforms who take part without a seat. For developer guidance, see Building a guessing game for visionOS.

**Account for people who are physically together.** When people using Vision Pro share the same room, they see each other through passthrough rather than as spatial Personas. A spatial template can move a remote participant's spatial Persona into a seat, but it can't move someone who's physically present. If your activity depends on specific positions, guide people with visual cues like position markers, the way a tabletop game might show each player which seat to take. For developer guidance, see Configure your visionOS app for sharing with people nearby.

**Provide the best seat orientation for your content.** By default, seats face toward the center of your content, but you have full control over seat direction. For developer guidance, see `SpatialTemplateSeatElement`.

**Support the maximum number of seats.** Apple Vision Pro supports up to **five spatial Personas** in an activity, so include five seats whenever your activity allows. Adding or removing seats as people come and go can be disorienting, so define every seat up front and keep a seat in place after someone leaves, letting anyone take a spot the moment they join. If your activity has a participant limit, like a two-player game, consider including spectator seats where others can watch and talk.

**Place seats at least a meter apart.** This gives people enough room to interact comfortably without crowding each other. People can still share gestures like a handshake or a high five, but if a spatial Persona gets too close to another, it's replaced with a contact photo, which breaks the sense of presence.

**Define the order in which people take seats.** When your custom template is set, the seats you specify are filled in the order each person joins. Order them so the arrangement stays balanced when not every seat is occupied; filling seats left to right, for example, can feel unbalanced when only a few people are present.

**Keep roles independent of seats.** Don't tie your app's roles, such as player, spectator, or team member, to seat assignments. A role needs to work for everyone in the activity, including those without a seat. Let people fill any open seat so they can join without delay. Reserve a specific spot only for a role that truly requires it, like a game host at the head of a table. For developer guidance, see `isSpatial` and `isNearbyWithLocalParticipant`.

## Native implementation

**Developer documentation**
- Group Activities
- Adding shared content collaboration to your app
- Presenting SharePlay activities from your app's UI
- Synchronizing data during a SharePlay activity
- Implementing SharePlay for immersive spaces in visionOS
- Adding spatial Persona support to an activity
- Configure your visionOS app for sharing with people nearby
- Building a guessing game for visionOS
- `SpatialTemplateSeatElement`
- `isSpatial`
- `isNearbyWithLocalParticipant`

**Related guidance:** Immersive experiences

**Videos:** Share visionOS experiences with nearby people · Design spatial SharePlay experiences · Add SharePlay to your app

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. SharePlay is Apple's proprietary synchronized-activity and shared-presence layer, built on Group Activities and tied to FaceTime and Messages. There is no web API that gives a browser a system-level invitation to join someone's activity, spatial Persona rendering, spatial templates, or automatic synchronization across devices. A web app cannot participate in SharePlay directly. The mappings below apply the same design reasoning to web co-viewing and real-time collaboration features built with WebRTC data channels, WebSockets, or a shared-state backend; they are inference, not Apple policy.

**"Use SharePlay for real-time experiences, and offer a way to continue asynchronously" → separate the live session from the persistent artifact.** A web watch party or live whiteboard session is ephemeral; the board, playlist, or document it produces should outlive it. Offering a share link or a saved copy when the session ends is the same pattern as Apple's Freeform example, and it prevents the live session from becoming the only way to collaborate.

**"Fit the experience to what people are doing together" → decide which state is shared and which is per-person, deliberately.** Co-viewing features generally share one view (the same content at the same timestamp). Games and role-based tools may need per-participant views. Deciding this up front determines the synchronization model; leaving it implicit leads to clients drifting into different views by accident.

**"Make it easy to start" → a single recognizable entry point, plus the platform share mechanism.** A clearly labeled "watch together" or "start session" control, combined with the Web Share API for sending the invite link, mirrors Apple's pairing of an in-app button with the system share sheet.

**"Join without friction" → land joiners directly on the shared content.** When someone opens an invite link, route them to the session rather than to a home page or marketing view. If sign-in or payment is required, present it as a short, self-dismissing step and return to the session immediately afterward. Defer profile setup and other nonessential steps until after they're connected. Apple's suggestion of provisional access for nonsubscribers maps to guest or trial access for invitees.

**"Describe activities clearly and concisely" → the invite link preview matters.** The Open Graph title, description, and image of a session link are the web's version of the activity description people see before joining. Keep them short enough that messaging apps don't truncate them.

**"Keep people oriented as an activity changes" → attribute shared state changes.** When one participant pauses, seeks, or edits, show who did it (a brief toast, a presence cursor, initials next to a contribution). Unattributed changes to shared state feel like bugs.

**"Resolve conflicts naturally" → a simple, predictable rule such as last-write-wins at the UX level.** This applies to any concurrent-editing web feature, whatever the underlying mechanism (operational transforms, CRDTs, or server arbitration). Avoid building "take control" UI for single-user tools when social negotiation over voice or chat can decide turns.

**"Let participants customize for comfort and accessibility" → keep captions, volume, and zoom local.** These settings belong to each client and must never be broadcast to the session.

**"Make it easy to leave and rejoin" → a persistent rejoin affordance.** If someone navigates away within the app, keep a visible indicator that the session is still running and a one-click way back, similar to a minimized call bar.

**"Support Picture in Picture for shared video" → the web has a direct counterpart.** The Picture-in-Picture API (and Document Picture-in-Picture where supported) lets shared video keep playing while the person uses other tabs, which serves the same purpose Apple describes.

**Where the mapping breaks down:** spatial Personas, shared context in physical space, spatial templates, seats, seat orientation, the five-Persona limit, and the one-meter seat spacing are specific to visionOS spatial computing. A web session can borrow the *policy* ideas (roles independent of seats, stable slots that don't shift as people come and go, participant-initiated transitions between stages), but there is no web analogue to arranging people around 3D content in a room, and forcing a seating metaphor onto a 2D video grid stretches the analogy past where it holds.

## Do / Don't

| Do | Don't |
|---|---|
| Use SharePlay for activities people do together at the same moment, and offer a way to share or save afterward | Rely on the live session as the only way to collaborate |
| Choose between one shared view and role-specific views based on the activity | Let participants drift into different views without a reason |
| Offer a clear start control that includes the SharePlay symbol | Hide the way to start a shared activity |
| Take joiners straight to the shared content; use a self-dismissing view for sign-in, download, or subscription | Show views unrelated to the activity when someone joins |
| Offer provisional access to nonsubscribers or support Family Sharing | Block nonsubscribers without a path to join |
| Keep activity descriptions brief (for a movie: title, short summary, poster) | Write descriptions long enough to be truncated |
| Show who changed the activity with in-app cues | Change the activity for everyone without explanation |
| Use SharePlay as a noun or verb, unmodified | Write "spatial SharePlay", "SharePlayed", "SharePlays", or "SharePlaying" |
| Support Picture in Picture for shared video on iOS, iPadOS, and macOS | Force people to stop watching to do something else |
| In visionOS, prefer starting an activity from a window | Start in an immersive space without custom UI to help people begin |
| Let mid-task participants opt in to immersion changes | Pull everyone into a new immersion level automatically |
| Keep volume and subtitles unique to each participant | Apply one person's comfort settings to the whole group |
| Support participants who aren't represented by a spatial Persona | Depend solely on facial expressions or gestures |
| Split complex activities into stages with their own templates, and let people trigger transitions | Swap seats or roles unexpectedly, or transition frequently |
| Define five seats up front, at least a meter apart, in a balanced fill order | Add or remove seats as people come and go |
| Keep roles independent of seats | Tie player, spectator, or team roles to specific seats |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
