---
title: Managing notifications
url: https://developer.apple.com/design/human-interface-guidelines/managing-notifications
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Managing notifications

Notifications can give people timely and important information, whether the device is locked or in use.

## Core guidance

You need to get permission before sending any notification. The system lets people change this decision in settings, where they can also silence all notifications (except for government alerts in some locales).

### Integrating with Focus

People appreciate receiving a notification for something they care about, but they don't always appreciate being interrupted. To help people manage the experience, the system lets them specify delivery times and set up a Focus.

- A **Focus** helps people filter notifications during a time period they reserve for an activity like sleeping, working, reading, or driving.
- **Delivery scheduling** lets people choose whether to receive notification alerts immediately or in a summary that's delivered at times they choose.

People identify the contacts and apps that can break through a Focus to deliver notification alerts. In a Work Focus, for example, people might want to receive alerts from work colleagues, family members, and work-related apps as soon as notifications arrive. People might also want to receive all Time Sensitive notification alerts during a Focus. A Time Sensitive notification contains essential information people appreciate getting right away.

> **Note (Apple):** Even though a Focus might delay the delivery of a notification alert, the notification itself is available as soon as it arrives.

To support these behavior customizations, you first identify the types of notifications your app or game can send. If you support direct communications — like phone calls and messages — you use communication notifications; for all other types of tasks, you use noncommunication notifications. To support communication notifications, you adopt SiriKit intents, which means people can use Siri to customize notification behaviors; for developer guidance, see `INSendMessageIntent` and `UNNotificationContentProviding`.

You need to specify a system-defined interruption level for each noncommunication notification you send. The system uses the interruption level to help determine when to deliver the alert; when a communication notification arrives, the system uses the sender to determine when to deliver the alert.

The system defines four interruption levels for noncommunication notifications:

- **Passive.** Information people can view at their leisure, like a restaurant recommendation.
- **Active (the default).** Information people might appreciate knowing about when it arrives, like a score update on their favorite sports team.
- **Time Sensitive.** Information that directly impacts the person and requires their immediate attention, like an account security issue or a package delivery.
- **Critical.** Urgent information about health and safety that directly impacts the person and demands their immediate attention. Critical notifications are extremely rare and typically come from governmental and public agencies or apps that help people manage their health or home.

Notification alerts in each system-defined interruption level can behave in the following ways:

| Interruption level | Overrides scheduled delivery | Breaks through Focus | Overrides Ring/Silent switch on iPhone and iPad |
|---|---|---|---|
| Passive | No | No | No |
| Active | No | No | No |
| Time Sensitive | Yes | Yes | No |
| Critical | Yes | Yes | Yes |

> **Note (Apple):** Because a Critical notification can override the Ring/Silent switch and break through scheduled delivery and Focus, you must get an entitlement to send one.

### Best practices

**Build trust by accurately representing the urgency of each notification.** People have several ways to adjust how they receive your notifications — including turning off all notifications — so it's essential to be as realistic as possible when assigning an interruption level. You don't want people to feel that a notification uses a high level of urgency to interrupt them with low-priority information.

**Use the Time Sensitive interruption level only for notifications that are relevant in the moment.** To help people understand the benefits of letting Time Sensitive notifications break through a Focus or scheduled delivery, make sure the notification is about an event that's happening now or will happen within an hour. The first time a Time Sensitive notification arrives from your app, the system describes how such a notification works and gives people a way to turn it off if they don't agree that the information requires their immediate attention. Going forward, the system periodically gives people additional opportunities to evaluate how your Time Sensitive notification is working for them. For developer guidance, see `UNNotificationInterruptionLevel`.

### Sending marketing notifications

**Don't use notifications to send marketing or promotional content unless people explicitly agree to receive such information.** When people want to learn about new features, content, or events related to your app or game, they can grant their permission to receive marketing notifications. For example, people who use a subscription app might appreciate getting an offer to become a subscriber, and game players might want to receive a special offer related to a live game event.

