# LyrixBot Top.gg Long Description: Notes

## Files

| File | Purpose |
|---|---|
| `lyrixbot-topgg-description.html` | **The paste-ready description.** HTML fragment, inline styles only. Paste into the Long Description field. |
| `lyrixbot-topgg-preview.html` | Same content wrapped in a page, with images loading from `images/`. Open it locally to review. |
| `images/` | Screenshots renamed to web-safe names (no spaces or `&`). `images/not-used/` holds the two screenshots I held back. |

## Before you paste: four placeholders

Find and replace in `lyrixbot-topgg-description.html`:

| Placeholder | Replace with |
|---|---|
| `{{IMG_BASE}}` | Public folder URL where you host the `images/` files, no trailing slash (e.g. a GitHub repo raw URL or your own site) |
| `{{INVITE_URL}}` | Your bot invite link |
| `{{DASHBOARD_URL}}` | Your dashboard URL |
| `{{SUPPORT_URL}}` | Your support server invite |

Top.gg can only load images from public URLs, so the files have to be hosted somewhere first. Discord CDN links are signed and expire, so avoid them for a permanent listing.

## C. Image mapping

| Original file | Renamed to | What it actually shows | Section |
|---|---|---|---|
| Verification Embed.png | moderation-verification-embed.png | Verification panel with a button (`/setup-verification`) | Moderation & Security |
| Mod Cases.png | moderation-actions-dashboard.png | Dashboard **Moderation Actions & Temp Bans** page (not a cases list, despite the filename) | Moderation & Security |
| Moderation Settings.png | moderation-settings-dashboard.png | Dashboard Moderation page: mod-log channel, text commands, aliases | Moderation & Security |
| Ticket Department Embed.png | tickets-department-select.png | Department dropdown (System A) | Ticket Systems |
| Ticket Embed.png | tickets-panel-embed.png | Button ticket panel (System B) | Ticket Systems |
| Ticket Settings.png | tickets-settings-dashboard.png | Dashboard System Config > Ticket System | Ticket Systems |
| Apply Embed.png | apply-panel-embed.png | Application panel with button | Staff Applications |
| Apply Questions.png | apply-form-dashboard.png | Dashboard Apply page with the question form | Staff Applications |
| Staffs Leaderboard.png | staff-leaderboard-embed.png | `/leaderboard`, paginated | Staff Points & Management |
| Staffs Profile.png | staff-profile-embed.png | `/profile` with rank, points, message and voice progress | Staff Points & Management |
| Achievements Emded.png | staff-achievements-embed.png | `/achievements`, 0/6 unlocked | Staff Points & Management |
| Shop Page.png | dashboard-shop-page.png | Dashboard Shop page | Ranks, Daily Rewards & Shop |
| GiveAway Embed.png | community-giveaway-embed.png | Giveaway embed with Enter button | Community & Engagement |
| Suggestion Embed.png | community-suggestion-embed.png | Suggestion with votes, status, Consider/Approve/Deny, thread | Community & Engagement |
| Quran Radio.png | islamic-radio-panel.png | `/radio` control panel | Islamic Features |
| Quran Radio Setup.png | islamic-radio-setup.png | `/setup-islamic radio` voice channel picker | Islamic Features |
| Azkar Embed.png | islamic-azkar-embed.png | `/azkar` morning azkar message | Islamic Features |
| Admin Overview.png | dashboard-admin-overview.png | Dashboard admin overview | Web Dashboard |
| Commands Page.png | dashboard-commands-page.png | Dashboard command management | Web Dashboard |
| Inbox Page.png | dashboard-inbox-page.png | Dashboard inbox | Web Dashboard |
| **Rank Pic.png** | staff-rank-card.png | **Not used.** `/rank` output shows only an empty ring and bar, with no name, level or XP. It looks unfinished or rendered without data. | none |
| **Server Style Page.png** | dashboard-style-guide.png | **Not used.** This is the dashboard's internal Style guide page (colour and spacing tokens), not a feature for server owners. | none |

