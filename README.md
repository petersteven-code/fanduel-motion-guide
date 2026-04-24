# FanDuel Motion Guide

A comprehensive motion design system for the FanDuel sportsbook app. Defines the animation language across all major screens and components — from the curve vocabulary to real screen walkthroughs with exact timing specs and Reanimated-ready code.

## What's inside

**8 app screens** with annotated animation breakdowns:
- Lobby — staggered load-in sequence
- Game Detail — shared axis navigation
- Bet Slip — 3-act placement choreography
- Live Betting — real-time odds flash system
- Win State — celebration sequence
- Parlay Builder — leg-add choreography and boost unlock
- My Bets — pending/win/loss state transitions
- Search — idle → focused → results state machine

**Components** — Buttons, Odds Pills, Tab Bar, Bottom Sheet, Toast

**The 6 named curves** — FanDuel's motion vocabulary, each with a sports metaphor and Reanimated token

| Curve | Type | Feel |
|---|---|---|
| `fd.snap` 🏈 | Spring s:500 d:38 | Zero-latency, tactile |
| `fd.kick` ⚡ | bezier(0,0,0.06,1) 340ms | Explosive enter |
| `fd.drive` 🏃 | bezier(0.4,0,0.1,1) 320ms | Screen-to-screen |
| `fd.release` 🏀 | bezier(0.34,1.45,0.64,1) 440ms | Slight overshoot |
| `fd.crowd` 🏆 | bezier(0.34,1.8,0.64,1) 520ms | Peak moments only |
| `fd.rebound` ⚾ | Spring s:220 d:7 | Elastic, oscillating |

## Using the tokens

```typescript
import { fd } from './motionTokens';

// Productive — UI entering the screen
withTiming(opacity, { duration: 340, easing: Easing.bezier(0, 0, 0.06, 1) }); // fd.kick

// Expressive — celebration, unlock, win state
withTiming(scale, { duration: 520, easing: Easing.bezier(0.34, 1.8, 0.64, 1) }); // fd.crowd

// Snap — buttons, toggles, instant feedback
withSpring(scale, { stiffness: 500, damping: 38 }); // fd.snap
```

## Two-mode framework

**Productive (90% of the app)** — fast, functional, gets out of the way. Use `fd.snap`, `fd.kick`, `fd.drive`.

**Expressive (peak moments only)** — theatrical, earned. Use `fd.release`, `fd.crowd`, `fd.rebound`. Reserved for: win states, bet confirmation, boost unlocks, parlay celebrations.

## Viewing the guide

Open `index.html` in any browser, or visit the GitHub Pages URL if enabled.
