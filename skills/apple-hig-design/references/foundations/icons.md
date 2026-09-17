---
title: Icons
url: https://developer.apple.com/design/human-interface-guidelines/icons
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2025-06-09
---

# Icons

An effective icon is a graphic asset that expresses a single concept in ways people instantly understand.

## Core guidance

Apps and games use a variety of simple icons to help people understand the items, actions, and modes they can choose. Unlike app icons, which can use rich visual details like shading, texturing, and highlighting to evoke the app's personality, an interface icon typically uses streamlined shapes and touches of color to communicate a straightforward idea.

You can design interface icons — also called glyphs — or you can choose symbols from the SF Symbols app, using them as-is or customizing them to suit your needs. Both interface icons and symbols use black and clear colors to define their shapes; the system can apply other colors to the black areas in each image. For guidance, see SF Symbols.

### Best practices

**Create a recognizable, highly simplified design.** Too many details can make an interface icon confusing or unreadable. Strive for a simple, universal design that most people will recognize quickly. In general, icons work best when they use familiar visual metaphors that are directly related to the actions they initiate or content they represent.

**Maintain visual consistency across all interface icons in your app.** Whether you use only custom icons or mix custom and system-provided ones, all interface icons in your app need to use a consistent size, level of detail, stroke thickness (or weight), and perspective. Depending on the visual weight of an icon, you may need to adjust its dimensions to ensure that it appears visually consistent with other icons.

> *Image caption:* To help achieve visual consistency, adjust individual icon sizes as necessary…
> *Image caption:* …and use the same stroke weight in every icon.

**In general, match the weights of interface icons and adjacent text.** Unless you want to emphasize either the icons or the text, using the same weight for both gives your content a consistent appearance and level of emphasis.

**If necessary, add padding to a custom interface icon to achieve optical alignment.** Some icons — especially asymmetric ones — can look unbalanced when you center them geometrically instead of optically. For example, the download icon shown below has more visual weight on the bottom than on the top, which can make it look too low if it's geometrically centered.

> *Image caption:* An asymmetric icon can look off center even though it's not.

In such cases, you can slightly adjust the position of the icon until it's optically centered. When you create an asset that includes your adjustments as padding around an interface icon, you can optically center the icon by geometrically centering the asset.

> *Image caption:* Moving the icon a few pixels higher optically centers it; including the pixels in padding simplifies centering.

Adjustments for optical centering are typically very small, but they can have a big impact on your app's appearance.

> *Image caption:* Before optical centering (left) and after optical centering (right).

**Provide a selected-state version of an interface icon only if necessary.** You don't need to provide selected and unselected appearances for an icon that's used in standard system components such as toolbars, tab bars, and buttons. The system updates the visual appearance of the selected state automatically.

> *Image caption:* In a toolbar, a selected icon receives the app's accent color.

**Use inclusive images.** Consider how your icons can be understandable and welcoming to everyone. Prefer depicting gender-neutral human figures and avoid images that might be hard to recognize across different cultures or languages. For guidance, see Inclusion.

**Include text in your design only when it's essential for conveying meaning.** For example, using a character in an interface icon that represents text formatting can be the most direct way to communicate the concept. If you need to display individual characters in your icon, be sure to localize them. If you need to suggest a passage of text, design an abstract representation of it, and include a flipped version of the icon to use when the context is right-to-left. For guidance, see Right to left.

> *Image caption:* Create localized versions of an icon that displays individual characters.
> *Image caption:* Create a flipped version of an icon that suggests reading direction.

**If you create a custom interface icon, use a vector format like PDF or SVG.** The system automatically scales a vector-based interface icon for high-resolution displays, so you don't need to provide high-resolution versions of it. In contrast, PNG — used for app icons and other images that include effects like shading, textures, and highlighting — doesn't support scaling, so you have to supply multiple versions for each PNG-based interface icon. Alternatively, you can create a custom SF Symbol and specify a scale that ensures the symbol's emphasis matches adjacent text. For guidance, see SF Symbols.

**Provide alternative text labels for custom interface icons.** Alternative text labels — or accessibility descriptions — aren't visible, but they let VoiceOver audibly describe what's onscreen, simplifying navigation for people with visual disabilities. For guidance, see VoiceOver.

**Avoid using replicas of Apple hardware products.** Hardware designs tend to change frequently and can make your interface icons and other content appear dated. If you must display Apple hardware, use only the images available in Apple Design Resources or the SF Symbols that represent various Apple products.

### Standard icons

