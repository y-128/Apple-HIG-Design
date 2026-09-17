---
title: Widgets
url: https://developer.apple.com/design/human-interface-guidelines/widgets
platforms: [iOS, iPadOS, macOS, visionOS, watchOS]
last_updated: 2025-12-16
---

# Widgets

A widget provides quick access to essential information and focused interactions from your app or game in additional contexts.

## Core guidance

Widgets help people organize and personalize their devices by displaying timely, glanceable content and offering specific functionality. They appear in various contexts for a consistent experience across platforms. For example, a person might place a Weather widget on the Home Screen and Lock Screen of their iPhone and iPad, on the desktop and Notification Center of their Mac, on a horizontal or vertical surface when they wear Apple Vision Pro, or at a fixed position in the Smart Stack of Apple Watch.

### Anatomy

Widgets come in different sizes, ranging from small accessory widgets on iPhone, iPad, and Apple Watch to system family widgets that include an extra large size on iPad, Mac, and Apple Vision Pro. Widgets adapt their appearance to the context in which they appear and respond to a person's device customization. Consider three aspects when you design widgets: the widget size to support, the context (devices and system experiences) in which it may appear, and the rendering modes and color treatment it receives based on size and context.

The WidgetKit framework provides default appearances and treatments for each widget size to fit the system experience or device where it appears. However, it's important to consider creating a custom widget design that can provide the best experience for your content in each specific context.

#### System family widgets

System family widgets offer a broad range of sizes — small, medium, large, extra large, and extra large portrait — and may include one or more interactive elements. The following table shows supported contexts for each system family widget size:

| Widget size | iPhone | iPad | Mac | Apple Vision Pro |
|---|---|---|---|---|
| System small | Home Screen, Today View, StandBy, and CarPlay | Home Screen, Today View, and Lock Screen | Desktop and Notification Center | Horizontal and vertical surfaces |
| System medium | Home Screen and Today View | Home Screen and Today View | Desktop and Notification Center | Horizontal and vertical surfaces |
| System large | Home Screen and Today View | Home Screen and Today View | Desktop and Notification Center | Horizontal and vertical surfaces |
| System extra large | Not supported | Home Screen and Today View | Desktop and Notification Center | Horizontal and vertical surfaces |
| System extra large portrait | Not supported | Not supported | Not supported | Horizontal and vertical surfaces |

#### Accessory widgets

Accessory widgets display a very limited amount of information because of their size: accessory circular, accessory corner, accessory inline, and accessory rectangular. They appear on the following devices:

| Widget size | iPhone | iPad | Apple Watch |
|---|---|---|---|
| Accessory circular | Lock Screen | Lock Screen | Watch complications and in the Smart Stack |
| Accessory corner | Not supported | Not supported | Watch complications |
| Accessory inline | Lock Screen | Lock Screen | Watch complications |
| Accessory rectangular | Lock Screen | Lock Screen | Watch complications and in the Smart Stack |

#### Appearances

A widget can appear in full-color, in monochrome with a tint color, or in a clear, translucent style. Depending on the location, device, and a person's customization, the system may apply a tinted or clear appearance to the widget and its included full-color images, symbols, and glyphs.

For example, a small system widget appears differently depending on device and location:

- On the Home Screen of iPhone and iPad, people choose from light, dark, clear, and tinted appearances. In light and dark appearances, widgets have a full-color design. In a clear appearance, the system desaturates the widget and adds translucency, highlights, and the Liquid Glass material. In a tinted appearance, the system desaturates the widget and its content, then applies a person's selected tint color.
- On Apple Vision Pro, the widget appears as a 3D object, surrounded by a frame. It takes on a full-color appearance with a glass- or paper-like coating layer that responds to lighting conditions. People can also choose a tinted appearance that applies a color from a set of system-provided color palettes.
- On the Lock Screen of iPad, the widget takes on a monochromatic appearance without a tint color.
- On the Lock Screen of iPhone in StandBy, the widget appears scaled up in size with the background removed. When the ambient light falls below a threshold, the system renders the widget with a monochromatic red tint.

Similarly, a rectangular accessory widget takes on a monochromatic appearance without a tint color on the Lock Screen of iPhone and iPad. On Apple Watch, it can appear as a watch complication in both full-color and tinted appearances, and it can also appear in the Smart Stack.

