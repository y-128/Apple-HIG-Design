---
title: Notifications
url: https://developer.apple.com/design/human-interface-guidelines/notifications
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2023-10-24
---

# Notifications

A notification gives people timely, high-value information they can understand at a glance.

## Core guidance

Before you can send any notifications to people, you have to get their consent. After agreeing, people generally use settings to specify the styles of notification they want to receive, and to specify delivery times for notifications that have different levels of urgency.

### Anatomy

Depending on the platform, a notification can use various styles, such as:

- A banner or view on a Lock Screen, Home Screen, Home View, or desktop
- A badge on an app icon
- An item in Notification Center

A notification related to direct communication — like a phone call or message — can provide an interface that's distinct from noncommunication notifications, featuring prominent contact images (or avatars) and group names instead of the app icon.

### Best practices

**Provide concise, informative notifications.** People turn on notifications to get quick updates, so you want to provide valuable information succinctly.

**Avoid sending multiple notifications for the same thing, even if someone hasn't responded.** People attend to notifications at their convenience. If you send multiple notifications for the same thing, you fill up Notification Center, and people may turn off all notifications from your app.

**Avoid sending a notification that tells people to perform specific tasks within your app.** If it makes sense to offer simple tasks that people can perform without opening your app, you can provide notification actions. Otherwise, avoid telling people what to do because it's hard for people to remember such instructions after they dismiss the notification.

**Use an alert — not a notification — to display an error message.** People are familiar with both alerts and notifications, so you don't want to cause confusion by using the wrong component.

**Handle notifications gracefully when your app is in the foreground.** Your app's notifications don't appear when your app is in the front, but your app still receives the information. In this scenario, present the information in a way that's discoverable but not distracting or invasive, such as incrementing a badge or subtly inserting new data into the current view. For example, when a new message arrives in a mailbox that people are currently viewing, Mail simply adds it to the list of unread messages because sending a notification about it would be unnecessary and distracting.

**Avoid including sensitive, personal, or confidential information in a notification.** You can't predict what people will be doing when they receive a notification, so it's essential to avoid including private information that could be visible to others.

### Content

When a notification includes a title, the system displays it at the top where it's most visible. In a notification related to direct communication, the system automatically displays the sender's name in the title area; in a noncommunication notification, the system displays your app name if you don't provide a title.

**Create a short title if it provides context for the notification content.** Prefer brief titles that people can read at a glance, especially on Apple Watch, where space is limited. When possible, take advantage of the prominent notification title area to provide useful information, like a headline, event name, or email subject. If you can only provide a generic title for a noncommunication notification — like "New Document" — it can be better to let the system display your app name instead. Use title-style capitalization and no ending punctuation.

**Write succinct, easy-to-read notification content.** Use complete sentences, sentence case, and proper punctuation, and don't truncate your message — the system does this automatically when necessary.

**Provide generically descriptive text to display when notification previews aren't available.** In Settings, people can choose to hide notification previews for all apps. In this situation, the system shows only your app icon and the default title "Notification." To give people sufficient context to know whether they want to view the full notification, write body text that succinctly describes the notification content without revealing too many details, like "Friend request," "New comment," "Reminder," or "Shipment." Use sentence-style capitalization for this text.

**Avoid including your app name or icon.** The system automatically displays a large version of your app icon at the leading edge of each notification; in a communication notification, the system displays the sender's contact image badged with a small version of your icon.

**Consider providing a sound to supplement your notifications.** Sound can be a great way to distinguish your app's notifications and get someone's attention when they're not looking at the device. You can create a custom sound that coordinates with the style of your app or use a system-provided alert sound. If you use a custom sound, make sure it's short, distinctive, and professionally produced. A notification sound can enhance the user experience, but don't rely on it to communicate important information, because people may not hear it. Although people might also want a vibration to accompany alert sounds, you can't provide such a vibration programmatically.

### Notification actions

A notification can present a customizable detail view that contains **up to four buttons** people use to perform actions without opening your app. For example, a Calendar event notification provides a Snooze button that postpones the event's alarm for a few minutes.

**Provide beneficial actions that make sense in the context of your notification.** Prefer actions that let people perform common, time-saving tasks that eliminate the need to open your app. For each button, use a short, title-case term or phrase that clearly describes the result of the action. Don't include your app name or any extraneous information in the button label, keep the text brief to avoid truncation, and take localization into account as you write it.

**Avoid providing an action that merely opens your app.** When people tap a notification or its preview, they expect your app to display related content, so presenting an action button that does the same thing clutters the detail view and can be confusing.

**Prefer nondestructive actions.** If you must provide a destructive action, make sure people have enough context to avoid unintended consequences. The system gives a distinct appearance to the actions you identify as destructive.

**Provide a simple, recognizable interface icon for each notification action.** An interface icon reinforces an action's meaning, helping people instantly understand what it does. The system displays your interface icon on the trailing side of the action title. When you use SF Symbols, you can choose an existing symbol that represents your command or edit a related symbol to create a custom icon.