20 of 22 screenshots are placed, each exactly once.

## D. Compatibility notes

**What Top.gg documents.** Its support article says long descriptions support regular Markdown and HTML, that custom CSS is allowed, and that any custom code must follow their Bot Guidelines. It does not document JavaScript, so I did not use any.

**What this file uses.**
- HTML only, as a fragment (no `<html>`, `<head>` or `<body>`). Mixing Markdown into HTML blocks is fragile, so I did not.
- Inline `style` attributes on every element. I chose these over a `<style>` block because they survive if a sanitizer strips or rewrites stylesheets.
- Elements: `div`, `h1`-`h3`, `p`, `ul`, `ol`, `li`, `table`, `code`, `span`, `i`, `a`, `img`.
- Layout uses `display:flex; flex-wrap:wrap`. If flex were stripped, the cards would simply stack vertically, so it degrades safely. I checked the preview at 1100px and 400px wide with no horizontal overflow.
- Colours: accent `#8B5CF6`, dark backgrounds `#0f0a1f` and `#171030`. The description draws its own dark panel, so it looks the same whether Top.gg shows its page in light or dark mode.

**Not verified (please test).**
- I could not find Top.gg's exact sanitizer rules, so check the preview on the bot's edit page before submitting. If something is stripped, tell me which part and I will make a simpler version.
- I could not confirm a maximum length for the field. The file is about 48 KB because of inline styles. If the form rejects it, I can produce a leaner version.
- Anchor links, fixed positioning, animations, external fonts and embedded video are not used.

## E. Final review

Checked programmatically against `topgg-commands-english-v2.json`:
- Every `/command` and subcommand written on the page exists in the file. No misspellings, none invented.
- All 72 commands appear on the page, each in the section where it belongs.
- No script, iframe or external resource in the HTML. The only external URLs are your four placeholders.
- No server count, user count, uptime or other statistic is claimed. The dashboard screenshots show "Members: 1155" in their header, which I did not mention.

Checked by reading the screenshots: each caption and alt text describes only what is visible.

## Things you should decide

1. **Languages.** Your brief says English, Arabic and French, and the page says that. But `/settings language` in the command file offers 16 choices (including Spanish, German, Japanese, Russian, Turkish, Korean, Hindi and others) plus "Server default". If those are not fully translated, a member who picks one may get English, which looks like a bug. Either finish them, trim the picker, or tell me they are complete and I will update the page.
2. **Ticket scope.** The page says the dashboard limits (max open, auto-close, first-response target, reopen window) belong to the dashboard-configured system, because that is what the screenshot shows. It does not say whether department tickets also follow them, or whether `/ticket`, `/ticketstaff` and `/tag` work in both systems. I listed those commands separately without claiming either. Tell me and I will tighten the wording. Also, your brief says "ticket categories" (plural) but the settings screenshot has a single Category field, so the page says "the category".
3. **Points rate.** "A point comes from every 300 messages or 10 hours in voice" comes from the leaderboard footer, so the page scopes it to "the server in these screenshots". If it is a fixed default, drop that scoping.
4. **Sidebar page names.** The last paragraph of the dashboard section names pages (Analytics, Anti-Raid Protection, Live Stat Channels, and so on) that I only know from the sidebar labels, not from using them. Delete any you consider unfinished.
5. **Shop.** The Shop section is described exactly as the dashboard page words it. Its sample payment text and the ProBot credits option may draw questions from a reviewer. Remove the section if you prefer.
6. **Privacy in screenshots.** Several show real-looking usernames and avatars (the leaderboard, profile, suggestion and giveaway embeds). Blur them if those are real members.
7. **Sample content.** The giveaway prize reads "7k Robux". A neutral prize in a re-captured screenshot would be safer for a public listing.
8. **Rank card.** `/rank` is described in text only. Re-capture it with real data and it can go in the Ranks section.
9. **"Developed by Senju"** in the footer comes from the embed footers in your screenshots. Remove it if you want something else there.