Each appearance includes a rendering mode that depends on the platform and a person's appearance settings:

- **Full color** — used for system family widgets across all platforms to display the widget in full color. It doesn't change the color of your views.
- **Accented** — used for system family widgets across all platforms and for accessory widgets on Apple Watch. The system removes the background and replaces it with a tinted color effect for a tinted appearance and a Liquid Glass background for a clear appearance. It divides the widget's views into an accent group and a primary group, then applies a solid color to each group.
- **Vibrant** — used for widgets on the Lock Screen of iPhone and iPad, and on iPhone in StandBy in low-light conditions. It desaturates text, images, and gauges, and creates a vibrant effect by coloring content appropriately for the Lock Screen background or a macOS desktop. People can customize the Lock Screen with a tint color, and the system applies a red tint for widgets on iPhone in StandBy in low-light conditions.

The following table lists the occurrences for each rendering mode per platform:

| Platform | Full-color | Accented | Vibrant |
|---|---|---|---|
| iPhone | Home Screen, Today view, StandBy and CarPlay (with the background removed) | Home Screen and Today view | Lock Screen, StandBy in low-light conditions |
| iPad | Home Screen and Today view | Home Screen and Today view | Lock Screen |
| Apple Watch | Smart Stack, complications | Smart Stack, complications | Not supported |
| Mac | Desktop and Notification Center | Not supported | Desktop |
| Apple Vision Pro | Horizontal and vertical surfaces | Horizontal and vertical surfaces | Not supported |

### Best practices

**Choose simple ideas that relate to your app's main purpose.** Include timely content and relevant functionality. For example, the Weather widgets prioritize current high and low temperatures and conditions because that's what people using the Weather app are usually most interested in.

**Aim to create a widget that gives people quick access to the content they want.** People appreciate widgets that display meaningful content and offer useful actions and deep links to key areas of your app. Replicating an app icon offers little additional value, and people may be less likely to keep it on their screens.

**Prefer dynamic information that changes throughout the day.** If a widget's content never appears to change, people may not keep it in a prominent position. Although widgets don't update from minute to minute, it's important to find ways to keep their content fresh to invite frequent viewing.

**Look for opportunities to surprise and delight.** For example, you might design a unique visual treatment for your calendar widget on meaningful occasions, like birthdays or holidays.

**Offer widgets in multiple sizes when doing so adds value.** Small widgets use their limited space to typically show a single piece of information while larger sizes support additional layers of information and actions. Avoid expanding a smaller widget's content to simply fill a larger area — it's more important to create one widget in the size that best represents the content than to offer the widget in every size.

**Balance information density.** Sparse layouts can make the widget seem unnecessary, while overly dense layouts are less glanceable. Create a layout that provides essential information at a glance and allows people to view additional details by taking a longer look. If your layout is too dense, use a larger widget size or replace text with graphics.

**Display only the information that's directly related to the widget's main purpose.** In larger widgets you can display more data — or more detailed visualizations — but don't lose sight of the widget's primary purpose. All Calendar widgets, for example, stay centered on a person's upcoming events, expanding the range of information as the size increases.

**Use brand elements thoughtfully.** Incorporate brand colors, typefaces, and stylized glyphs to make your widget recognizable but don't overpower useful information or make it look out of place. When you include brand elements, people seldom need your logo or app icon to recognize your widget. If a small logo is warranted — for example, when a widget displays content from multiple sources — place it small, in the top-right corner.

**Choose between automatically displaying content and letting people customize displayed information.** The Stocks widget, for example, lets people select the stocks they track, while the Podcasts widget automatically displays recent content because customization isn't needed.

**Avoid mirroring your widget's appearance within your app.** Including an app element that looks like your widget but doesn't behave like it can confuse people, and they may be less likely to try other ways of interacting with it because they expect widget-like behavior.

**Let people know when authentication adds value.** If your widget provides additional functionality when someone is signed in, make sure they know — for example, "Sign in to view reservations" when people are signed out.

#### Updating widget content

To remain relevant and useful, widgets periodically refresh their information but don't support continuous, real-time updates, and the system may adjust update limits depending on various factors.

**Keep your widget up to date.** Finding the appropriate update frequency depends on knowing how often the data changes and estimating when people need to see new data. A tidal-conditions widget, for example, is useful updating hourly even though conditions change constantly. If people are likely to check more frequently than you can update, consider displaying text that describes when the data was last updated.

