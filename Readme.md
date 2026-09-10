# To-Do List App (Vanilla JS)

A single-file, dependency-free to-do list app. Part of my [365 Days of
Coding](#) challenge — built to be genuinely usable, not just a checkbox
demo.

**[Live demo](#)** — replace with your GitHub Pages link after deploying.

## Features

- Add, edit (double-click a task), complete, and delete tasks
- Filter by All / Active / Completed — persists across refreshes
- "Clear completed" bulk action
- Duplicate-task guard (case-insensitive)
- Data persists in `localStorage` — survives refresh and closing the tab
- Keyboard support: `Enter` to add/save, `Esc` to cancel an edit
- Entrance/exit animations, with `prefers-reduced-motion` respected
- Accessible: semantic HTML, `aria-live` regions, labeled controls
- Mobile-friendly layout

## Architecture

Everything lives in one `todo.html` (HTML + CSS + JS) for easy hosting
and reading in one pass. The JS follows a simple one-directional data
flow:

```
tasks[] (source of truth)
   → addTask / toggleTask / deleteTask / editTask / clearCompleted
   → saveTasks() (localStorage)
   → render() (rebuilds the DOM from tasks[] + currentFilter)
```

The task list uses **event delegation** — one click listener on the
`<ul>` handles every row, so newly rendered items never need listeners
re-attached.

## Running locally

No build step. Just open `todo.html` in a browser, or serve the
folder with any static server:

```bash
npx serve .
```

## Possible next steps

- Drag-to-reorder tasks
- Due dates / priority levels
- Sync across devices (would need a backend)

## Tech

HTML, CSS, JavaScript — no frameworks, no build tools.