For icons to represent common actions in menus, toolbars, buttons, and other places in interfaces across Apple platforms, you can use these SF Symbols. Apple's table also shows a rendered glyph for each row; since that's a graphic asset rather than text data, only the action name and its SF Symbol name are reproduced below — look up the symbol name in the SF Symbols app, or pass it to `Image(systemName:)`, to see the glyph itself.

#### Editing

| Action | Symbol name |
|---|---|
| Cut | `scissors` |
| Copy | `document.on.document` |
| Paste | `document.on.clipboard` |
| Done, Save | `checkmark` |
| Cancel, Close | `xmark` |
| Delete | `trash` |
| Undo | `arrow.uturn.backward` |
| Redo | `arrow.uturn.forward` |
| Compose | `square.and.pencil` |
| Duplicate | `plus.square.on.square` |
| Rename | `pencil` |
| Move to Folder | `folder` |
| Attach | `paperclip` |
| Add | `plus` |
| More | `ellipsis` |

#### Selection

| Action | Symbol name |
|---|---|
| Select | `checkmark.circle` |
| Deselect, Close | `xmark` |
| Delete | `trash` |

#### Text formatting

| Action | Symbol name |
|---|---|
| Superscript | `textformat.superscript` |
| Subscript | `textformat.subscript` |
| Bold | `bold` |
| Italic | `italic` |
| Underline | `underline` |
| Align Left | `text.alignleft` |
| Center | `text.aligncenter` |
| Justified | `text.justify` |
| Align Right | `text.alignright` |

#### Search

| Action | Symbol name |
|---|---|
| Search | `magnifyingglass` |
| Find, Find and Replace, Find Next, Find Previous, Use Selection for Find | `text.page.badge.magnifyingglass` |
| Filter | `line.3.horizontal.decrease` |

#### Sharing and exporting

| Action | Symbol name |
|---|---|
| Share, Export | `square.and.arrow.up` |
| Print | `printer` |

#### Users and accounts

| Action | Symbol name |
|---|---|
| Account, User, Profile | `person.crop.circle` |

#### Ratings

| Action | Symbol name |
|---|---|
| Dislike | `hand.thumbsdown` |
| Like | `hand.thumbsup` |

#### Layer ordering

| Action | Symbol name |
|---|---|
| Bring to Front | `square.3.layers.3d.top.filled` |
| Send to Back | `square.3.layers.3d.bottom.filled` |
| Bring Forward | `square.2.layers.3d.top.filled` |
| Send Backward | `square.2.layers.3d.bottom.filled` |

#### Other

| Action | Symbol name |
|---|---|
| Alarm | `alarm` |
| Archive | `archivebox` |
| Calendar | `calendar` |

## Platform considerations

No additional considerations for iOS, iPadOS, tvOS, visionOS, or watchOS.

### macOS

**Document icons**

If your macOS app can use a custom document type, you can create a document icon to represent it. Traditionally, a document icon looks like a piece of paper with its top-right corner folded down. This distinctive appearance helps people distinguish documents from apps and other content, even when icon sizes are small.

If you don't supply a document icon for a file type you support, macOS creates one for you by compositing your app icon and the file's extension onto the canvas. For example, Preview uses a system-generated document icon to represent JPG files.

In some cases, it can make sense to create a set of document icons to represent a range of file types your app handles. For example, Xcode uses custom document icons to help people distinguish projects, AR objects, and Swift code files.

To create a custom document icon, you can supply any combination of background fill, center image, and text. The system layers, positions, and masks these elements as needed and composites them onto the familiar folded-corner icon shape.

> *Image caption:* macOS composites the elements you supply — background fill, center image, and text — to produce your custom document icon.

Apple Design Resources provides a template you can use to create a custom background fill and center image for a document icon. As you use this template, follow the guidelines below.

**Design simple images that clearly communicate the document type.** Whether you use a background fill, a center image, or both, prefer uncomplicated shapes and a reduced palette of distinct colors. Your document icon can display as small as 16x16 px, so you want to create designs that remain recognizable at every size.

**Designing a single, expressive image for the background fill can be a great way to help people understand and recognize a document type.** For example, Xcode and TextEdit both use rich background images that don't include a center image.

**Consider reducing complexity in the small versions of your document icon.** Icon details that are clear in large versions can look blurry and be hard to recognize in small versions. For example, to ensure that the grid lines in a custom heart document icon remain clear in intermediate sizes, you might use fewer lines and thicken them by aligning them to the reduced pixel grid. In the 16x16 px size, you might remove the lines altogether.

> *Image caption:* The 32x32 px icon has fewer grid lines and a thicker EKG line. The 16x16 px @2x icon retains the EKG line but has no grid lines. The 16x16 px @1x icon has no EKG line and no grid lines.