**Use system functionality to refresh dates and times in your widget.** Because widget update frequency is limited, let the system automatically refresh date and time information to preserve update opportunities. Determine the update frequency that fits your data and show content quickly without hiding stale data behind placeholder content.

**Use animated transitions to bring attention to data updates.** By default, many SwiftUI views animate content updates. Use standard and custom animations with a duration of up to two seconds to let people know when new information is available or content displays differently.

#### Adding interactivity

People tap or click a widget to launch its corresponding app. A widget can also include buttons and toggles to offer additional functionality without launching the app — the Reminders widget, for example, includes toggles to mark a task complete. When people interact with a widget in areas that aren't buttons or toggles, the interaction launches the app.

**Offer simple, relevant functionality and reserve complexity for your app.** Useful widgets offer an easy way to complete a task or action directly related to their content.

**Ensure that a widget interaction opens your app at the right location.** Deep link to details and actions directly related to the widget's content rather than making people navigate there themselves.

**Offer interactivity while remaining glanceable and uncluttered.** Multiple interaction targets — SwiftUI links, buttons, and toggles — might make sense for your content, but avoid app-like layouts. Pay attention to target size so people can tap or click with confidence and without accidental interactions. Inline accessory widgets offer only one tap target.

#### Choosing margins and padding

Widgets scale to adapt to the screen sizes of different devices and onscreen areas. Supply content at appropriate sizes and let the system resize or scale it as necessary. In iOS, the system ensures your widget looks good on small devices by resizing content designed for large devices. In iPadOS, the system renders your widget at a large size before scaling it down for the Home Screen. Use the values in Specifications and Apple Design Resources for guidance; use SwiftUI for your production widget to ensure flexibility.

**In general, use standard margins to ensure legibility.** Use the standard margin width for widgets — 16 points for most widgets — to avoid crowding their edges and creating a cluttered appearance. If you need tighter margins — for example, to create content groupings for graphics, buttons, or background shapes — setting margins of 11 points can work well. Widgets use smaller margins on the desktop on Mac and on the Lock Screen, including in StandBy.

**Coordinate the corner radius of your content with the corner radius of the widget.** Use a SwiftUI container to apply the correct corner radius so your content looks good within a widget's rounded corners.

#### Displaying text in widgets

**Prefer using the system font, text styles, and SF Symbols.** The system font helps your widget look at home on any platform, and makes it easier to display great-looking text in a variety of weights, styles, and sizes. Use SF Symbols to align and scale symbols with system-font text. If you use a custom font, do so sparingly and make sure it's easy to read at a glance — it often works well to pair a custom font for large text with SF Pro for smaller text.

**Avoid very small font sizes.** In general, display text using fonts at 11 points or larger. Text smaller than 11 points can be too hard for many people to read.

**Avoid rasterizing text.** Always use text elements and styles to ensure your text scales well and VoiceOver can speak your content.

> **Note (Apple):** In iOS, iPadOS, and visionOS, widgets support Dynamic Type sizes from Large to AX5 when you use `Font` to choose a system font or `custom(_:size:)` to choose a custom font.

#### Using color

**Use color to enhance a widget's appearance without competing with its content.** Beautiful colors draw the eye, but they're best when they don't prevent people from absorbing a widget's information at a glance. In your asset catalog, you can also specify the colors you want the system to use as it generates your widget's editing-mode user interface.

**Convey meaning without relying on specific colors to represent information.** Widgets can appear monochromatic (with or without a custom tint color), and in watchOS the system may invert colors depending on the chosen watch face. Use text and iconography in addition to color to express meaning.

**Use full-color images judiciously.** When a person chooses a tinted or clear appearance, the system by default desaturates full-color images. You can choose to render images in full color even in tinted or clear appearances, but this draws special attention to the widget and can make it feel as if it doesn't belong to the platform. Consider reserving full-color images to represent media content, such as album art, and use full-color images with smaller dimensions than the size of the widget.

### Rendering modes

#### Full-color

**Support light and dark appearances.** Prefer light backgrounds for the light appearance and dark backgrounds for the dark appearance, and consider using semantic system colors for text and backgrounds so colors dynamically adapt to the current appearance. You can also support different appearances by putting color variants in your asset catalog.

#### Accented

