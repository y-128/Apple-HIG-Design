---
title: Game Center
url: https://developer.apple.com/design/human-interface-guidelines/game-center
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2025-06-09
---

# Game Center

Game Center is Apple's social gaming network, which lets players track their progress and connect with friends across Apple platforms, and boosts the discovery of your game across players' devices.

## Core guidance

Supporting Game Center in your game allows players to:

- Discover new games their friends are playing.
- Seamlessly invite friends to play.
- See the latest activity from their games across the system, in the Apple Games app, the App Store, notifications, and more.

By enabling the player activities listed above, supporting Game Center also helps surface your game to more players across Apple platforms.

You can add Game Center into your game using the GameKit framework, which provides a full-featured UI that makes it easy for players to access and view their Game Center data within your game. Alternatively, you can also use GameKit to present this data within your own custom UI.

### Accessing Game Center

To provide the best Game Center experience for your players, begin by determining whether the player is signed in to their Game Center account on the system when they launch your game. If they aren't, initialize the player with Game Center at that time. This provides the most seamless user experience, and maximizes discovery opportunities for your game, such as in the Top Played chart and in social recommendations through players' friends.

#### Integrating the access point

The Game Center access point is an Apple-designed UI element that lets players view their Game Center profile and information without leaving your game.

In iOS, iPadOS, and macOS the access point leads players to the Game Overlay, a system overlay that allows players to view their progress and start game activities.

In visionOS and tvOS, the access point leads players to the in-game dashboard, a full-screen view of a player's Game Center activity that appears on top of your game.

**Display the access point in menu screens.** Consider adding the access point to the main menu or the settings area of your game. Avoid displaying the access point during active gameplay or in temporary splash screens, cinematic flows, or tutorials that might precede your game's main menu screen.

**Avoid placing controls near the access point.** You can choose to present the access point at any of the four corners of the screen in a fixed position. Remember that the access point has both a collapsed and expanded version, so check whether the access point overlaps any important UI and controls and adjust your layout accordingly.

> **Note (Apple):** In visionOS, the locations of the access point vary based on game type, such as immersive or volume-based. For developer guidance, see Adding an access point to your game.

**Consider pausing your game while the Game Overlay or dashboard is present.** Pausing your game can help players view their Game Center information without feeling like the game is continuing without them.

#### Using custom UI

Your game can include custom links into the Game Overlay (in iOS, iPadOS, macOS) or the dashboard (in visionOS and tvOS). Your custom UI can deep-link into specific areas within both such as leaderboards or a player's Game Center profile.

**Use the artwork Game Center provides in custom links.** When referencing Game Center features in custom UI, use the official artwork from Apple Design Resources. Preserve the appearance of this artwork and don't adjust the dimensions or visual effects.

**Use the correct terminology in custom links.** The following table describes how to use Game Center terminology correctly so that you can avoid confusing players in custom UI.

| Term | Incorrect terms | Localization |
|---|---|---|
| Game Center | GameKit, GameCenter, game center | Use the system-provided translation of Game Center |
| Game Center Profile | Profile, Account, Player Info | Use the system-provided translation of Game Center and localize Profile |
| Achievements | Awards, Trophies, Medals | — |
| Leaderboards | Rankings, Scores, Leaders | — |
| Challenges | Competitions | — |
| Add Friends | Add, Add Profiles, Include Friends | — |

### Achievements

Achievements give players an added incentive to stay engaged with your game. Game Center achievements appear in a collectible card format that highlights the player's progress and showcases your artwork.

> *Image caption:* Achievements overview and Achievement detail views showing the collectible card format.

#### Integrating achievements into your game

**Align with Game Center achievement states.** Game Center defines four achievement states: locked, in-progress, hidden, and completed. The system groups achievements by completion status, displaying completed achievements in the Completed group and all other achievements in the Locked group. When you map your achievements to the four Game Center achievement states, you give players a consistent experience and you help them see at a glance the types of achievements your game offers.

**Determine a display order.** The order in which you upload achievements is the order in which they appear, so consider the order you want before uploading files. For example, you might want your achievements to appear in an order that corresponds to the most common path through your game.