**Avoid placing important content in the top-right corner of your background fill.** The system automatically masks your image to fit the document icon shape and draws the white folded corner on top of the fill. See Specifications below for the background image sizes to supply.

**If a familiar object can convey a document's type or its connection with your app, consider creating a center image that depicts it.** Design a simple, unambiguous image that's clear and recognizable at every size. The center image measures half the size of the overall document icon canvas. For example, to create a center image for a 32x32 px document icon, use an image canvas that measures 16x16 px. See Specifications below for the center image sizes to supply.

**Define a margin that measures about 10% of the image canvas and keep most of the image within it.** Although parts of the image can extend into this margin for optical alignment, it's best when the image occupies about 80% of the image canvas. For example, most of the center image in a 256x256 px canvas would fit in an area that measures 205x205 px.

**Specify a succinct term if it helps people understand your document type.** By default, the system displays a document's extension at the bottom edge of the document icon, but if the extension is unfamiliar you can supply a more descriptive term. For example, the document icon for a SceneKit scene file uses the term "scene" instead of the file extension "scn". The system automatically scales the extension text to fit in the document icon, so be sure to use a term that's short enough to be legible at small sizes. By default, the system capitalizes every letter in the text.

## Specifications

### Document icon minimum display size

A document icon can display as small as **16x16 px**. Designs — background fill, center image, and text alike — must stay recognizable at that size.

### Document icon background fill sizes

| @1x | @2x |
|---|---|
| 512x512 px | 1024x1024 px |
| 256x256 px | 512x512 px |
| 128x128 px | 256x256 px |
| 32x32 px | 64x64 px |
| 16x16 px | 32x32 px |

### Document icon center image sizes

| @1x | @2x |
|---|---|
| 256x256 px | 512x512 px |
| 128x128 px | 256x256 px |
| 32x32 px | 64x64 px |
| 16x16 px | 32x32 px |

The center image measures half the size of the overall document icon canvas — for example, a 32x32 px document icon uses a 16x16 px center-image canvas.

### Document icon margin

Keep a margin of about **10%** of the image canvas free, so the image occupies roughly **80%** of the canvas. Example: in a 256x256 px canvas, most of the center image should fit within a 205x205 px area.

> **Source limitation:** Apple's "Standard icons" table renders each row's icon as an image glyph inside a JS-driven layout; the captured PDF preserves the action labels and SF Symbol names but not the glyph artwork itself. No symbol names appear to be missing from the extracted rows, but if Apple's live page groups additional actions under a symbol not distinguishable from the PDF's text flow, that grouping would not be reflected here. Verify against the SF Symbols app for the authoritative glyph.

## Native implementation

**Related**
- App icons
- SF Symbols

**Videos:** Designing Glyphs

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**"Create a recognizable, highly simplified design" → keep UI icons legible at 16–24 px.** Apple's reasoning is that too much detail becomes noise at small sizes; the same physics applies to any SVG icon rendered at typical UI sizes. A shared icon set built around a simple, high-contrast silhouette (the way Feather, Heroicons, or Material Symbols are drawn) survives shrinking better than a detailed illustration converted into an icon.

**"Maintain visual consistency across all interface icons" → standardize on one icon set with one grid.** Apple's rule that size, detail, stroke weight, and perspective must match across icons maps directly to picking a single icon library (or a single internal set) built on one `viewBox` grid and one stroke width, rather than mixing icons pulled from different libraries with different visual weights. Mixing sets is the web equivalent of mixing custom and system icons without reconciling their weight.

**"Match the weights of interface icons and adjacent text" → tune stroke-width to the surrounding font-weight.** If body text sits at a regular weight, a heavy-stroke icon reads as louder than the text around it and vice versa. Icon sets that expose a stroke-width variable (or ship separate regular/bold variants) let you match icon weight to type weight the way SF Symbols' weight axis matches SF's.

**"Add padding to achieve optical alignment" → the geometric center of an SVG's `viewBox` is not its optical center.** This is one of the cleanest one-to-one mappings in the whole page: an asymmetric icon (an arrow, a play triangle, a chevron) centered by its bounding box reads as off-balance for exactly the reason Apple describes. The fix is the same — pad the `viewBox` asymmetrically, or nudge the path with a small transform, so the *visual* mass sits centered even though the box isn't.

**"Provide a selected-state version only if necessary" → this is where the mapping breaks down.** Apple can say this because toolbars, tab bars, and buttons are system components that recolor a selected icon automatically. The web has no equivalent OS-level pipeline: a selected nav icon changes appearance only because you wrote the CSS for it. The closest practice is to draw one icon and drive its selected appearance with `currentColor` plus a state-based class or `aria-selected` selector, rather than shipping two separate icon assets — but you own that wiring yourself; nothing does it for you by default.

