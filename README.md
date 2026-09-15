# 🎵 Music Player

A minimalist, single-track music player built with plain HTML, CSS, and JavaScript. It features a custom-styled progress bar, animated play/pause control, and skip-forward/skip-backward buttons — all without relying on the browser's default `<audio>` controls.

![Preview](https://i.pinimg.com/736x/33/f3/a7/33f3a796fc3f26330f1c785279947768.jpg)

## Features

- 🎧 Custom play/pause button with animated icon swap (Font Awesome)
- ⏱ Custom-styled progress/seek bar synced to playback
- ⏮ ⏭ Skip backward / skip forward controls
- 📱 Responsive, centered layout
- 🎨 Dark, glassy UI with circular album art

## Tech Stack

- **HTML5** — structure and native `<audio>` element (hidden default controls)
- **CSS3** — custom styling for player, progress bar, and control buttons
- **JavaScript (vanilla)** — playback logic, progress sync, icon state handling
- **Font Awesome** (via Kit) — icons for playback controls

## Project Structure

```
.
├── index.html      # Markup and player logic
├── style.css       # Player styling and icon states
└── *.mp3           # Audio track (song file referenced by <source>)
```

## Getting Started

1. Clone or download this repository.
2. Make sure the audio file referenced in the `<source>` tag matches the actual file name in your project folder.
3. Open `index.html` in your browser — no build step or server required.

> **Note:** Some browsers restrict autoplay and certain media features when files are opened directly via `file://`. If you run into playback issues, try serving the folder with a simple local server (e.g. `npx serve` or the VS Code Live Server extension).

## How It Works

- The native `<audio controls>` UI is disabled; playback is fully controlled through JavaScript (`song.play()` / `song.pause()`) and a custom `<input type="range">` element synced every 500ms to `currentTime`.
- The play/pause icon toggles between `fa-play` and `fa-pause` by swapping CSS classes. Because Font Awesome's Kit script performs dynamic icon subsetting on page load, an icon added only via JavaScript after load may not render — this is handled with a workaround (see `style.css` / hidden icon technique) rather than a JS bug fix alone.
- Skip forward/backward buttons adjust `song.currentTime` by a fixed interval (e.g. ±10 seconds), clamped between `0` and `song.duration`.

## Customization

- **Skip interval:** change the seconds value inside the skip functions to adjust how far forward/backward each click moves.
- **Track/cover art:** update the `<source src="...">` and `.song-img` `src` attributes, plus the `<h1>` and `<p>` tags for title/artist.
- **Colors/theme:** all visual styling lives in `style.css` (`#06081d`, `#12163a`, `#252fbd` are the core palette values).

## Known Limitations

- Single-track player — no playlist or queue support.
- Skip forward/backward and play/pause icon behavior depend on JavaScript being fully loaded and wired to the corresponding button IDs; double-check `onclick` handlers are present when modifying the markup.

## License

This project is open for personal and educational use. Audio and image assets are for demonstration purposes only — replace them with content you have rights to use before publishing or distributing.
