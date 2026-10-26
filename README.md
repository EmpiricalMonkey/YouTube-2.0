# Intentional Video — Version 1

A static, mobile-friendly YouTube library without a recommendation feed, Shorts feed, or autoplay.

## Try it

For a quick desktop test, serve this folder with `python3 -m http.server 8000` and open `http://localhost:8000`.

To install on Android, upload the *contents* of this folder to any static HTTPS host (for example GitHub Pages, Cloudflare Pages, or Netlify), open the HTTPS site in Chrome, and choose **Add to Home screen / Install app**. HTTPS is required for PWA installation on a phone.

## Use

- Paste a YouTube watch/share link or video ID into the search field. It is saved to your library and opened in the player.
- Search directly inside the app by supplying your own **YouTube Data API v3** key in Settings. Without a key, in-app search is unavailable, but paste-link playback and the library work.
- Edit a saved video's title/category, or remove it.
- Export a JSON backup and import it on another device. This is **manual** transfer, not sync.
- Playback progress is saved approximately every five seconds while a video is playing, when the YouTube iframe API permits it.

## API key setup (optional)

1. Create/select a project in Google Cloud Console.
2. Enable **YouTube Data API v3**.
3. Create an API key and restrict it to YouTube Data API v3. Configure an appropriate quota.
4. In this app's Settings, paste the key and save it.

**Security:** The key is stored in your browser's localStorage and used directly from the browser. Do not use a sensitive or unrestricted key; do not embed a key in public source code. Browser-referrer restrictions can be configured for a fixed hosted domain. For stronger protection, use a server-side API proxy in a future version.

## Known limitations

- YouTube's embedded player can still show YouTube-controlled suggestions, overlays, and advertisements. The app does not bypass YouTube Premium or YouTube policies.
- Direct search filters out videos under four minutes using YouTube's `videoDuration=medium` filter (which includes 4–20 minutes); longer videos can also be returned. This is not a perfect Shorts filter.
- Some videos disable embedding and will not play here.
- This app does not intercept YouTube links from other apps; Android link interception requires additional platform configuration.
- Library data lives in the browser profile and may be erased when site data is cleared. Back it up with Export.
- Offline shell may load, but videos and search require internet.
- Video metadata lookup can fail due to YouTube cross-origin restrictions; the app asks for a title when needed.
