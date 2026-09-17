---
title: Searching
url: https://developer.apple.com/design/human-interface-guidelines/searching
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2026-06-08
---

# Searching

People use various search techniques to find content on their device, within an app, and within a document or file.

## Core guidance

To search for content within an app, people generally expect to use a search field. When it makes sense, you can personalize the search experience by using what you know about how people interact with your app — for example, displaying recent searches, search suggestions, completions, or corrections based on terms people searched earlier in your app.

In some cases, people appreciate the ability to scope a search or filter the results — for example, searching for items by creation date, file size, or file type (see Scope bars and tokens). You can also help people find content within an open document or file by implementing ways to find content in a window or page in your iOS, iPadOS, or macOS app.

In iOS, iPadOS, and macOS, Spotlight helps people find content across all apps in the system and on the web. When you index and provide information about your app's content, people can use Spotlight to find content your app contains without opening it first — see Systemwide search, below.

### Best practices

**If search is important, give it a primary position in your app or view.** For example, in the Notes app, a search field is in the bottom toolbar alongside other important actions. In apps that use tab bars, like Photos and Apple TV, search is a dedicated tab.

**Aim to make your app's content searchable through a single location.** People appreciate having one clearly identified location they can use to find anything they're looking for in your app. For apps with clearly distinct sections, it may still be useful to offer a local search — for example, search acts as a filter on the current view when searching your songs and albums in the iOS Music app.

**Clearly display the current scope of a search.** Use descriptive placeholder text, a scope bar, or a title to help reinforce what someone is currently searching. For example, in the Mail app there is always a clear reference to the mailbox someone is searching.

**Provide suggestions to make searching easier.** Displaying a person's recent searches before they start typing, or offering predictive search suggestions while they're typing, helps people search faster and type less. For developer guidance, see `searchSuggestions(_:)`.

**Take privacy into consideration before displaying search history.** People might not appreciate having their search history appear where others might see it. If you do show search history, provide a way for people to clear it if they want.

### Systemwide search

**Make your app's content searchable in Spotlight.** You can share content with Spotlight by making it indexable and specifying descriptive attributes known as metadata. Spotlight extracts, stores, and organizes this information to allow for fast, comprehensive searches.

**Define metadata for custom file types you handle.** Supply a Spotlight File Importer plug-in that describes the types of metadata your file format contains. For developer guidance, see `CSImportExtension`.

**Use Spotlight to offer advanced file-search capabilities within the context of your app.** For example, you might include a button that instantly initiates a Spotlight search based on the current selection, then display a custom view that presents the search results or a filtered subset of them.

**Prefer using the system-provided open and save views.** These generally include a built-in search field that people can use to search and filter the entire system. For related guidance, see File management.

**Implement a Quick Look generator if your app produces custom file types.** A Quick Look generator helps Spotlight and other apps show previews of your documents. For developer guidance, see Quick Look.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, tvOS, visionOS, or watchOS.

## Native implementation

**Related**
- Search fields

**Developer documentation**
- Adding your app's content to Spotlight indexes — Core Spotlight
- `searchSuggestions(_:)`
- `CSImportExtension`
- Quick Look

**Videos:** Design intuitive search experiences

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**"People generally expect to use a search field" → a real `<input type="search">`, discoverable, not a hidden trigger behind an icon-only affordance.** Apple's expectation is that search is an established, recognizable pattern — people already know what a search field looks like and where to expect it. On the web, an icon that expands into a field on click adds a discovery step Apple's own guidance argues against for anything "important." If search matters to your product, show the field, don't hide it behind an icon; save the icon-trigger pattern for genuinely secondary search.

**"Give it a primary position" → placement in the visual hierarchy, not just presence in the DOM.** A search input that exists in markup but sits below the fold or inside a rarely opened menu doesn't satisfy this rule any more than an app that buries search three taps deep would satisfy Apple's. The web-native equivalent of Apple's tab-bar or toolbar placement is putting the field in persistent header or navigation chrome that's visible without scrolling.

**"A single, clearly identified location" → one canonical search entry point, federated results underneath it.** The principle transfers directly: resist the temptation to scatter multiple independent search boxes across a site's sections unless, like Apple's Music example, each is genuinely scoped to a distinct local context and clearly labeled as such.

**"Clearly display the current scope" → visible scope state, not just a placeholder that's easy to miss.** Placeholder text disappears the moment someone starts typing, so if scope is placeholder-only, the person loses the reminder exactly when they need it most (mid-query, checking whether they searched the right thing). A persistent chip, tab, or label alongside the input — not inside it — carries the scope indicator through the whole interaction, which is closer to what Apple's Mail mailbox reference actually does.

**Search suggestions and recent searches → an `aria-live` region and a real combobox pattern, typed for assistive tech.** A visual dropdown of suggestions under a search field is not automatically usable — screen reader users need the suggestions exposed through the ARIA combobox/listbox pattern (`role="combobox"`, `aria-expanded`, `aria-activedescendant`) so they can navigate the list the same way sighted users see it appear. This is a case where the web has more plumbing to get right than Apple's guidance implies, because a native search-suggestions API on iOS or macOS already wires accessibility for you.

**Search-history privacy → applies unchanged, plus the browser's own autofill.** Apple's warning about displaying search history where others might see it applies as-is to a shared or public computer. The web layers on an extra wrinkle Apple's platforms mostly abstract away: browser-level form autofill can also surface prior queries independent of anything your app stores, so clearing your own app's history doesn't necessarily clear what autocomplete offers.

**Systemwide search (Spotlight) → no full web equivalent; the nearest analogue is structured metadata for external search engines.** Spotlight is an OS-level index with an app-specific API contract (`CSSearchableItem`, Core Spotlight). Nothing on the web gives your site a comparable guarantee of being indexed and surfaced by a general "system search" the user already has open — the closest a web app gets is exposing good `<meta>` descriptions, structured data (schema.org `SearchAction`), and a sitemap so external search engines and browser omnibox suggestions can find your content, but this is a much weaker and slower-updating channel than Spotlight's live, on-device index. If your product's search matters primarily *inside* the session, this Apple pattern mostly doesn't translate — build strong in-app search instead of trying to replicate Spotlight indexing on the web.

## Do / Don't

| Do | Don't |
|---|---|
| Give search a primary, visible position if it matters | Hide an important search field behind a discovery step |
| Offer one clear, canonical search location | Scatter multiple unlabeled search boxes across the app |
| Display the current search scope persistently | Rely on placeholder text alone to convey scope |
| Offer recent searches and predictive suggestions | Force people to retype searches they've already made |
| Let people clear their search history | Expose search history with no way to remove it |
| Make custom file types indexable and previewable | Leave custom content invisible to systemwide search |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
