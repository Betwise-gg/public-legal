# What We Need for App Store & Play Store (Legal Docs)

Both the App Store and Play Store **require a Privacy Policy URL** before you can publish. A EULA/TOS isn't strictly required by the stores, but it's strongly recommended — and yes Keith, a EULA is what I mean by TOS.

We need both hosted as web pages. I have a repo ready for that: https://github.com/Betwise-gg/public-legal

---

## 1. Privacy Policy

This needs to disclose what data we collect, how we use it, and what third parties are involved.

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

### Other Key Points

- **Offline-first** — the app works without internet. Data syncs when connection is available.
- **Guest mode** — users can use the app without creating an account (data stays local only).
- **Data deletion** — users need to be able to request deletion of their data (required by GDPR, CCPA, and both app stores).
- **No selling of data** — we don't sell user data to third parties.

---

## 2. EULA / Terms of Service

### What It Should Cover

1. **Not a gambling platform** — Flopiq is a poker session *tracking and analysis* tool. No real money changes hands through the app. Users log their own sessions after the fact.

2. **User-generated content** — users own their hand histories and data. We need a license to store, sync, and display it within the app.

3. **AI assistant disclaimer** — the AI can make mistakes when interpreting hand descriptions. Users should review and verify entries.

4. **Subscriptions** — *(still being finalized)* There will likely be a free tier with limited AI usage and paid tiers with higher limits. Details TBD — the policy should be written flexibly enough to accommodate changes here.

5. **Account suspension** — standard clause that we can suspend accounts for abuse.

6. **Data portability & deletion** — users can request data export or account deletion.

7. **Age restriction** — **Open question:** Since we're a tracking/analysis tool and don't host any actual gambling, we may not need 18+. Probably 13+ (standard for apps with accounts/social features, per COPPA). Worth a quick check on what the stores require for poker-adjacent apps.

8. **Beta disclaimer** — the app is currently in beta. Features may change, data may be reset.

9. **Limitation of liability** — standard disclaimer that we're not responsible for poker decisions made based on the app's data or AI suggestions.

---

## What I Need From You

- A recycled EULA and Privacy Policy that you can adapt using the info above
- I'll answer any follow-up questions about specific data flows or technical details
- Once drafted, I'll host them at the public-legal repo and link them from the app + store listings

Both docs can be fairly standard/boilerplate with the specifics from above plugged in. Nothing unusual about our data practices — it's a pretty standard "user account + user-generated content + cloud sync" setup with an AI feature on top.
