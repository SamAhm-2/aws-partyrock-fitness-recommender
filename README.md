# ⚡ AWS-PartyRock-Fitness-Recommender

> AI-powered fitness app built on Amazon PartyRock — recommends personalized workouts, playlists, nutrition, and mindset support based on the user's current energy level using prompt engineering and Amazon Bedrock.

🔗 **[Try the live app →](https://partyrock.aws/u/SamiaAhm/xrMbikqF4/EnerFit-Fitness-That-Matches-Your-Energy)**

---

## 🧠 What is this app?

This is a generative AI wellness companion built on **Amazon PartyRock** that creates a complete, personalized fitness session plan based on how you feel right now. Instead of following a rigid schedule, it adapts everything — the workout, the music, the food, the motivation — to your current energy and situation.

You describe your inputs. The AI builds your entire session.

---

## ✨ What the App Does

The app takes 6 user inputs and generates 8 outputs — all in one go.

### 📥 Inputs
| Input | Options |
|---|---|
| **Energy Level** | Slider: Exhausted → Low → Good → Moderate → Peak |
| **Available Time** | 15 / 30 / 45 / 60 minutes |
| **Available Equipment** | None / Basic home / Home furniture / Full home gym / Commercial gym / Outdoor space |
| **Fitness Level** | Beginner / Intermediate / Advanced |
| **Primary Goal** | Get moving / Build strength / Lose weight / Feel better |
| **Dietary Considerations** | Open text (e.g. halal, vegetarian, allergies) |

### 📤 Outputs
1. 🏋️ **Your Movement Guide** — Full structured workout (warm-up → main circuit → cool-down) with modifications for your energy level
2. 🖼️ **Movement Visual** — AI-generated image matching the workout style and energy
3. 🎵 **Workout Playlist** — Phased music recommendations (BPM-matched to warm-up, circuit, cool-down) with Spotify/Apple Music/YouTube search instructions
4. 🥗 **Your Fuel Guide** — Pre- and post-workout meal options with prep times, portion sizes, and dietary considerations
5. 🍽️ **Meal Inspiration Image** — AI-generated clean food image based on the nutrition guide
6. 🧘 **Your Mindset Boost** — Personalized motivational message that acknowledges your energy level and tone
7. 🌅 **Mindset Image** — AI-generated visual with colors and imagery matched to energy (soft/calming for low, dynamic/vibrant for high)
8. 💬 **Personal Coach Chat** — Open-ended conversational AI coach that adapts its tone to your inputs and answers follow-up questions

---

## 🛠️ How I Built This (No Code!)

This app was built entirely using **[Amazon PartyRock](https://partyrock.aws)** — AWS's no-code generative AI playground powered by Amazon Bedrock.

### What is PartyRock?

PartyRock lets anyone build AI-powered apps by:
- Connecting **widgets** (text inputs, sliders, AI outputs, image generation, chatbots)
- Writing **natural language prompts** to instruct the AI
- Chaining widget outputs so later outputs build on earlier ones
- Zero coding or cloud setup required

### My Building Process

**Step 1 — Define the problem**
Most fitness apps are rigid — they don't care if you slept badly or are stressed. I wanted an app that takes your current state as the starting point and adapts everything around it.

**Step 2 — Design the inputs**
I chose inputs that genuinely change what advice makes sense: energy level (slider), time, equipment, fitness level, goal, and dietary needs. Each one filters the AI's output in a meaningful way.

**Step 3 — Build the widget chain**
Each output widget has its own prompt. Later widgets (like the playlist and nutrition guide) read from the workout output, so everything stays consistent and connected.

**Step 4 — Write and refine the prompts**
The core skill here is prompt engineering — writing clear instructions that tell the AI how to behave, what to output, and what to avoid. Each of the 8 outputs has a distinct prompt with its own tone, format, and logic.

**Step 5 — Test across energy levels**
I tested with extreme inputs ("exhausted" vs "peak energy") to make sure the app adapted meaningfully — different workouts, different music energy, different meal portions, different motivational tones.

---

## 🤖 What I Learned About AI

| Concept | What it means in practice |
|---|---|
| **Prompt Engineering** | How you word instructions to the AI dramatically changes output quality |
| **Multi-widget chaining** | Later AI outputs can read earlier ones — creating a coherent, connected experience |
| **Conditional logic in prompts** | "If energy is low, use soft calming colors" — AI follows if/then instructions |
| **Context shapes everything** | Dietary needs, fitness level, and equipment all change what good advice looks like |
| **Structured output** | Asking the AI for specific formats (phases, tables, sections) produces consistent, usable results |
| **No-code AI** | Tools like PartyRock make generative AI accessible without a CS degree |

---

## 🚀 Try It Yourself

1. Visit: [EnerFit on PartyRock](https://partyrock.aws/u/SamiaAhm/xrMbikqF4/EnerFit-Fitness-That-Matches-Your-Energy)
2. Set your energy slider and fill in your inputs
3. Get a full personalized session plan — workout, playlist, meals, mindset, and a coach to talk to

---

## 🧱 Tech Stack

| Layer | Tool |
|---|---|
| Platform | [Amazon PartyRock](https://partyrock.aws) |
| AI Models | Amazon Bedrock (text + image generation) |
| Deployment | PartyRock hosted (no infrastructure needed) |
| Code | None — 100% no-code |

---

## 💡 Why This Project?

I built this to explore how **generative AI can make wellness genuinely adaptive**. The challenge wasn't just getting the AI to generate a workout — it was getting 8 different outputs to feel like one coherent, personalized experience. That required thinking carefully about how prompts connect, how tone shifts with context, and how to give users something actually useful rather than generic.

It was also my first real hands-on experience with prompt engineering, and I wanted to document the process clearly enough that others could learn from it or build on it.

---

## 📂 Repository Contents

| File | What it covers |
|---|---|
| `README.md` | Project overview, features, inputs/outputs, lessons learned |
| `PROMPT_DESIGN.md` | Prompt engineering breakdown for each of the 8 outputs |
| `HOW_TO_BUILD.md` | Step-by-step guide to recreating this on PartyRock |

---

## 📬 Connect

Built by **Samia Ahmad**
[LinkedIn](https://www.linkedin.com/in/samia-ahmedusa/) • [PartyRock Profile](https://partyrock.aws/u/SamiaAhm)

---

*Made with ☁️ Amazon PartyRock · Part of my AWS AI/ML learning journey*

