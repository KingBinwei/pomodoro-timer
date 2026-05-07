# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-file Pomodoro timer app (`pomodoro.html`) — vanilla HTML/CSS/JS. No build step or server needed; open directly in a browser.

## Commands

- **Run the app**: Open `pomodoro.html` in a browser (no build required)
- **No test/lint infrastructure exists** — the project is a static HTML file

## Architecture

- **Single file**: `pomodoro.html` contains HTML structure, CSS styles, and JS logic in one file
- **State management**: A plain `state` object holds mode, seconds, timerId, and counters. No framework.
- **Timer**: `setInterval` at 1s interval via `tick()`. Timer cleared/reset via `stopTimer()` helper.
- **Persistence**: Settings (work/shortBreak/longBreak durations) saved to `localStorage` under key `pomodoro-settings`. Loaded on page init and hydrated into `<input>` elements.
- **Notifications**: Browser `Notification` API for session completion alerts.
- **Keyboard shortcuts**: Space (start/pause), R (reset). Ignored when `<input>` is focused.

## Git

- **Auto-push**: `.git/hooks/post-commit` automatically pushes to `origin master` after every commit
- **Remote**: `origin` → `KingBinwei/pomodoro-timer` on GitHub
- After making changes to the project, commit them and the hook handles the push

## Settings (`package.json`)

The `@anthropic-ai/sdk` dependency is not used by the HTML app and should not be removed unless confirmed unused.

## Frontend Design

This project follows the [SKILL.md](SKILL.md) (Anthropic Frontend Design) guidelines. Key principles:

- **Aesthetic direction**: Before coding, commit to a bold, intentional design direction. No generic "AI" aesthetics.
- **Typography**: Choose distinctive fonts. Never use Inter, Roboto, Arial, or system-ui as primary fonts.
- **Color**: CSS variables for consistency. Dominant colors with sharp accents.
- **Motion**: CSS animations for micro-interactions. Staggered reveals, scroll-triggering, hover states.
- **Layout**: Unexpected compositions — asymmetry, overlap, grid-breaking elements.
- **Visual details**: Gradient meshes, noise textures, geometric patterns, grain overlays.
- **Forbidden**: Purple gradients on white backgrounds, overused font families, predictable layouts.