**Group widget components into an accented and a primary group.** The accented rendering mode divides the widget's view hierarchy into an accent group and a primary group. On iPhone, iPad, and Mac, the system tints primary and accented content white. On Apple Watch, the system tints primary content white and accented content in the color of the watch face.

#### Vibrant

**Offer enough contrast to ensure legibility.** In vibrant rendering mode, the opacity of pixels within an image determines the strength of the blurred background material effect — fully transparent pixels let the background material pass through as is. The brightness of pixels determines how vibrant they appear on the Lock Screen: brighter gray values provide more contrast, darker values less.

**Create optimized assets for the best vibrant effect.** Render content like images, numbers, and text at full opacity. Use white or light gray for the most prominent content and darker grayscale values for secondary elements to establish hierarchy. Confirm image content has sufficient contrast in grayscale, and use opaque grayscale values — rather than opacities of white — for the best vibrant material effect.

### Previews and placeholders

**Design a realistic preview to display in the widget gallery.** Highlighting your widget's capabilities — and clearly representing the experience each widget type or size provides — helps people make an informed decision. You can display real data, but if it takes too long to generate or load, display realistic simulated data instead.

**Design placeholder content that helps people recognize your widget.** An installed widget displays placeholder content while its data loads. Combine static interface components with semi-opaque shapes that stand in for dynamic content — for example, rectangles of different widths to suggest lines of text, and circles or squares in place of glyphs and images.

**Write a succinct widget description.** The widget gallery displays descriptions that help people understand what each widget does. Begin with an action verb — for example, "See the current weather conditions and forecast for a location" or "Keep track of your upcoming events and meetings." Avoid unnecessary phrases that reference the widget itself, like "This widget shows…," "Use this widget to…," or "Add this widget." Use approachable language and sentence-style capitalization.

**Group your widget's sizes together, and provide a single description.** If your widget is available in multiple sizes, group them together so people don't think each size is a different widget, and provide one description regardless of how many sizes you offer.

**Consider coloring the Add button.** After people choose your app in the widget gallery, an Add button appears below the group of widgets you offer. You can specify a color for this button to help remind people of your brand.

## Platform considerations

No additional considerations for macOS. Not supported in tvOS.

### iOS, iPadOS

Widgets on the Lock Screen are functionally similar to watch complications and follow design principles for Complications in addition to design principles for widgets. Provide useful information in your Lock Screen widget rather than treating it only as an additional way to launch into your app. In many cases, a design for complications also works well for widgets on the Lock Screen (and vice versa), so consider creating them in tandem.

Your app can offer widgets on the Lock Screen in three shapes: inline text that appears above the clock, and circular and rectangular shapes that appear below the clock.

**Support the Always-On display on iPhone.** Devices with the Always-On display render Lock Screen widgets with reduced luminance. Use levels of gray that provide enough contrast, and make sure your content remains legible.

**Offer Live Activities to show real-time updates.** Widgets don't show real-time information. If your app lets people track the progress of a task or event for a limited amount of time with frequent updates, consider offering Live Activities instead. Widgets and Live Activities use the same underlying frameworks and share design similarities, so it can be a good idea to develop them in tandem and reuse code and design components for both.

#### StandBy and CarPlay

On iPhone in StandBy, the system displays two small system family widgets side-by-side, scaled up to fill the Lock Screen. By supporting StandBy, you also ensure your widgets work well in CarPlay — CarPlay and StandBy widgets both use the small system family widget with the background removed, scaled up to best fit the grid on the Widgets screen. Glanceable information and large text are especially important in CarPlay to make your widget easy to read on a car's display.

**Limit usage of rich images or color to convey meaning in StandBy.** Instead, make use of the additional space by scaling up and rearranging text so people can glance at the widget from a greater distance. To seamlessly blend with the black background, don't use background colors for your widget in StandBy. On iPhone in StandBy in low-light conditions, the system renders widgets in a monochromatic look with a red tint.

### visionOS

Widgets in visionOS are 3D objects that people place on a horizontal or vertical surface. When placed, a widget persists in that location even when the person turns Apple Vision Pro off and back on. Widgets have a consistent, real-world scale, and their size, mounting style, and treatment style impact how a person perceives them.

visionOS widgets appear in full-color by default, but switch to the accented rendering mode when people personalize them with tint colors from a range of system-provided color palettes. People can also customize the frame width of widgets that use the elevated mounting style. visionOS doesn't provide systemwide light or dark appearances; however, some widgets — like the Music poster widget — can offer their own light/dark customization option generated from their content.

