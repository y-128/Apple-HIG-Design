---
title: Workouts
url: https://developer.apple.com/design/human-interface-guidelines/workouts
platforms: [iOS, iPadOS, watchOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Workouts

A great workout or fitness experience encourages people to engage with their current activity and helps them track their progress on their devices.

## Core guidance

People can wear their Apple Watch during many types of workouts, and they might carry their iPhone or iPad during fitness activities like walking, wheelchair pushing, and running. In contrast, people tend to use their larger or more stationary devices like iPad Pro, Mac, and Apple TV to participate in live or recorded workout sessions by themselves or with others.

You can create a workout experience for Apple Watch, iPhone, or iPad that helps people reach their goals by leveraging activity data from the device and using familiar components to display fitness metrics.

### Best practices

**In a watchOS fitness app, use workout sessions to provide useful data and relevant controls.** During a fitness app's active workout sessions, watchOS continues to display the app as time passes between wrist raises, so it's important to provide the workout data people are most likely to care about. For example, you might show elapsed or remaining time, calories burned, or distance traveled, and offer relevant controls like lap or interval markers.

**Avoid distracting people from a workout with information that's not relevant.** For example, people don't need to review the list of workouts you offer or access other parts of your app while they're working out.

> *Image caption:* An arrangement that many watchOS workout apps use, including Workout: large buttons that control the in-progress session — such as End, Resume, and New — appear on the leftmost screen; metrics and other data appear on a dedicated screen that people can read at a glance; if supported, media playback controls appear on the rightmost screen.

**Use a distinct visual appearance to indicate an active workout.** During a workout, people appreciate being able to recognize an active session at a glance. The metrics page can be a good way to show that a session is active because the values update in real time. In addition to displaying updating values, you can further distinguish the metrics screen by using a unique layout.

**Provide workout controls that are easy to find and tap.** In addition to making it easy for people to pause, resume, and stop a workout, be sure to provide clear feedback that indicates when a session starts or stops.

**Help people understand the health information your app records if sensor data is unavailable during a workout.** For example, water may prevent a heart-rate measurement, but your app can still record data like the distance people swam and the number of calories they burned. If your app supports the Swimming or Other workout types, explain the situation using language that's similar to the language used in the system-provided Workout app.

> *Image caption:* Example text from the Workout app: "GPS is not used during a Pool Swim, and water may prevent a heart-rate measurement, but Apple Watch will still track your calories, laps, and distance using the built-in accelerometer. In this type of workout, you earn the calorie equivalent of a brisk walk anytime sensor readings are unavailable." And for open-water swimming: "GPS will only provide distance when you do a freestyle stroke. Water might prevent a heart-rate measurement, but calories will still be tracked using the built-in accelerometer."

**Provide a summary at the end of a session.** A summary screen confirms that a workout is finished and displays the recorded information. Consider enhancing the summary by including Activity rings, so that people can easily check their current progress.

**Discard extremely brief workout sessions.** If a session ends a few seconds after it starts, either discard the data automatically or ask people if they want to record the data as a workout.

**Make sure text is legible for when people are in motion.** When a session requires movement, use large font sizes, high-contrast colors, and arrange text so that the most important information is easy to read.

**Use Activity rings correctly.** The Activity rings view is an Apple-designed element featuring one or more rings whose colors and meanings match those in the Activity app. Use them only for their documented purpose.

## Platform considerations

No additional considerations for iOS or iPadOS. Not supported in macOS, tvOS, or visionOS.

> **Source limitation:** The Core guidance section describes people using iPad Pro, Mac, and Apple TV "to participate in live or recorded workout sessions by themselves or with others," but the Platform considerations section states this pattern is not supported in macOS, tvOS, or visionOS. The source doesn't reconcile this — the larger-device use case it describes is likely served by a different pattern, such as Playing video, rather than the workout-session APIs and controls this page documents, but the source text doesn't say so explicitly.

## Native implementation

**Related**
- Activity rings

**Developer documentation**
- WorkoutKit
- Workouts and activity rings — HealthKit

**Key APIs**
- WorkoutKit — building custom workouts
- HealthKit — workout sessions and Activity rings data

**Videos:** Track workouts with HealthKit on iOS and iPadOS · Build custom workouts with WorkoutKit · Build a workout app for Apple Watch

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance, and for this pattern the honest answer is that it doesn't transfer. Workouts, as this page describes them, are bound to hardware the web cannot reach: a Digital Crown and wrist-raise wake detection on Apple Watch, GPS and heart-rate sensors read through HealthKit, and an accelerometer used as a fallback when water blocks optical heart-rate sensing. None of this is exposed to a web page.

**What is categorically unavailable.** There is no web API for heart rate, no web API for a wrist-worn accelerometer, no concept of a background "workout session" that keeps a page active across a wrist-lower/wrist-raise cycle the way `HKWorkoutSession` does, and no web equivalent of Activity rings as a system-recognized, cross-app visual language — a ring graphic built in CSS or SVG would just be a ring graphic, carrying none of the shared meaning Apple's guidance depends on ("use them only for their documented purpose" presumes the purpose is already documented and recognized system-wide, which only Apple's own element is).

**What narrow principle does transfer.** If a web app displays fitness data synced from elsewhere (a phone's HealthKit export, a manual log, a third-party fitness API), three of Apple's presentation principles still apply regardless of platform: keep the display of an in-progress or recorded session free of unrelated navigation and content, so people aren't hunting through chrome while exhausted or in motion; use large text, high contrast, and prioritized information hierarchy for any UI meant to be read while moving; and provide a clear end-of-session summary rather than leaving people to infer that a session ended. These are legibility-under-motion and focus principles that hold regardless of where the data came from — they just have to be built on data the web page received from somewhere else, not sensed by the page itself.

**Where this pattern is genuinely out of scope for a web project.** If a task involves live sensor-driven workout tracking, wrist-worn haptic/visual feedback, or anything resembling `HKWorkoutSession`, that is watchOS/iOS-bound work outside what a website can implement; the correct response is to say so, not to stretch the Vibration API or the (largely unsupported) Sensor APIs into a substitute.

## Do / Don't

| Do | Don't |
|---|---|
| Show the workout data people care about most — time, calories, distance | Bury essential metrics behind navigation during an active workout |
| Keep the active-workout screen free of unrelated app content | Let people browse other parts of your app mid-workout |
| Give an active session a visually distinct, real-time appearance | Make an active and inactive session look the same at a glance |
| Explain what's being tracked when a sensor is unavailable (e.g., during swimming) | Leave people guessing why a metric like heart rate isn't updating |
| Provide a clear end-of-session summary | End a workout with no confirmation or recap |
| Discard or confirm extremely short sessions rather than logging them silently | Automatically record a session that ended a few seconds after starting |
| Use large, high-contrast, prioritized text for in-motion legibility | Use small text or low contrast in a screen meant to be read while moving |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
