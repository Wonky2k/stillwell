# Stillwell — Product Roadmap

*A living document of ideas, future features, and improvements. Updated as new ideas emerge.*

---

## Current Status

Stillwell is a working hosted prototype at the middle-path stage:
- Single-page HTML app deployed via Vercel with a proxy backend
- API key held server-side (users need only enter their first name)
- Manual health data entry as primary data source
- Four expert personas delivering AI-powered feedback
- Session memory via localStorage (device-bound)
- Onboarding flow capturing motivation and baseline
- Wellness slider (self-reported score) at each check-in
- Session history with progress chart
- Small trusted test pool in active use

---

## Near-Term Improvements
*Refinements to the current prototype based on early testing*

- [ ] **Same-day data pre-fill** — detect if health metrics have already been entered today and offer to reuse them, avoiding repeated manual entry across multiple same-day sessions
- [ ] **Improved streak display** — already fixed for distinct calendar dates; confirm feels right across longer usage patterns
- [ ] **Slider default position** — consider whether starting at 5 ("Getting by") is the right neutral, or whether no default (user must move the slider) produces more considered responses
- [ ] **Action follow-through** — at the start of the next session, a brief prompt asking whether the user acted on the previous session's Tonight/Tomorrow actions; feed that into persona context
- [ ] **Notification / reminder** — a simple prompt to return for the next check-in (requires move beyond static HTML)
- [ ] **Export / share action plan** — allow users to save or share their "Your next 48 hours" summary card

---

## Platform & Infrastructure
*Moving from prototype toward a real product*

- [ ] **Proper iOS app** — required for reliable native Apple Health / HealthKit integration; solves the data accuracy problem with the Shortcuts approach (sleep data summing issue). Unlocks App Store distribution.
- [ ] **User accounts and authentication** — currently all data is device-bound via localStorage; accounts would allow cross-device access and proper data persistence
- [ ] **Cloud data persistence** — move session history and onboarding from localStorage to a database; enables multi-device use, data backup, and longitudinal analytics
- [ ] **Android support** — currently iOS/Apple Health focused; Google Fit / Health Connect integration for Android users
- [ ] **Pre-built Apple Shortcut** — when URL is stable (already solved with Vercel), provide a downloadable one-tap Shortcut for users who want to pull Apple Health data automatically; requires solving the sleep data aggregation bug first

---

## Apple Health Integration
*Specific to solving the data reliability problem*

- [ ] **Sleep data deduplication** — the core technical problem; Shortcuts sums overlapping sleep segments producing impossible values (e.g. 49 hours). Requires native HealthKit in an iOS app to filter by source and stage correctly
- [ ] **Source filtering** — allow users to specify their preferred data source (Apple Watch, Oura, Whoop etc.) to avoid double-counting across devices
- [ ] **Background refresh** — in a native app, health data could be pulled automatically each morning without any user action

---

## Feedback & Persona Quality
*Improving the core AI feedback experience*

- [ ] **Action follow-up loop** — personas reference whether previous actions were followed; creates genuine continuity and accountability without pressure
- [ ] **Longer memory window** — currently uses last 5 sessions; experiment with longer windows (10–20 sessions) as users build history
- [ ] **Persona voice refinement** — ongoing tuning based on user feedback; which persona voices resonate most, which feel off
- [ ] **Milestone messages** — currently at sessions 3, 7, 14, 21; review whether these land well in practice and adjust copy based on feedback
- [ ] **Progress acknowledgement** — when wellness score trends upward over multiple sessions, personas should proactively name the improvement and connect it to specific behaviours
- [ ] **Relapse sensitivity** — when a user who has been improving has a noticeably worse session, personas should acknowledge it with extra care rather than treating it as a standard session
- [ ] **Seasonal / contextual awareness** — inject day of week and time of day context so personas can reference patterns (e.g. "you tend to score lower on Mondays")

---

## User Experience
*UX improvements identified through testing and design thinking*