**Adapt your design and content for the spatial experience Apple Vision Pro provides.** Widgets don't float in isolation — they're part of living rooms, kitchens, offices, and more. Consider this context early. For example, the Music widget adapts to a poster-like appearance that's glanceable across the room with large typography and a high-resolution image, while a productivity app might offer a small widget that easily fits on a desk.

**Test your widgets across the full range of system color palettes and in different lighting conditions.** Make sure tone, contrast, and legibility remain consistent and intentional. If you exclude UI elements from tinting, test every provided tint color palette to confirm the untinted elements stay legible.

**Thresholds and sizes.** Widgets on Apple Vision Pro can adapt based on a person's proximity. visionOS provides two key thresholds to design for: the *simplified* threshold for viewing at a distance, and the *default* threshold for viewing nearby. **Design a responsive layout that shows the right level of detail for each threshold.** At a distance, display a simplified version with fewer details and a larger type size, and remove interactive elements like buttons or toggles. Nearby, show more details with a smaller type size. Maintain shared elements across both thresholds so the layout feels continuous.

**Offer widget family sizes that fit a person's surroundings well.** Widgets map to real-world dimensions and have a permanent presence in a person's spatial environment. Think about where people might place your widget — mounted to a wall, on a sideboard, next to a workspace — and choose a size right for that context.

**Display content in a way that remains legible from a range of distances.** People can scale a widget from 75 to 125 percent in size. Use print design principles — clear hierarchy, strong typography, scale — to keep content glanceable, and include high-resolution assets that look good scaled up to every size.

**Mounting styles.** The *elevated* style, on horizontal surfaces (a desk), always appears elevated and gently tilts backward for readability, casting a soft shadow that grounds it on the surface; on vertical surfaces (a wall) it can also sit flush like a picture frame. The *recessed* style, only available on vertical surfaces, sets content back into the surface for a cutout-like depth effect. By default, widgets use the elevated style because it works on both horizontal and vertical surfaces.

**Choose the mounting style that fits your content and the experience you want to create.** Elevated is ideal for content that should stand out and feel present, like reminders, media, or glanceable data. Recessed is ideal for immersive or ambient content, like weather or editorial content, and is vertical-surface only. If you choose to only support recessed, people can't place the widget on a horizontal surface — a weather app, for example, might support only recessed for its large and extra-large sizes (to suggest looking out of a window) while supporting only elevated for its small size.

> **Developer note (Apple):** Use the `supportedMountingStyles(_:)` property of your `WidgetConfiguration` to declare supported mounting styles — elevated, recessed, or both — for all widgets in the configuration. To offer a widget that supports only one style alongside widgets that support both, create separate widget configurations.

**Test your elevated widget designs with each system-provided frame width.** People can choose from different system-defined frame widths for elevated widgets, and you can't change your layout based on the choice, so make sure your layout stays visually balanced for every frame width.

**Treatment styles.** The *paper* style creates a more grounded, print-like look that feels solid and part of its surroundings, becoming darker or lighter as lighting conditions change. The *glass* style creates a lighter, layered look with depth and visual separation between foreground and background; foreground elements always stay bright and legible regardless of ambient light. **Choose paper** for a print-like look that feels like a real object in the room — the Music poster widget uses it to display albums and playlists like framed artwork. **Choose glass** for information-rich widgets where foreground content, like headlines, must stay sharp and legible over a softer, print-like background image.

### watchOS

**Provide a colorful background that conveys meaning.** By default, widgets in the Smart Stack use a black background. Consider a custom background color that provides additional meaning — the Stocks app, for example, uses a red background for falling values and green for rising values.

**Encourage the system to display or elevate the position of your watchOS widget in the Smart Stack.** Relevancy information helps the system show your widget when people need it most. Relevance can be location-based or specific to ongoing system actions, like a workout.

## Specifications

> **Source limitation:** Apple's iOS dimensions table appears to include a seventh column — likely an "Inline (pt)" size — that did not extract cleanly from the source PDF. Only fragments of that column's header ("In") and values ("2", "24", "N") remain in the captured text, and they cannot be reliably reconstructed. The table below reproduces the six columns that extracted intact (screen size, Small, Medium, Large, Circular, Rectangular) and omits the unreliable seventh column rather than guessing at its values.