### Badging

A badge is a small, filled oval containing a number that can appear on an app icon to indicate the number of unread notifications that are available. After people address unread notifications, the badge disappears from the app icon, reappearing when new notifications arrive. People can choose whether to allow an app to display badges in their notification settings.

**Use a badge only to show people how many unread notifications they have.** Don't use a badge to convey numeric information that isn't related to notifications, such as weather-related data, dates and times, stock prices, or game scores.

**Make sure badging isn't the only method you use to communicate essential information.** People can turn off badging for your app, so if you rely on it to show people when there's important information, people can miss the message. Always make sure that you make important information easy for people to find as soon as they open your app.

**Keep badges up to date.** Update your app's badge as soon as people open the corresponding notifications. You don't want people to think there are new notifications available, only to find that they've already viewed them all. Reducing a badge's count to zero removes all related notifications from Notification Center.

**Avoid creating a custom image or component that mimics the appearance or behavior of a badge.** People can turn off notification badges if they choose, and will become frustrated if they have done so and then see what appears to be a badge.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, tvOS, or visionOS.

### watchOS

On Apple Watch, notifications occur in two stages: short look and long look. People can also view notifications in Notification Center. On supported devices, people can double-tap to respond to notifications.

You can help people have a great notification experience by designing app-specific assets and actions that are relevant on Apple Watch. If your watchOS app has an iPhone companion that supports notifications, watchOS can automatically provide default short-look and long-look interfaces if necessary.

**Short looks.** A short look appears when the wearer's wrist is raised and disappears when it's lowered.

**Avoid using a short look as the only way to communicate important information.** A short look appears only briefly, giving people just enough time to see what the notification is about and which app sent it. If your notification information is critical, make sure you deliver it in other ways, too.

**Keep privacy in mind.** Short looks are intended to be discreet, so it's important to provide only basic information. Avoid including potentially sensitive information in the notification's title.

**Long looks.** Long looks provide more detail about a notification. If necessary, people can swipe vertically or use the Digital Crown to scroll a long look. After viewing a long look, people can dismiss it by tapping it or simply by lowering their wrist.

A custom long-look interface can be static or dynamic. The static interface lets you display a notification's message along with additional static text and images. The dynamic interface gives you access to the notification's full content and offers more options for configuring the appearance of the interface.

You can customize the content area for both static and dynamic long looks, but you can't change the overall structure of the interface. The system-defined structure includes a sash at the top of the interface and a Dismiss button at the bottom, below all custom buttons.

**Consider using a rich, custom long-look notification to let people get the information they need without launching your app.** You can use SwiftUI Animations to create engaging, interruptible animations; alternatively, you can use SpriteKit or SceneKit.

**At the minimum, provide a static interface; prefer providing a dynamic interface too.** The system defaults to the static interface when the dynamic interface is unavailable, such as when there is no network or the iPhone companion app is unreachable. Be sure to create the resources for your static interface in advance and package them with your app.

**Choose a background appearance for the sash.** The system-provided sash, at the top of the long-look interface, displays your app icon and name. You can customize the sash's color or give it a blurred appearance. If you display a photo at the top of the content area, you'll probably want to use the blurred sash, which has a light, translucent appearance that gives the illusion of overlapping the image.

**Choose a background color for the content area.** By default, the long look's background is transparent. If you want to match the background color of other system notifications, **use white with 18% opacity**; otherwise, you can use a custom color, such as a color within your brand's palette.

**Provide up to four custom actions below the content area.** For each long look, the system uses the notification's type to determine which of your custom actions to display as buttons in the notification UI. The system always displays a Dismiss button at the bottom of the long-look interface, below all custom buttons. If your watchOS app has an iPhone companion that supports notifications, the system shares the actionable notification types already registered by your iPhone app and uses them to configure your custom action buttons.

**Double tap.** People can double-tap to respond to notifications on supported devices. When a person responds to a notification with a double tap, the system selects the first nondestructive action as the response.

**Keep double tap in mind when choosing the order of custom actions you present as responses to a notification.** Because a double tap runs the first nondestructive action, consider placing the action that people use most frequently at the top of the list. For example, a parking app that provides custom actions for extending the time on a paid parking spot could offer options to extend the time by 5 minutes, 15 minutes, or an hour, with the most common choice listed first.

## Native implementation

**Related**
- Managing notifications
- Alerts

**Developer documentation**
- Asking permission to use notifications — User Notifications
- User Notifications UI
- User Notifications

**Key APIs**
- `hiddenPreviewsBodyPlaceholder` — supplies the generic body text shown when notification previews are hidden
- `UNNotificationSound` — supplies a system or custom notification sound

**Videos:** Send communication and Time Sensitive notifications · The Push Notifications primer

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy — and this topic maps to the web more directly than most, because the browser's Notifications API and Push API were deliberately modeled on the same OS-level notification centers Apple's guidance describes.

