# 🧩 Prompt Design — AWS-PartyRock-Fitness-Recommender

This document explains the prompt engineering behind each of the 8 outputs in this app. Since PartyRock apps are powered by natural language instructions, the prompt IS the logic — there is no code.

---

## What is Prompt Engineering?

Prompt engineering is the practice of crafting clear, specific instructions for an AI model to produce useful, consistent outputs. Good prompts answer:

- **Who** is the AI acting as? (role/persona)
- **What** should it do with the user's input?
- **How** should it format the response?
- **What** should it avoid?

This app has **6 inputs** and **8 outputs**. Each output has its own prompt — and later outputs read from earlier ones, creating a connected, coherent experience.

---

## The 6 User Inputs

| Input | Type | Options |
|---|---|---|
| Energy Level | Slider | Exhausted / Low / Good / Moderate / Peak |
| Available Time | Select | 15 / 30 / 45 / 60 minutes |
| Available Equipment | Select | None / Basic home / Home furniture / Full home gym / Commercial gym / Outdoor space |
| Fitness Level | Select | Beginner / Intermediate / Advanced |
| Primary Goal | Select | Get moving / Build strength / Lose weight / Feel better |
| Dietary Considerations | Open text | e.g. halal, vegetarian, allergies |

These inputs feed into every prompt. Changing any one of them meaningfully changes the outputs.

---

## Output 1: 🏋️ Your Movement Guide

**What it generates:**
A complete structured workout — warm-up, main circuit, cool-down — with exercise names, sets/reps or duration, and energy-level modifications.

**Prompt design decisions:**
- **Role:** "You are an adaptive fitness coach" — sets a consistent, knowledgeable persona
- **All 5 workout inputs referenced:** energy level, time, equipment, fitness level, and goal each shape the plan
- **Structured output format:** Warm-Up → Main Circuit → Cool-Down, with timing and rep counts, keeps output scannable and immediately usable
- **Modification section:** The prompt explicitly instructs the AI to include low-energy fallbacks (e.g., "skip to cool-down if dizzy", "do 1 round instead of 2")
- **Guardrail:** When energy is low, the prompt instructs the AI not to generate high-intensity or demanding workouts regardless of the stated goal

**Example of prompt logic:**
> "If the user's energy is Exhausted or Low, prioritize gentle activation over intensity. Include explicit modifications so the user can scale down further if needed."

---

## Output 2: 🖼️ Movement Visual

**What it generates:**
An AI-generated image that visually represents the workout style and energy level.

**Prompt design decisions:**
- Reads from the Movement Guide output and energy level input
- Conditional visual tone: soft and calm imagery for low energy, active and dynamic for peak energy
- The prompt describes the *feeling* of the image, not just the subject — e.g., "peaceful home movement" vs "energetic gym session"

---

## Output 3: 🎵 Workout Playlist

**What it generates:**
A phased music playlist with specific song recommendations, BPM ranges, rationale for each track, and setup instructions for Spotify, Apple Music, and YouTube Music.

**Prompt design decisions:**
- Reads from both the Movement Guide output AND the energy level input
- **BPM logic built into the prompt:** warm-up (90–100 BPM) → main circuit (100–128 BPM) → cool-down (60–85 BPM). The AI follows this structure consistently because it is explicitly defined
- **Platform instructions included:** The prompt asks the AI to provide search terms and step-by-step playlist setup for 3 platforms — this required very specific output formatting instructions
- **Tone-matching:** Low energy → familiar, gentle, uplifting tracks. Peak energy → high-tempo, motivating tracks. The prompt maps energy level to music character explicitly
- **Why this is non-trivial:** A vague prompt like "suggest workout music" produces a flat, unphased list with no BPM logic, no rationale, and no setup guidance. Specificity in the prompt is what produces a genuinely useful output

---

## Output 4: 🥗 Your Fuel Guide

**What it generates:**
Pre- and post-workout meal options with specific ingredients, portion sizes, prep times, a do/don't list, hydration guidance, and a quick shopping list — all calibrated to the workout intensity and energy level.

**Prompt design decisions:**
- **Portion scaling:** The prompt instructs the AI to scale calorie guidance to workout intensity (e.g., 150–200 cal pre-workout for gentle sessions, more for high-intensity ones)
- **Dietary considerations as a hard constraint:** The open-text dietary input is passed directly into the prompt. In a halal example, the AI flags halal certification on chicken and yogurt, and avoids non-halal options entirely. A prompt that ignores this input would produce useless or harmful recommendations
- **Structured pre/post split:** The prompt explicitly requires separate pre-workout and post-workout sections, each with multiple options at different prep times, so users can choose based on what they have available
- **Do/Don't guardrails:** Instructing the AI to include explicit "avoid" guidance (e.g., no heavy fried food post-workout) adds practical value that a basic meal suggestion prompt would miss

