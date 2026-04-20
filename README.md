# Spotify Token Generator

Single-page webapp to generate access + refresh tokens for the Spotify Web API using the Authorization Code flow.

## Usage

1. Serve this directory locally:
   ```sh
   python3 -m http.server 8888
   ```
2. Open http://127.0.0.1:8888 in your browser.
3. In your [Spotify app](https://developer.spotify.com/dashboard) settings, add `http://127.0.0.1:8888/` as a Redirect URI.
4. Enter Client ID + Secret, pick scopes, click **Authorize with Spotify**.
5. Copy the access and refresh tokens from the result page.

Credentials are stored in `localStorage` for convenience and never leave your browser (token exchange goes directly to Spotify).

## Deploy to Coolify

1. Point Coolify at this repo and pick **Docker Compose** as the build pack.
2. Deploy — Coolify assigns an HTTPS domain and proxies it to the container's port 80.
3. In your Spotify app dashboard, add that HTTPS URL (e.g. `https://your-app.coolify.example/`) as a Redirect URI.
4. Open the URL — the app reads its own origin and shows the exact redirect URI to paste into Spotify.

Spotify rejects plain `http://` redirect URIs except for `127.0.0.1` loopback, so HTTPS from Coolify is what makes remote deployment work.
