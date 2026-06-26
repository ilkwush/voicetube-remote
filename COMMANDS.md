# VoiceTube Remote Command Reference

This document lists the commands currently recognized by VoiceTube Remote.

Commands can be spoken through the microphone button or entered in the typed-command field. Commands are normalized to lowercase, so capitalization does not matter.

## Quick start

1. Open a YouTube video.
2. Open the VoiceTube Remote extension.
3. Press the microphone button or type a command.
4. Say or enter a command such as `pause`, `volume fifty`, or `forward thirty`.

> Some commands require an active or existing YouTube video tab. Navigation commands can open YouTube pages directly.

---

## 1. Playback controls

| Primary command | Other accepted phrases | What it does | Requires video page |
| --- | --- | --- | --- |
| `play` | `resume`, `start`, `start video` | Resumes the current video. | Yes |
| `pause` | `hold`, `stop video` | Pauses the current video. | Yes |
| `toggle` | `play pause` | Switches between play and pause. | Yes |
| `restart` | `start over`, `beginning` | Moves to the beginning and starts playback. | Yes |
| `next video` | `next`, `skip video`, `skip to next` | Clicks YouTube’s next-video control. | Yes |
| `previous video` | `previous`, `prev video`, `last video`, `go back video` | Goes back to the previous page or uses the previous-video control when available. | Existing YouTube tab |

### Examples

```text
play
pause
restart
next video
previous video
```

---

## 2. Play a named video or search query

| Command format | What it does |
| --- | --- |
| `play <search query>` | Opens YouTube search, waits for the results, and attempts to play the first result. |
| `play <YouTube URL>` | Opens the specified YouTube video. |
| `play <video ID>` | Opens the video matching the 11-character YouTube video ID. |
| `play video <YouTube URL or video ID>` | Opens a specific YouTube video. |
| `load <YouTube URL or video ID>` | Opens a specific YouTube video. |
| `open <YouTube URL or video ID>` | Opens a specific YouTube video when the value is a valid YouTube URL or video ID. |

### Examples

```text
play lo-fi music
play jazz for studying
play video https://www.youtube.com/watch?v=dQw4w9WgXcQ
load dQw4w9WgXcQ
```

The parser accepts standard YouTube links, shortened `youtu.be` links, Shorts links, live links, embed links, and valid 11-character video IDs.

Start times included in supported links are preserved when possible.

> Current source note: the smart background-tab routing improvement is still planned. The current uploaded source may activate or reuse a YouTube tab when these commands run.

---

## 3. Search without automatically playing

| Primary format | Other accepted formats | What it does |
| --- | --- | --- |
| `search video <query>` | `search <query>`, `search for <query>`, `find <query>`, `find video <query>`, `look up <query>` | Opens the YouTube search-results page for the query. |

### Examples

```text
search video mechanical keyboard review
search for relaxing music
find video JavaScript tutorial
look up gaming mouse comparison
```

---

## 4. Timeline controls

| Primary command | Other accepted phrases | What it does |
| --- | --- | --- |
| `forward` | `ahead`, `skip` | Moves forward 10 seconds by default. |
| `forward <number>` | `ahead <number>`, `skip <number>` | Moves forward by the specified number of seconds. |
| `back` | `rewind`, `backward` | Moves backward 10 seconds by default. |
| `back <number>` | `rewind <number>`, `backward <number>` | Moves backward by the specified number of seconds. |
| `go to <time>` | `jump to <time>`, `seek to <time>` | Moves playback to a specific timestamp. |

### Examples

```text
forward
forward thirty
skip 45
back fifteen
rewind 10
go to 1 minute 20 seconds
jump to 2:35
seek to 90
```

Numbers may be entered as digits or common English number words.

Supported time styles include:

```text
90
1:30
2 minutes 15 seconds
1 hour 5 minutes
```

---

## 5. Volume and sound

| Primary command | Other accepted phrases | What it does |
| --- | --- | --- |
| `mute` | `silent` | Mutes the video. |
| `unmute` | `sound on` | Restores sound. |
| `volume up` | `louder` | Increases volume by 10 percentage points. |
| `volume down` | `quieter` | Decreases volume by 10 percentage points. |
| `volume <number>` | `volume to <number>`, `volume at <number>`, `sound <number>` | Sets volume from 0 to 100. |

### Examples

```text
mute
unmute
volume up
volume down
volume fifty
volume to 75
sound 20
```

Values below 0 are limited to 0, and values above 100 are limited to 100.

---

## 6. Playback speed

| Primary command | Other accepted phrases | What it does |
| --- | --- | --- |
| `faster` | `speed up` | Increases speed by 0.25×. |
| `slower` | `slow down` | Decreases speed by 0.25×. |
| `normal speed` | `regular speed` | Resets playback speed to 1×. |

### Examples

```text
faster
speed up
slower
normal speed
```

Playback speed is limited to a range of 0.25× to 2×.

---

## 7. Comment drafting

| Primary format | Other accepted formats | What it does |
| --- | --- | --- |
| `comment <text>` | `leave comment <text>`, `write comment <text>`, `draft comment <text>`, `add comment <text>` | Scrolls to the comment area, opens the editor, and inserts the text for review. |

### Example

```text
comment this explanation was very helpful
```

### Safety behavior

The command **does not submit or publish the comment automatically**. Review the inserted text and click YouTube’s Comment button yourself.

