---
title: Maps
url: https://developer.apple.com/design/human-interface-guidelines/maps
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2024-12-18
---

# Maps

A map displays outdoor or indoor geographical data in your app or on your website.

## Core guidance

A map uses a familiar interface that supports much of the same functionality as the system-provided Maps app, such as zooming, panning, and rotation. A map can also include annotations and overlays and show routing information, and you can configure it to use a standard graphical view, a satellite image-based view, or a view that's a hybrid of both.

### Best practices

**In general, make your map interactive.** People expect to be able to zoom, pan, and otherwise interact with maps in familiar ways. Noninteractive elements that obscure the map can interfere with people's expectations for how maps behave.

**Pick a map emphasis style that suits the needs of your app.** There are two emphasis styles to choose from:

- The default style presents a version of the map with fully saturated colors, and is a good option for most standard map applications without a lot of custom elements. This style is also useful for keeping visual alignment between your map and the Maps app, in situations when people might switch between them.
- The muted style, by contrast, presents a desaturated version of the map. This style is great if you have a lot of information-rich content that you want to stand out against the map.

> *Image caption:* Default style — a fully saturated map.
> *Image caption:* Muted style — a desaturated map, useful when information-rich content needs to stand out.

**Help people find places in your map.** Consider offering a search feature combined with a way to filter locations by category. The search field for a shopping mall map, for example, might include filters that make it easy to find common store types, like clothing, housewares, electronics, jewelry, and toys.

**Clearly identify elements that people select.** When someone selects a specific area or other element on the map, use distinct styling like an outline and color variation to call attention to the selection.

**Cluster overlapping points of interest to improve map legibility.** A cluster uses a single pin to represent multiple points of interest within close proximity. As people zoom in on a map, clusters expand to progressively reveal individual points of interest.

> *Image caption:* Points of interest shown as a single cluster pin, then as individual points of interest once zoomed in.

**Help people see the Apple logo and legal link.** It's fine when parts of your interface temporarily cover the logo and link, but don't cover these elements all the time. Follow these guidelines to help keep the Apple logo and legal link visible:

- Use adequate padding to separate the logo and link from the map boundaries and your custom controls. For example, it works well to use 7 points of padding on the sides of the elements and 10 points above and below them.
- Avoid causing the logo and link to move with your interface. It's best when the Apple logo and legal link appear to be fixed to the map.
- If your custom interface can move relative to the map, use the lowest position of the custom element to determine the placement of the logo and link. For example, if your app lets people pull up a custom card from the bottom of the screen, place the Apple logo and legal link 10 points above the lowest resting position of the card.

> **Note (Apple):** The Apple logo and legal link aren't shown on maps that are smaller than 200x100 pixels.

### Custom information

**Use annotations that match the visual style of your app.** Annotations identify custom points of interest on your map. The default annotation marker has a red tint and a white pin icon. You can change the tint to match the color scheme of your app. You can also change the icon to a string or image, like a logo. An icon string can contain any characters, including Unicode characters, but keep it to two to three characters in length for readability.

**If you want to display custom information that's related to standard map features, consider making them independently selectable.** When you support selectable map features, the system treats Apple-provided features (including points of interest, territories, and physical features) independently from other annotations that you add. You can configure custom appearances and information to represent these features when people select them.

**Use overlays to define map areas with a specific relationship to your content.**

- Above roads, the default level, places the overlay above roads but below buildings, trees, and other features. This is great for situations where you want people to have an idea of what's below the overlay, while still clearly understanding that it's a defined space.
- Above labels places the overlay above both roads and labels, hiding everything beneath it. This is useful for content that you want to be fully abstracted from the features of the map, or when you want to hide areas of the map that aren't relevant.

**Make sure there's enough contrast between custom controls and the map.** Insufficient contrast makes controls hard to see and can cause them to blend in with the map. Consider using a thin stroke or light drop shadow to help a custom control stand out, or applying blend modes to the map area to increase its contrast with the controls atop it.

### Place cards

Place cards display rich place information in your app or website, such as operating hours, phone numbers, addresses, and more. This enables you to provide structured and up-to-date information for places that you specify, and add depth to search results.

#### Displaying place cards in a map

You can present a place card that appears directly in your map anytime someone selects a place. This is a great way to provide place information in a map with multiple places that you specify, like a map of bookstores that an author plans to visit on their book signing tour.

You can also display place cards for other places on a map, such as points of interest, territories, and physical features, to provide valuable context to people about nearby places.

> **Developer note (Apple):** In websites, you can embed a custom map that displays a place card by default for a single place that you specify, using the Maps Embed API.

The system defines several place card styles, which specify the size, appearance, and information included in a place card.

- The automatic style lets the system determine the place card style based on the size of your map view.
- The callout style displays a place card in a popover style next to the selected place. You can further specify the style of a callout — the full callout style displays a large, detailed place card, and the compact callout style displays a space-saving, more concise place card. If you don't specify a callout style, the system defaults to the automatic callout style, which determines the callout style based on your map's view size.
- The caption style displays an "Open in Apple Maps" link.
- The sheet style displays a place card in a sheet.

