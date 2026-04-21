# 🧩 Prompt Design — aws-partyrock-fitness-recommender

This document explains the prompt engineering behind EnerFit. Since PartyRock apps are powered by natural language instructions (prompts), the prompt IS the code.

---

## What is Prompt Engineering?

Prompt engineering is the practice of crafting clear, specific instructions for an AI model to produce useful, consistent outputs. It's a skill — the same way you'd write a clear brief for a human, you write a clear prompt for an AI.

Good prompts answer:
- **Who** is the AI acting as? (role/persona)
- **What** should it do with the user's input?
- **How** should it format or tone the response?
- **What** should it avoid?

---

## This App's Core Prompt (Concept)

The prompt I wrote for EnerFit follows this structure:

```
You are a friendly, knowledgeable fitness coach. 
The user will describe their current energy level in their own words.

Based on their energy level, recommend:
1. A type of workout (e.g., HIIT, yoga, strength training, walking)
2. A suggested duration (e.g., 20 minutes, 45 minutes)
3. A brief reason why this workout suits their current state
4. One motivational tip to get started

Keep your tone warm, encouraging, and realistic. 
Do not push intense workouts if the user seems tired or low energy.
Format the response in a clear, easy-to-read way.
```

---

## Why This Prompt Works

| Element | Purpose |
|---|---|
| **Role definition** ("You are a fitness coach") | Gives the AI a consistent persona and expertise frame |
| **Input description** (energy level) | Tells the AI exactly what variable to focus on |
| **Structured output** (4 numbered items) | Ensures responses are consistent and scannable |
| **Tone instruction** (warm, encouraging) | Controls the feel of responses |
| **Guardrail** (don't push intense workouts) | Prevents the AI from giving harmful/inappropriate advice |

---

## Iteration Process

### Version 1 — Too generic
The first prompt just said "recommend a workout based on energy." The AI gave the same medium-intensity suggestion every time.

**Problem:** Not enough context or specificity.

### Version 2 — Added structure
I added the 4-point output format. Responses became more consistent and useful.

**Problem:** Tone was sometimes clinical or robotic.

### Version 3 — Added tone + guardrails
Added the persona and tone instructions. Also added the guardrail about not recommending intense workouts for tired users.

**Result:** Responses felt personalized, realistic, and human.

---

## Key Lessons Learned

1. **Specificity beats vagueness** — the more specific your prompt, the better the output
2. **Structure the output** — asking for numbered or formatted responses makes AI answers more consistent
3. **Set guardrails** — tell the AI what NOT to do, not just what to do
4. **Persona matters** — giving the AI a role helps it stay consistent across responses
5. **Test edge cases** — I tested extremes ("I'm completely exhausted" vs "I'm super energized") to make sure the AI responded appropriately to both

---

## What I'd Improve Next

- Add more input dimensions: sleep quality, time available, equipment access
- Add a follow-up prompt that lets users ask questions about the recommended workout
- Experiment with different tones for different user preferences (gentle vs. motivational)
