# Stead iOS app — product analysis for the new website

Source: the `steadcompile17` iOS app, run in the iPhone 18 Pro simulator (iOS 27) with the app's built-in demo data.
Screenshots: `screenshots/` (1206×2622, iPhone 18 Pro, status bar set to 9:41).

## What the product is now

Stead is a **native iPhone app** that checks incoming SMS and WhatsApp messages for scam warning signs and brings a family member in before money moves. The current site still describes the earlier **web prototype** (desktop "window" demo, `/demo` `/parent` `/guardian` routes, "incoming messages simulated"). The new site should present the iPhone app.

**One line:** Stead quietly checks new messages for scam warning signs, and brings your family in when it matters.
**Tagline (in app):** Safer, together.

## How it works (as the app actually does it)

1. **A message arrives** in Messages or WhatsApp.
2. **An iOS 27 Shortcuts automation** passes the notification text to Stead in about a second, with the app closed. One-time setup of about two minutes.
3. **On-phone rules check it first.** Normal messages never leave the phone.
4. **Only messages with warning signs get a closer AI look** (Claude, through a Supabase function; the message text is not stored).
5. **Stead explains it in plain words**: a level, a short title, the specific warning signs, what it can't confirm, and one safe next step. It can read the warning aloud.
6. **Family gets a heads-up** when it's serious, if the user agreed. They see a short summary, never the chat, and can mark it "I'm checking".

## Three warning levels (colour-coded throughout)

| Level | Colour | Example in the demo |
|---|---|---|
| **Worth a look** | Blue | Teacher's WhatsApp: "open the attached statement on a computer, forward to finance" → *This account may be hacked* |
| **Be careful** | Amber | "Parcel held at customs, pay ₩3,000 within 24 hours: bit.ly/…" → *Possible fake government notice*, 6 warning signs |
| **Stop. Talk to family first** | Red | A bank verification code arriving right after a scam message → *Don't share codes or send money. Call your family now.* |

## Standout features (the site should lead with these)

1. **Family code against hacked accounts.** If "Daniel" messages "Mum urgent, transfer RM3000, don't call", Stead asks Mum to get Daniel's 6-digit family code first. Only the real Daniel can open it in Stead, with his face. A hacker can't. *(screenshot 11)*
2. **Catches the follow-up, not just the first message.** A real bank one-time code that arrives after a scam message is raised to red ("Stop"), because that is the moment money is lost. *(screenshots 04, 05)*
3. **Explains, never scores.** No "safe" label and no percentage. Instead: "Why Stead is worried", "What Stead can't confirm", "Safe next step". *(06, 07, 09)*
4. **Privacy by design.** Normal messages stay on the phone; only flagged ones get an AI look; family sees a summary, never the chats; links in messages are not clickable inside Stead. *(03)*
5. **Built for older adults.** Large type, a friendly cat mascot whose face changes colour with the level, read-aloud, one big "Check a message" button.
6. **Multilingual from day one.** Demo cases in Korean, Malay and English (Seoul, Kuala Lumpur and beyond).

## Two sides of the app

- **Protected person ("Me")**: Home, Activity, Family, Settings tabs. *(04–11)*
- **Family member ("Someone in my family")**: pairs by scanning a family QR, gets live alerts and taps "I'm checking". *(12)*

## Screenshot guide

| File | Shows | Best use on site |
|---|---|---|
| 01-welcome | Splash: cat, "Stead · Safer, together." | Hero / app icon moment |
| 02-who-is-this-for | Choose "Me" or "Someone in my family" | "Two sides" section |
| 03-privacy-promise | "How Stead protects you" + "Tell my family when it's serious" toggle | Privacy section |
| 04-home-warning | Home: red cat, "Stop. Talk to family first", 7 checked / 6 warnings / 5 shared | **Hero phone** |
| 05-needs-a-look | List showing all three levels side by side | Warning levels section |
| 06-check-detail | "Worth a look · This account may be hacked" | Scenarios |
| 07-safe-next-step | Safe next step + "Ask family to check" | "Explain" section |
| 08-activity | Activity tab, Warnings / Everything | Feature grid |
| 09-parcel-scam-warning | "Be careful · Possible fake government notice", 6 signs | **Main "how it reads a message" shot** |
| 10-family | Family circle, "How the family code works" | Family section |
| 11-family-code-check | "Ask Daniel for the family code" on an RM3000 request | **Signature feature shot** |
| 12-guardian-pair | Guardian: "Hi Daniel", Scan family QR, Live alerts | Guardian section |

## Honesty notes for the copy

- Screenshots 06, 09 and 11 show "Preliminary: quick on-phone check", because the AI backend isn't connected in this build. With the backend live, those screens show the full AI review instead. Either keep the line (it's honest and on-brand) or retake these once the backend is configured.
- The guardian's live case list needs the backend, so it couldn't be captured. Screenshot 12 is the pairing screen.
- All names, numbers and links are sample data (`.example`, `bit.ly/parcel-example`).
- Automatic checking needs **iOS 27** and the Shortcuts setup; say so plainly.
- Keep the existing promise: Stead points out warning signs; it can't guarantee a message is safe or a scam.