> *Image caption:* The four place card styles side by side — full callout, compact callout, caption, and sheet.

Full callout style place cards appear differently depending on a person's device. The system presents the full callout style place card in a popover style in iPadOS and macOS, and as a sheet in iOS.

**Consider your map presentation when choosing a style.** The full callout style place card offers people the richest experience, presenting them with the most information about a place directly in your map. However, be sure to choose a place card style that fits in the context of your map. For example, if your app displays a small map with many annotations, consider using the compact callout style for a space-saving presentation that shows place information while maintaining the context of the other places that you specify in your map.

**Make sure your place card looks great on different devices and window sizes.** If you choose to specify a style, ensure that the content in your place card remains viewable on different devices and as window sizes change. For full callout style place cards, you can set a minimum width to prevent text from overflowing on smaller devices.

**Avoid duplicating information.** Consider what information you already display in your app or website when you choose a place card style. For example, the full callout style place card might display information that your app already shows. In this case, the compact callout or caption style might be a better complement.

**Keep the location on your map visible when displaying a place card.** This helps people maintain a sense of where the location is on your map while getting detailed place information. You can set an offset distance for your place card and point it to the selected location.

#### Adding place cards outside of a map

You can also display place information outside of a map in your app or website. For example, you might want to display a list of places rather than a map, like in search results or a store locator, and present a place card when people select one.

> **Note (Apple):** If you don't display a place card directly within a map view, you must include a map in the place card.

**Use location-related cues in surrounding content to help communicate that people can open a place card.** For example, you can display place names and addresses alongside a button for more details to help indicate that people can interact with it to get place information. For a space-efficient design, you can include a map pin icon with a place name to help communicate that people can open a place card.

### Indoor maps

Apps connected with specific venues like shopping malls and stadiums can design custom interactive maps that help people locate and navigate to indoor points of interest. Indoor maps can include overlays that highlight specific areas, such as rooms, kiosks, and other locations. They can also include text labels, icons, and routes.

> *Image caption:* Three examples of indoor maps for venues like shopping malls and stadiums.

**Adjust map detail based on the zoom level.** Too much detail can cause a map to appear cluttered. Show large areas like rooms and buildings at all zoom levels. Then, progressively add more detailed features and labels as the map is zoomed in. An airport map might show only terminals and gates when zoomed out, but reveal individual stores and restrooms when zoomed in.

**Use distinctive styling to differentiate the features of your map.** Using color along with icons can help distinguish different types of areas, stores, and services, and make it easy for people to quickly find what they're looking for.

**Offer a floor picker if your venue includes multiple levels.** A floor picker lets people quickly jump between floors. If you implement this feature, keep floor numbers concise for simplicity. In most cases, a list of floor numbers — rather than floor names — is sufficient.

**Include surrounding areas to provide context.** Adjacent streets, playgrounds, and other nearby locations can all help orient people when they use your map. If these areas are noninteractive, use dimming and a distinct color to make them appear supplemental.

**Consider supporting navigation between your venue and nearby transit points.** Make it easy to enter and exit your venue by offering routing to and from nearby bus stops, train stations, parking lots, garages, and other transit locations. You might also offer a way for people to quickly switch over to Apple Maps for additional navigation options.

**Limit scrolling outside of your venue.** This can help people avoid getting lost when they swipe too hard on your map. When possible, keep at least part of your indoor map visible onscreen at all times. To help people stay oriented, you may need to adjust the amount of scrolling you permit based on the zoom level.

**Design an indoor map that feels like a natural extension of your app.** Don't try to replicate the appearance of Apple Maps. Instead, make sure area overlays, icons, and text match the visual style of your app.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, tvOS, or visionOS.

### watchOS

On Apple Watch, maps are static snapshots of geographic locations. Place a map in your interface at design time and show the appropriate region at runtime. The displayed region isn't interactive; tapping it opens the Maps app on Apple Watch. You can add up to five annotations to a map to highlight points of interest or other relevant information.

**Fit the map interface element to the screen.** The entire element needs to be visible on the Apple Watch display without requiring scrolling.

**Show the smallest region that encompasses the points of interest.** The content within a map interface element doesn't scroll, so all key content must be visible within the displayed region.

## Specifications

| Element | Value |
|---|---|
| Apple logo/legal link padding from map boundaries and controls | 7 pt sides, 10 pt above and below |
| Apple logo/legal link placement relative to a movable custom element | 10 pt above the element's lowest resting position |
| Minimum map size to show Apple logo and legal link | 200×100 px |
| Annotation icon string length | 2–3 characters (for readability) |
| watchOS maximum annotations per map | 5 |

## Native implementation

**Developer documentation**
- MapKit
- MapKit JS
- Indoor Mapping Data Format
- Displaying overlays on a map
- Displaying place information using the Maps Embed API

