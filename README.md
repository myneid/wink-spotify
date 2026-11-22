# Spotify for Wink

The bundled Spotify player for [Wink](https://github.com/myneid/wink), published as a portable web-plugin example. Requires Wink 0.8.0 or later on macOS 13+. Older Wink hosts do not provide the streaming-token bridge.

## Use it

Install [Wink](https://github.com/myneid/wink/releases/latest), then choose **Apps → Spotify → Connect with Spotify**. Spotify opens in your browser for consent. Choose **Play in Wink** to use Spotify’s Web Playback SDK without a separate Spotify app. Premium is required. Existing users must disconnect and reconnect once to grant streaming permission. This is experimental: SDK/iframe initialization passes, but audible account playback remains unverified.

Wink includes this plugin already. **Do not install this repository over the bundled copy:** Wink rejects duplicate IDs, and the native `spotify` capability is deliberately restricted to the trusted bundled package. Publishing this source does not grant arbitrary GitHub plugins access to that bridge. Generic web plugins can be installed from GitHub; this privileged example ships with Wink.

## Features

Keyboard-driven player, album artwork, track search, liked songs, playlist browsing, queue viewing/addition, device selection, play/pause, skip, seek, volume, shuffle and repeat. Space toggles playback, N/P skip, and / focuses search.

## OAuth and access

The public Wink client ID is bundled; no client secret or developer registration is needed by users. Uses PKCE via Wink's native bridge, with callback `http://127.0.0.1:43821/callback`. Refresh tokens stay in macOS Keychain. The bundled SDK receives a short-lived access token through the native bridge; no credentials are stored in this repository.

**The Spotify app is currently in development mode.** Only accounts authorized under Spotify's current development rules can use it. A public download is not unrestricted Spotify access. Public availability requires Spotify approval; playback controls require an eligible Premium account. Live account login and playback have not yet been end-to-end verified.

## Development

`manifest.json`, `index.html`, `app.js`, and `style.css` match Wink's bundled `Resources/Plugins/org.blink.spotify` package. No dependencies or build scripts. See the [plugin API](https://github.com/myneid/wink/blob/main/docs/plugins.md). The HTML/CSS/JS contract is designed to be portable; Blink/iOS is not implemented or tested. This is a terminal-style web UI, not a PTY/Kitty-graphics TUI.

To try changes, copy these four files into a Wink source checkout's bundled package directory and build Wink. Host native changes belong in the Wink repository. Keep the two copies synchronized when releasing.

Playlist editing, library mutation and podcasts are not implemented. Unofficial project; not affiliated with Spotify.

## License

GPL-3.0; see [LICENSE](LICENSE).
