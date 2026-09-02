# Putting the new welcome email into Loops — click by click

One important thing discovered while building this: **Loops does not let
you paste raw HTML** into its editor. Custom designs go in as a small
zip file uploaded through the editor's **"Code"** option. That zip is
already made for you: **`welcome-email-loops.zip`** in this folder.
Don't unzip it — it gets dragged in whole.

Time needed: about 10 minutes.

---

## Step 0 — Two quick checks before touching anything

### A. Find where the welcome email lives

1. Log in at **app.loops.so**.
2. Look at the left sidebar. The places our welcome email could live:
   - **Loops** — automations drawn as a flowchart (most likely). Click
     it and look for the one that sends the welcome email (probably
     named something like "Welcome" and triggered when a new contact
     joins).
   - **Transactional** — emails sent by code. If the welcome email is
     here instead, **stop and tell your Claude session** — the
     transactional version needs slightly different placeholder text
     inside the file, and you'll get a corrected zip in a minute.
3. Open the welcome loop. You'll see boxes connected by lines: a
   **trigger** box at the top ("Contact added" or similar) and an
   **email** box below it.

**The one rule: never delete or edit the trigger box.** That box is
what makes the email send when someone joins. We only ever open the
email box.

### B. Check the referral link's name

The new template contains the placeholder `{referralLink}`. Loops
replaces that with each person's own link — but only if a contact
property with **exactly that name** exists and holds a **full link**
(starting with https://...).

1. Click **Audience** in the left sidebar.
2. Click any contact — a panel opens showing their details
   ("properties"): email, date added, and any custom ones.
3. Look for the property holding their referral link or code.
   - If it's named **referralLink** and contains a full
     `https://www.getmodascout.com/?ref=...` link → carry on.
   - If it has a **different name**, or holds only a short code like
     `AB12CD` (no https), or **doesn't exist at all** → stop here and
     paste what you found into your Claude session. The zip will be
     corrected to match (a one-minute job). Uploading with a wrong
     name means everyone gets an email with a blank or broken link —
     this check is what prevents that.

---

## Step 1 — Take a "before" picture

Uploading the new design **replaces** what's currently in the email
box, and there's no simple undo. So first: open the existing welcome
email in the editor, and take a screenshot of it (press
**Cmd + Shift + 3** to snap the whole screen — it saves to your
Desktop). If anything goes wrong, the old email can be rebuilt from
that picture.

---

## Step 2 — Upload the new design

1. Inside the welcome loop, click the **email box** → open its editor.
   You'll see the current email in the middle and a settings panel on
   the right.
2. In that right-hand panel, find the styling choices and pick
   **Code**. A file drop-zone appears ("drag and drop a .zip").
3. Open Finder → **Desktop → Claude → ModaScout → website → email** and
   drag **`welcome-email-loops.zip`** onto the drop zone.
4. The editor should now show the black ModaScout email — same as the
   preview file in this folder.
5. Set the **subject line** (field above the email). Suggestion:
   **You're on the list — welcome to ModaScout**
6. Check the **From** name/address while you're here: it should read
   **ModaScout** and use a getmodascout.com address — see
   DELIVERABILITY.md if it doesn't.

---

## Step 3 — Send yourself a test (always, before real people get it)

1. Still in the email editor, look for the **test send** option — a
   button or menu item labelled **"Send test email"** (sometimes behind
   a **···** menu or a paper-plane icon near the top of the editor).
2. Enter your own email address and send.
3. In your inbox (check **spam too** — that's data, not failure),
   confirm:
   - the black design shows properly (try it on your iPhone as well),
   - the **Share your link** button opens getmodascout.com with
     `?ref=` and a code on the end — *note: in a test send, Loops may
     show the placeholder as blank or as literal text if your own
     contact doesn't have the referral property; judge the link on a
     test to an address that's actually in the waitlist*,
   - the **Unsubscribe** link at the bottom is present,
   - the three social links go to TikTok / Instagram / X.

---

## Step 4 — Save and leave everything else alone

1. Save / go back to the flowchart. Confirm the loop's on/off toggle is
   still **On** (top of the loop screen).
2. Don't touch the trigger box, don't duplicate the loop, don't create
   a new loop. Done.

From the next signup onwards, the new email goes out automatically —
the trigger never changed, only the contents of the email box.

---

## If something looks broken

Nothing sent yet = nothing lost. Close the editor without saving if it
offers that, or re-upload the zip and try again. Worst case, describe
what you see to your Claude session (a screenshot pasted into Cowork is
perfect) and it will be fixed from here.
