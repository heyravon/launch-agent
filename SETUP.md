# How to Set Up Your AI Launch Agent

## What the agent does

The launch agent turns one product photo or video plus one sentence into a full launch in about two minutes. It is a page Claude builds for you, connected to your own accounts:

- **Writes** an on-brand social caption and a launch email (Claude).
- **Posts** to TikTok or other networks, now or at your audience's best hour (Metricool).
- **Emails** your customer list a designed, branded email with the ad in it (Gmail).
- **Files** a record of each launch in a Google Drive folder (Google Drive).

Nothing posts or sends until you see the exact post, the exact email and every recipient, and tap yes.

## Before you start: accounts to connect

Set these up first. Every connector is added in claude.ai under **Settings > Connectors**. Use the same Google account for Drive and Gmail, the one you want emails sent from.

| What | Why the agent needs it | How to set it up |
|---|---|---|
| Claude (paid plan) | Builds the page and writes the content | claude.ai, a plan with Projects and connectors |
| Metricool account | Publishes the social posts | Free account at metricool.com, then add the **Metricool** connector in Claude |
| TikTok (or Instagram, etc.) | Where posts go | In TikTok: switch to a **Business account** and turn **Private account off**. Then connect it inside Metricool (Brand settings > Connections) |
| Google Drive connector | Holds your ads, email list and launch records | Add **Google Drive** in Claude Connectors |
| Gmail connector | Sends the launch email | Add **Gmail** in Claude Connectors, same Google account as Drive |
| Canva (optional) | Designs graphics and a brand kit | Add **Canva** in Claude Connectors |

Open the finished page in a web browser (Chrome, Safari, Edge) on a computer. Some Claude desktop and phone apps can't send large files.

## Step 1: the prompt that builds the agent

Start a new Claude Project (or Claude Code session) with the connectors above turned on, then paste this prompt. Replace the parts in brackets.

```text
Build me a launch agent as an Artifact page I can reuse for every product launch.
It should use my connected Metricool, Google Drive and Gmail connectors, and Claude
for writing. Keep it simple: one card, steps top to bottom.

Steps on the page:
1. A box where I paste a Google Drive share link to my photo or video. Read the
   file's details from Drive, tell me if it's a photo or video, and warn me if
   the file isn't shared as "Anyone with the link" or is a PNG (TikTok needs JPG).
2. A box for one line about the product (name, price, sizes, where to buy).
3. One "Create with AI" button that writes, in my brand voice:
   - a social caption (hook, short invitation, 5 to 8 hashtags, under 300 characters)
   - a launch email: subject, short headline, and 3 short paragraphs
   Both stay editable, with separate "Rewrite" buttons.
4. A launch email section: read my recipients from a Google Sheet called
   "Email list" in a Drive folder called "[Your Brand] - Posts" (create the
   folder if missing). Send as a designed HTML email: brand header, the ad
   image full width with a "Play the film" bar linking to it, headline,
   paragraphs, one button linking to my TikTok profile, and a footer.
   Send to me with the whole list in BCC.
5. When to post: "Post now" (default), "Best time in the next 24 hours" (from
   Metricool's best-time data), or in 1 hour. Plus a TikTok audience choice
   (everyone, followers, only me, or finish on my phone) and an "AI-generated"
   label that's on by default.
6. A "Post it" button that first shows me the exact post, the exact email and
   every recipient, and only acts after I tap "Yes, post and send". Then:
   schedule the post in Metricool (give TikTok a title from the caption's first
   line, send Drive links as direct-download links), send the email through
   Gmail, and save a text record of the launch in the Drive folder.

Show clear error messages with the reason, never a generic "something went wrong".
My Metricool brand posts to: [TikTok @yourhandle]. My timezone: [America/Los_Angeles].
```

## Step 2: the prompt that makes it on-brand

Once the page works, send your brand guide in the same conversation. Fill in your own details; the example values are Emerald & Rose Atelier's.

```text
Apply my brand to the launch agent: the page, the email design and the AI writing.

Brand name: [Emerald & Rose Atelier], [made-to-order dresses, Seattle]
Colors: [Emerald #14382E] main (headlines, dark backgrounds, brand name),
[Blush #FFF5F7] background, [Rose #F7A8C4] accents and thin lines,
[Hot pink #C2185B] for one button only, [Sage #D6EADF] secondary.
About 60% background, 30% main color, 10% accents.
Fonts: [Playfair Display] for headlines (italics for emphasis, like
"Meet *The Celeste*"), [DM Sans] light for body text.
Logo: the name in small, widely spaced capitals: [EMERALD & ROSE / ATELIER · SEATTLE],
with the "&" in [Rose].
Look: [quiet luxury, fashion-magazine editorial, lots of white space, hairline rules].
Avoid: [emojis, gradients, clip art, heavy bold, anything like a sale flyer].
Voice: [warm, bold and elegant, like a stylist who's also your best friend].
Words to use: [crafted, made for your moment, made to order, confident, Seattle].
Words to avoid: [cheap, deal, hurry, "buy now!!!"].
Sign-off line for every email: ["Made for your moment. Crafted in Seattle."]
Prefill my business name and add a preview of the designed email.
```

## Step 3: set up the folder and email list

The agent creates the Drive folder on first use. Then:

1. Open the folder **[Your Brand] - Posts** in Google Drive.
2. Add a Google Sheet named exactly **Email list**, with `email` and `name` in row 1.
3. Put one customer email per row in column A. Only add people who agreed to hear from you.
4. Put each new ad (JPG photo or MP4 video) in Drive. Right-click it, choose **Share**, and set **General access** to **Anyone with the link**.

Open the page and allow Claude, Metricool, Google Drive and Gmail when it asks. That's a one-time step per connector.

## Using it for each launch

1. Paste the Drive link to your ad.
2. Type one line, for example: "The Celeste dress, made to order, sizes 0 to 24, link in bio."
3. Tap **Create with AI**, then read and edit the caption and email.
4. Pick when to post and who can see it on TikTok.
5. Tap **Post it**, check the post, email and recipients, then tap **Yes, post and send**.

From a Drive link Claude can look at photos but not watch videos, so for a video make the one line descriptive.

## Troubleshooting

These are the errors we actually hit while building it, and what fixed each one.

| Error message | What it means | Fix |
|---|---|---|
| Failed to normalize media | Metricool couldn't download the file | Set the Drive file to "Anyone with the link" |
| The 'image/png' type is not allowed | TikTok photo posts only take JPG or WebP | Save the image as JPG (Canva: Share, Download, JPG) |
| TikTok title is required | TikTok posts need a title | Ask Claude to use the caption's first line as the title |
| The account type does not allow the specified privacy options | The TikTok account is private or personal | Make the account public and a Business account, reconnect it in Metricool, or post as "only me" and switch to Everyone in TikTok |
| no_file_route | The Claude app can't send large files | Use Drive links, or open the page in a web browser |
| Email sends from the wrong address | Gmail is connected with a different Google account | Reconnect Gmail in Settings > Connectors with the right account |
