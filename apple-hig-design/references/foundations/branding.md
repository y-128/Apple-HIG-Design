---
title: Branding
url: https://developer.apple.com/design/human-interface-guidelines/branding
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: unknown
---

# Branding

Apps and games express their unique brand identity in ways that make them instantly recognizable while feeling at home on the platform and giving people a consistent experience.

> **Source limitation:** The captured PDF for this page contains no Change log section at all (the sidebar table of contents lists only Branding / Best practices / Platform considerations / Resources). `last_updated` cannot be derived and is left as `unknown` rather than invented.

## Core guidance

In addition to expressing your brand in your app icon and throughout your experience, you have several opportunities to highlight it within the App Store.

### Best practices

**Use your brand's unique voice and tone in all the written communication you display.** For example, your brand might convey feelings of encouragement and optimism by using plain words, occasional exclamation marks and emoji, and simple sentence structures.

**Consider choosing an accent color.** On most platforms, you can specify a color that the system applies to app elements like interface icons, buttons, and text. In macOS, people can also choose their own accent color that the system can use in place of the color an app specifies.

**Consider using a custom font.** If your brand is strongly associated with a specific font, be sure that it's legible at all sizes and supports accessibility features like bold text and larger type. It can work well to use a custom font for headlines and subheadings while using a system font for body copy and captions, because the system fonts are designed for optimal legibility at small sizes.

**Ensure branding always defers to content.** Using screen space for an element that does nothing but display a brand asset can mean there's less room for the content people care about. Aim to incorporate branding in refined, unobtrusive ways that don't distract people from your experience.

**Help people feel comfortable by using standard patterns consistently.** Even a highly stylized interface can be approachable if it maintains familiar behaviors. For example, place UI components in expected locations and use standard symbols to represent common actions.

**Resist the temptation to display your logo throughout your app or game unless it's essential for providing context.** People seldom need to be reminded which app they're using, and it's usually better to use the space to give people valuable information and controls.

**Avoid using a launch screen as a branding opportunity.** Some platforms use a launch screen to minimize the startup experience, while simultaneously giving the app or game a little time to load resources. A launch screen disappears too quickly to convey any information, but you might consider displaying a welcome or onboarding screen that incorporates your branding content at the beginning of your experience.

**Follow Apple's trademark guidelines.** Apple trademarks must not appear in your app name or images.

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, tvOS, visionOS, or watchOS.

## Native implementation

**Related**
- Marketing resources and identity guidelines
- Show more with app previews
- Color

**Developer documentation**
- Apple Trademark List
- Guidelines for Using Apple Trademarks
- App Store Marketing Guidelines

**Videos:** Communicate your brand identity on iOS

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Brand voice and tone → this is medium-independent and transfers unchanged.** Apple's advice about plain words, restrained exclamation marks and emoji, and simple sentence structures applies to any UI copy, on any platform, for the same reason: tone is a content decision, not a rendering decision.

**Accent color → the web equivalent is a CSS custom property, not a hard-coded value.** Defining a brand accent as a token (e.g., a single custom property referenced everywhere a system would apply tint) mirrors Apple's model of "the system applies this color to icons, buttons, and text." The macOS detail — that a user can override an app's accent color with their own system preference — has no true web parallel; browsers don't expose a user-level "override this site's accent color" preference the way macOS does at the OS level, so a web app's accent color is effectively fixed by the site unless the user runs a personal stylesheet extension.

**Custom fonts for headlines, system font for body → the reasoning is legibility at small sizes, and it holds on the web.** Apple's rationale — system fonts are tuned for legibility at small sizes, so save the custom/brand font for headlines where size affords more error margin — is a font-rendering argument, not a platform-specific one. It applies equally to a custom brand webfont: use it for large display text, and lean on the system font stack (or a well-hinted, thoroughly tested webfont) for dense body copy.

**Branding defers to content → this is a screen-real-estate argument that generalizes directly.** A persistent logo bar or branded chrome that eats vertical space on a small viewport is the same mistake as an app burning Home Screen or in-app space on decoration instead of content — the reasoning (space given to pure branding is space taken from what people came for) doesn't change with platform.

**Avoid a branding-only launch screen → maps to avoiding a branding-only splash screen or loading page on the web.** The same critique applies: a screen people see once, briefly, and can't interact with is a poor place to spend branding effort; an onboarding flow or first-run experience is the better vehicle, exactly as Apple recommends.

**Follow Apple's trademark guidelines → has no web analogue by definition.** This guidance is specific to using Apple's own marks and is not a principle to generalize — a web app has no equivalent "platform owner's trademark" constraint unless it separately integrates a third-party brand, in which case that third party's own trademark guidelines apply directly, not by inference.

## Do / Don't

| Do | Don't |
|---|---|
| Use a consistent brand voice and tone in your copy | Mix tones inconsistently across the app |
| Choose an accent color the system can apply to icons, buttons, and text | Hard-code brand color into every element individually |
| Reserve a custom font for headlines and subheadings | Use a custom font for dense body copy where legibility suffers |
| Let branding stay refined and unobtrusive | Spend screen space on brand assets that display nothing else |
| Use standard UI patterns and standard symbols for common actions | Invent unfamiliar patterns purely for stylistic differentiation |
| Show your logo only when it provides essential context | Display your logo throughout the app as a reminder |
| Save branding for a welcome or onboarding screen | Use the launch screen as a branding opportunity |
| Follow Apple's trademark guidelines exactly | Use an Apple trademark in your app name or images |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
