# Voice Changer Studio — Fish Audio

A Fish Audio voice changer site: Text to Voice, Speech to Voice with a cloning
profile, Create Clone, Play / Download, and Share to Messenger.

## What it does

- **Text to Voice** — type text, pick a cloning profile, generate speech.
  Default model `s2.1-pro-free`, default speed 0.7x (Calm).
- **Speech to Voice** — record your own voice with the microphone or upload an
  audio file, transcribe it, then generate the same words in the chosen
  cloning profile's voice.
- **Create Clone** — save a voice by name + Voice ID, or create a new
  persistent Fish Audio voice model from a 15–30 second sample (POST /model).
- **Play / Download** — play the generated clip in the browser, download it as
  MP3 / WAV / Opus.
- **Share to Messenger** — opens the Facebook Messenger share page; the text is
  copied to the clipboard, and the downloaded audio can be attached in
  Messenger.

Pre-loaded cloning voice: **শান্ত এবং স্মৃতিময় কণ্ঠ**
(`8d83fd34cae54ff9ab8d82537b8fff9d`).

## API key — read this first

This site is a static page. It calls `https://api.fish.audio` directly from
the visitor's browser. **No API key is stored in this repo, in any file, or in
any commit.** Never commit a key here.

To use the site:

1. Open the live site.
2. Paste your Fish Audio API key once into the site's **API key panel**.
   The key is saved only in your own browser and is never sent anywhere
   except to `api.fish.audio`.
3. Get a key at https://fish.audio/app/api-keys (sign in, open Get Started,
   click "Get your API key"). Keep it private — anyone with the key can spend
   your Fish Audio credit.

## Environment variables (Vercel)

These are optional defaults for the deployment. The static page itself reads
its API key from the in-page panel in the visitor's browser, not from server
environment variables — setting them does not inject a key into the page.

| Variable | Value | Scope |
| --- | --- | --- |
| `NEXT_PUBLIC_FISH_AUDIO_VOICE_ID` | `8d83fd34cae54ff9ab8d82537b8fff9d` | Production, Preview |
| `NEXT_PUBLIC_FISH_AUDIO_MODEL` | `s2.1-pro-free` | Production, Preview |
| `FISH_AUDIO_API_KEY` | *(enter in Vercel as a Secret — never in a file or commit)* | Production, Preview |

## Deploy

- Static site: `index.html` at the repo root, `vercel.json` enables clean URLs.
- Import this repo in Vercel (framework: Other / static), or use the Clone
  flow from this repo. No build step is needed.
- API credit: paid models (`s2.1-pro`) need Fish Audio API credit and return
  402 when credit is 0. The site defaults to the free model
  `s2.1-pro-free` and auto-retries on free when a paid model fails with 402.

## Files

- `index.html` — the whole site (single static page).
- `vercel.json` — static hosting settings for Vercel.
- `README.md` — this file.