---

## Output 5: 🍽️ Meal Inspiration Image

**What it generates:**
A clean, visually appealing AI-generated food image based on the Fuel Guide output.

**Prompt design decisions:**
- Reads from the Fuel Guide output, not directly from user inputs
- Prompted to produce a "clean, Instagram-worthy, focused" food image — aesthetic direction is part of the prompt
- Style is calibrated to the meal recommendations (e.g., light fruit and nuts for low energy, fuller recovery meals for intense sessions)

---

## Output 6: 🧘 Your Mindset Boost

**What it generates:**
A short, personalized motivational message that acknowledges where the user is emotionally and energetically, followed by a relevant quote.

**Prompt design decisions:**
- Reads energy level and goal inputs
- **Tone instruction is explicit:** The prompt specifies warm, honest, and non-toxic-positivity. On low-energy days, the AI is instructed to validate rest and gentleness — not push "hustle harder" messaging
- **Two-part structure:** The prompt requires (1) a personal message that mirrors the user's state, then (2) a relevant motivational quote. This structure is enforced in the prompt, not left to the AI to decide
- **What to avoid:** The prompt explicitly discourages generic, high-energy cheerleading when the user signals exhaustion

---

## Output 7: 🌅 Mindset Image

**What it generates:**
An AI-generated motivational image with visual tone matched to the user's energy level.

**Prompt design decisions:**
- Uses explicit conditional logic in the prompt:
  - Exhausted / Low energy → soft, calming colors, peaceful imagery (e.g., gentle morning light, nature)
  - Good / Moderate → balanced, steady progress imagery
  - Peak → dynamic, vibrant, energetic imagery
- This if/then structure is written directly into the prompt — the AI reliably follows it because the conditions are clearly defined

---

## Output 8: 💬 Personal Coach Chat

**What it generates:**
An open-ended conversational AI coach the user can ask anything — about their workout, nutrition, motivation, or how to adapt the plan.

**Prompt design decisions:**
- **System prompt carries full context:** The coach is initialized with the user's energy level, goal, fitness level, and the outputs already generated — so it responds as if it already knows the user's session
- **Tone adapts to energy input:** A user who selected "Exhausted" gets a gentler, more supportive coach. A "Peak" user gets an energizing, push-harder tone. This is set in the system prompt
- **Scope guardrail:** The coach is instructed to stay relevant to fitness, nutrition, and mindset — and reference the personalized plan already created rather than giving generic advice

---

## How the Widgets Connect

```
User Inputs
(energy slider, time, equipment, fitness level, goal, dietary needs)
        │
        ├──▶ [1] Movement Guide
        │           │
        │           ├──▶ [2] Movement Visual (reads workout + energy)
        │           ├──▶ [3] Playlist (reads workout structure + energy)
        │           ├──▶ [4] Fuel Guide (reads energy + workout intensity)
        │           │           │
        │           │           └──▶ [5] Meal Image (reads fuel guide output)
        │           │
        │           └──▶ [6] Mindset Boost (reads energy + goal)
        │                       │
        │                       └──▶ [7] Mindset Image (reads energy level)
        │
        └──▶ [8] Coach Chat (reads ALL inputs + ALL outputs for full context)
```

This chain is what makes the app feel like one coherent experience rather than 8 separate AI responses.

---

## Iteration Process

**Version 1 — Single output**
Only generated a workout. Output was generic and didn't vary meaningfully with energy level.
Problem: Not enough inputs, no downstream features.

**Version 2 — More inputs, better structure**
Added time, equipment, fitness level, and goal. Workout output became specific and usable.

**Version 3 — Nutrition, playlist, mindset added**
Each new widget required its own prompt, tested independently, then checked for consistency with the workout output.

**Version 4 — Images and coach chat**
Image prompts required conditional tone logic. The coach chat required a system prompt that summarized all prior outputs as context for the conversation.

---

## Key Lessons Learned

| Lesson | What it means in practice |
|---|---|
| **Multi-widget = multi-prompt** | Each output needs its own carefully written instructions |
| **Chaining outputs** | Later prompts can read earlier outputs — this is what creates coherence |
| **Conditional logic works** | "If X, then Y" instructions in prompts are reliably followed |
| **Dietary input changes everything** | Ignoring a dietary constraint makes nutrition output useless or harmful |
| **Specificity beats vagueness** | "Phased playlist with BPM ranges and platform setup" produces far better results than "suggest music" |
| **Tone must be set per feature** | The playlist, mindset boost, and coach chat each needed different tone instructions |

---

## What I'd Build Next

- **Sleep quality input** — adjust recovery guidance and workout intensity based on how well the user slept
- **Progress tracking** — allow users to log sessions and see patterns over time
- **Weekly planner** — generate a full week of sessions based on goals and schedule
- **Shareable session card** — a visual summary of the plan the user could save or post