### iOS dimensions

| Screen size (portrait, pt) | Small (pt) | Medium (pt) | Large (pt) | Circular (pt) | Rectangular (pt) |
|---|---|---|---|---|---|
| 430×932 | 170x170 | 364x170 | 364x382 | 76x76 | 172x76 |
| 428x926 | 170x170 | 364x170 | 364x382 | 76x76 | 172x76 |
| 414x896 | 169x169 | 360x169 | 360x379 | 76x76 | 160x72 |
| 414x736 | 159x159 | 348x157 | 348x357 | 76x76 | 170x76 |
| 393x852 | 158x158 | 338x158 | 338x354 | 72x72 | 160x72 |
| 390x844 | 158x158 | 338x158 | 338x354 | 72x72 | 160x72 |
| 375x812 | 155x155 | 329x155 | 329x345 | 72x72 | 157x72 |
| 375x667 | 148x148 | 321x148 | 321x324 | 68x68 | 153x68 |
| 360x780 | 155x155 | 329x155 | 329x345 | 72x72 | 157x72 |
| 320x568 | 141x141 | 292x141 | 292x311 | N/A | N/A |

### iPadOS dimensions

| Screen size (portrait, pt) | Row | Small (pt) | Medium (pt) | Large (pt) | Extra large (pt) |
|---|---|---|---|---|---|
| 768x1024 | Canvas | 141x141 | 305.5x141 | 305.5x305.5 | 634.5x305.5 |
| 768x1024 | Device | 120x120 | 260x120 | 260x260 | 540x260 |
| 744x1133 | Canvas | 141x141 | 305.5x141 | 305.5x305.5 | 634.5x305.5 |
| 744x1133 | Device | 120x120 | 260x120 | 260x260 | 540x260 |
| 810x1080 | Canvas | 146x146 | 320.5x146 | 320.5x320.5 | 669x320.5 |
| 810x1080 | Device | 124x124 | 272x124 | 272x272 | 568x272 |
| 820x1180 | Canvas | 155x155 | 342x155 | 342x342 | 715.5x342 |
| 820x1180 | Device | 136x136 | 300x136 | 300x300 | 628x300 |
| 834x1112 | Canvas | 150x150 | 327.5x150 | 327.5x327.5 | 682x327.5 |
| 834x1112 | Device | 132x132 | 288x132 | 288x288 | 600x288 |
| 834x1194 | Canvas | 155x155 | 342x155 | 342x342 | 715.5x342 |
| 834x1194 | Device | 136x136 | 300x136 | 300x300 | 628x300 |
| 954x1373 * | Canvas | 162x162 | 350x162 | 350x350 | 726x350 |
| 954x1373 * | Device | 162x162 | 350x162 | 350x350 | 726x350 |
| 970x1389 * | Canvas | 162x162 | 350x162 | 350x350 | 726x350 |
| 970x1389 * | Device | 162x162 | 350x162 | 350x350 | 726x350 |
| 1024x1366 | Canvas | 170x170 | 378.5x170 | 378.5x378.5 | 795x378.5 |
| 1024x1366 | Device | 160x160 | 356x160 | 356x356 | 748x356 |
| 1192x1590 * | Canvas | 188x188 | 412x188 | 412x412 | 860x412 |
| 1192x1590 * | Device | 188x188 | 412x188 | 412x412 | 860x412 |

*\* When Display Zoom is set to More Space.*

### visionOS dimensions

| Widget | Size in pt | Size in mm (scaled to 100%) |
|---|---|---|
| Small | 158x158 | 268x268 |
| Medium | 338x158 | 574x268 |
| Large | 338x354 | 574x600 |
| Extra large | 450x338 | 763x574 |
| Extra large portrait | 338x450 | 574x763 |

### watchOS dimensions

| Apple Watch size | Size of a widget in the Smart Stack (pt) |
|---|---|
| 40mm | 152x69.5 |
| 41mm | 165x72.5 |
| 44mm | 173x76.5 |
| 45mm | 184x80.5 |
| 49mm | 191x81.5 |

## Native implementation

**Related**
- Layout