**Be succinct when describing achievements.** The achievement card limits the title and description to two lines each. If your title or description wraps beyond two lines, the card truncates the text. Use title-style capitalization for the achievement title and sentence-style capitalization for the description.

**Give players a sense of progress.** When you use progressive achievements, the system displays player progress and provides encouraging messages like "You're more than halfway to completing Great Lakes Freighter in The Coast. Keep going!" to help motivate players to complete them.

#### Creating achievement images

**Design rich, high-quality images that help players feel rewarded.** Achievements are a prominent feature in Game Center UI, so it's essential to design high-quality assets that catch the eye and encourage players to return to your game. Avoid reusing the same asset to represent more than one achievement. If you don't provide an asset for an achievement, the card shows a placeholder image instead.

**Create artwork in the appropriate size and format.** The system applies a circular mask to your achievement image, so be sure to keep content centered. Use the following specifications to create images.

**iOS, iPadOS, macOS, visionOS / tvOS**

| Attribute | Value |
|---|---|
| Format | PNG, TIF, or JPG |
| Color space | sRGB or P3 |
| Resolution | 72 DPI (minimum) |
| Image size | 512x512 pt (1024x1024 px @2x) |
| Mask diameter | 512 pt (1024 px @2x) |

### Leaderboards

Leaderboards are a great way to encourage friendly competition within your game. When you adopt Game Center, players can easily check their ranking against friends and global players as well as receive notifications when their friends challenge them or pass their score on a leaderboard. You can take advantage of the system-designed UI or present leaderboard information within custom UI.

> *Image caption:* Leaderboards overview and Leaderboard detail views.

**Choose a leaderboard type.** Game Center supports two types of leaderboards: classic and recurring.

A classic leaderboard tracks a player's best all-time score. Classic leaderboards are always active with no ending. Example goals for a classic leaderboard:

- Strive for the most perfect score in a rhythm game.
- Collect the most coins in a single dungeon run.
- Achieve the longest continuous time in an endless runner.

A recurring leaderboard resets based on a time interval you define, such as every week or every day. Recurring leaderboards can increase engagement by giving players more chances to take the lead. Examples of features that work well with recurring leaderboards:

- Daily rotating puzzles
- Seasonal or holiday-themed events
- Weekly leaderboards for different battle modes

**Take advantage of leaderboard sets for multiple leaderboards.** Leaderboard sets are an organization system that can make it easier for players to find the board they're looking for. Consider grouping leaderboard sets by themes or gameplay experiences, such as:

- Difficulty modes (Easy, Standard, Hard)
- Activity types (Combat, Crafting, Farming)
- Genres and themes (Disco, Pop, Rock)

**Add leaderboard images.** Leaderboard artwork gives you another opportunity to reinforce your game's visual aesthetic. Aim to create a unique image for each leaderboard in your game that reflects and showcases the gameplay involved in leaderboard ranking. Leaderboards appear across the system, promoting ways for players to engage and compete with friends, and having compelling images helps attract players and gives them a sense of the experience.

For games that run in iOS, iPadOS, and macOS, use a single image for your leaderboard image. For games that run in tvOS, provide a set of images that animate when the artwork is in focus. For help creating focusable images, download the tvOS template from Apple Design Resources.

**iOS, iPadOS, macOS / tvOS**

| Attribute | Value |
|---|---|
| Format | JPEG, JPG, or PNG |
| Color space | sRGB or P3 |
| Resolution | 72 DPI (minimum) |
| Image size | 512x512 pt (1024x1024 px @2x) |
| Cropped area | 512x312 pt (1024x624 px @2x) |

> **Note (Apple):** Be mindful of how cropping might affect your leaderboard artwork. In iOS, iPadOS, and macOS, the system crops artwork for leaderboards that are part of a leaderboard set. In tvOS, the focus effect on leaderboard artwork may crop your images at the edges of some layers. Make sure your primary content stays comfortably visible in both these scenarios.

### Challenges

Challenges turn single player activities into multiplayer experiences with friends. Challenges are built on top of leaderboards and allow players to connect with their friends and participate in competitions with time limits.

> *Image caption:* Challenges overview and Challenge detail views.

