# What We Need for App Store & Play Store (Legal Docs)

We need up to **3 separate documents**. Here's what each one is, whether it's required, and what it needs to cover for Flopiq.

All docs will be hosted as web pages at: https://github.com/Betwise-gg/public-legal

---

## Quick Summary: What's Required?

| Document | App Store (Apple) | Play Store (Google) | Do we need a custom one? |
|----------|-------------------|---------------------|--------------------------|
| **Privacy Policy** | **Required** — must provide URL in App Store Connect | **Required** — must provide URL in Play Console + in-app | Yes, we must write our own |
| **EULA** | Optional — Apple provides a [standard EULA](https://www.apple.com/legal/internet-services/itunes/dev/stdeula/) that applies automatically if we don't provide one | Not required | Recommended (see below) |
| **Terms of Service** | Not required by the store | Not required by the store | Recommended (see below) |

### Additional Store Requirements (not documents, but forms we fill out)

- **Apple Privacy Nutrition Labels** — a form in App Store Connect where we declare what data the app collects. Filled out by Stan based on the data table below.
- **Google Data Safety Section** — same concept for Play Console. Required for all apps, even on closed testing tracks. Filled out by Stan.

---

## EULA vs. Terms of Service — They're Different Things

**EULA (End-User License Agreement)** — governs the *software license*. It says: "we grant you a license to use this app on your device, here are the restrictions." It's about the *code* you install.

**Terms of Service (TOS)** — governs the *service/platform*. It says: "here are the rules for using our platform, your account, user content, and our cloud features." It's about the *service* you access.

**For Flopiq, we arguably need both** because the app is installed software (EULA) AND a cloud-synced service with accounts, social features, and AI (TOS). In practice, many apps combine them into one document. Keith — up to you whether to keep them separate or merge into one "Terms of Use" that covers both.

If we don't provide a custom EULA for Apple, their [standard EULA](https://www.apple.com/legal/internet-services/itunes/dev/stdeula/) applies automatically. It's very generic and doesn't cover our AI features, subscriptions, or content rules — so a custom one is recommended.

---

## 1. Privacy Policy (REQUIRED)

Must be hosted at a public URL. Linked from both store listings AND from within the app (settings screen).

### Data We Collect

| Category | What exactly | How |
|----------|-------------|-----|
| **Account info** | Email address | Google or Apple sign-in (OAuth). We never handle passwords directly. |
| **Poker data** | Sessions, hands, betting actions, notes | User enters manually or via AI assistant. Stored locally on device + synced to our server. |
| **Profile info** | Display name, avatar, appearance preferences | User-provided in settings. |
| **Device location** | GPS coordinates (latitude/longitude) | **Opt-in only.** Used to find nearby poker rooms/casinos. User must grant permission; the app works fine without it (manual venue search). Not stored long-term — only used at the moment of the search. |
| **Venue names** | Casino/card room names + cached coordinates | User searches via Google Places. We cache venue name and coordinates for up to 30 days (per Google's ToS). |
| **Social data** | Friend connections, chat messages, shared hands, activity feed | User-initiated. Stored on our server. |
| **Crash reports & diagnostics** | Device model, OS version, app version, email, user ID | Sent automatically to Sentry (crash reporting service). |
| **AI assistant usage** | Conversations with the hand entry assistant | Proxied through our server to Anthropic (Claude). We track usage counts for rate limiting. |
| **Images** | Seat/player avatar photos | User uploads. Stored in Supabase Storage. |

### Third-Party Services to Disclose

- **Supabase** — authentication, database, file storage, real-time sync
- **Google Places API** — venue/casino search
- **Anthropic (Claude)** — AI hand entry assistant (proxied through our server, not direct)
- **Sentry** — crash reporting and error tracking
- **Apple & Google** — OAuth sign-in, push notifications, app distribution

### Other Privacy Points

- **Offline-first** — the app works without internet. Data syncs when connection is available.
- **Guest mode** — users can use the app without creating an account (data stays local only).
- **Data deletion** — users need to be able to request deletion of their data (required by GDPR, CCPA, and both app stores).
- **No selling of data** — we don't sell user data to third parties.

---

## 2. EULA (RECOMMENDED)

Covers the software license. Apple's standard EULA applies by default if we don't provide one, but a custom EULA lets us add clauses specific to our app.

### What a Custom EULA Should Cover

1. **License grant** — non-exclusive, non-transferable license to use the app on user's devices
2. **Restrictions** — no reverse engineering, no redistribution, no scraping
3. **Apple's minimum terms** — Apple [requires specific clauses](https://www.apple.com/legal/internet-services/itunes/dev/minterms/) if we write a custom EULA:
   - Agreement is between Betwise/Flopiq and the user (not Apple)
   - Apple has no obligation for maintenance or support
   - Apple is not responsible for product claims or IP infringement
4. **Termination** — we can revoke the license for violations
5. **Limitation of liability** — standard disclaimer

---

## 3. Terms of Service (RECOMMENDED)

Covers the platform/service rules. This is where the Flopiq-specific stuff lives.

### What TOS Should Cover

1. **Not a gambling platform** — Flopiq is a poker session *tracking and analysis* tool. No real money changes hands through the app. Users log their own sessions after the fact.

2. **User-generated content** — users own their hand histories and data. We need a license to store, sync, and display it within the app.

3. **AI assistant disclaimer** — the AI can make mistakes when interpreting hand descriptions. Users should review and verify entries.

4. **Subscriptions** — *(still being finalized)* There will likely be a free tier with limited AI usage and paid tiers with higher limits. Details TBD — the policy should be written flexibly enough to accommodate changes here.

5. **Account suspension** — standard clause that we can suspend accounts for abuse.

6. **Data portability & deletion** — users can request data export or account deletion.

7. **Age restriction** — **Open question:** Since we're a tracking/analysis tool and don't host any actual gambling, we may not need 18+. Probably 13+ (standard for apps with accounts/social features, per COPPA). Worth a quick check on what the stores require for poker-adjacent apps.

8. **Beta disclaimer** — the app is currently in beta. Features may change, data may be reset.

9. **Limitation of liability** — not responsible for poker decisions made based on the app's data or AI suggestions.

10. **Acceptable use** — no cheating tools, no sharing others' data without consent, no abusive content in social features.

---

## What I Need From You, Keith

- **Privacy Policy** — adapt/recycle one using the data table and third-party list above. This is the blocker for store submission.
- **EULA + TOS** — either as two separate docs or combined into one "Terms of Use." If recycling an old EULA, make sure to add the Flopiq-specific TOS clauses (AI disclaimer, content rules, etc.) and Apple's required minimum EULA terms.
- I'll answer any follow-up questions about specific data flows or technical details.
- Once drafted, I'll host them at the public-legal repo and link them from the app + store listings.

Nothing unusual about our data practices overall — it's a standard "user accounts + user-generated content + cloud sync" setup, with an AI feature and location-based venue search on top.
