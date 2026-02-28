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
   - `?view=judge` - Judge control panel
   - `?view=projector` - Fullscreen projector display (default if no `view` provided)
   - `?view=overlay` - OBS transparent overlay
   - `?view=scoreboard` - Scoreboard-only view

3. Select room with URL parameter on any view:
   - `?room=1` or `?roomId=1`
   - Example projector URL: `overlay.html?view=projector&room=finals`
   - Example overlay URL: `overlay.html?view=overlay&room=finals`
   - If no room is provided, all views default to room `1`.
   - Room `1` is always open (no judge password lock) so it can be used as a safe starting room.
   - Room names are normalized to lowercase (`Practice` and `practice` connect to the same room).
   - Sync happens only within the exact same room name (for example, `quiz` syncs only with `quiz`, not with `1`).

4. Load CSV with format:
   - Columns: `[Question #, Language 1 Question, Language 1 Answer, Language 2 Question, Language 2 Answer, ...]`
   - OR with headers: `Language 1 Question`, `Language 1 Answer`, etc.

5. Enter room ID in judge setup (or use URL room param) to choose which Firebase room to sync across machines.

6. Projector text sizing:
   - In Judge Setup, use `Text -` / `Text +` under `Projector Text Size`.
   - This affects projector question text only.
   - Projector text also scales up automatically on higher-resolution displays.

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