**Never use the Time Sensitive interruption level to send a marketing notification.** People may have agreed to receive marketing notifications from your app, but such a notification must never break through a Focus or scheduled delivery setting.

**Get people's permission if you want to send them promotional or marketing notifications.** Before you send these notifications to people, you must receive their explicit permission to do so. Create an alert, modal view, or other interface that describes the types of information you want to send and gives people a clear way to opt in or out.

**Make sure people can manage their notification settings within your app.** In addition to requesting permission to send informational or marketing notifications, you must also provide an in-app settings screen that lets people change their choice. For guidance, see Settings.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, tvOS, or visionOS.

### watchOS

By default, the notification settings people use for apps on their iPhone apply to the same apps on their Apple Watch. People can manage these settings in the Apple Watch app on iPhone, or they can access per-notification options — such as Mute 1 Hour or Turn off Time Sensitive — by swiping left when a notification arrives on their Apple Watch.

## Native implementation

**Related**
- Privacy

**Developer documentation**
- User Notifications

**Key APIs**
- `INSendMessageIntent` — SiriKit intent adopted to support communication notifications
- `UNNotificationContentProviding` — communication notification content
- `UNNotificationInterruptionLevel` — set a notification's interruption level (passive, active, time sensitive, critical)

**Videos:** Send communication and Time Sensitive notifications · The Push Notifications primer

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Permission before sending → the Notifications API requires the same opt-in, but the web's default expectation from users is more suspicious.** `Notification.requestPermission()` maps directly to Apple's "get permission before sending any notification." The gap is contextual: because so many websites have abused permission prompts for marketing, users on the web are conditioned to reflexively deny notification permission requests, especially ones fired on page load. Apple's own guidance — ask at a meaningful moment, not immediately — matters even more on the web, where a mistimed prompt can cost you the ability to ever ask again in that browser profile.

**Interruption levels → there is no web equivalent, and this is a genuine capability gap, not just an inference gap.** Passive/Active/Time Sensitive/Critical is an OS-enforced priority system that interacts with Focus, scheduled delivery, and the Ring/Silent switch — none of which a web page can influence. Web Push notifications (via the Push API and Service Workers) are a single, undifferentiated tier: they either get shown or they don't, largely subject to per-site and per-browser heuristics the page has no visibility into. There is no way for a web app to mark a push notification as more urgent than another, and no way to break through a browser or OS-level "do not disturb" state the way Time Sensitive or Critical do. Design web push as if every notification is roughly "Active" — never assume the equivalent of Time Sensitive delivery guarantees exist.

**"Never use elevated urgency for marketing" → the principle transfers even though the mechanism doesn't.** Since the web has no interruption-level system to misuse, the equivalent failure mode is different: sending push notifications at a volume or frequency that gets a site's permission silently revoked, or gets the site's notifications auto-suppressed by the browser's spam heuristics (both Chrome and Firefox maintain per-site quality signals that downrank notification permission prompts and can quietly stop delivering pushes from over-sending sites). The underlying discipline — reserve interruption for what's genuinely urgent, treat marketing as opt-in and separate — applies whether or not the platform enforces it structurally.

**Explicit opt-in and in-app management for marketing notifications → this maps cleanly to a dedicated consent flow plus a settings page that calls `Notification.permission` and lets people revisit their choice**, though the web can't reach into the OS-level toggle the way an iOS app's Settings deep link can; a denied web permission can typically only be reversed by the person manually changing it in browser site settings, which the page cannot do on their behalf or link them directly into on every browser.

## Do / Don't

| Do | Don't |
|---|---|
| Get explicit permission before sending any notification | Send notifications without having requested permission |
| Set an interruption level that honestly reflects a notification's urgency | Mark low-priority information as Time Sensitive to force delivery |
| Reserve Time Sensitive for events happening now or within the hour | Use Time Sensitive for marketing or non-urgent content |
| Get explicit opt-in before sending marketing or promotional notifications | Send promotional content without separate, explicit permission |
| Provide an in-app settings screen for notification preferences | Leave notification management only in system Settings with no in-app control |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
