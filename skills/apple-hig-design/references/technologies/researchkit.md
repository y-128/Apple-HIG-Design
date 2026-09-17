---
title: ResearchKit
url: https://developer.apple.com/design/human-interface-guidelines/researchkit
platforms: [iOS, iPadOS]
last_updated: 2023-09-12
---

# ResearchKit

A research app lets people everywhere participate in important medical research studies.

## Core guidance

The ResearchKit framework provides predesigned screens and transitions that make it easy to design and build an engaging custom research app.

> **Note (Apple):** These guidelines are for informational purposes only and don't constitute legal advice. Contact an attorney to obtain advice with respect to the development of a research app and any applicable laws.

### Creating the onboarding experience

When opening a research app for the first time, people encounter a series of screens that introduce them to the study, determine their eligibility to participate, request permission to proceed with the study, and, when appropriate, grant access to personal data. These screens aren't typically revisited once they've been completed, so clarity is essential.

**Always display the onboarding screens in the correct order.**

#### 1. Introduction

Provide an introduction that informs and provides a call to action. Clearly describe the subject and purpose of your study. Also allow existing participants to quickly log in and continue an in-progress study.

#### 2. Determine eligibility

**Determine eligibility as soon as possible.** People don't need to move on to the consent section if they're not eligible for the study. Only present eligibility requirements that are necessary for your study. Use simple, straightforward language that describes the requirements, and make it easy to enter information.

#### 3. Get informed consent

Make sure participants understand your study before you get their consent. ResearchKit helps you make the consent process concise and friendly, while still allowing you to incorporate into the consent any legal requirements or requirements set by an institutional review board or ethics review board. Make sure that your app complies with the applicable App Store Guidelines, including the consent requirements. Typically, the consent section explains how the study works, ensures that participants understand the study and their responsibilities, and gets the participant's consent.

**Break a long consent form into easily digestible sections.** Each section can cover one aspect of the study, such as data gathering, data use, potential benefits, possible risks, time commitment, how to withdraw, and so on. For each section, use simple, straightforward language to provide a high-level overview. If necessary, provide a more detailed explanation of the section that participants can read by tapping a Learn More button. Participants need to be able to view the entire consent form before they agree to participate.

**If it makes sense, provide a quiz that tests the participant's understanding.** You might do this for questions the participant would otherwise be asked when obtaining consent in person.

**Get the participant's consent and, if appropriate, some contact information.** After agreeing to join the study, participants receive a confirmation dialog, followed by screens in which they provide their signature and contact details. Most research apps email participants a PDF version of the consent form for their records.

#### 4. Request permission to access data

**Get permission to access the participant's device or data, and to send notifications.** Clearly explain why your research app needs access to location, Health, or other data, and don't request access to data that isn't critical to your study. If your app requires it, also ask for permission to send notifications to the participant's device.

### Conducting research

To get input from participants, your study might use surveys, active tasks, or a combination of both. Depending on the architecture of your study, participants may interact with each section multiple times or only once.

**Create surveys that keep participants engaged.** ResearchKit provides many customizable screens you can use in your surveys, and makes it easy to present questions that require different types of answers, such as true or false, multiple choice, dates and times, sliding scales, and open-ended text entry. As you use ResearchKit screens to design a survey, follow these guidelines to provide a great experience:

- Tell participants how many questions there are and about how long the survey will take.
- Use one screen per question.
- Show participants their progress in the survey.
- Keep the survey as short as possible. Several short surveys tend to work better than one long survey.
- For questions that require some additional explanation, use the standard font for the question and a slightly smaller font for the explanatory text.
- Tell participants when the survey is complete.

**Make active tasks easy to understand.** An active task requires the participant to engage in an activity, such as speaking into the microphone, tapping fingers on the screen, walking, or performing a memory test. Follow these guidelines to encourage participants to perform an active task and give them the best chance of success:

- Describe how to perform the task using clear, simple language.
- Explain any requirements, such as if the task must be performed at a particular time or under specific circumstances.
- Make sure participants can tell when the task is complete.

