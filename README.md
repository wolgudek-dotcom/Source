# International Quiz Overlay

A web-based quiz application with real-time Firebase sync supporting multiple views for judges, projectors, and OBS streaming.

## Features

- **Judge View**: Control questions, scores, and toggle visibility
- **Projector View**: Display questions fullscreen for the audience
- **OBS Overlay View**: Transparent overlay for streaming with team scores and current question
- **Multi-language Support**: CSV-based questions with left/right language pairs
- **Real-time Sync**: Firebase-based synchronization across computers
- **Responsive Design**: Adaptive text sizing for different resolutions

## Setup

### Firebase Configuration
Update `FIREBASE_CONFIG` in `overlay.html` with your Firebase credentials.

### Usage

1. Open in browser: `file:///path/to/overlay.html`
2. Select view with URL parameter:
   - `?view=judge` - Judge control panel (default)
   - `?view=projector` - Fullscreen projector display
   - `?view=overlay` - OBS transparent overlay
   - `?view=scoreboard` - Scoreboard-only view

3. Load CSV with format:
   - Columns: `[Question #, Language 1 Question, Language 1 Answer, Language 2 Question, Language 2 Answer, ...]`
   - OR with headers: `Language 1 Question`, `Language 1 Answer`, etc.

4. Enter room ID to enable Firebase sync across machines

## CSV Format Example

```
#,English Question,English Answer,Polski Question,Polski Answer
1,What is 2+2?,4,Ile to 2+2?,4
2,Capital of France?,Paris,Stolica Francji?,Paryż
```

## Features

- Auto-adjusting text size with invisible resizing (no blinking)
- Double line breaks for emphasis (muted prefix + bold main text in judge view)
- Language dividers in overlay view
- Team scoring system
- Toggle answer visibility
- Blank/unblank questions for audience
- Scoreboard swapping