- [ ] **Returning user data pre-population** — for manual entry users, pre-fill yesterday's metrics as a starting point to reduce friction
- [ ] **Progressive onboarding** — currently all four onboarding stages happen at once; explore spreading the deeper questions across the first few sessions so new users aren't overwhelmed
- [ ] **Offline mode** — basic check-in and history browsing should work without a connection; AI feedback queues for when connectivity returns
- [ ] **Dark mode** — Stillwell's palette lends itself to a dark variant; worth exploring for evening use
- [ ] **Haptic feedback** — on mobile, subtle haptics on the wellness slider would make it feel more considered and tactile
- [ ] **Persona selection** — advanced option for users to choose which persona leads their session, or to mute a persona they find less useful
- [ ] **Session length options** — a "quick check-in" mode with fewer questions for busy days alongside the full session

---

## History & Progress Visualisation
*Expanding the Your Journey screen*

- [ ] **Weekly summary view** — group sessions by week showing average wellness score and dominant pillar; gives a higher-level view of trends
- [ ] **Pillar trend lines** — separate lines for each of the four pillars showing which areas are improving or worsening over time
- [ ] **Action effectiveness tracking** — connect actions given in past sessions to subsequent wellness scores; show which types of actions correlate with improvement
- [ ] **Personal bests** — surface meaningful moments e.g. "Your highest wellness score was 8, on a Thursday three weeks ago"
- [ ] **Goal progress** — connect session history back to the user's original onboarding vision; show how far they've moved toward what they described

---

## Commercialisation
*Features and infrastructure needed for a commercial product*

- [ ] **Pricing model** — API costs are low at prototype scale (~£0.001–0.003 per session) but need a sustainable model at scale; subscription likely most appropriate given ongoing API usage
- [ ] **Usage monitoring** — track API call volume and cost per user to inform pricing decisions
- [ ] **Terms of service and privacy policy** — required before public launch; clarity on what data is stored, how it is used, and Anthropic's role as the underlying AI provider
- [ ] **Accessibility audit** — colour contrast, screen reader support, font sizing for users with visual impairments
- [ ] **Clinical review** — given the wellness and mental health adjacent nature of the content, a review by a qualified professional before broad public launch would be prudent
- [ ] **Referral / sharing** — allow users to invite friends; early growth mechanism that fits the "trusted recommendation" positioning
- [ ] **Team / couples mode** — two users sharing a Stillwell experience; could be valuable for partners or close colleagues supporting each other

---

## Strategic / Longer Term
*Bigger ideas worth holding*

- [ ] **Wearable partnerships** — direct integrations with Oura, Whoop, Garmin as data sources beyond Apple Health
- [ ] **Practitioner dashboard** — a version for therapists, coaches, or GPs to use with clients; they see aggregate trends (with consent) and can add context to the AI feedback
- [ ] **Corporate wellness** — a version for teams or organisations; anonymised aggregate data gives HR or wellbeing leads a picture of team health without individual surveillance
- [ ] **Research partnerships** — anonymised, consented data at scale could be genuinely valuable to wellness researchers; a potential revenue stream and credibility builder
- [ ] **White label** — license Stillwell to other wellness brands or healthcare providers who want AI-powered qualitative feedback without building their own

---

## Ideas Parking Lot
*Rough ideas not yet fully formed — worth revisiting*

- Ability for users to add their own custom questions to the check-in
- A "not today" mode for days when the user just wants to log a wellness score without a full session
- Integration with calendar data to contextualise busy periods, travel, or events
- Voice input for the open text field — lower friction for users who find typing a barrier
- A "letter to my future self" feature — at onboarding, the user writes a note to themselves; surfaced back at a milestone session
- Against recommended actions, the offer to click through to specific actionable help i.e. a tailored exercise program for the week, dietary advice and recipe suggestions, practical advise to help sleep

---

*Last updated: March 2026*
*To add ideas: edit this file directly in GitHub or discuss in the development chat*
