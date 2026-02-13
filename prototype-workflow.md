# Challey — Interactive Prototype Workflow

> **Purpose:** A complete, actionable guide for any UI/UX designer to build the Challey interactive prototype. This document covers every screen, every tap target, every transition, every emotional moment, and every edge case. Challey is not an app — it's a family experience. Build it that way.

---

## Table of Contents

1. [Philosophy & Design Principles](#1-philosophy--design-principles)
2. [Brand Identity](#2-brand-identity)
3. [User Roles](#3-user-roles)
4. [Screen Inventory](#4-screen-inventory)
5. [Navigation Architecture](#5-navigation-architecture)
6. [Flow 1: Onboarding — Create a Family](#6-flow-1-onboarding--create-a-family)
7. [Flow 2: Onboarding — Kid Joins Family](#7-flow-2-onboarding--kid-joins-family)
8. [Flow 3: Kid Chore Workflow](#8-flow-3-kid-chore-workflow)
9. [Flow 4: Kid Rewards & Cash-Out](#9-flow-4-kid-rewards--cash-out)
10. [Flow 5: Chore Swaps](#10-flow-5-chore-swaps)
11. [Flow 6: Shout-Outs & Kindness](#11-flow-6-shout-outs--kindness)
12. [Flow 7: Living Room (Family Social)](#12-flow-7-living-room-family-social)
13. [Flow 8: Leaderboard & Badges](#13-flow-8-leaderboard--badges)
14. [Flow 9: Parent Dashboard & Verification](#14-flow-9-parent-dashboard--verification)
15. [Flow 10: Parent Reward & Chore Management](#15-flow-10-parent-reward--chore-management)
16. [Flow 11: Parent Family Management & Settings](#16-flow-11-parent-family-management--settings)
17. [Flow 12: Companion Widget (Chal)](#17-flow-12-companion-widget-chal)
18. [Flow 13: Notifications](#18-flow-13-notifications)
19. [Celebrations & Emotional Design](#19-celebrations--emotional-design)
20. [State Machines](#20-state-machines)
21. [Empty States & Edge Cases](#21-empty-states--edge-cases)
22. [Asset Map](#22-asset-map)
23. [Interaction Patterns](#23-interaction-patterns)
24. [Accessibility Requirements](#24-accessibility-requirements)
25. [Prototype Build Checklist](#25-prototype-build-checklist)

---

## 1. Philosophy & Design Principles

### Challey Is a Family Experience

Challey was born from a 13-year-old named Maggie who said: *"I enjoy doing chores. But I have no way of reporting what I have done to my parents."* That statement defines everything we build. Challey is not a task manager. It is a **communication and recognition platform** that uses chores as the vehicle for family connection.

Every screen, every animation, every micro-interaction must reinforce one feeling: **this family is working together, and everyone is seen**.

### The Five Design Commandments

1. **Simple, Fast, Awesome** — Every core action completes in under 5 taps. No bloat. No friction. If a feature doesn't serve the family relationship, cut it.

2. **Recognition Over Transactions** — Points and rewards exist, but the real product is acknowledgment. A parent's emoji reaction on a chore matters more than the points. A sibling shout-out matters more than the leaderboard position.

3. **Teen-First, Not Childish** — Maggie is 13. The UI must respect teen autonomy. Navy and ocean blue palette. Clean typography. No baby colors, no cartoon clutter. Mature but warm.

4. **No Dead Ends** — Every screen has a clear next action. Every denial has a path forward. Every empty state has a call-to-action. The user is never stranded.

5. **Celebrate Everything** — Confetti on chore completion. Confetti on reward redemption. Confetti on shout-outs. Confetti on swaps. Every positive family moment gets a celebration. This is joy engineering.

### The Core Loop

```
Parent assigns chore → Kid completes chore → Kid uploads photo proof
    → Parent verifies → Points awarded → Kid redeems reward
        → Parent fulfills → Family celebrates in Living Room
```

Every feature in the app either supports this loop directly or enriches the family experience around it (swaps, shout-outs, badges, leaderboard, companion).

---

## 2. Brand Identity

### Color Palette — Ocean Theme (Default)

| Token | Hex | Usage |
|---|---|---|
| `--primary` | `#1B2A4A` | Navy blue. Headers, primary text, bottom nav active |
| `--secondary` | `#2E86AB` | Teal. Links, secondary buttons, info badges |
| `--accent` | `#F18F01` | Orange. CTAs, streak fire, highlights, active states |
| `--bg-light` | `#E8F4F8` | Light cyan. Page backgrounds |
| `--bg-card` | `#FFFFFF` | White. Card surfaces |
| `--text` | `#1B2A4A` | Primary text (matches primary) |
| `--text-secondary` | `#666666` | Gray. Captions, timestamps, helpers |
| `--border` | `#DDDDDD` | Light gray. Card borders, dividers |
| `--success` | `#2A9D8F` | Green. Approved states, positive deltas |
| `--warning` | `#F4A261` | Amber. Pending, approaching limits |
| `--danger` | `#E63946` | Red. Decline, redo, errors, logout |
| `--pink` | `#FF69B4` | Hot pink. Shout-outs, kindness features |
| `--purple` | `#8B5CF6` | Purple. Swap features |

### Alternative Themes (User-Selectable in Settings)

| Theme | Primary | Secondary | Accent |
|---|---|---|---|
| **Sunset** | `#2D1B69` | `#FF6B35` | `#FFD700` |
| **Forest** | `#1B3A2D` | `#4A8C6F` | `#F5A623` |
| **Midnight** | `#0D1117` | `#58A6FF` | `#39D353` |
| **Bubblegum** | `#8B1A4A` | `#FF69B4` | `#FFE066` |
| **Arctic** | `#2C3E50` | `#74B9FF` | `#FFFFFF` |

### Dark Mode Overrides

| Token | Light Value | Dark Value |
|---|---|---|
| `--bg-light` | `#E8F4F8` | `#1A1D23` |
| `--bg-card` | `#FFFFFF` | `#1E2A3A` |
| `--text` | `#1B2A4A` | `#E8F4F8` |
| `--text-secondary` | `#666666` | `#A0A0A0` |
| `--border` | `#DDDDDD` | `#333333` |

### Typography

| Element | Font | Weight | Size | Color |
|---|---|---|---|---|
| App Title (Splash) | Inter | 700 | 48px | `--primary` |
| Screen Header | Inter | 700 | 24px | `--primary` |
| Section Header | Inter | 600 | 18px | `--primary` |
| Card Title | Inter | 600 | 16px | `--primary` |
| Body | Inter | 400 | 14px | `--text` |
| Caption / Timestamp | Inter | 400 | 12px | `--text-secondary` |
| Button Label | Inter | 600 | 14px | White (on filled) |
| Badge / Tag | Inter | 700 | 10px | Varies |
| Points Display (Large) | Inter | 700 | 36px | `--accent` |

### Spacing Scale

| Token | Value | Usage |
|---|---|---|
| `--space-xs` | 4px | Icon internal padding |
| `--space-sm` | 8px | Tight spacing, inline elements |
| `--space-md` | 16px | Card padding, standard gaps |
| `--space-lg` | 24px | Section spacing |
| `--space-xl` | 32px | Major section breaks |
| `--space-2xl` | 48px | Page-level margins |

### Border Radius

| Element | Radius |
|---|---|
| Buttons | 8px |
| Cards | 12px |
| Modals | 16px |
| Badges / Pills | 24px (full pill) |
| Avatar / Icons | 50% (circle) |
| Photo frames | 8px |

### Shadows

| Level | Value |
|---|---|
| Card | `0 2px 8px rgba(27, 42, 74, 0.08)` |
| Card Hover/Active | `0 4px 16px rgba(27, 42, 74, 0.12)` |
| Modal / Overlay | `0 8px 32px rgba(27, 42, 74, 0.16)` |
| FAB | `0 4px 12px rgba(27, 42, 74, 0.2)` |
| Bottom Nav | `0 -2px 8px rgba(0, 0, 0, 0.06)` |

---

## 3. User Roles

### Family Admin (Parent Who Creates Family)

- **Auth:** Email/password or OAuth (Apple, Google, Facebook)
- **Max per family:** 1
- **Full control:** Everything a Parent can do, plus family code management, member deletion, points economy configuration, companion settings
- **Icon convention:** Crown or star indicator on avatar

### Parent / Guardian

- **Auth:** Email/password or OAuth (invited by Admin)
- **Max per family:** 9 (total 10 adults including admin)
- **Core actions:** Create/assign chores, verify completions, manage rewards, review swaps, boost shout-outs, give badges, fulfill redemptions, manage wishlists, post in Living Room

### Kid

- **Auth:** Family Code + Member Code + 4-digit PIN (no email, COPPA compliant)
- **Max per family:** 10
- **Age range:** 13-17 (designed for teens)
- **Core actions:** View/complete chores, upload photo proof, browse/redeem rewards, manage wishlist, initiate swaps, send shout-outs, view leaderboard, post in Living Room, customize theme

---

## 4. Screen Inventory

### Total: 75+ Screens Across 2 Roles

#### Onboarding & Auth (17 screens)

| # | Screen | File | Role |
|---|---|---|---|
| 1 | Splash | `screens/01-splash.svg` | All |
| 2 | Join or Create | `screens/02-join-family.svg` | All |
| 3 | Enter Family Code | `screens/03a-join-family-code.svg` | Kid |
| 4 | Set PIN | `screens/03b-kid-set-pin.svg` | Kid |
| 5 | Confirm PIN | `screens/03c-kid-confirm-pin.svg` | Kid |
| 6 | Enter PIN (Login) | `screens/03d-kid-enter-pin.svg` | Kid |
| 7 | Forgot PIN | `screens/03e-kid-forgot-pin.svg` | Kid |
| 8 | Family Preview | `screens/03f-join-family-preview.svg` | Kid |
| 9 | Setup Profile | `screens/03g-join-setup-profile.svg` | Kid |
| 10 | Create Family Auth | `screens/04a-create-family-auth.svg` | Parent |
| 11 | Manual Signup | `screens/04b-create-family-manual.svg` | Parent |
| 12 | Select Role | `screens/04c-create-family-role.svg` | Parent |
| 13 | Name Family | `screens/04d-create-family-name.svg` | Parent |
| 14 | Pick Family Pet | `screens/04e-pick-family-pet.svg` | Parent |
| 15 | Welcome Family | `screens/04f-welcome-family.svg` | Parent |
| 16 | Add Kids | `screens/05b-add-kids.svg` | Parent |
| 17 | Add Kids Success | `screens/05c-add-kids-success.svg` | Parent |

#### Parent Setup Wizard (3 screens)

| # | Screen | File | Role |
|---|---|---|---|
| 18 | Setup Chores | `screens/05d-setup-chores.svg` | Parent |
| 19 | Setup Rewards | `screens/05e-setup-rewards.svg` | Parent |
| 20 | Setup First Post | `screens/05f-setup-first-post.svg` | Parent |

#### Kid Core Experience (33 screens)

| # | Screen | Category |
|---|---|---|
| 21 | Kid Chores (List + Tabs) | Chores |
| 22 | Kid Chore Detail | Chores |
| 23 | Kid Chore Completion (Photo Upload) | Chores |
| 24 | Kid Rewards Shop | Rewards |
| 25 | Kid Reward Detail | Rewards |
| 26 | Kid Redeem Confirm | Rewards |
| 27 | Kid Wishlist | Rewards |
| 28 | Kid Add Wish | Rewards |
| 29 | Kid Cash-Out Request | Rewards |
| 30 | Kid Cash-Out Pending | Rewards |
| 31 | Kid Cash-Out Paid | Rewards |
| 32 | Kid Points Dashboard | Points |
| 33 | Kid Board (Leaderboard) | Board |
| 34 | Sibling Profile | Board |
| 35 | Kid Living Room | Social |
| 36 | Kid Settings | Settings |
| 37-49 | Swap Flow (13 screens) | Swaps |
| 50-54 | Shout-Out Flow (5 screens) | Kindness |

#### Parent Core Experience (16 screens)

| # | Screen | File |
|---|---|---|
| 55 | Parent Dashboard (Empty) | `screens/05a-parent-dashboard-empty.svg` |
| 56 | Parent Dashboard (Populated) | `screens/05g-parent-dashboard.svg` |
| 57 | Parent Verify (Swipe Cards) | `screens/06a-parent-verify.svg` |
| 58 | Parent Verify (No Photo) | `screens/06a2-parent-verify-nophoto.svg` |
| 59 | Parent Verify (Reject) | `screens/06a3-parent-verify-reject.svg` |
| 60 | Parent Rewards Catalog | `screens/06b-parent-rewards.svg` |
| 61 | Parent Create Reward | `screens/06c-parent-create-reward.svg` |
| 62 | Parent Create Chore | `screens/06d-parent-create-chore.svg` |
| 63 | Parent Living Room | `screens/06e-parent-living-room.svg` |
| 64 | Parent Family Management | `screens/06f-parent-family.svg` |
| 65 | Parent Invite Member | `screens/06f2-parent-invite-member.svg` |
| 66 | Parent Settings | `screens/06g-parent-settings.svg` |
| 67 | Parent Companion Config | `screens/06h-parent-companion-config.svg` |
| 68 | Parent Swap Review | `screens/06i-parent-swap-review.svg` |
| 69 | Parent Shout-Out Review | `screens/06j-parent-shoutout-review.svg` |
| 70 | Parent Wishlist Review | `screens/06k-parent-wishlist.svg` |
| 71 | Parent Give Badge | `screens/06l-parent-give-badge.svg` |

#### Overlays & Modals (4+)

| # | Screen | Type |
|---|---|---|
| 72 | Notifications Panel | `screens/06m-notifications-panel.svg` |
| 73 | Companion Intro Modal | Overlay |
| 74 | Year-End Recap (POST-MVP) | Full-screen overlay |
| 75 | Confetti / Celebration Overlay | Animation layer |

---

## 5. Navigation Architecture

### Kid Bottom Tab Bar (5 Tabs, Always Visible)

```
┌─────────┬─────────┬─────────┬─────────┬─────────┐
│  Chores │ Rewards │ Points  │  Board  │  Living  │
│  (home) │  (shop) │  (pts)  │ (rank)  │  Room    │
└─────────┴─────────┴─────────┴─────────┴─────────┘
```

| Tab | Icon | Active Color | Default Screen |
|---|---|---|---|
| Chores | Checkmark circle | `--accent` | Kid Chores List |
| Rewards | Gift box | `--accent` | Kid Rewards Shop |
| Points | Coin / Star | `--accent` | Kid Points Dashboard |
| Board | Trophy | `--accent` | Kid Leaderboard |
| Living Room | Home / Chat | `--accent` | Kid Living Room Feed |

**Rules:**
- Active tab: filled icon + `--accent` color + label
- Inactive tabs: outline icon + `--text-secondary` + label
- Tab bar has `--bg-card` background with top shadow
- Companion widget floats above the tab bar (bottom-right)
- Tab bar is hidden during onboarding flows

### Parent Bottom Tab Bar (5 Tabs)

```
┌──────────┬─────────┬─────────┬─────────┬─────────┐
│Dashboard │ Verify  │ Rewards │ Living  │ Family  │
│  (home)  │ (swipe) │ (mgmt)  │  Room   │ (mgmt)  │
└──────────┴─────────┴─────────┴─────────┴─────────┘
```

### Header Bar (Both Roles)

```
┌──────────────────────────────────────────┐
│  ← Back    Screen Title    ⚙️  🔔  💰    │
└──────────────────────────────────────────┘
```

| Element | Position | Action |
|---|---|---|
| Back arrow | Left | Navigate to previous screen (stack pop) |
| Screen title | Center | Non-interactive label |
| Settings gear | Right | Navigate to Settings screen |
| Notification bell | Right | Open Notifications Panel (overlay) |
| Points badge | Right (kid only) | Shows current balance, taps to Points Dashboard |

---

## 6. Flow 1: Onboarding — Create a Family

### Screens & Transitions

```
[01-splash] ──tap "Get Started"──▶ [02-join-family]
                                          │
                              ┌───────────┴───────────┐
                     tap "Join"                  tap "Create"
                         │                            │
                    (→ Flow 2)              [04a-create-family-auth]
                                                      │
                                          ┌───────────┴───────────┐
                                  tap OAuth btn              tap "Email"
                                     │                            │
                              [OAuth provider]         [04b-create-family-manual]
                                     │                            │
                                     └──────────┬─────────────────┘
                                                │
                                       [04c-create-family-role]
                                                │
                                     tap role (Dad/Mom/etc.)
                                                │
                                       [04d-create-family-name]
                                                │
                                         tap "Continue"
                                                │
                                       [04e-pick-family-pet]
                                                │
                                    tap pet + name it + "Continue"
                                                │
                                       [04f-welcome-family]
                                      (displays family code)
                                                │
                                         tap "Set Up"
                                                │
                                       [05b-add-kids]
                                                │
                                      add 1-10 kids + "Done"
                                                │
                                       [05c-add-kids-success]
                                    (shows member codes per kid)
                                                │
                                         tap "Next"
                                                │
                                       [05d-setup-chores]
                                     (preset chore selection)
                                                │
                                         tap "Next"
                                                │
                                       [05e-setup-rewards]
                                     (preset reward selection)
                                                │
                                         tap "Next"
                                                │
                                       [05f-setup-first-post]
                                     (write welcome message)
                                                │
                                         tap "Finish"
                                                │
                                       [05g-parent-dashboard]
                                        (populated, ready)
```

### Screen-by-Screen Details

#### 01 — Splash

- **Layout:** Centered vertically. Logo mark (checkmark circle) at 80px. "Challey" at 48px bold. Tagline "Chores. Points. Rewards." at 16px light.
- **Background:** `--bg-light` with subtle gradient
- **CTA:** "Get Started" button, full-width, `--accent` background, white text, 48px height, 8px radius
- **Animation:** Logo fades in (300ms), title slides up (400ms, 100ms delay), button fades in (400ms, 300ms delay)
- **Asset:** `splash/splash-screen.svg`

#### 02 — Join or Create Family

- **Layout:** Two large cards stacked vertically, equal height
- **Card 1 — "Join a Family":** Family tree icon, "I have a family code" subtitle. Taps to → Flow 2 (Kid Join)
- **Card 2 — "Create a Family":** Plus/home icon, "I'm starting a new family" subtitle. Taps to → 04a
- **Style:** Cards have `--bg-card` background, `--border` border, 12px radius, hover state lifts shadow
- **Asset:** `screens/02-join-family.svg`

#### 04a — Create Family Auth

- **Layout:** Header "Create Your Family", subtitle "Let's get started"
- **OAuth buttons (stacked, full-width, 48px height):**
  - "Continue with Apple" — black background, white Apple logo + text
  - "Continue with Google" — white background, Google G logo, dark text, border
  - "Continue with Facebook" — Facebook blue background, white F logo + text
- **Divider:** "or" with horizontal lines
- **Email button:** "Sign up with Email" — outline style, `--secondary` border
- **Transition:** OAuth → provider flow → 04c. Email → 04b.
- **Asset:** `screens/04a-create-family-auth.svg`

#### 04b — Manual Email Signup

- **Fields:** First Name, Last Name, Email, Password (all required, 44px height inputs)
- **Validation:** Real-time inline errors below fields. Password: 8+ chars.
- **CTA:** "Create Account" — `--accent`, full-width
- **Transition:** Success → 04c
- **Asset:** `screens/04b-create-family-manual.svg`

#### 04c — Select Parent Role

- **Header:** "What should the kids call you?"
- **Grid (2×2):** Four cards with large emoji + label:
  - 👨 Dad | 👩 Mom | 🧑 Guardian | 👤 Relative
- **Selection:** Tap highlights card with `--accent` border + checkmark
- **CTA:** "Continue" (enabled after selection)
- **Transition:** → 04d
- **Asset:** `screens/04c-create-family-role.svg`

#### 04d — Name the Family

- **Header:** "Name your family"
- **Input:** Large text field, placeholder "The Johnson Family"
- **Auto-preview:** Below input: "Your family code: JOHN13" (generated from name + random digits)
- **Helper text:** "Kids will use this code to join"
- **CTA:** "Continue"
- **Transition:** → 04e
- **Asset:** `screens/04d-create-family-name.svg`

#### 04e — Pick Family Pet

- **Header:** "Choose a family companion!"
- **Subtitle:** "This pet will encourage your kids along the way"
- **Grid (4×3):** 12 mascot options, each showing the mascot SVG + name below:

| Mascot | Asset | Default Name |
|---|---|---|
| Dog | `mascots/chal-dog.svg` | Buddy |
| Cat | `mascots/chal-cat.svg` | Whiskers |
| Octopus | `mascots/chal-octopus.svg` | Inky |
| Bunny | `mascots/chal-bunny.svg` | Hopper |
| Hamster | `mascots/chal-hamster.svg` | Nibbles |
| Parrot | `mascots/chal-parrot.svg` | Squawk |
| Turtle | `mascots/chal-turtle.svg` | Shelly |
| Fox | `mascots/chal-fox.svg` | Dash |
| Panda | `mascots/chal-panda.svg` | Bamboo |
| Penguin | `mascots/chal-penguin.svg` | Waddles |
| Lion | `mascots/chal-lion.svg` | Mane |
| Frog | `mascots/chal-frog.svg` | Ribbit |

- **Selection:** Tap highlights with `--accent` border + bounce animation
- **Name input:** "Name your pet" text field below grid (pre-filled with default)
- **CTA:** "Continue"
- **Transition:** → 04f
- **Asset:** `screens/04e-pick-family-pet.svg`, `mascots/*.svg`

#### 04f — Welcome Family

- **Celebration:** Confetti animation on load (see Section 19)
- **Header:** "Welcome, [Family Name]!" with 🎉
- **Family code display:** Large card with code (e.g., "JOHN13"), tap-to-copy icon
- **Member codes:** Admin code shown + "Share these with your kids" instruction
- **CTA:** "Let's Set Up" → 05b
- **Asset:** `screens/04f-welcome-family.svg`, `celebrations/family-created.svg`

#### 05b — Add Kids

- **Header:** "Add your kids"
- **Per-kid row:** Name input, Birthday picker, Age auto-calculated
- **"Add Another Kid" button:** outline, max 10
- **CTA:** "Done" → 05c
- **Asset:** `screens/05b-add-kids.svg`

#### 05c — Add Kids Success

- **Celebration:** Small confetti burst
- **Display:** Per-kid card showing name + generated member code (e.g., "MAG01")
- **Instruction:** "Share each kid's code. They'll use it with the family code to join."
- **CTA:** "Next — Set Up Chores" → 05d
- **Asset:** `screens/05c-add-kids-success.svg`

#### 05d — Setup Chores (Preset Selection)

- **Header:** "Quick-start some chores"
- **Categories (expandable cards):**
  - 🍳 Kitchen: Wash dishes, Wipe counters, Empty dishwasher, Take out trash
  - 🛏️ Bedroom: Make bed, Pick up clothes, Vacuum room, Organize desk
  - 🌿 Outdoor: Mow lawn, Water plants, Sweep patio, Pick up yard
  - 🛋️ Living Areas: Vacuum living room, Dust furniture, Clean bathroom
- **Interaction:** Toggle individual chores on/off. Pre-set point values shown.
- **CTA:** "Next" → 05e (or "Skip" link)
- **Asset:** `screens/05d-setup-chores.svg`

#### 05e — Setup Rewards (Preset Selection)

- **Categories:**
  - 📱 Screen Time: 30min gaming (30pts), 1hr TV (50pts), Movie night (80pts)
  - 🍦 Food & Treats: Pick dinner (60pts), Ice cream outing (40pts)
  - 💵 Cash: $1 (20pts), $5 (100pts), $10 (200pts)
- **Auto-calculated:** Points derived from dollar value × rate (default 20pts/$1)
- **CTA:** "Next" → 05f
- **Asset:** `screens/05e-setup-rewards.svg`

#### 05f — Setup First Post

- **Header:** "Write a welcome message"
- **Subtitle:** "This will be the first post in your family's Living Room"
- **Textarea:** Pre-filled with "Welcome to our family on Challey! Let's earn some points! 🎉"
- **CTA:** "Finish Setup" → Parent Dashboard
- **Asset:** `screens/05f-setup-first-post.svg`

---

## 7. Flow 2: Onboarding — Kid Joins Family

### Screens & Transitions

```
[01-splash] ──tap "Get Started"──▶ [02-join-family]
                                          │
                                  tap "Join a Family"
                                          │
                                   [03a-join-family-code]
                                  Enter Family Code + Member Code
                                          │
                                     tap "Join"
                                          │
                              ┌───────────┴───────────┐
                        New kid (no PIN)         Returning kid (has PIN)
                              │                            │
                     [03b-kid-set-pin]            [03d-kid-enter-pin]
                              │                            │
                     [03c-kid-confirm-pin]           validate PIN
                              │                            │
                     PINs match?                    correct?
                    ┌────┴────┐               ┌────┴────┐
                   Yes       No              Yes       No
                    │    "PINs don't          │    "Wrong PIN"
                    │     match" error        │     (5 tries max)
                    │                         │         │
                    │                         │    [03e-kid-forgot-pin]
                    │                         │
                    ▼                         ▼
              🎉 CONFETTI            Kid Chores Screen
                    │
            Kid Chores Screen
         + Companion Intro Modal
```

### Screen-by-Screen Details

#### 03a — Enter Family Code

- **Header:** "Join Your Family"
- **Field 1:** "Family Code" — text input, uppercase, auto-format (e.g., "JOHN13")
- **Field 2:** "Your Member Code" — text input (e.g., "MAG01")
- **Helper text:** "Ask your parent for these codes"
- **CTA:** "Join" — validates both codes against backend
- **Error states:** "Family not found", "Member code not recognized"
- **Asset:** `screens/03a-join-family-code.svg`

#### 03b — Set PIN

- **Header:** "Create Your PIN"
- **Subtitle:** "Choose 4 numbers you'll remember"
- **Display:** 4 dots (empty → filled as digits entered, with scale animation)
- **Input:** Numeric keypad (0-9 grid + backspace)
- **Behavior:** Auto-advances to 03c when 4th digit entered
- **Asset:** `screens/03b-kid-set-pin.svg`

#### 03c — Confirm PIN

- **Header:** "Confirm Your PIN"
- **Subtitle:** "Enter it one more time"
- **Same layout as 03b**
- **On match:** Confetti → Kid Chores + Companion Intro Modal
- **On mismatch:** Shake animation on dots, "PINs don't match — try again", clear both, return to 03b
- **Asset:** `screens/03c-kid-confirm-pin.svg`

#### 03d — Enter PIN (Returning Login)

- **Header:** "Welcome back, [Name]!"
- **Avatar:** Kid's profile image or default initial circle
- **Display:** 4 dots
- **Input:** Numeric keypad
- **On success:** Navigate to Kid Chores
- **On failure:** Shake dots, increment attempt counter (max 5)
- **On max failures:** Show "Too many attempts" → link to 03e
- **Asset:** `screens/03d-kid-enter-pin.svg`

#### 03e — Forgot PIN

- **Header:** "Forgot Your PIN?"
- **Body:** "No worries! Ask [Dad/Mom] to reset it in their settings."
- **CTA:** "Got It" → returns to 03d
- **Background action:** Notification sent to all parent/admin users
- **Asset:** `screens/03e-kid-forgot-pin.svg`

---

## 8. Flow 3: Kid Chore Workflow

### Main Chore Screen

**Layout components (top to bottom):**

1. **Header bar:** Settings gear (left), "My Chores" title (center), notification bell + points badge (right)
2. **Streak card:** 🔥 "X-Day Streak!" with orange gradient background (hidden if no streak)
3. **Birthday banner (conditional):** "🎂 Happy Birthday! Double points today!" with confetti sparkle
4. **Tab bar:** "To Do" | "In Progress" | "Done" — horizontal, scrollable
5. **Chore cards:** Stacked list per active tab
6. **Companion widget:** Bottom-right, above tab bar

**Chore card anatomy:**

```
┌─────────────────────────────────────────────┐
│  🍽️  Wash the Dishes              ⇄ (swap)  │
│  Due: Today                    20 pts ⭐     │
│  ┌──────────┐  ┌──────────┐                 │
│  │Started it│  │  Done!   │                 │
│  └──────────┘  └──────────┘                 │
└─────────────────────────────────────────────┘
```

| Element | Action |
|---|---|
| Card body tap | → Chore Detail screen |
| "Started it" button | Optional. Moves chore to "In Progress" tab. Button style: outline, `--secondary` |
| "Done!" button | → Chore Completion screen (photo upload). Button style: filled, `--accent` |
| ⇄ swap icon | → Swap Request flow (Section 10) |
| Points badge | Display only. `--accent` color |

### Chore Detail Screen

- **Back arrow** → return to Chore List
- **Chore emoji** at 48px centered
- **Chore name** at 24px bold
- **Description** body text
- **Due date** with calendar icon
- **Points value** large display
- **Assigned by** parent name
- **Redo feedback** (if status = REDO_REQUESTED): orange card with parent's note, icon
- **CTAs:**
  - "Mark Complete" → Chore Completion
  - "Request Swap" → Swap Flow

### Chore Completion Screen (Photo Upload)

- **Header:** "Almost done!"
- **Photo upload area:** Large dashed border rectangle, camera icon center, "Take a photo of your work" text
  - Tap → device camera / photo picker
  - After upload → preview thumbnail replaces dashed area, "Change Photo" link
- **Note textarea:** "Add a note (optional)" — max 200 chars
- **CTA:** "Submit for Verification" — `--accent`, full-width
  - Disabled until photo uploaded (photo is **MANDATORY**)
- **On submit:** Confetti celebration → toast "Submitted!" → navigate back to Chore List
- **Post-submit:** Chore moves to "Done" tab with "Pending" badge
- **Celebration asset:** `celebrations/chore-complete.svg`

### Redo Handling

When parent requests redo:
- Chore returns to "To Do" tab
- Card shows orange left border + redo icon
- Redo note from parent displayed in italic quote card
- Kid can resubmit (same photo flow)
- No limit on redo cycles

---

## 9. Flow 4: Kid Rewards & Cash-Out

### Rewards Shop

**Layout:**

1. **Header:** "Reward Shop" + points balance badge
2. **Wishlist shortcut:** "My Wishlist ([N])" link → Wishlist screen
3. **Reward cards (grid or list):**

```
┌─────────────────────────────────┐
│  🎮  30min Gaming                │
│  Play your favorite game         │
│                                  │
│  30 pts ($1.50)                  │
│  ┌──────────────────────────┐   │
│  │  ✓ You can get this!     │   │ (green if affordable)
│  │  × 15 pts away           │   │ (gray if not)
│  └──────────────────────────┘   │
│  [Add to Cart]                   │
└─────────────────────────────────┘
```

4. **Floating cart bar (when items added):**

```
┌─────────────────────────────────────────┐
│  🛒 2 items  •  80 pts    [Redeem All]  │
└─────────────────────────────────────────┘
```

- Cart bar slides up from bottom (above tab bar)
- "Redeem All" validates total ≤ balance

### Reward Detail (on card tap)

- Large emoji (80px)
- Name, description, point cost (36px), dollar equivalent
- Current balance displayed
- "Redeem Now" button (if affordable) or disabled state with "X pts away"
- Back arrow → shop

### Redeem Confirm

- Reward summary card
- "You'll spend: X pts"
- "Points remaining: Y pts"
- "[Dad] will be notified to fulfill this reward"
- "Confirm" button → **CONFETTI** → toast → navigate to Shop
- Points deducted immediately
- **Celebration asset:** `celebrations/reward-redeemed.svg`

### Wishlist

- List of kid's wishes with status badges (Approved ✅ / Pending ⏳)
- Each card: item name, description, price, occasion tag (Birthday/Christmas/Holiday/Anytime)
- "Add a Wish" FAB → Add Wish form
- **Empty state asset:** `empty-states/empty-wishlist.svg`

### Add Wish Form

- Fields: "What do you want?", "Why do you want it?", approximate price, link (optional)
- Occasion multi-select pills: Birthday, Christmas, Holiday, Anytime
- "Add to Wishlist" → success toast, navigate back

### Cash-Out Flow

**Step 1 — Request:**
- 💰 Money emoji at 56px
- "Cash Out Your Points" header
- Range slider: 20–200 pts, step 10
- Quick-select buttons: 40 pts / 100 pts / 200 pts
- Real-time dollar conversion: "= $X.XX"
- "Request Cash Out" → **CONFETTI** → Step 2

**Step 2 — Status Tracking (4-step progress):**

```
  ✅ Requested          (green circle, completed)
  ⏳ Waiting for Dad    (spinner, active)
  ○  Dad confirms paid  (gray, pending)
  ○  You confirm        (gray, pending)
```

Each step updates as parent acts:
- Parent marks paid → Step 3 activates: "Dad sent your cash!"
- Kid confirms receipt → Step 4: **CONFETTI** → Complete

**Points deducted at request time** (not on parent approval). If parent declines → points refunded.

---

## 10. Flow 5: Chore Swaps

### Swap Initiation (from Chore Card ⇄ icon or Chore Detail)

```
[Swap Request] → Choose type:
    ├── "Swap with Sibling" → [Select Sibling]
    │       → [Select Their Chore + Optional Incentive]
    │       → [Confirm & Send] → 🎉
    │
    └── "Request from Parent" → [Choose/Suggest Chore]
            → [Confirm & Send] → success screen
```

### Sibling Swap Detail

#### Select Sibling
- Sibling cards: avatar (40px), name, age, "X chores available"
- Tap → moves to chore selection

#### Select Chore + Incentive
- **Your chore card** (top, locked, grayed): shows what you're giving up
- **Sibling's chores** (selectable list): tap to select
- **"Sweeten the Deal"** section:
  - Toggle: "Offer bonus points"
  - Slider: 0–20 pts from own balance
  - Shows remaining balance after transfer
- CTA: "Send Swap Request"

#### Confirm
- Side-by-side comparison: "You give → You get" with arrow between
- Incentive line (if offered): "+X pts bonus"
- "Send to [Name]" → **CONFETTI** → success
- **Celebration asset:** `celebrations/swap-accepted.svg` (used on acceptance)

### Incoming Swap (Kid B receives)

- Notification + in-app card
- Shows: who's requesting, what they want, what they offer, any bonus points
- **Three buttons:**
  - ❌ Decline (neutral)
  - ↩️ Counter (purple outline)
  - ✅ Accept (green fill)

### Counter-Offer Flow
- Kid B proposes a different chore or a "favor" (text-only promise)
- Counter goes back to Kid A with same 3 options
- Loop continues until accept or decline

### Parent Swap (Kid → Parent)
- Kid picks own chore to trade
- Kid picks from unassigned chore pool OR writes a custom suggestion (name, description, points)
- Optional reason textarea
- Sent to parent for approve/decline

---

## 11. Flow 6: Shout-Outs & Kindness

### Send a Shout-Out

**This is the heart of Challey's family experience.** Design it to feel warm, not transactional.

```
[Select Sibling] → [Create Shout-Out] → [Preview & Confirm] → 🎉 → [Sent Success]
```

#### Select Sibling
- Header with pink/warm gradient: 💕 "Give a Shout-Out"
- "Celebrate something awesome your sibling did!"
- Sibling cards (same as swap select but with heart accents)

#### Create Shout-Out
- **Badge selection grid (2×3):**

| Badge | Icon | Asset |
|---|---|---|
| Amazing Sibling | ⭐ Star | `badges/amazing-sibling.svg` |
| Kind Heart | ❤️ Heart | `badges/kind-heart.svg` |
| Best Helper | 🤝 Handshake | `badges/best-helper.svg` |
| So Funny | 😂 Laughing | `badges/so-funny.svg` |
| Super Brave | 🦁 Lion | `badges/super-brave.svg` |
| Team Player | ⚡ Lightning | `badges/team-player.svg` |

- Tap badge → highlight with pink border + scale animation
- **"What did they do?"** textarea (encouraged but optional)
- **"Gift Points" section:**
  - Toggle on/off
  - Slider: 1–25 pts from own balance
  - Remaining balance shown

#### Preview & Confirm
- Preview card styled like a Living Room post:
  - Sender avatar + name
  - Badge icon + name
  - Quote of the message
  - Gifted points badge
- "Dad and Mom will also see this and can reward you both with extra points!"
- "Send Shout-Out" pink button → **CONFETTI** (pink-themed)

#### Sent Success
- Pink gradient background
- "Sent to [Dad] for review!" (shout-outs route through parents)
- "Dad can boost it with extra points for both of you!"
- "Back to Living Room" button

### Receive a Shout-Out

- Notification: "[Name] sent you a shout-out!"
- Screen shows:
  - Pink header gradient
  - Sender's avatar + name
  - Badge with animation (use animated SVG variant)
  - Message quote
  - Gifted points (with sparkle)
  - **Boost card (if parent boosted):** "Dad boosted this! +X pts" with parent's note
- "Thank You!" button → small confetti + toast
- "Give a Shout-Out Back" button (pink)

### Parent Shout-Out Review

- Parent sees pending shout-out
- **Boost section:**
  - 🚀 "Boost This Shout-Out"
  - "Reward both kids for being kind to each other"
  - Point selector chips: 5 / 10 / 15 / 25 pts per kid
  - Optional note textarea
  - Preview: "Both [Sender] and [Recipient] will each receive +X pts"
  - "Boost & Deliver" button → confetti
- "Skip — just deliver" outline button

---

## 12. Flow 7: Living Room (Family Social)

### Purpose

The Living Room is where the family story unfolds. It transforms chore tracking into a shared narrative. **Every family milestone lives here.**

### Post Types

| Type | Generated | Left Border | Badge Text | Content |
|---|---|---|---|---|
| **Parent Announcement** | Manual | None (pinned 📌) | PINNED | Text + optional photo |
| **Chore Completed** | Auto | `--success` green | CHORE DONE | Photo proof + chore name + points earned |
| **Shout-Out** | Auto | `--pink` | SHOUT-OUT | Badge + message + gifted points |
| **Streak Milestone** | Auto | `--accent` orange | MILESTONE | 🔥 streak count + celebration |
| **Reward Redeemed** | Auto | `--secondary` teal | REWARD | Reward emoji + name + points spent |
| **Photo Post** | Manual | None | None | Photo + caption |

### Post Card Anatomy

```
┌──────────────────────────────────────────────┐
│  📌 PINNED                                    │ (conditional)
│  👨 Dad  •  2 hours ago                       │
│                                               │
│  Welcome to our family on Challey! Let's      │
│  earn some points! 🎉                         │
│                                               │
│  ❤️ 3   💬 1   😂 😍 🔥                       │
└──────────────────────────────────────────────┘
```

| Element | Interaction |
|---|---|
| Author avatar + name | Non-interactive |
| Timestamp | Non-interactive |
| Post body | Non-interactive |
| Photo (if present) | Tap → full-screen lightbox |
| Reaction bar | Tap emoji to toggle reaction |
| 💬 Comment count | Tap → expand comments inline |
| Pin icon (parent only) | Tap → toggle pin status |

### Living Room Feed Rules

- Pinned posts always at top
- Remaining posts reverse-chronological
- Auto-generated posts include a type badge (colored pill)
- Camera FAB (floating action button) bottom-right for new manual posts
- **Empty state:** `empty-states/empty-feed.svg` — "No posts yet! Complete a chore to get started."

### Streak Milestones That Auto-Post

| Streak | Message |
|---|---|
| 3 days | "🔥 [Name] is on a 3-day streak!" |
| 7 days | "🔥 [Name] hit a 7-day streak! On fire!" |
| 14 days | "🔥 14 days! [Name] is unstoppable!" |
| 30 days | "🔥 30 days! [Name] is a chore champion!" |
| 60 days | "🔥 60-day streak! Legendary!" |
| 100 days | "🔥 100 DAYS! [Name] is a Challey legend!" |
| 365 days | "🔥 ONE YEAR! [Name] completed a full year of streaks!" |

---

## 13. Flow 8: Leaderboard & Badges

### Board Screen

**Layout (top to bottom):**

1. **"My Swag" section:** Kid's avatar + collected badges displayed as pill icons
2. **"Spotlight" card:** "This Week's MVP: [Name]" with 👑 crown emoji, gradient background
3. **"Family Rankings" list:**

```
  🥇  [Avatar] Maggie    🔥 12-day streak    187 pts
  🥈  [Avatar] Jake      🔥 5-day streak     142 pts
  🥉  [Avatar] Emma                            98 pts
```

- Current kid's row highlighted with light `--accent` background
- Rankings based on points earned this week (Mon–Sun)
- Tiebreaker: longest streak → most chores completed
- Tap sibling row → Sibling Profile

4. **"Give a Shout-Out" banner:** Pink background, heart emoji, taps to → Shout-Out flow

### Sibling Profile

- Large avatar (80px), name, age
- Badges section (horizontal scroll of earned badges)
- Stat grid (2×2): Day Streak | Points This Month | Chores Completed | Shout-Outs
- "Give a Shout-Out" button (pink)
- Back arrow → Board

---

## 14. Flow 9: Parent Dashboard & Verification

### Parent Dashboard

The dashboard is the parent's command center. Everything flows from here.

**Layout (scrollable, top to bottom):**

1. **Header:** "Family Dashboard" / "[Family Name]"
2. **Quick stats row (3 cards):** Active Chores | Pending Verifications | Completed This Week
3. **Birthday prep card (conditional, 7 days before birthday):**
   - "🎂 [Name]'s Birthday in X days!"
   - Quick actions: Remove chores / Double points / View wishlist / Birthday badge
4. **Pending Verifications section:**
   - Card per pending chore (kid avatar, chore name, time since submission)
   - "View All" → Verify screen
5. **Swap Requests section (purple cards):**
   - Tap → Swap Review screen
6. **Rewards to Fulfill:**
   - Cash-outs (green): "[Name] wants $X" + "Hand Cash" button
   - Redemptions (yellow if overdue): "[Name] redeemed [Reward]" + "Mark as Given"
7. **Sibling Kindness section:**
   - Pending shout-out summaries
   - "Review & Boost" button → Shout-Out Review
8. **Kids Overview:**
   - Per-kid cards: avatar, name, age, current points, active chores count, streak, progress bar
9. **Action buttons:**
   - "Create New Chore" (primary, full-width)
   - "Wishlists" + "Give Badge" (side by side)
10. **"+" FAB** (bottom-right) → quick-add chore modal

### Verification Screen (The Swipe Experience)

**This is the signature parent interaction. Make it delightful.**

- **Header:** "Verify Chores" / "[N] waiting for review"
- **Card stack (Tinder-style swipe):**
  - Top card is active, cards behind peek slightly
  - Card content:
    - Kid avatar + name (top left)
    - Chore name (bold)
    - Time since submission (e.g., "2 hours ago")
    - Points value badge
    - **Photo proof** (large, takes ~60% of card)
    - Kid's note (italic quote card below photo)
    - **Emoji reaction bar:** 👏 🔥 ⭐ 💪 ❤️ (toggleable, multi-select)

- **Swipe interactions:**
  - **Swipe RIGHT** → Green "APPROVED ✓" overlay flashes → card flies off right → points credited → auto-post to Living Room
  - **Swipe LEFT** → Red "REDO ✗" overlay flashes → redo comment bar appears at bottom
  - **"Approve All" button** (top-right) → batch approve all pending

- **Redo comment bar:**
  - Input: "What needs fixing?" with Send button
  - On send: card flies off left, chore returns to kid's To Do with parent's note

- **All caught up state:**
  - ✅ Large checkmark
  - "All caught up! No more chores to review."
  - "Back to Dashboard" button
  - **Empty state asset:** `empty-states/no-pending.svg`

- **Assets:** `screens/06a-parent-verify.svg`, `screens/06a2-parent-verify-nophoto.svg`, `screens/06a3-parent-verify-reject.svg`

---

## 15. Flow 10: Parent Reward & Chore Management

### Rewards Catalog

- List of all rewards with emoji, name, description, point cost, dollar equivalent
- "Edit" link per card → inline edit or edit modal
- "Add New Reward" button → Create Reward form
- **Asset:** `screens/06b-parent-rewards.svg`

### Create Reward Form

| Field | Type | Validation |
|---|---|---|
| Reward Name | Text | Required, max 50 chars |
| Description | Textarea | Optional, max 200 chars |
| Dollar Value | Number with $ prefix | Required, min $0.25 |
| Points (auto-calc) | Display only | = Dollar × rate (default 20pts/$1) |
| Icon/Emoji | Text, max 2 chars | Required |
| Available To | Multi-select | "All Kids" or individual names |

- **CTA:** "Create Reward" → success toast → navigate to catalog
- **Asset:** `screens/06c-parent-create-reward.svg`

### Create Chore Form

| Field | Type | Validation |
|---|---|---|
| Chore Name | Text | Required, max 50 chars |
| Description | Textarea | Optional, max 200 chars |
| Assign To | Multi-select chips | Kid names + "All Kids" option |
| Point Value | Number | Required, min 1 |
| Due Date | Date picker | Optional |
| Frequency | Select | One-time / Daily / Weekly / Monthly |

- **CTA:** "Create Chore" → success toast → navigate to dashboard
- **Asset:** `screens/06d-parent-create-chore.svg`

---

## 16. Flow 11: Parent Family Management & Settings

### Family Management Screen

- **Adults section:** Cards with avatar, name, role, ADMIN badge (if applicable)
- **Kids section:** Cards with avatar, name + age, points balance, active chore count
- **"Invite Family Member"** button → Invite screen
- **"Family Settings"** button → Settings
- **Asset:** `screens/06f-parent-family.svg`

### Parent Settings (Complete)

| Section | Contents |
|---|---|
| **Family Code** | Gradient card displaying code + copy button |
| **My Profile** | Avatar, name, email, role (editable) |
| **My Kids** | Per-kid rows: avatar, name, member code, "Reset PIN" action, "Add Kid" button |
| **Family Pet** | Link to companion config with pet emoji preview |
| **Points Economy** | Slider 5–50 pts/$1 (step 5, default 20). Presets: Easy (10), Standard (20), Hard (40). Live preview of example calculation |
| **Appearance** | Dark mode toggle + color theme grid (6 options) |
| **Notifications** | Toggles: chore completions (on), reward redemptions (on), cash-out requests (on), weekly summaries (off) |
| **Management** | Links: Manage Rewards, Family Members, Invite Parent |
| **Account** | Change Password, Update Email, Log Out (red text) |
| **Footer** | "Challey v3.0.0 / Made with care for families" |

- **Asset:** `screens/06g-parent-settings.svg`

### Companion Config

- **Message type toggles:**
  - Motivation & Encouragement (default on)
  - Chore Tips & Productivity (default on)
  - Fun Facts & Learning (default on)
  - Kindness Reminders (default on)
  - Financial Literacy (off, POST-MVP badge)
- **Suggestion mode radio:** Encouraging (default) / Coaching / Educational
- **Custom messages:** List with "Add" button for family-specific messages
- **AI Suggestions card (dimmed):** "Coming soon" POST-MVP teaser
- **Asset:** `screens/06h-parent-companion-config.svg`

---

## 17. Flow 12: Companion Widget (Chal)

### Visual Design

- **Position:** Fixed, bottom-right corner, 16px above bottom tab bar, 16px from right edge
- **Size:** Pet emoji body 48px, speech bubble 200px max width
- **Z-index:** Above page content, below modals

### Anatomy

```
                    ┌───────────────────────┐
                    │ Great job starting    ✕│
                    │ your chores today!     │
                    │          ~ Buddy  🐕   │
                    └───────────┬───────────┘
                                │ (speech bubble arrow)
                            ┌──────┐
                            │ 🐕  │ (bouncing)
                            └──────┘
                              ● (pulse dot, conditional)
```

### Behavior Rules

| Trigger | Behavior | Chance | Delay |
|---|---|---|---|
| Screen navigation | Show contextual message | 30% | 1500ms |
| Idle on screen | Pulse indicator dot | 100% | Every 12s |
| Body tap | Show context menu (4 options) | 100% | Immediate |
| Confetti event | Celebration mode (bounce + message) | 100% | Alongside confetti |
| Speech bubble ✕ | Dismiss bubble, pet returns to idle | 100% | Immediate |

### Context Menu (on body tap)

1. "Encourage me" → motivation message
2. "Give me a tip" → productivity tip
3. "Fun fact" → random fun fact
4. "Hide Chal" → hides widget until re-enabled in Settings

### Contextual Messages (by Screen)

| Screen | Sample Messages |
|---|---|
| Chores (empty) | "No chores right now! Enjoy your free time!" |
| Chores (items) | "Let's knock these out! You've got this!" |
| Rewards | "Ooh, saving up for something good?" |
| Points | "Look at all those points! You're crushing it!" |
| Board | "Every point counts! Keep climbing!" |
| Living Room | "Your family is proud of you!" |
| Verification (parent) | "Swipe right to make their day!" |

### First-Visit Modal (Companion Intro)

- Trigger: First time kid reaches Chores screen
- Semi-transparent backdrop
- Centered card: Pet emoji (64px), "Meet [PetName]!", description of what Chal does
- "Hey [PetName]! Let's go!" button → dismiss, show widget with welcome bubble

---

## 18. Flow 13: Notifications

### Notification Panel

- **Trigger:** Tap bell icon in header
- **Type:** Overlay panel (slides in from right or drops down)
- **Header:** "Notifications" + close button (✕)
- **List (scrollable):** Newest first

### Notification Types

| Type | Icon Color | Example Text | Tap Action |
|---|---|---|---|
| New chore assigned | `--secondary` teal | "Dad assigned: Wash Dishes (20 pts)" | → Chore Detail |
| Chore approved | `--success` green | "Dad approved your chore! +20 pts 👏🔥" | → Chores Done tab |
| Redo requested | `--danger` red | "Dad wants you to redo: Wash Dishes" | → Chore Detail |
| Swap received | `--purple` | "[Name] wants to swap with you!" | → Incoming Swap |
| Swap accepted | `--success` green | "[Name] accepted your swap!" | → Chores |
| Shout-out received | `--pink` | "[Name] sent you a shout-out! 💕" | → Shout-Out Received |
| Badge received | `--accent` | "Dad gave you: Super Star! ⭐" | → Board |
| Cash-out update | `--success` green | "Dad sent your cash! Confirm receipt." | → Cash-Out Status |
| Streak reminder | `--accent` orange | "Don't break your streak! Complete a chore today 🔥" | → Chores |

### Actionable Notifications (colored backgrounds)

- **Yellow:** Reward fulfillment needed (parent)
- **Purple:** Swap request pending (both roles)
- **Pink:** Shout-out to review/receive (both roles)

- **Asset:** `screens/06m-notifications-panel.svg`

---

## 19. Celebrations & Emotional Design

### Confetti System

Every positive family moment triggers a celebration. This is non-negotiable.

| Event | Confetti Style | Duration | Additional |
|---|---|---|---|
| Family created | Full-screen burst, multi-color | 3s | Welcome message |
| Kid joins family | Full-screen burst | 2s | Companion intro follows |
| Chore submitted | Medium burst, bottom-up | 2s | Toast: "Submitted!" |
| Chore approved | Full-screen, gold sparkles | 2.5s | Points +X animation |
| Reward redeemed | Full-screen burst | 2.5s | Toast: "Reward incoming!" |
| Shout-out sent | Pink-themed burst | 2s | Toast: "Sent to Dad!" |
| Shout-out received + thanked | Small pink burst | 1.5s | Toast: "Thank you!" |
| Swap accepted | Purple-themed burst | 2s | Toast: "Swapped!" |
| Cash-out confirmed | Gold coin burst | 2.5s | Toast: "All done!" |
| Badge awarded | Star burst | 2s | Badge animation |
| Streak milestone | Fire-themed burst | 2s | Auto-post to Living Room |

### Celebration SVG Assets

| Event | Static | Animated |
|---|---|---|
| Chore complete | `celebrations/chore-complete.svg` | `celebrations/animated/chore-complete.svg` |
| Family created | `celebrations/family-created.svg` | `celebrations/animated/family-created.svg` |
| Reward redeemed | `celebrations/reward-redeemed.svg` | `celebrations/animated/reward-redeemed.svg` |
| Shout-out sent | `celebrations/shoutout-sent.svg` | `celebrations/animated/shoutout-sent.svg` |
| Swap accepted | `celebrations/swap-accepted.svg` | `celebrations/animated/swap-accepted.svg` |

### Toast Messages

- Position: Top-center, slides down
- Duration: 2.5s auto-dismiss
- Style: Rounded pill, `--bg-card` background, shadow, icon + text
- Animation: Slide in (300ms ease-out), fade out (300ms)

### Birthday Experience

| Trigger | Action |
|---|---|
| 7 days before | Birthday prep card on parent dashboard |
| Day of (kid login) | Birthday banner on chore screen with 🎂 |
| Day of (system) | All chores award double points |
| Day of (system) | "Birthday Pass: Skip 1 chore free" coupon |
| Day of (system) | Birthday badge auto-awarded |
| Day of (siblings) | Prompted to send birthday shout-outs |

---

## 20. State Machines

### Chore State Machine

```
                    ┌──────────┐
                    │ ASSIGNED │
                    └────┬─────┘
                         │ kid taps "Started it" (optional)
                         ▼
                   ┌──────────────┐
                   │ IN_PROGRESS  │ (skippable if kid taps "Done!" directly)
                   └────┬─────────┘
                        │ kid taps "Done!" + uploads photo + submits
                        ▼
              ┌─────────────────────┐
              │ AWAITING_VERIFICATION│
              └────────┬────────────┘
                 ┌─────┴──────┐
                 │            │
          parent approves   parent requests redo
                 │            │
                 ▼            ▼
           ┌──────────┐  ┌───────────────┐
           │ APPROVED  │  │ REDO_REQUESTED│
           └──────────┘  └───────┬───────┘
                                 │ kid resubmits
                                 ▼
                       (back to AWAITING_VERIFICATION)
```

### Cash-Out State Machine

```
  ┌───────────┐
  │ REQUESTED │ (points deducted)
  └─────┬─────┘
        │ parent sees request
        ▼
  ┌──────────────┐
  │ PARENT_REVIEW│
  └────┬────┬────┘
       │    │
   approve  decline
       │    │
       ▼    ▼
  ┌──────┐ ┌───────────┐
  │ PAID │ │ CANCELLED │ (points refunded)
  └──┬───┘ └───────────┘
     │ kid confirms receipt
     ▼
  ┌───────────┐
  │ COMPLETED │
  └───────────┘
```

### Swap State Machine

```
  ┌───────────┐
  │ PROPOSED  │
  └─────┬─────┘
        │ recipient sees request
        ▼
  ┌──────────────┐
  │   PENDING    │
  └──┬───┬───┬───┘
     │   │   │
  accept │  decline
     │   │   │
     │ counter│
     │   │   │
     ▼   ▼   ▼
  ┌──┐ ┌──┐ ┌──┐
  │✓ │ │↩ │ │✗ │
  └──┘ └──┘ └──┘
   │     │     │
   │  back to  │
   │ PROPOSED  │
   │ (reversed)│
   │           │
   ▼           ▼
COMPLETED   DECLINED
(chores swap,
 parent notified)
```

### Shout-Out State Machine

```
  ┌────────┐
  │ CREATED│ (kid sends)
  └───┬────┘
      │ routes to parent
      ▼
  ┌──────────────┐
  │ PARENT_REVIEW│
  └───┬──────┬───┘
      │      │
    boost  skip
      │      │
      ▼      ▼
  ┌────────────┐
  │ DELIVERED  │ (to recipient)
  └─────┬──────┘
        │ recipient taps "Thank You!"
        ▼
  ┌───────────┐
  │ COMPLETED │
  └───────────┘
```

---

## 21. Empty States & Edge Cases

### Empty State Screens

| Context | Asset | Headline | Body | CTA |
|---|---|---|---|---|
| No chores assigned | `empty-states/no-chores.svg` | "No chores right now!" | "Enjoy your free time. Dad will assign some soon." | None |
| No rewards available | `empty-states/no-rewards.svg` | "No rewards yet!" | "Ask Dad to add some rewards to the shop." | None |
| No activity in points | `empty-states/no-activity.svg` | "No activity yet" | "Complete chores to start earning points!" | "Go to Chores" |
| Empty Living Room | `empty-states/empty-feed.svg` | "Nothing here yet!" | "Complete a chore to get the first post!" | "Go to Chores" |
| Empty wishlist | `empty-states/empty-wishlist.svg` | "Your wishlist is empty" | "Add things you'd love to earn!" | "Add a Wish" |
| No pending verifications | `empty-states/no-pending.svg` | "All caught up!" | "No chores waiting for review." | "Back to Dashboard" |

### Edge Cases

| Scenario | Behavior |
|---|---|
| Kid has 0 points, tries to redeem | Button disabled, shows "X pts away" in gray |
| Kid tries cash-out below minimum (20 pts) | Slider starts at 20, can't go lower |
| Kid has insufficient points for swap incentive | Slider max capped at current balance |
| Parent declines cash-out | Points refunded, status → CANCELLED, toast notification |
| Two kids swap simultaneously for same chore | First accepted wins, second gets "This chore is no longer available" |
| Streak break | No celebration, streak counter resets, no penalty |
| PIN lockout (5 failed attempts) | Lock screen, "Too many attempts", link to Forgot PIN |
| PINs don't match on setup | Shake animation, error text, clear both fields, return to Set PIN |
| No photo uploaded on chore completion | "Submit" button stays disabled (photo is mandatory) |
| Points rate changes | All existing reward point costs auto-recalculate, existing balances unchanged |
| Family has only 1 kid | Swap "with sibling" option hidden, shout-out option hidden |
| Kid is only family member online | Leaderboard shows all kids regardless of online status |

---

## 22. Asset Map

### Directory Structure

```
assets/
├── badges/                    # Parent-awarded badge icons
│   ├── amazing-sibling.svg
│   ├── best-helper.svg
│   ├── kind-heart.svg
│   ├── so-funny.svg
│   ├── super-brave.svg
│   ├── team-player.svg
│   └── animated/             # Animated variants (for award moments)
│       ├── amazing-sibling.svg
│       ├── best-helper.svg
│       ├── kind-heart.svg
│       ├── so-funny.svg
│       ├── super-brave.svg
│       └── team-player.svg
│
├── celebrations/              # Success moment visuals
│   ├── chore-complete.svg
│   ├── family-created.svg
│   ├── reward-redeemed.svg
│   ├── shoutout-sent.svg
│   ├── swap-accepted.svg
│   └── animated/
│       ├── chore-complete.svg
│       ├── family-created.svg
│       ├── reward-redeemed.svg
│       ├── shoutout-sent.svg
│       └── swap-accepted.svg
│
├── mascots/                   # Companion pet options (12)
│   ├── chal-bunny.svg         ├── chal-cat.svg
│   ├── chal-dog.svg           ├── chal-fox.svg
│   ├── chal-frog.svg          ├── chal-hamster.svg
│   ├── chal-lion.svg          ├── chal-octopus.svg
│   ├── chal-panda.svg         ├── chal-parrot.svg
│   ├── chal-penguin.svg       ├── chal-turtle.svg
│   └── animated/              # Bouncing/idle animations
│       └── (same 12 files)
│
├── empty-states/              # Zero-content placeholder illustrations
│   ├── empty-feed.svg
│   ├── empty-wishlist.svg
│   ├── no-activity.svg
│   ├── no-chores.svg
│   ├── no-pending.svg
│   └── no-rewards.svg
│
├── components/                # Reusable UI element references
│   ├── buttons.svg
│   ├── cards.svg
│   └── navigation.svg
│
├── icons/                     # System icons
│   ├── app-icon.svg
│   ├── app-icon-android-adaptive-bg.svg
│   ├── app-icon-android-adaptive-fg.svg
│   ├── favicon.svg
│   └── family-tree.png
│
├── logo/                      # Brand mark variations
│   ├── challey-logo-full.svg
│   ├── challey-logo-stacked.svg
│   ├── challey-logo-white.svg
│   ├── challey-mark.svg
│   └── challey-mark-light.svg
│
├── onboarding/                # First-time experience illustrations
│   ├── family-ready.svg
│   ├── join-or-create.svg
│   ├── pet-selection.svg
│   ├── pin-setup.svg
│   └── welcome-hero.svg
│
├── screens/                   # Full screen wireframe mockups
│   ├── 01-splash.svg  ...  06m-notifications-panel.svg
│   └── preview.html          # Browser preview of all screens
│
├── splash/                    # App launch screens
│   ├── splash-screen.svg
│   └── splash-screen-android.svg
│
├── store/                     # App store marketing assets
│   ├── feature-graphic.svg
│   ├── promo-banner.svg
│   └── screenshot-1-chores.svg ... screenshot-5-parent.svg
│
└── gemini-designs/            # AI-generated design explorations
    ├── badges/ + badges-v2/
    ├── logo/ (concept variations)
    ├── mascots/ (animated alternates)
    └── brand-showcase.html
```

---

## 23. Interaction Patterns

### Touch Gestures

| Gesture | Context | Action |
|---|---|---|
| **Tap** | Buttons, cards, tabs | Primary selection |
| **Swipe Right** | Parent verification card | Approve chore |
| **Swipe Left** | Parent verification card | Request redo |
| **Long Press** | Living Room post (parent) | Pin/unpin option |
| **Pull Down** | Any list view | Refresh content |
| **Scroll** | All screens | Vertical scroll (no horizontal scroll except tab bars) |
| **Pinch Zoom** | Photo proof (lightbox) | Zoom in/out on photo |

### Animations

| Animation | Duration | Easing | Usage |
|---|---|---|---|
| Page transition | 300ms | ease-in-out | Screen-to-screen navigation |
| Card press | 100ms | ease-out | Scale to 0.98 on touch start |
| Button press | 150ms | ease-out | Scale to 0.95 + darken 10% |
| Tab switch | 200ms | ease-out | Underline slides, content fades |
| Modal appear | 300ms | ease-out | Fade backdrop + slide up content |
| Modal dismiss | 200ms | ease-in | Reverse of appear |
| Toast in | 300ms | ease-out | Slide down from top |
| Toast out | 300ms | ease-in | Fade out |
| Confetti | 2000-3000ms | linear | Particle system, gravity fall |
| PIN dot fill | 150ms | ease-out | Scale from 0 to 1 |
| PIN shake (error) | 400ms | ease-in-out | Horizontal shake 3 cycles |
| Companion bounce | 600ms | ease-in-out | Vertical bounce, infinite idle |
| Companion bubble | 300ms | ease-out | Slide up + fade in |
| Swipe card fly-off | 300ms | ease-in | Translate + rotate off-screen |
| Points counter | 500ms | ease-out | Count up animation (+X pts) |
| Badge award | 800ms | spring | Scale from 0 → 1.1 → 1.0 |

### Haptic Feedback (Mobile)

| Event | Haptic Type |
|---|---|
| Button tap | Light impact |
| Swipe approve/reject | Medium impact |
| Confetti trigger | Success notification |
| Error (wrong PIN) | Error notification |
| Points earned | Success notification |

---

## 24. Accessibility Requirements

| Requirement | Implementation |
|---|---|
| **Color contrast** | All text ≥ 4.5:1 ratio against background (WCAG AA) |
| **Touch targets** | Minimum 44×44px for all interactive elements |
| **Screen reader** | All images have alt text; all buttons have aria-labels |
| **Focus management** | Visible focus rings on keyboard navigation |
| **Reduced motion** | Respect `prefers-reduced-motion`: disable confetti particles, use fade instead of slide transitions, stop companion bounce |
| **Font scaling** | Support up to 200% text zoom without layout break |
| **Keyboard nav** | All flows completable via keyboard (desktop) |
| **Error identification** | Errors announced by screen reader + visual indicator + text description |

---

## 25. Prototype Build Checklist

Use this checklist to track build progress. Each item represents a buildable, testable unit.

### Phase 1: Foundation
- [ ] Set up HTML/CSS framework with design tokens (colors, typography, spacing)
- [ ] Build bottom tab bar component (kid + parent variants)
- [ ] Build header bar component (back arrow, title, settings, bell, points badge)
- [ ] Build card component (base style, interactive state)
- [ ] Build button component (primary, secondary, outline, danger, disabled)
- [ ] Build modal/overlay component
- [ ] Build toast notification component
- [ ] Build confetti celebration system
- [ ] Implement theme switching (6 themes + dark mode)
- [ ] Implement role switcher (kid ↔ parent toggle for demo)

### Phase 2: Onboarding
- [ ] 01 Splash screen
- [ ] 02 Join or Create selection
- [ ] 03a-03g Kid join flow (code entry, PIN setup, PIN login, forgot PIN)
- [ ] 04a-04f Parent create flow (auth, signup, role, name, pet, welcome)
- [ ] 05b-05c Add kids flow
- [ ] 05d-05f Setup wizard (chores, rewards, first post)
- [ ] Companion intro modal

### Phase 3: Kid Core
- [ ] Kid Chores screen (list + tabs + streak card + birthday banner)
- [ ] Kid Chore Detail screen
- [ ] Kid Chore Completion (photo upload + mandatory photo gate)
- [ ] Kid Rewards Shop (grid + cart bar)
- [ ] Kid Reward Detail + Redeem Confirm
- [ ] Kid Wishlist + Add Wish form
- [ ] Kid Cash-Out flow (request + 4-step status)
- [ ] Kid Points Dashboard
- [ ] Kid Board (leaderboard + MVP spotlight + sibling profile)
- [ ] Kid Living Room (feed with all post types)
- [ ] Kid Settings (theme, dark mode, notifications, companion toggle)

### Phase 4: Kid Social
- [ ] Swap flow — sibling (select, pick chore, incentive, confirm, sent)
- [ ] Swap flow — parent (select/suggest, confirm, sent)
- [ ] Swap flow — incoming (receive, accept/decline/counter)
- [ ] Shout-out flow — send (select sibling, pick badge, write note, gift points, confirm)
- [ ] Shout-out flow — receive (view, thank you, boost display)

### Phase 5: Parent Core
- [ ] Parent Dashboard (populated with all sections)
- [ ] Parent Dashboard (empty state)
- [ ] Parent Verify (swipe card stack + approve/redo + emoji reactions)
- [ ] Parent Rewards Catalog + Create Reward form
- [ ] Parent Create Chore form
- [ ] Parent Living Room (feed + pin + create post)
- [ ] Parent Family Management + Invite Member
- [ ] Parent Settings (all sections)
- [ ] Parent Companion Config

### Phase 6: Parent Workflows
- [ ] Parent Swap Review (kid-to-sibling + kid-to-parent)
- [ ] Parent Shout-Out Review (view + boost + deliver)
- [ ] Parent Wishlist Review (approve/decline + add as reward)
- [ ] Parent Give Badge (select kids, choose badge, reason, bonus points)
- [ ] Notifications panel

### Phase 7: Polish
- [ ] Wire all navigation links (every tap target → correct destination)
- [ ] Add all empty states with correct assets
- [ ] Add companion widget with contextual messages
- [ ] Add all confetti triggers with correct celebration assets
- [ ] Add all toast messages
- [ ] Test complete flows end-to-end:
  - [ ] Parent creates family → adds kids → sets up chores/rewards
  - [ ] Kid joins → completes chore → parent verifies → points awarded
  - [ ] Kid redeems reward → parent fulfills
  - [ ] Kid initiates swap → sibling accepts → parent notified
  - [ ] Kid sends shout-out → parent boosts → sibling receives
  - [ ] Kid cashes out → parent pays → kid confirms
- [ ] Verify all role-specific elements show/hide correctly
- [ ] Test theme switching across all screens
- [ ] Test dark mode across all screens
- [ ] Verify accessibility (contrast, touch targets, screen reader labels)

---

## Appendix: File Reference

| Document | Path |
|---|---|
| This workflow | `C:\Projects\challey-demo\prototype-workflow.md` |
| Discovery document | `C:\Projects\pmo\challey\docs\discovery.md` |
| Technical specification | `C:\Projects\pmo\challey\docs\specification.md` |
| Future versions roadmap | `C:\Projects\pmo\challey\docs\future-versions.md` |
| Interactive prototype v1 | `C:\Projects\challey-demo\index.html` |
| Interactive prototype v2 | `C:\Projects\challey-demo\index-v2.html` |
| Asset preview gallery | `C:\Projects\challey-demo\assets\preview.html` |
| Screen mockup preview | `C:\Projects\challey-demo\assets\screens\preview.html` |
| Mascot preview | `C:\Projects\challey-demo\assets\mascots\preview.html` |
| Badge animated preview | `C:\Projects\challey-demo\assets\badges\animated\preview.html` |
| Celebration preview | `C:\Projects\challey-demo\assets\celebrations\animated\preview.html` |
| Project state | `C:\Projects\pmo\challey\state.json` |

---

*This document is the single source of truth for building the Challey interactive prototype. Every screen, every tap, every transition, every celebration is documented here. When in doubt, return to the Five Design Commandments: Simple. Fast. Awesome. Recognition over transactions. Celebrate everything.*

*Challey is not an app. It's the moment a kid finishes their chores and their dad says "I see you." Build that.*
