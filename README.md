# Todo Item Card — Frontend Wizards Stage 1a

An advanced, interactive, and fully accessible Todo Task Card. Built with semantic HTML5, plain CSS, and vanilla JavaScript. No frameworks, no dependencies — one file.

---

## Live Demo

> [Insert your live GitHub Pages URL here]

---

## What changed from Stage 0

| Feature | Stage 0 | Stage 1a |
|---|---|---|
| Edit mode | Dummy button | Full inline edit form with save/cancel |
| Status | Display only | Interactive segmented control (Pending / In Progress / Done) |
| Priority indicator | Badge only | Colored left border + dot + badge, all in sync |
| Description | Always visible | Collapsible with expand/collapse toggle |
| Overdue | Red text | Red badge + red card border accent |
| Time updates | Every 60s | Every 30s, granular (hr / min / days) |
| Done state | Strike-through | Timer stops, shows "Completed" |
| State snapshot | None | Cancel restores previous values |
| Focus management | Basic | Edit opens to first field; close returns to Edit button |

---

## Features

- All Stage 0 `data-testid` attributes preserved
- All Stage 1a `data-testid` attributes added
- Edit form: title, description, priority, due date — save updates card live
- Cancel restores the exact previous state via snapshot
- Status segmented control stays in sync with the checkbox at all times
- Priority changes the left border color, dot color, and badge color simultaneously
- Expand/collapse on description with `aria-expanded` and `aria-controls`
- Overdue indicator appears automatically when past due date
- Time remaining stops when status is set to Done
- Timer updates every 30 seconds
- Fully keyboard navigable: Tab → Checkbox → Status buttons → Expand → Edit → Delete
- Responsive from 320px to 1200px

---

## data-testid Reference

### Stage 0 (all preserved)

| Element | data-testid |
|---|---|
| Card root | `test-todo-card` |
| Task title | `test-todo-title` |
| Description | `test-todo-description` |
| Priority badge | `test-todo-priority` |
| Due date | `test-todo-due-date` |
| Time remaining | `test-todo-time-remaining` |
| Status display | `test-todo-status` |
| Checkbox | `test-todo-complete-toggle` |
| Tags list | `test-todo-tags` |
| Work tag | `test-todo-tag-work` |
| Urgent tag | `test-todo-tag-urgent` |
| Edit button | `test-todo-edit-button` |
| Delete button | `test-todo-delete-button` |

### Stage 1a (new)

| Element | data-testid |
|---|---|
| Priority dot indicator | `test-todo-priority-indicator` |
| Overdue badge | `test-todo-overdue-indicator` |
| Status segmented control | `test-todo-status-control` |
| Expand/collapse toggle | `test-todo-expand-toggle` |
| Collapsible container | `test-todo-collapsible-section` |
| Edit form container | `test-todo-edit-form` |
| Edit title input | `test-todo-edit-title-input` |
| Edit description textarea | `test-todo-edit-description-input` |
| Edit priority select | `test-todo-edit-priority-select` |
| Edit due date input | `test-todo-edit-due-date-input` |
| Save button | `test-todo-save-button` |
| Cancel button | `test-todo-cancel-button` |

---

## Design decisions

- **Segmented control for status** — chosen over a dropdown for faster switching and clearer visual feedback; each state has a distinct background color
- **Left border as priority indicator** — a persistent color-coded border communicates priority at a glance without taking up extra space
- **Snapshot for cancel** — on Edit open, state is cloned; Cancel restores it, preventing partial edits from leaking
- **CSS line-clamp for collapse** — native CSS truncation; JS only toggles the class
- **Timer stops on Done** — prevents confusing "Overdue" messages on completed tasks

---

## Known limitations

- Focus trap inside the edit form is not implemented (noted as optional bonus in spec)
- Tags are hard-coded; dynamic tag management is not part of Stage 1a
- Delete button shows a browser alert — no confirmation modal

---

## Accessibility notes

- All form fields have `<label for="">` associations
- Status control uses `role="group"` + `aria-labelledby` + `aria-pressed` on each button
- Expand toggle uses `aria-expanded` + `aria-controls` pointing to the description element
- Overdue badge uses `role="alert"` for immediate screen reader announcement
- Time remaining uses `aria-live="polite"` + `aria-atomic="true"`
- Focus returns to Edit button after save or cancel
- All interactive elements have visible focus-visible outlines

---

## Project structure

```
/
├── todo-card.html   # Complete component — markup, styles, script
└── README.md        # This file
```
