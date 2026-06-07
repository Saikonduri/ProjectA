# checkpoint.md — ProjectA Login Page

## What exists
Single-file gamified login page (`index.html`) with a neon/cyberpunk aesthetic.

## UI & Design
- Dark background (`#0a0a0f`) with animated purple grid, floating color orbs, and floating particles
- Fonts: Orbitron (headings/labels), Inter (body)
- Color palette: neon purple `#bf00ff`, cyan `#00f5ff`, pink `#ff006e`, green `#39ff14`
- Glassmorphism card (backdrop-filter blur, semi-transparent border)
- Social login buttons: Google, Discord, GitHub (SVG icons, no real auth wired up)
- Stats strip at bottom: Players / Online / Max Level (static values: 2.4M / 8.2K / 99+)

## Gamification system (all client-side JS)
- XP bar at top of card, fills to 100 XP
- Achievement toast (top-right, slides in with spring easing, auto-dismisses after 3s)
- Floating "+XP" pop labels on XP gain
- XP events and unlock conditions:

| Key          | Points | Trigger                              |
|--------------|--------|--------------------------------------|
| `firstChar`  | 10     | First keystroke in username field    |
| `validEmail` | 20     | Username ≥ 3 chars                   |
| `strongPass` | 30     | Password strength score ≥ 3          |
| `rememberMe` | 10     | "Keep me logged in" checkbox checked |
| `signup`     | 5      | "Create one" footer link clicked     |
| `social`     | 15     | Any social login button clicked      |

- Konami code (↑↑↓↓←→←→BA) grants +50 XP bonus
- Each achievement fires only once per session (`shown` flag)

## Password strength scoring
Score increments for: length ≥ 6, length ≥ 10, special char present, uppercase + digit present.  
Labels: weak af / mid tbh / decent / built different

## Form submit behavior
Simulates 1.8s async delay, then validates (username ≥ 3, password ≥ 4). On success: fills XP to 100, shows "GG EZ" toast, turns button green. No real backend.

## What's not built yet
- Actual authentication / backend
- Sign-up page / flow
- Real social OAuth integration
- Mobile layout testing
- Password visibility toggle
- Forgot password link
