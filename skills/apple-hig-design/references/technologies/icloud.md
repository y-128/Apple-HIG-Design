---
title: iCloud
url: https://developer.apple.com/design/human-interface-guidelines/icloud
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2025-06-09
---

# iCloud

iCloud is a service that lets people seamlessly access the content they care about — photos, videos, documents, and more — from any device, without performing explicit synchronization.

## Core guidance

A fundamental aspect of iCloud is transparency. People don't need to know where content resides. They can just assume they're always accessing the latest version.

**Make it easy to use your app with iCloud.** People turn on iCloud in Settings and expect apps to work with it automatically. If you think people might want to choose whether to use iCloud with your app, show a simple option the first time your app opens that provides a choice between using iCloud for all data or not at all.

**Avoid asking which documents to keep in iCloud.** Most people expect all of their content to be available in iCloud and don't want to manage the storage of individual documents. Consider how your app handles and exposes content, and try to perform more file-management tasks automatically.

**Keep content up to date when possible.** In an app that supports iCloud, it's best when people always have access to the most recent content. However, you need to balance this experience with respect to device storage and bandwidth constraints. If your app works with very large documents, it may be better to let people control when updated content is downloaded. If your app fits in this category, design a way to indicate that a more recent version of a document is available in iCloud. When a document is updating, provide subtle feedback if the download takes more than a few seconds.

**Respect iCloud storage space.** iCloud is a finite resource for which people pay. Use iCloud to store information people create and understand, and avoid using it for app resources or content you can regenerate. Even if your app doesn't implement iCloud support, remember that iCloud backups include the contents of every app's Documents folder. To avoid using up too much space, be picky about the content you place in the Documents folder.

**Make sure your app behaves appropriately when iCloud is unavailable.** If someone manually turns off iCloud or turns on Airplane Mode, you don't need to display an alert notifying them iCloud is unavailable. However, it may still be helpful to unobtrusively let people know that changes they make won't be available on other devices until they restore iCloud access.

**Keep app state information in iCloud.** In addition to storing documents and other files, you can use iCloud to store settings and information about the state of your app. For example, a magazine app might store the last page viewed so when the app is opened on another device, someone can continue reading from where they left off. If you use iCloud to store settings, make sure it's for ones people want applied to all of their devices. For example, some settings might be more useful at work than at home.

**Warn about the consequences of deleting a document.** When someone deletes a document in an app that supports iCloud, the document is removed from iCloud and all other devices too. Show a warning and ask for confirmation before performing the deletion.

**Make conflict resolution prompt and easy.** To the extent possible, try to detect and resolve version conflicts automatically. If this can't be done, display an unobtrusive notification that makes it easy to differentiate and choose between the conflicting versions. Ideally, conflict resolution occurs as early as possible, so time isn't wasted in the wrong version.

**Include iCloud content in search results.** People with iCloud accounts assume their content is universally available, and they expect search results to reflect this perspective.

**For games, consider saving player progress in iCloud.** Although you can implement this functionality yourself, the GameSave framework offers an efficient solution. It synchronizes save data across devices and offers built-in alerts you can use to help players handle syncing issues during offline play or when conflicts arise. Alternatively, you can implement custom UI that uses GameSave data to resolve these situations.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, tvOS, visionOS, or watchOS.

## Native implementation

**Developer documentation**
- CloudKit
- GameSave

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

iCloud itself is Apple's proprietary sync backend — there's no web equivalent of "turning on iCloud in Settings," and a web app cannot participate in it directly (short of building against CloudKit JS, which requires an Apple Developer account and only serves Apple's own auth model). What transfers is the design philosophy behind it: transparency about where data lives, and sync as a default rather than a chore.

**"Transparency about where content resides" → sync should be invisible until it fails.** Apple's core principle is that people shouldn't have to think about which device holds the current version. On the web, this maps to background sync via the Service Worker Background Sync API or a WebSocket/polling-based sync layer, paired with optimistic UI updates. The user types, sees the change immediately, and the network round-trip happens without a visible "syncing" state unless it's slow or fails.

**"Avoid asking which documents to keep" → avoid manual sync toggles per item.** The web analogue is the same anti-pattern to avoid: per-document "keep offline" switches create exactly the storage-management burden Apple warns against. If offline access matters, cache everything reasonable by default (via the Cache API or IndexedDB) rather than making the user curate a list.

**"Provide subtle feedback when a download takes more than a few seconds" → this maps directly.** A sync spinner or "Saving…" indicator that appears only past a short delay threshold — rather than flashing on every keystroke — is standard web practice and follows the same reasoning: don't create UI noise for the common fast case.

**"Behave appropriately when iCloud is unavailable" → this is the offline-first / PWA principle.** The web equivalent is detecting `navigator.onLine` changes and network errors, queuing writes locally (IndexedDB is the standard store), and syncing when connectivity returns — without a jarring "you're offline" modal for routine disconnects. The Background Sync API exists specifically to defer a failed write until connectivity resumes, which is the direct structural analogue of iCloud's own retry behavior.

**"Make conflict resolution prompt and easy" → this is the hardest part to carry over, and where the mapping is weakest.** Apple's iCloud/CloudKit stack does last-writer-wins or record-level conflict resolution for you at the platform level. The web has no equivalent platform service — a web app that allows offline editing on multiple devices must implement its own conflict detection (version vectors, timestamps, or CRDTs) and its own resolution UI from scratch. This is a case where the platform gives Apple far more than it gives the web; don't assume "just use IndexedDB" gets you what iCloud gives native apps for free.

**"Warn before deleting, since deletion propagates everywhere" → applies unchanged.** Any sync system where a delete on one client removes data from all clients and the server needs the same confirmation step Apple describes. This isn't iCloud-specific reasoning; it's a property of any multi-device sync architecture, web included.

## Do / Don't

| Do | Don't |
|---|---|
| Sync automatically once iCloud is enabled | Make people choose which documents to keep in iCloud |
| Show subtle feedback for downloads over a few seconds | Show nothing during a long, silent sync |
| Detect and resolve version conflicts automatically when possible | Force people to manually reconcile every conflict |
| Warn before deleting content that removes it from every device | Delete silently across all devices |
| Include iCloud content in search results | Exclude synced content from search |
| Store only settings people want applied across all their devices | Sync settings that only make sense on one device |
| Be picky about what goes in the Documents folder | Fill Documents with regenerable app resources that bloat backups |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
