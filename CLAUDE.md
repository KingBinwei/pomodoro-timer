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
