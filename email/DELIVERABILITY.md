# Why our emails land in spam — and what to click in Loops

Written for clicking through the Loops website. No Terminal, no code.

## The short version

Spam filters ask three questions about every email:

1. **Is the sender who they say they are?** — proven by two invisible
   signatures called **SPF** and **DKIM**. Loops calls this **domain
   verification**. This is by far the biggest factor, and it's a
   one-time setup.
2. **Can people opt out?** — there must be a working unsubscribe link.
   (The new template has one built in; Loops fills in the address.)
3. **Do people actually open these emails?** — reputation builds over
   time. Nothing to click for this one; it follows from 1 and 2.

If our welcome emails sometimes land in spam, the number one suspect is
that **getmodascout.com is not verified in Loops**. Check that first.

---

## 1. Check whether our domain is verified (the single most important thing)

1. Go to **app.loops.so** in your browser and log in.
2. Find **Settings** — the gear icon / "Settings" entry in the left
   sidebar (bottom area).
3. Inside Settings, click **Domain** (the page also lives at
   `app.loops.so/sending-domain`).
4. You'll see a screen listing DNS records — rows named **SPF**,
   **DKIM** and **MX**, each with a small clipboard/copy icon next to
   a long string of technical text. You don't need to understand the
   strings.
5. Look at the status next to each record:
   - **Green "Records present"** next to every row → we are verified.
     Deliverability's biggest problem is already solved — skip to
     section 2.
   - Anything not green (pending / missing / red) → we are **not**
     verified, and that's very likely why emails go to spam.

### If it's NOT verified

The records shown on that screen have to be copied into the settings of
the company where **getmodascout.com** was registered (GoDaddy,
Namecheap, etc. — whoever the domain was bought from). Two ways:

- **If Noah manages the domain:** on that same Loops screen there's an
  option to **export / share the records** so you can send them to
  whoever manages DNS. Do that and send them to Noah with: "please add
  these to getmodascout.com's DNS, then I'll press Verify."
- **If you have the registrar login:** their websites all have a
  "DNS" or "DNS records" page where you paste each record (copy each
  one with the clipboard icon in Loops). It's copy-paste, no typing.

Then go back to the Loops Domain page and click **Verify** (records can
take up to a few hours to be noticed after they're added — if it fails,
wait and press Verify again later).

### Why this one thing matters most

Since 2024, Gmail and Yahoo **require** these signatures from anyone
sending sign-up emails. Without them, our emails look like they might be
forged — and "might be forged" is exactly what the spam folder is for.
No amount of nice design fixes an unverified domain.

---

## 2. Quick free check of our DNS (2 minutes)

1. Go to **loops.so/tools/dns-checker** (free, no login).
2. Type **getmodascout.com** and run the check.
3. It shows SPF / DKIM / DMARC / MX in plain pass–fail terms. Green
   across the board = healthy.

If DMARC shows as missing: that's a third, optional signature that
tells inboxes "reject fakes of this domain." Worth adding later —
it's one more DNS record for whoever manages the domain (Loops' docs
have a guide: loops.so/docs/deliverability/dmarc-dkim-setup). Not the
urgent one; SPF/DKIM verification is.

---

## 3. Prove it worked — read a real email's "passport"

After the domain is verified, send yourself a test from Loops (steps in
HOW-TO-UPDATE-LOOPS.md), then:

1. Open the email in **Gmail** (on a computer).
2. Click the **three dots** in the top-right of the message → **Show
   original**.
3. A new tab opens with a summary table at the top. You want to see:
   - **SPF: PASS**
   - **DKIM: PASS**

Both green PASSes = inboxes now trust us.

**Optional score check:** go to **mail-tester.com** (free). It shows a
one-time email address — copy it, send a test from Loops to that
address, then click "check your score." Anything 8/10 or above is
good. It also lists, in plain English, anything still counting
against us.

---

## 4. Things in the email itself (already handled, just don't undo them)

- **Unsubscribe link** — the new template includes Loops' required
  `{unsubscribe_link}` in the footer. Never delete it; Loops won't
  send properly without it, and spam filters check for it.
- **Real text, not one big image** — the new template is almost all
  text, which filters like. Keep it that way if it's ever edited.
- **Small size** — the email is ~20KB. Gmail clips emails over ~100KB
  (and clipping hides the unsubscribe link, which hurts spam scores),
  so avoid pasting big images into it later.
- **A "from" name people recognise** — in Loops the sender should read
  something like **ModaScout** with an address on our own domain
  (e.g. hello@getmodascout.com), not a gmail.com address. This is on
  the same Settings → Domain page area. Sending "from" a Gmail/Yahoo
  address while using Loops is a classic instant-spam trigger.

## What NOT to worry about

Word myths ("free" in the subject = spam, etc.) barely matter compared
to the above. Fix the domain verification and the rest is polish.
