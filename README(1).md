# VoiceTube Remote

A lightweight Manifest V3 Chrome extension for controlling YouTube with voice or typed commands.

VoiceTube Remote can control playback, search for videos, adjust sound and speed, draft comments, manage captions, react to videos, loop playback, and navigate YouTube without repeatedly using the on-page controls.

> Built with vanilla HTML, CSS, and JavaScript. No dependency installation or build step is required.

## Features

- Voice and typed command input
- Play, pause, restart, next, and previous controls
- Search YouTube and play a result
- Open videos using a YouTube URL or video ID
- Seek forward, backward, or to a specific time
- Volume, mute, and playback-speed controls
- Comment drafting for review
- Like and dislike actions
- Fullscreen controls
- Video looping
- Captions and subtitles controls
- Subscribe and unsubscribe actions
- YouTube home and account-area navigation
- Compact popup and full-page remote interfaces

## Supported command examples

### Playback and navigation

| Command | Action |
| --- | --- |
| `play` | Resume playback |
| `pause` | Pause playback |
| `play lo-fi study music` | Search for and play a video |
| `play video <YouTube URL>` | Open a specific video |
| `load <video ID>` | Open a video by ID |
| `search video jazz` | Open YouTube search results |
| `next video` | Play the next video |
| `previous video` | Go back to the previous page |
| `restart` | Restart the current video |
| `open YouTube` | Open the YouTube home page |
| `open account page` | Open the YouTube account area |

### Timeline, sound, and speed

| Command | Action |
| --- | --- |
| `forward thirty` | Seek forward 30 seconds |
| `back fifteen` | Seek backward 15 seconds |
| `go to 1 minute 20 seconds` | Seek to a specific time |
| `volume fifty` | Set volume to 50% |
| `volume up` | Increase volume |
| `volume down` | Decrease volume |
| `mute` | Mute playback |
| `unmute` | Restore sound |
| `faster` | Increase playback speed |
| `slower` | Decrease playback speed |
| `normal speed` | Reset speed to 1× |

### Video-page actions

| Command | Action |
| --- | --- |
| `comment great explanation` | Insert a comment draft for review |
| `like` | Like the current video |
| `dislike` | Dislike the current video |
| `fullscreen` | Enter fullscreen |
| `exit fullscreen` | Exit fullscreen |
| `loop` | Repeat the current video |
| `stop loop` | Disable looping |
| `subtitles on` | Enable captions |
| `subtitles off` | Disable captions |
| `captions on` | Enable captions |
| `captions off` | Disable captions |
| `subscribe` | Subscribe to the current channel |
| `unsubscribe` | Start YouTube's unsubscribe flow |

## Complete command reference

See [COMMANDS.md](COMMANDS.md) for every supported command, accepted phrase, example, requirement, and limitation.

## Safety behavior

The `comment <text>` command inserts text into the YouTube comment field for review. It does **not** automatically publish the comment.

Unsubscribe confirmation is handled through YouTube's own confirmation interface.

## Installation

1. Download or clone this repository.
2. Open Chrome and visit `chrome://extensions/`.
3. Enable **Developer mode**.
4. Click **Load unpacked**.
5. Select the `chrome-extension` folder.
6. Open a YouTube video.
7. Click the VoiceTube Remote extension icon.
8. Allow microphone access when prompted.

For longer voice-control sessions, select **Open full remote**. Chrome closes popup scripts when the popup is dismissed, while the full remote remains open in a browser tab.

## Development

The project uses plain JavaScript and does not require npm packages.

After changing extension files:

1. Open `chrome://extensions/`.
2. Find **VoiceTube Remote**.
3. Click the reload button.
4. Refresh any open YouTube tabs.

### Run parser tests

Node.js is required only for the parser tests:

```bash
node chrome-extension/popup-parser.test.cjs
```

## Project structure

```text
.
├── README.md
├── LICENSE
├── .gitignore
├── index.html
├── app.js
├── styles.css
└── chrome-extension/
    ├── manifest.json
    ├── command-parser.js
    ├── content.js
    ├── popup-parser.test.cjs
    ├── popup.css
    ├── popup.html
    ├── popup.js
    ├── remote.css
    ├── remote.html
    └── README.md
```

The root HTML, CSS, and JavaScript files contain the standalone prototype. The `chrome-extension` folder contains the installable unpacked Chrome extension.

## Permissions

The extension requests:

- `activeTab` to interact with the currently permitted page
- `tabs` to find, create, update, and navigate YouTube tabs
- `scripting` to make the YouTube control script available
- Access to YouTube URL patterns required for page control

## Privacy

The project does not include its own analytics service, account system, database, or project-owned backend.

Voice recognition is provided by the browser. Microphone permission and speech processing therefore depend on Chrome and the user's browser settings.

## Known limitations

- Voice recognition accuracy depends on Chrome, the operating system, microphone quality, accent, and background noise.
- YouTube may change its page structure, which can require selector updates.
- Some controls require an active YouTube video page.
- Browser autoplay policies may require direct user interaction before audio begins.
- The smart background-tab routing improvement is not yet included in this uploaded source version.

## Planned smart tab routing

The planned routing update will apply only to video-loading commands:

- If the active tab is already a YouTube video page, load the requested video there.
- Otherwise, create a new YouTube tab in the background without replacing the user's working tab.
- Do not change comment, like, dislike, fullscreen, loop, captions, subscribe, unsubscribe, or account-navigation behavior.

## Security

Never publish extension signing keys.

The following files are intentionally excluded from this repository:

```text
*.pem
*.key
*.crx
.env
```

## Contributing

Focused bug reports and pull requests are welcome. Include:

- Command used
- Expected behavior
- Actual behavior
- Current YouTube page type
- Chrome version
- Relevant console error

Avoid unrelated refactoring when changing command routing or YouTube selectors.

## License

Licensed under the [MIT License](LICENSE).

Copyright © 2026 Kitagawa.