### Managing personal information and providing encouragement

ResearchKit offers a profile screen you can use to let participants manage personal information while they're in your research app. It's also a good idea to design a custom screen that motivates people and gives them a way to track progress in the study. Ideally, both screens are accessible at all times in your app.

**Use a profile to help participants manage personal data related to your study.** A profile screen can let people edit data that might change during the course of the study — such as weight or sleep habits — and remind them of upcoming activities. A profile screen can also provide an easy way to leave a study and view important information, such as the consent document and privacy policy.

**Use a dashboard to show progress and motivate participants to continue.** If appropriate for your study, use a dashboard to provide encouraging feedback, such as daily progress, weekly assessments, results from specific activities, and even results that compare the participant's results with aggregated results from others in the study.

## Platform considerations

No additional considerations for iOS or iPadOS. Not supported in macOS, tvOS, visionOS, or watchOS.

## Native implementation

**Related**
- Research & Care > ResearchKit

**Developer documentation**
- Research & Care > Developers
- Protecting user privacy — HealthKit
- ResearchKit GitHub project

**Videos:** What's new in CareKit · Build a research and care app, part 1: Setup onboarding · ResearchKit and CareKit Reimagined

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. ResearchKit as a framework — its predesigned screen transitions, device-sensor-driven active tasks, and tight HealthKit integration — has no web equivalent; a browser can't perform the same range of sensor-backed active tasks (gait, tremor, memory games using device motion) with the same fidelity, and there's no bundled framework that ships this onboarding flow pre-built.

Unlike HomeKit or CareKit, though, the *onboarding and consent structure* this page describes has a strong, direct web analogue, because informed-consent research and IRB-governed surveys already run on the web (REDCap, Qualtrics, and purpose-built clinical trial platforms all implement variants of this flow). The reasoning transfers almost unchanged: fixed screen order (introduction, eligibility, consent, permissions) prevents participants from consenting before they understand what they're agreeing to, so a web consent flow should enforce the same sequence rather than letting a participant jump ahead via a bookmarked URL or a browser back-button skip. "Break a long consent form into digestible sections with a high-level summary and an optional deeper explanation" is directly implementable as a web accordion or a summary-plus-"Learn more" disclosure pattern. "Determine eligibility before consent" argues for a short screening form gating access to the full consent document, not the reverse. The permission-request principle is identical to HealthKit's: ask for browser permissions (location, camera, microphone, notifications) only when the specific task needs them, with the reason stated in plain language before the browser's native prompt appears — never a custom screen standing in for it.

Where the mapping breaks down is data fidelity and legal weight. A web consent flow can capture a typed name and a checkbox, but Apple's guidance assumes a signature captured on a touch device and an emailed PDF record — a web implementation needs an explicit e-signature and record-retention design of its own, and (per Apple's own disclaimer on this page) what counts as valid consent is a legal question, not a design one, and varies by jurisdiction and IRB. Active tasks that rely on high-frequency accelerometer or gyroscope data have only partial web equivalents via the Generic Sensor API and DeviceMotion events, with lower sampling rates, no guaranteed background execution, and inconsistent browser support — treat any web-based active task as a degraded substitute, not a port.

## Do / Don't

| Do | Don't |
|---|---|
| Show onboarding screens in a fixed order: intro, eligibility, consent, permissions | Let participants reach consent before eligibility is determined |
| Break consent into short sections with an optional "Learn More" for detail | Present one long, undifferentiated consent document |
| Use plain, simple language for eligibility and consent text | Use dense legal language without a plain-language summary |
| Request data or notification permissions with a clear, contextual explanation | Request access to data that isn't critical to the study |
| Use one screen per survey question and show progress | Bundle many questions onto one screen with no progress indicator |
| Keep individual surveys short; use several short surveys over one long one | Force a single long survey when shorter ones would work |
| Clearly explain how to perform and how to tell when an active task is complete | Leave participants unsure whether a task requirement (timing, conditions) was met |
| Give participants an always-accessible profile and progress dashboard | Bury the consent document or a way to leave the study |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
