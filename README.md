## Name: Faridat Suleiman
## Jazzmin.jsx
## Description: TicketApp — React (CDN, single-file)

This is the React implementation delivered as a single HTML file using CDN scripts (React, ReactDOM, Babel). No build step is required — you can open `index.html` directly in a browser or serve it via any static server.

## Quick Start
- Double-click `react/index.html` to open in your default browser.
  

## What’s Included
- Landing page with wavy hero, decorative circles, features section
- Auth (Login/Signup) with validation and toasts
- Protected routes (Dashboard, Tickets) using localStorage session key `ticketapp_session`
- Dashboard stats (total, open, resolved)
- Full Ticket CRUD stored in `ticketapp_tickets`
- Responsive, accessible UI consistent with Vue and Twig versions

## File Structure
```
react/
  index.html  # All CSS + JS inline (via <style> and <script type="text/babel">)
```

## Routes (hash-based)
- `/` Landing
- `/auth/login` Login
- `/auth/signup` Signup
- `/dashboard` Dashboard (protected)
- `/tickets` Ticket Management (protected)

If you visit a protected route without a valid session, you’ll be redirected to `/auth/login` and see a toast: “Your session has expired — please log in again.”

## Authentication
- Storage key: `ticketapp_session`, JSON with `{ token, user }`
- Login/Signup accept any valid email and a password of at least 6 characters
- Logout clears the session and returns to the Landing page

## Tickets Data
- Storage key: `ticketapp_tickets`
- Ticket shape: `{ id, title, status, description }`
- Status must be one of `open | in_progress | closed`

## Validation Rules
- Required: `title`, `status`
- Allowed `status`: `open`, `in_progress`, `closed`
- `description` length ≤ 1000
- Inline error messages appear under fields, and toasts provide user feedback

## Error Handling
- Invalid inputs → inline error + toast
- Unauthorized access → redirect + toast
- Use clear messages such as:
  - “Your session has expired — please log in again.”
  - “Failed to load tickets. Please retry.” (reserved for future network scenarios)

## Design & Accessibility
- Max width 1440px centered
- Wavy SVG hero with overlapping circles
- Cards for stats and tickets with rounded corners and shadows
- Status colors:
  - open → green
  - in_progress → amber
  - closed → gray
- Semantic HTML, visible focus outlines, sufficient contrast, ARIA for toasts and errors

## Test Credentials
- Any new email/password that passes validation will sign up and log you in
- Example: user@example.com / Passw0rd!

## Known Notes
- Data persists per browser via localStorage; clear it to reset
- Babel in-browser is slower than a built bundle (acceptable for this demo)

## Troubleshooting
- If routing behaves oddly on file://, use a local static server (recommended)
- Clear `ticketapp_session` and `ticketapp_tickets` from localStorage if state becomes inconsistent
- Try a modern browser (Chromium, Firefox, Safari) if styles look off
