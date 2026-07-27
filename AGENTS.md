# CHAPITO Development Guide

## Project Overview

CHAPITO is a Sales Intelligence Dashboard for a CPG distribution company.

The application is currently built as a single-page dashboard.

Main application:

- index.html

Admin interface:

- admin.html

---

## General Rules

Always preserve existing functionality unless explicitly requested.

Never remove features without asking.

Maintain responsive behavior.

Keep the UI consistent with the current design language.

Prefer improving existing components instead of replacing them.

---

## JavaScript

Use modern vanilla JavaScript.

Avoid unnecessary external libraries.

Always destroy and recreate Chart.js charts correctly.

Avoid memory leaks.

Keep code readable and modular.

---

## HTML

Maintain semantic HTML.

Avoid duplicate IDs.

Keep accessibility in mind.

---

## CSS

Maintain current visual style.

Use existing spacing and typography.

Do not introduce random colors.

---

## Dashboard Rules

Executive Scorecard

Portfolio

Customers

Sales Team

Opportunities

Compare

Canceladas

must continue working after every change.

---

## Git

Before finishing:

- check for JavaScript errors
- verify charts render correctly
- verify filters still work
- verify no console errors

Never commit automatically unless requested.

Never push automatically unless requested.

---

## Responses

Explain briefly what changed.

List modified files.

Mention any assumptions.