**Developer documentation**
- WidgetKit
- Developing a WidgetKit strategy — WidgetKit
- Preparing widgets for additional platforms, contexts, and appearances
- Displaying the right widget background
- Creating accessory widgets and watch complications
- Updating your widgets for visionOS
- Making a configurable widget
- Keeping a widget up to date
- Animating data updates in widgets and Live Activities
- Optimizing your widget for accented rendering mode and Liquid Glass
- Asset management
- Supporting Dark Mode in your interface

**Key APIs**
- `WidgetConfiguration` — declares a widget's supported families and behavior
- `supportedMountingStyles(_:)` — declares supported visionOS mounting styles (elevated, recessed, or both)
- `ContainerRelativeShape` — applies the widget's own corner radius to your content
- `padding(_:_:)` — sets widget margins
- `widgetAccentable(_:)` — marks a view as part of the accent group in accented rendering mode
- `WidgetRenderingMode` — detects the current rendering mode (full color, accented, vibrant)
- `Font`, `custom(_:size:)` — choose a system or custom font that supports Dynamic Type in a widget
- `RelevanceKit` — supplies relevance information to elevate a watchOS widget's Smart Stack position

**Videos:** WidgetKit foundations · What's new in widgets · Design widgets for visionOS

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**No web platform surface plays the role of a widget.** A widget's value comes from living outside the app, on system-owned real estate (Home Screen, Lock Screen, desktop, a wearable's watch face) that the app doesn't control and that the person curates themselves. Browsers grant no site that kind of persistent, ambient placement — a web page can't install itself onto an OS home screen, a lock screen, or another surface's grid, no matter how the page is built. This part of the guidance is platform-bound, and the honest thing to say is that there's no true equivalent, not a stretched one.

**What does transfer: the "glanceable summary, not a mini-app" principle.** Apple's insistence that a widget show essential, dynamic information rather than replicate the app maps onto any embeddable, glanceable web surface a developer does control — a dashboard summary card, a browser extension popup, an email digest, or a PWA's home-screen icon paired with `shortcuts` in the web app manifest (which jump straight to a relevant screen, echoing "deep link to details and actions directly related to the widget's content"). The same failure mode Apple warns against — a widget that's just a launcher — applies just as much to a dashboard card that's just a link.

**"Prefer dynamic information that changes throughout the day" → avoid static summary cards.** A dashboard tile that never changes invites the same fate as a widget nobody keeps: people stop looking at it. If a card's data is genuinely slow-moving, showing a last-updated timestamp (Apple's own fallback for widgets that can't refresh fast enough) is honest where a card that looks live but isn't is not.

**Rendering modes (full-color, accented, vibrant) → theme-aware, not brand-fixed, color.** Apple's tinted and vibrant modes exist because a widget shares a system-owned background it doesn't control and must stay legible against whatever the person chose. The web analogue is respecting `prefers-color-scheme` and, where relevant, `prefers-contrast`, and not hard-coding a card's colors against an assumed light background — the same discipline, aimed at the same problem: content living somewhere it doesn't own.

**Minimum text size (11 pt) → don't shrink embeddable summary text below body-adjacent sizes.** The reasoning transfers even though the surface doesn't: a glanceable card is glanced at, briefly and often from a slight distance (a second monitor, a phone propped up), so the same "don't go below what's comfortably readable at a glance" logic applies to any compact web card's type scale.

**Interactivity limits → keep embedded actions single-purpose.** Apple's warning against app-like layouts in a widget is really a warning against over-scoping a surface that was granted for one glanceable purpose. A dashboard card or extension popup that grows toggles, forms, and multi-step flows has the same problem — it's no longer a summary, and it invites the interactions a full page should own instead.

## Do / Don't

| Do | Don't |
|---|---|
| Show timely, glanceable content specific to your app's purpose | Replicate your app icon as a widget's content |
| Offer the widget size that best represents your content | Force a small widget's content to fill a larger size |
| Deep link to the exact detail the widget shows | Make people navigate after tapping the widget |
| Use the system font, text styles, and SF Symbols | Use fonts smaller than 11 points |
| Use semantic system colors so appearances adapt automatically | Rely on color alone to convey meaning |
| Design realistic previews and placeholder content | Leave placeholder content indistinguishable from real content |
| In visionOS, match mounting and treatment style to the content's purpose | Ignore lighting and proximity thresholds in visionOS |
| Provide relevance information to help the Smart Stack surface your widget | Assume a widget will always appear where you placed it |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