**Key APIs**
- `MKStandardMapConfiguration.EmphasisStyle` — sets the default or muted map emphasis style
- `MKAnnotationView` — displays custom annotations on a map
- `MKMapFeatureOptions` — configures selectable Apple-provided map features
- `MKOverlayLevel` — sets an overlay's level (above roads or above labels)
- `mapItemDetailSelectionAccessory(_:)` / `mapView(_:selectionAccessoryFor:)` / `selectionAccessory` — configure place cards for places you specify
- `mapFeatureSelectionAccessory(_:)` / `selectableMapFeatureSelectionAccessory` — configure place cards for Apple-provided map features
- `MapItemDetailSelectionAccessoryStyle` / `MKSelectionAccessory.MapItemDetailPresentationStyle` / `PlaceSelectionAccessoryStyle` — set place card presentation styles
- `offset(_:)` / `accessoryOffset` / `selectionAccessoryOffset` — offset a place card from its selected location
- `mapItemDetail(_:)` / `PlaceDetail` — display place cards outside of a map view
- `mapItemDetailSheet(item:displaysMap:)` / `init(mapItem:displaysMap:)` — present a place card as a sheet, with or without an embedded map
- `WKInterfaceMap` — displays a static map snapshot on watchOS

**Videos:** Go further with MapKit · Unlock the power of places with MapKit

## Web translation *(derived — not from Apple)*

Unlike most technology frameworks in this collection, Maps has a genuine, Apple-provided web analogue: MapKit JS, listed directly in Apple's own developer documentation links above, brings the same map data, styling, and much of the same interaction model to websites. The Maps Embed API additionally lets a website embed a single-place card without writing any map code. So for this topic, "Web translation" is partly a literal API and partly a set of general map-UI principles that apply whether you use MapKit JS, Google Maps, Mapbox GL, or another provider.

**Interactivity expectations transfer directly.** People bring the same zoom/pan/rotate mental model to any embedded web map, regardless of provider — Apple's "don't obscure the map with noninteractive elements" rule is really about respecting an interaction contract people already have, and that contract is the same on the web.

**Emphasis styles map to provider style layers.** The default-vs-muted choice generalizes to any map SDK's style configuration: a fully saturated base style for a map-first experience, a desaturated or custom style when your own markers, routes, or data overlays need to read as the primary content. The reasoning — match saturation to whether the map or your data should dominate visually — holds regardless of provider.

**Clustering is a standard, provider-agnostic web pattern.** Libraries like Supercluster implement the same progressive-disclosure idea Apple describes: collapse nearby points into one pin, expand them as the person zooms in. The legibility argument (avoid pin overlap at low zoom) is identical on the web.

**Attribution requirements are a genuine constraint, not a suggestion, across providers.** Apple's Apple-logo-and-legal-link rule has a direct counterpart in nearly every map provider's terms of service — Google Maps, Mapbox, and OpenStreetMap-based tiles all require a visible, unobstructed attribution element, often with their own minimum padding and minimum-map-size rules analogous to Apple's 7pt/10pt padding and 200×100px floor. Treat attribution placement as a hard requirement to check against your specific provider's current terms, not just a design nicety.

**Place cards map to info windows, popovers, or bottom sheets.** Apple's automatic/callout/caption/sheet taxonomy is a useful vocabulary for a decision most web map integrations face regardless of provider: show rich detail in a popover anchored to the pin on a wide viewport, and collapse to a full-width sheet or modal on narrow viewports — the same responsive-breakpoint logic CSS media queries already express. "Avoid duplicating information already shown in your list or store locator" is a general information-architecture rule, not Maps-specific.

**Indoor maps have no equivalent first-party web offering.** Indoor Mapping Data Format and IMDF-based rendering exist for native apps; there's no equivalent standardized, widely supported browser API for indoor venue maps, so a web indoor map is typically a custom SVG or canvas overlay built by hand rather than something a map SDK gives you out of the box. The zoom-progressive-detail and floor-picker principles still apply as UX guidance, but you're implementing them yourself rather than configuring a framework feature.

**watchOS's static, noninteractive map has a rough web parallel in a static map image endpoint** (most providers offer one), useful when embedding a map in a constrained or low-interaction context such as an email or a print view — but this is a niche case, not the default web pattern.

## Do / Don't

| Do | Don't |
|---|---|
| Keep the map interactive with standard zoom, pan, and rotation | Cover the map permanently with noninteractive elements |
| Choose default (saturated) or muted (desaturated) emphasis to match your content density | Use the default style when dense custom content needs to stand out |
| Cluster overlapping points of interest and expand them on zoom | Show many overlapping, unclustered pins at low zoom levels |
| Keep the Apple logo and legal link visible with correct padding | Let custom controls or interface elements permanently cover the logo and link |
| Match custom annotations to your app's visual style; keep icon strings to 2–3 characters | Use long, illegible icon strings in annotation markers |
| Choose a place card style that fits your map's context and avoids duplicating shown information | Use the full callout style when your app already displays the same information elsewhere |
| Keep the selected location visible when a place card is shown | Let a place card fully obscure the location it describes |
| Design indoor maps as a natural extension of your app's visual style | Try to replicate the appearance of Apple Maps in a custom indoor map |
| On watchOS, size the static map region to fit the screen without scrolling | Rely on scrolling to reveal key points of interest on watchOS |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
