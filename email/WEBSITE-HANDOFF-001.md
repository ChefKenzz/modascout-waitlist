# WEBSITE-HANDOFF-001 — new waitlist welcome email (2 Sep 2026)

## What got built tonight (all in Desktop → Claude → ModaScout → website → email)

- A new welcome email in the site's black-and-white style: warm
  welcome, "what happens next", a referral card ("each friend who
  joins moves you up 10 spots") with a button and a visible copy of
  the person's link, social links, and the unsubscribe line Loops
  requires. Built the way email clients need it (Gmail / Apple Mail /
  Outlook safe), ~20KB, plus a plain-text version.
- **PREVIEW — double-click me.html** — double-click it to see the
  email exactly as recipients will, desktop and iPhone side by side.
  (The referral link in the preview is a sample.)
- **welcome-email-loops.zip** — the file that actually goes into
  Loops. Important discovery: Loops doesn't accept pasted HTML;
  custom designs are uploaded as this zip through the editor's
  "Code" option. Don't unzip it.
- **DELIVERABILITY.md** — plain-English guide to why emails land in
  spam. The headline: check whether getmodascout.com is verified in
  Loops (Settings → Domain → green "Records present"). That single
  thing matters more than everything else combined.
- **HOW-TO-UPDATE-LOOPS.md** — click-by-click: how to upload the zip
  into the existing welcome email without touching the trigger, and
  how to send yourself a test first.
- Everything is committed and pushed to the modascout-waitlist repo
  (in an email/ folder). The live page was not touched.

## What I (Chef) do tomorrow — about 10 minutes of clicking

1. Double-click **PREVIEW — double-click me.html** and decide if I
   like it. Any wording change: just tell Claude.
2. Open **DELIVERABILITY.md** → do section 1 (check domain
   verification in Loops). If it's not green, that's the spam
   problem found.
3. Open **HOW-TO-UPDATE-LOOPS.md** → follow it top to bottom. Step 0B
   matters most: check what the referral-link property is actually
   called on a contact in Loops **before** uploading. If it's not
   `referralLink` holding a full https link, paste what I found back
   into Claude for a corrected zip.

## What needs Noah

1. **Domain verification (if not already green):** the DNS records
   Loops shows under Settings → Domain need adding wherever
   getmodascout.com is registered. Loops has an export/share option
   for exactly this. This is the #1 spam fix.
2. **Referral link into Loops:** confirm how signups get from
   Supabase into Loops and that each contact carries a property with
   their full referral link (https://www.getmodascout.com/?ref=CODE).
   The email shows that property; if contacts only carry the short
   code (or nothing), that sync needs a small change on his side.
3. **Confirm the welcome email lives in the "Loops" tab** (an
   automation), not "Transactional" — if it's transactional, tell
   Claude, the zip needs a small placeholder change.

## Open questions logged in the Brain

- Exact name of the referral-link property in Loops (blocks going live).
- Is the sending domain verified? (Chef checks tomorrow.)
- Who holds the registrar login for getmodascout.com DNS?