**Consent transfers directly, but the mechanics and stakes around asking for it are worse on the web.** Apple's "get consent before sending anything" is `Notification.requestPermission()` gated behind `Notification.permission`, typically paired with the Push API and a service worker to receive messages while the site isn't open. The difference is what happens around the prompt. iOS shows the system permission dialog once, at the moment the app calls the API, and a person who denies it can still find their way back through Settings. On the web, browsers actively police *when* a site is allowed to ask: Chrome and Firefox track a site's historical grant rate and will silently downgrade the native prompt to a muted, non-modal request — or block it outright — for sites that ask too early or too often. This makes Apple's implicit assumption (you get one clean shot at the system dialog) false on the web. The practical consequence is that a soft, in-page ask that explains the value first, and defers the real browser prompt until after someone opts in to that soft ask, isn't just good practice — it is often the only way to get the real dialog to render normally at all.

**"Avoid sending multiple notifications for the same thing" is the single highest-leverage principle to carry over, because the web's failure mode is permanent, not per-notification.** Apple warns that spamming leads people to turn off notifications for the app. On the web, permission is typically an all-or-nothing, origin-level grant with no in-app "mute this category" escape hatch as convenient as iOS's per-app Settings screen — so once revoked, most browsers require the person to dig into browser-level site settings to restore it, and few do. This is the mechanism behind "notification fatigue": each redundant push measurably raises the odds of a permanent opt-out, not just an ignored message. The concrete mitigation Apple gestures at (avoid resending the same thing) has an exact API-level tool on the web: the Notification constructor's `tag` option collapses a repeated update into the existing notification instead of stacking a new one, which is the direct technical analogue of Apple's own advice.

**"Handle notifications gracefully when your app is in the foreground" maps onto the Page Visibility API.** Apple's rule — don't fire a system notification when the app is already frontmost, update the in-app UI instead — has a clean web equivalent: check `document.visibilityState` (or the more granular Page Lifecycle API) before calling `showNotification()` from a service worker, and route foregrounded updates into an in-page toast, unread counter, or live-updating list instead. Firing an OS-level notification while the tab already has focus is the same mistake Apple is warning against, just easier to make on the web because a service worker doesn't automatically know the page is visible.

**Sensitive content in the notification body carries over unchanged, and arguably matters more.** A web push notification renders through the OS's own notification chrome — the same Lock Screen, banner, and notification center surfaces Apple's guidance is about — so the "you can't predict who's looking at the screen when it arrives" reasoning applies without modification.

**Hidden-preview placeholder text has no reliable web counterpart, and this is a real gap, not a stretch.** iOS's "Hide previews" is a system setting the app can query and design around with `hiddenPreviewsBodyPlaceholder`. No analogous API tells a web page whether the OS is suppressing its notification content, because that decision, where it exists at all, is made entirely by the OS or browser outside the page's visibility. Write body text that would be reasonable either way rather than assuming you can detect and design for the hidden state.

**Custom notification sound is a mapping that breaks down.** Apple's guidance to consider a short, professionally produced custom sound assumes a platform capability the web doesn't reliably have: the Notifications spec once included a `sound` option, but no major browser ever shipped it, and the option was removed from the living standard. Web notifications play whatever system sound the OS assigns to browser notifications generally, not a per-site custom sound. Don't design around a sound you can't actually attach.

**Badging maps closely through the Badging API, with a real scope limitation.** `navigator.setAppBadge()` and `clearAppBadge()` are the direct web equivalent of Apple's badge guidance, including the same rule that a badge should represent unread-notification count and nothing else. The limitation: Badging API support is generally restricted to installed, standalone-display PWAs on platforms whose browser implements it, so it isn't available to an ordinary browser tab the way an app icon badge is always available on iOS. Treat it as available only for the installed-app case, and don't build a fallback that mimics a badge in a regular tab — Apple's own warning against imitating badge appearance applies just as much to a fake badge built out of DOM elements on the web.

**Short look, long look, and double-tap are watchOS hardware interactions with no web equivalent.** These depend on wrist-raise detection, the Digital Crown, and a dedicated small-screen notification pipeline that only exists on Apple Watch. There is nothing on the web that approximates a glance-length auto-dismissing preview or a hardware double-tap gesture; this part of the guidance is platform-bound and should be treated as such rather than forced into an analogy.

## Do / Don't

| Do | Don't |
|---|---|
| Ask for consent with context, after establishing value | Request notification permission immediately on page load |
| Send one updated notification per event (use a shared tag) | Send a new notification every time the same thing happens |
| Update in-app UI when the app is already in the foreground | Fire a notification for content the person is already viewing |
| Keep titles and bodies short, in sentence case, unpunctuated titles | Truncate manually or pad text to fill space |
| Offer at most four clear, nondestructive-first actions | Add an action that just opens the app |
| Use badges only for unread-notification counts | Reuse the badge to show unrelated numeric data |
| Update badges the moment notifications are read | Let a badge count go stale after someone reads the notification |
| Treat a denied permission as a signal to reduce frequency, not re-prompt | Re-request permission repeatedly after a decline |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