**"Use inclusive images" → applies to the web without modification.** Gender-neutral pictograms and cross-culturally legible metaphors are exactly as important in a web icon set as in an Apple interface icon, for the same reason: an icon that only reads correctly to one culture or gender fails at its one job.

**"Include text only when essential, localize it, and flip it for RTL" → maps directly, with one addition.** An icon with baked-in glyphs (a formatting "B" or "A") needs a localized variant per script, same as Apple's example. The RTL flip maps to `transform: scaleX(-1)` or, more robustly, to authoring the icon with CSS logical properties so it flips automatically under `direction: rtl` — the web actually has slightly more automatic support here than a hand-maintained flipped asset.

**"Use a vector format like PDF or SVG, not PNG" → SVG for UI icons, full stop.** This is Apple's clearest rule and it transfers unchanged: SVG scales losslessly across every pixel density without shipping 1x/2x/3x raster variants, exactly as PDF/SVG interface icons do on Apple platforms. Where a project still ships PNG icon sprites, it's carrying the exact tax Apple's guidance tells you to avoid — separate exports per density, and blurriness at any size not explicitly exported.

**"Provide alternative text labels" → `aria-label` (or an inline `<title>`) plays the role of the accessibility description.** Apple's reasoning — that the label isn't visible but lets an assistive technology describe the icon — carries over exactly to a screen reader reading an icon-only button. The corollary also carries over: a purely decorative icon next to a text label that already says the same thing should be hidden from assistive technology (`aria-hidden`) rather than doubly announced, the same way Apple doesn't want redundant labels cluttering VoiceOver's output.

**"Avoid replicas of Apple hardware products" → generalizes to avoid replicas of any specific device chrome.** The underlying reasoning — hardware silhouettes date quickly and make an interface look stale — applies just as much to a web icon that renders a specific phone or laptop bezel. Where it doesn't fully transfer: Apple can offer sanctioned hardware artwork through Apple Design Resources; the web has no equivalent authority to defer to, so the safer default is to avoid device-specific chrome in UI icons entirely rather than trying to find a "sanctioned" replica.

**The macOS document-icon system (folded-corner canvas, background fill + center image + text, size-tiered detail reduction, 10%/80% margin) → maps closely to favicon and PWA manifest icon tiers, with one real gap.** Apple's size tiers for document icons (512, 256, 128, 32, 16 px, each with a @2x variant) are the same idea as the size tiers a web manifest requests (16, 32, 48, 180, 192, 512 px and more) for different contexts — browser tab, home-screen tile, splash screen. The instruction to simplify detail at small sizes (fewer grid lines, thicker strokes, dropping detail entirely at 16x16 px) maps directly to designing a dedicated, simplified favicon rather than shrinking a detailed logo. The 10% margin / 80% content rule maps closely to the "safe zone" convention for `purpose: "maskable"` icons in a web manifest, where platforms crop the icon into a circle or squircle and only content within the central safe area is guaranteed to survive. Where the mapping genuinely breaks: macOS's system automatically draws the folded-corner frame around whatever background fill and center image you supply — the OS is compositing chrome on top of your art. No browser or OS does the equivalent for a favicon or manifest icon; what you export is what renders, safe-zone cropping aside, so there's no "the platform will frame this for me" assumption to lean on.

## Do / Don't

| Do | Don't |
|---|---|
| Design simple, universal interface icons built on familiar visual metaphors | Overload an icon with unnecessary detail |
| Keep size, level of detail, stroke weight, and perspective consistent across all icons in your app | Mix icon styles, weights, or perspectives within one app |
| Match icon weight to the weight of adjacent text | Let icon weight fight with the surrounding type for emphasis |
| Add padding so an asymmetric icon is optically, not just geometrically, centered | Leave an asymmetric icon geometrically centered and visually off-balance |
| Use inclusive, gender-neutral imagery that reads across cultures | Use imagery that's hard to recognize across cultures or languages |
| Localize any text baked into an icon and flip icons that imply reading direction for RTL | Ship a single unlocalized, non-mirrored icon containing text |
| Use vector formats (PDF or SVG) for custom interface icons | Rely on PNG and hand-supply a version for every resolution |
| Provide alternative text labels for custom interface icons | Leave custom icons without accessibility descriptions |
| Reduce detail in small document icon sizes and keep content within the ~80% safe area | Place important document-icon content in the top-right corner or over-detail small sizes |
| Use only Apple Design Resources artwork or SF Symbols to depict Apple hardware | Use hand-made replicas of Apple hardware products |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
