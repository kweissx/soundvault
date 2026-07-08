# soundvault

My personal music website — plus a tool to back up my Spotify library outside Spotify.

## Spotify Vault Export

`spotify-export.html` is a self-contained, single-page tool that downloads a permanent
record of everything you've liked and collected on Spotify:

- **Followed artists** (with genres)
- **Liked songs** (with the date you liked each one)
- **Saved albums**
- **Every playlist**, including all tracks in each
- **Top artists & tracks** (last 4 weeks / 6 months / all time)

It exports one complete **JSON archive** plus **CSV files** that open in Excel,
Numbers or Google Sheets. Everything runs in your browser and talks only to the
official Spotify API — no server, no third party ever sees your data.

### How to use it

1. **Serve the site locally** (Spotify login can't redirect back to a `file://` page):

   ```bash
   cd soundvault
   python3 -m http.server 8000
   ```

   Then open <http://127.0.0.1:8000/spotify-export.html>.

2. **Create a (free) Spotify app** — one-time setup:
   - Go to the [Spotify Developer Dashboard](https://developer.spotify.com/dashboard) and log in with your normal Spotify account.
   - Click **Create app**, name it anything.
   - Add the **Redirect URI** shown on the export page (e.g. `http://127.0.0.1:8000/spotify-export.html`) — it must match exactly.
   - Tick **Web API** under "Which API/SDKs are you planning to use?", save, and copy the **Client ID**.

3. **Connect & export**: paste the Client ID on the page, click **Connect**, approve the
   read-only permissions, then click **Start Export**. When it finishes, download the
   JSON archive and any CSVs you want and keep them somewhere safe (cloud drive,
   external disk, etc.). Re-run it every few months to keep your backup fresh.

### Note on full listening history

Spotify's API only exposes your recent/top listening, not every play from years past.
For your complete multi-year streaming history, additionally request the
**"Extended streaming history"** download once from
[spotify.com/account/privacy](https://www.spotify.com/account/privacy/) — Spotify
emails it to you within ~30 days. This tool covers everything you've *liked,
followed and playlisted*, which the privacy download does not include in convenient form.