**Create engaging challenges.** Challenges are great for short, skill-based gameplay activities that have a clear way of gauging players' accomplishments. Create challenges that take 1-5 minutes to play, with gameplay that players can complete individually. Examples of compelling challenges:

- Complete the fastest lap in a racing level.
- Defeat the most enemies in a single round.
- Solve a daily puzzle with the fewest mistakes.

**Avoid creating challenges that track overall progress or personal best scores.** These can give regular players an unfair advantage. Instead, track players' most recent score after each attempt at your challenge. This helps keep your challenge motivating by placing all players on a level playing field.

**Make it easy to jump into your challenge.** Players can access challenges through invitation links, the Game Overlay, or in the Games app in iOS, iPadOS, and macOS. Always deep-link to the exact mode or level where your challenge begins, and help first-time players complete any initial onboarding before beginning the challenge. For example, if your game requires a tutorial level to understand basic controls, launch the player into the tutorial first and present UI that lets them know your game automatically jumps into the challenge afterward.

**Create high-quality artwork that encourages players to engage with your challenges.** The system shows your challenge's artwork in the Game Overlay, Games app, and in the preview of an invitation link. Avoid placing the primary content of your artwork in an area where the challenge's title and description might cover it. If you need to use text in your challenge image, provide the appropriate localized versions through App Store Connect or Xcode.

| Attribute | Value |
|---|---|
| Format | JPEG, JPG, or PNG |
| Color space | sRGB or P3 |
| Resolution | 72 DPI (minimum) |
| Image size | 1920x1080 pt (3840x2160 px @2x) |
| Cropped area | 1465x767 pt (2930x1534 px @2x) |

### Multiplayer activities

Game Center supports both real-time and turn-based multiplayer activities that make it easy to connect players with friends or other players. Players can access multiplayer gameplay through party codes, the Game Overlay, the dashboard, or in the Games app.

> *Image caption:* Multiplayer levels overview and Multiplayer level detail views.

**Use party codes to invite players to multiplayer activities.** Game Center party codes are a great way to coordinate real-time multiplayer sessions whether you use Game Center matchmaking and networking facilities or provide your own. Game Center generates alpha-numeric party codes that are typically eight characters long, such as "2MP4-9CMF." When integrating party codes into your multiplayer games, consider the following guidelines for the best player experience:

- Allow players to join gameplay late, leave early, and return later.
- Provide a way for players to view the current party code in your game.
- Allow players to enter a party code manually.

**Support multiplayer activities through in-game UI.** The Game Overlay and Game Center dashboard help players find other people for a multiplayer match without leaving your game. Game Center's default multiplayer interface lets a player invite nearby or recent players, Game Center friends, and contacts. You can also choose to present multiplayer functionality within your custom UI.

**Provide engaging activity artwork.** Players see the preview image for a multiplayer activity throughout the system, such as in a party code, the Games app, or in-game UI.

| Attribute | Value |
|---|---|
| Format | JPEG, JPG, or PNG |
| Color space | sRGB or P3 |
| Resolution | 72 DPI (minimum) |
| Image size | 1920x1080 pt (3840x2160 px @2x) |
| Cropped area | 1465x767 pt (2930x1534 px @2x) |

## Platform considerations

No additional considerations for iOS, iPadOS, macOS, or visionOS.

### tvOS

**Display an optional image at the top of the dashboard.** In tvOS, you can add an additional piece of artwork to the dashboard to highlight your game's aesthetic. Use a simple, easily recognizable image that looks great at a distance. Consider using your game's logo or word mark; however, don't use your app icon for this image.

| Attribute | Value |
|---|---|
| Image size | 600x180 pt (1200x360 px @2x) |
| Format | PNG, TIF, or JPG |
| Color space | sRGB or P3 |
| Resolution | 72 DPI (minimum) |

### watchOS

**Be aware of Game Center support on watchOS.** While GameKit features and API are available for watchOS games, keep in mind that there's no system-supported Game Center UI that you can invoke on watchOS. Instead, Game Center content for watchOS games appears on a connected iPhone.

## Specifications

Achievement images (iOS, iPadOS, macOS, visionOS, tvOS):