The command may fail when:

- You are not signed in.
- Comments are disabled.
- The page is not a normal YouTube video page.
- YouTube changes the comment-box structure.

---

## 8. Reactions

| Primary command | Other accepted phrases | What it does |
| --- | --- | --- |
| `like` | `like video`, `thumbs up` | Likes the current video unless it is already liked. |
| `dislike` | `dislike video`, `thumbs down` | Dislikes the current video unless it is already disliked. |

### Examples

```text
like
dislike
thumbs up
```

These commands operate on the visible reaction controls of the current YouTube video.

---

## 9. Fullscreen

| Primary command | Other accepted phrases | What it does |
| --- | --- | --- |
| `fullscreen` | `full screen`, `enter fullscreen`, `enter full screen` | Enters YouTube player fullscreen mode. |
| `exit fullscreen` | `exit full screen`, `leave fullscreen`, `leave full screen`, `close fullscreen`, `close full screen` | Exits fullscreen mode. |

### Examples

```text
fullscreen
exit fullscreen
```

The extension avoids clicking the button when the requested fullscreen state is already active.

---

## 10. Video looping

| Primary command | Other accepted phrases | What it does |
| --- | --- | --- |
| `loop` | `loop video`, `repeat`, `repeat video`, `turn on loop` | Repeats the current video. |
| `stop loop` | `loop off`, `repeat off`, `disable loop`, `turn off loop` | Stops repeating the video. |

### Examples

```text
loop
repeat video
stop loop
```

Looping uses the video element’s loop setting and an ended-playback fallback.

---

## 11. Captions and subtitles

| Primary command | Other accepted phrases | What it does |
| --- | --- | --- |
| `subtitles on` | `subtitle on`, `captions on`, `caption on`, `cc on`, `open subtitles`, `open subtitle`, `open captions`, `open caption` | Turns captions on. |
| `subtitles off` | `subtitle off`, `captions off`, `caption off`, `cc off`, `close subtitles`, `close subtitle`, `close captions`, `close caption` | Turns captions off. |

The parser also accepts the common speech-recognition mistake `subtleties on` or `subtleties off`.

### Examples

```text
subtitles on
captions off
cc on
```

Captions must be available for the selected video.

---

## 12. Channel subscription

| Primary command | Other accepted phrases | What it does |
| --- | --- | --- |
| `subscribe` | `subscribe channel`, `follow channel` | Subscribes to the current video’s channel. |
| `unsubscribe` | `unsub`, `unsubscribe channel`, `stop subscription` | Opens and confirms YouTube’s unsubscribe flow when currently subscribed. |

### Examples

```text
subscribe
unsubscribe
follow channel
```

You must be signed in. YouTube may display menus or confirmation dialogs during unsubscribe.

---

## 13. YouTube navigation

### Home page

| Primary command | Other accepted phrases | Destination |
| --- | --- | --- |
| `open YouTube` | `home`, `main`, `main page`, `YouTube home`, `go home`, `go to home`, `home page`, `go to main page`, `open main page`, `YouTube main page` | `https://www.youtube.com/` |

### Account area

| Primary command | Other accepted phrases | Destination |
| --- | --- | --- |
| `open account` | `open account page`, `account`, `account page`, `my account`, `YouTube account`, `open YouTube account`, `settings page`, `open settings` | `https://www.youtube.com/account` |

### Examples

```text
open YouTube
home
open account
account page
open settings
```

These are intentional navigation commands and should remain separate from video-player controls.

> `my channel` is part of the planned design but is **not currently recognized by the uploaded parser**. It should be added separately before documenting it as supported.

---

## 14. Typed commands

Every voice command can also be typed into the extension’s command field.

Typed input is useful when:

- The microphone is unavailable.
- Speech recognition misunderstands a title.
- A YouTube URL or video ID is easier to paste.
- You want to test a command during development.

---

## 15. Number recognition

VoiceTube Remote recognizes:

- Digits: `10`, `45`, `100`
- Small number words: `one` through `nineteen`
- Tens: `twenty`, `thirty`, `forty`, and so on
- Combined words: `twenty five`
- Hundreds: `one hundred`

Examples:

```text
volume seventy
forward twenty five
go to one hundred
```

---

## 16. Commands that need a video page

These commands normally require a YouTube video player:

```text
play
pause
toggle
restart
next video
forward
back
go to
mute
unmute
volume
faster
slower
normal speed
like
dislike
fullscreen
exit fullscreen
loop
stop loop
subtitles on
subtitles off
subscribe
unsubscribe
comment <text>
```

Navigation, search, and video-loading commands can open or update a YouTube tab.

---

## 17. Troubleshooting

### “Open a YouTube video tab first”

Open a YouTube video and try the command again. The extension searches for the active YouTube tab first, then the most recently accessed YouTube tab.

### “No YouTube video player found”

The selected tab may be:

- YouTube’s home page
- A search page
- A channel page
- A page that has not finished loading

Open a normal watch page and retry.

### A button is not found

YouTube frequently changes its page layout. The extension may need updated selectors for:

- Like or dislike
- Subscribe
- Comments
- Captions
- Fullscreen

### Voice recognition does not start

Check:

- Chrome microphone permission
- Operating-system microphone access
- Whether another application is using the microphone
- Internet access required by the browser speech service
