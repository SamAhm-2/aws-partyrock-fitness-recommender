# 🔧 How to Build This App on PartyRock

A step-by-step guide to recreating (or remixing) this app using Amazon PartyRock — no coding required.

---

## Prerequisites

- A free AWS account (or sign in with Google/Apple at partyrock.aws)
- No coding experience needed
- The app has 6 inputs and 8 outputs — budget around 2–3 hours to build and test everything

---

## Step 1 — Create a PartyRock Account

1. Go to [partyrock.aws](https://partyrock.aws)
2. Click **Sign In** — use your AWS, Google, or Apple account
3. New users get free trial credits to build and test apps

---

## Step 2 — Start a New App

**Option A — Generate from description (recommended for beginners)**
Click **Generate app** and type something like:
> *"A fitness app that takes the user's energy level, available time, equipment, fitness level, goal, and dietary needs, then generates a personalized workout plan, music playlist, nutrition guide, and motivational support."*

PartyRock will auto-generate a starting layout you can refine.

**Option B — Build from scratch**
Click **Build app yourself** to start with a blank canvas and add widgets manually.

---

## Step 3 — Set Up Your Input Widgets

These are the 6 inputs the user fills in before the AI generates anything.

| Widget | Type | Options / Notes |
|---|---|---|
| Energy Level | Slider | Label stops: Exhausted, Low, Good, Moderate, Peak |
| Available Time | Single select | 15 min / 30 min / 45 min / 60 min |
| Available Equipment | Single select | None / Basic home / Home furniture / Full home gym / Commercial gym / Outdoor space |
| Fitness Level | Single select | Beginner / Intermediate / Advanced |
| Primary Goal | Single select | Get moving / Build strength / Lose weight / Feel better |
| Dietary Considerations | Text input | Open text — user types their dietary needs (e.g. halal, vegetarian, nut allergy) |

---

## Step 4 — Set Up Your Output Widgets (in order)

Build outputs in this order because later ones reference earlier ones.

### Output 1: Movement Guide (AI Text)
Write a prompt that:
- References all 6 user inputs using the `@` tag (e.g. `@EnergyLevel`, `@AvailableTime`)
- Instructs the AI to generate a Warm-Up → Main Circuit → Cool-Down structure
- Includes a modifications section for low-energy users
- Specifies rep counts, duration, and rest periods

### Output 2: Movement Visual (AI Image)
Write an image prompt that:
- References `@EnergyLevel` and `@MovementGuide`
- Describes the visual tone based on energy (calm/soft for low, active/dynamic for high)

### Output 3: Workout Playlist (AI Text)
Write a prompt that:
- References `@MovementGuide` and `@EnergyLevel`
- Specifies BPM ranges per phase: warm-up (90–100), circuit (100–128), cool-down (60–85)
- Asks for specific song recommendations with search terms
- Asks for setup instructions for Spotify, Apple Music, and YouTube Music

### Output 4: Fuel Guide (AI Text)
Write a prompt that:
- References `@EnergyLevel`, `@MovementGuide`, and `@DietaryConsiderations`
- Asks for separate pre-workout and post-workout meal options
- Specifies multiple options at different prep times
- Asks for portion guidance scaled to workout intensity
- Asks for a do/don't list, hydration tips, and a shopping list

### Output 5: Meal Inspiration Image (AI Image)
Write an image prompt that:
- References `@FuelGuide`
- Asks for a clean, well-lit, aesthetically styled food photo

### Output 6: Mindset Boost (AI Text)
Write a prompt that:
- References `@EnergyLevel` and `@PrimaryGoal`
- Instructs the AI to first acknowledge the user's current state, then encourage
- Specifies the tone (warm, honest, not aggressively positive)
- Asks for a relevant motivational quote at the end

### Output 7: Mindset Image (AI Image)
Write an image prompt with conditional logic:
- Low/Exhausted → soft, calming colors, peaceful imagery
- Good/Moderate → balanced, steady progress imagery
- Peak → dynamic, vibrant, energetic imagery

### Output 8: Personal Coach Chat (Chatbot)
Write a system prompt that:
- Gives the AI the user's full context: energy level, goal, fitness level, dietary needs
- Instructs it to reference the workout and nutrition plan already generated
- Sets tone to adapt based on energy level (gentle for low, energizing for peak)
- Keeps scope focused on fitness, nutrition, and mindset

---

## Step 5 — Connect the Widgets

In each output widget's prompt, use the `@` symbol to reference other widgets:
- `@EnergyLevel` — pulls in the slider value
- `@MovementGuide` — pulls in the workout text output
- `@FuelGuide` — pulls in the nutrition output
- And so on

This chaining is what makes all 8 outputs feel like one coherent session plan rather than 8 separate AI responses.

---

## Step 6 — Test Across Energy Levels

Before publishing, test with at least these 3 scenarios:

**Scenario A — Exhausted**
- Energy: Exhausted | Time: 15 min | Equipment: None | Level: Beginner | Goal: Get moving
- Check: Is the workout gentle? Is the playlist calm? Is the mindset message supportive, not pushy?

**Scenario B — Moderate**
- Energy: Moderate | Time: 30 min | Equipment: Basic home | Level: Intermediate | Goal: Feel better
- Check: Is the workout appropriately balanced? Does everything feel calibrated to "medium"?

**Scenario C — Peak**
- Energy: Peak | Time: 45 min | Equipment: Full home gym | Level: Advanced | Goal: Build strength
- Check: Is the workout challenging? Is the music high-energy? Is the mindset image dynamic?

---

## Step 7 — Publish & Share

1. Click **Publish** to make your app public
2. Copy the shareable link
3. Add the link to your GitHub README and LinkedIn post

---

## Tips for Remixing

- Add a **weekly planner** widget that generates a 5-day schedule based on the user's goal
- Add a **sleep quality input** to further refine recovery and intensity recommendations
- Add a **progress reflection** chatbot that asks how the session went and suggests adjustments
- Try different AI models in PartyRock to see how output quality and style varies

---

## Resources

- [PartyRock Documentation](https://partyrock.aws/guide)
- [Prompt Engineering Guide (Anthropic)](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview)
- [Amazon Bedrock Overview](https://aws.amazon.com/bedrock/)