| Attribute | Value |
|---|---|
| Format | PNG, TIF, or JPG |
| Color space | sRGB or P3 |
| Resolution | 72 DPI (minimum) |
| Image size | 512x512 pt (1024x1024 px @2x) |
| Mask diameter | 512 pt (1024 px @2x) |

Leaderboard images (iOS, iPadOS, macOS, tvOS):

| Attribute | Value |
|---|---|
| Format | JPEG, JPG, or PNG |
| Color space | sRGB or P3 |
| Resolution | 72 DPI (minimum) |
| Image size | 512x512 pt (1024x1024 px @2x) |
| Cropped area | 512x312 pt (1024x624 px @2x) |

Challenge artwork:

| Attribute | Value |
|---|---|
| Format | JPEG, JPG, or PNG |
| Color space | sRGB or P3 |
| Resolution | 72 DPI (minimum) |
| Image size | 1920x1080 pt (3840x2160 px @2x) |
| Cropped area | 1465x767 pt (2930x1534 px @2x) |

Multiplayer activity artwork:

| Attribute | Value |
|---|---|
| Format | JPEG, JPG, or PNG |
| Color space | sRGB or P3 |
| Resolution | 72 DPI (minimum) |
| Image size | 1920x1080 pt (3840x2160 px @2x) |
| Cropped area | 1465x767 pt (2930x1534 px @2x) |

tvOS dashboard image:

| Attribute | Value |
|---|---|
| Image size | 600x180 pt (1200x360 px @2x) |
| Format | PNG, TIF, or JPG |
| Color space | sRGB or P3 |
| Resolution | 72 DPI (minimum) |

## Native implementation

**Related**
- Designing for games
- Game controls
- Apple Design Resources

**Developer documentation**
- GameKit
- Creating activities for your game
- Creating engaging challenges from leaderboards
- Create games for Apple platforms
- Game Porting Toolkit
- Adding an access point to your game
- Rewarding players with achievements
- Encourage progress and competition with leaderboards
- Finding multiple players for a game

**Videos:** Get started with Game Center · Engage players with the Apple Games app

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

Game Center is a proprietary social and identity layer tied to a signed-in Apple ID and the GameKit framework — there is no web equivalent of the access point, the Game Overlay, achievement cards, or party codes, because none of those exist without Apple's backend and OS-level UI surfaces. A web game cannot present "the" Game Center access point; it can only build its own leaderboard and achievement UI, or integrate a third-party identity/leaderboard service (Steam, a custom backend, or a web-based auth provider), which is a different product with different conventions.

What does transfer is the underlying design reasoning, not the feature itself. The instruction to avoid displaying the access point during active gameplay reflects a general principle: don't let a system-level social surface compete with a moment the player is concentrating on. On the web this becomes "don't pop notification or social UI over active gameplay input," which is a reasonable rule for any browser game with keyboard or pointer-critical moments. Likewise, the achievement-state model (locked, in-progress, hidden, completed) is a useful generic pattern for any progress system, web included, independent of Game Center itself — but implementing it means building your own data model and UI, not calling an Apple API.

The terminology-consistency table is the one piece with a closer analogue: if a web game integrates any third-party service (a leaderboard SDK, a social plugin), using that service's official terms and artwork rather than inventing your own vocabulary reduces user confusion in exactly the way Apple describes — this is a general integration-hygiene principle, not something specific to Game Center.

## Do / Don't

| Do | Don't |
|---|---|
| Initialize the player with Game Center at launch if not signed in | Wait until deep in the game to prompt sign-in |
| Display the access point in menu or settings screens | Show the access point during active gameplay, splash screens, or tutorials |
| Use official Game Center artwork unmodified in custom UI | Adjust the dimensions or visual effects of Game Center artwork |
| Use Apple's terminology (Achievements, Leaderboards, Challenges) | Substitute terms like Trophies, Rankings, or Competitions |
| Map achievements to the four Game Center states | Invent a custom achievement-state taxonomy that doesn't map back |
| Keep achievement titles/descriptions within two lines | Rely on text beyond two lines that Game Center will truncate |
| Track most recent score for challenges | Use overall progress or personal-best scores in challenges |
| Deep-link challenges to the exact mode or level | Drop players at a generic menu and make them navigate manually |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
