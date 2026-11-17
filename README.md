# AI Launch Agent

A one-page launch studio for small brands. Paste a Google Drive link to a product photo or video, type one line about it, and the page:

- writes an on-brand social caption and a launch email with Claude,
- schedules the post on TikTok (or Instagram, Facebook, and more) through Metricool, now or at your audience's best hour,
- emails your customer list a designed HTML email through Gmail,
- saves a record of each launch in a Google Drive folder.

Nothing posts or sends until you see the exact post, the exact email and every recipient, and confirm.

The example styling and brand voice are Emerald & Rose Atelier's. Swap in your own.

## Important: this runs inside Claude, not as a normal website

`launch-agent.html` is a Claude Artifact page. It talks to Metricool, Google Drive and Gmail through **Claude's connectors** (`window.claude.use("mcp")`) and writes copy with **Claude** (`window.claude.use("sample")`). Those only exist when the page is opened as an Artifact on claude.ai.

If you open the file directly in a browser, or host it on GitHub Pages, it will load but say it can't reach your accounts. Nothing will post or send. The repo is a place to keep the source, share it, and track changes.

## Files

| File | What it is |
|---|---|
| `launch-agent.html` | The page itself (HTML, CSS and JavaScript in one file) |
| `SETUP.md` | Step-by-step setup guide: accounts to connect, the prompts that build it, the email list, and troubleshooting |
| `deck/Girl-Let-AI-Do-It-For-You.pdf` | The "Girl, Let AI Do It For You" workshop deck, where the launch agent is the Level 5 demo |

## Run it yourself

1. Connect **Metricool**, **Google Drive** and **Gmail** in claude.ai under Settings > Connectors (same Google account for Drive and Gmail).
2. Edit the `CONFIG` lines near the top of the script in `launch-agent.html`:
   - `ME`: your Gmail address (the email goes to you, with your list in BCC)
   - `FOLDER_NAME`: the Drive folder for your email list and launch records
   - `BRAND_VOICE` and the default business name, if you're not using the example brand
3. In a Claude conversation, ask Claude to publish the file as an Artifact with access to Metricool (`getBrandSettings`, `createScheduledPost`, `getBestTimeToPostByNetwork`), Google Drive (`create_file`, `search_files`, `read_file_content`, `get_file_metadata`, `get_file_permissions`), Gmail (`send_message`), and Claude writing (`sample`).
4. Open the page, allow each connector when asked, and follow `SETUP.md` to add your "Email list" sheet.

Or skip the file entirely and use the two prompts in `SETUP.md` to have Claude build a fresh one for you.

## Privacy

No account IDs, email addresses or social handles are stored in this repo. The page reads your Metricool brand and connected accounts at runtime. Your email list lives in your own Google Drive, not here. Don't commit a copy of your list.
