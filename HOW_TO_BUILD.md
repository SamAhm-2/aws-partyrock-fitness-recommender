# 🔧 How to Build EnerFit on PartyRock

A step-by-step guide to recreating (or remixing) this app using Amazon PartyRock.

---

## Prerequisites

- A free AWS account (or sign in with Google/Apple at partyrock.aws)
- No coding experience needed

---

## Step 1 — Create a PartyRock Account

1. Go to [partyrock.aws](https://partyrock.aws)
2. Click **Sign In** and use your AWS, Google, or Apple account
3. New users get free trial credits to build and test apps

---

## Step 2 — Start a New App

You have two options:

**Option A — Generate from description (recommended for beginners)**  
Click **Generate app** and type something like:  
> *"An app that asks users how energetic they feel today and recommends a personalized workout routine based on their energy level"*  
PartyRock will auto-generate a starting layout.

**Option B — Build from scratch**  
Click **Build app yourself** to start with a blank canvas and add widgets manually.

---

## Step 3 — Set Up Your Widgets

PartyRock apps are built from widgets. For EnerFit, you need:

### Widget 1: User Input
- **Type:** User Input
- **Label:** Something like *"How's your energy today?"*
- **Placeholder text:** *"e.g., I'm exhausted, running on 5 hours of sleep"*

### Widget 2: AI Text Generation
- **Type:** AI Text Generation
- **Connected to:** Widget 1 (so it reads the user's input)
- **Prompt:** Write your instructions here (see PROMPT_DESIGN.md for the full prompt)

### Optional Widget 3: Title / Header
- **Type:** Static Text
- Use this to add branding, instructions, or a description of the app

---

## Step 4 — Write Your Prompt

In the AI Text Generation widget, click the prompt field and write your instructions. 

To reference the user's input dynamically, use the `@` symbol to tag your input widget:
> *"Based on the user's energy level: @UserInput, recommend a workout..."*

This passes whatever the user typed directly into the AI prompt.

---

## Step 5 — Test Your App

1. Click **Preview** to see the app as a user would
2. Type different energy descriptions and see how the AI responds
3. Go back and refine your prompt based on what you observe

**Test these scenarios:**
- "I'm completely exhausted and barely slept"
- "I feel okay, moderate energy"
- "I'm feeling great and ready to push hard"

---

## Step 6 — Publish & Share

1. Click **Publish** to make your app public
2. Copy the shareable link
3. Share on LinkedIn, GitHub, or anywhere you want to showcase your work

---

## Tips for Remixing This App

- Add an **image generation widget** to show a visual of the recommended workout
- Add a **second input** for "time available" to make recommendations more practical
- Change the theme to fitness/health colors in the app settings
- Add a **chatbot widget** so users can ask follow-up questions

---

## Resources

- [PartyRock Documentation](https://partyrock.aws/guide)
- [Prompt Engineering Guide (Anthropic)](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview)
- [Amazon Bedrock Overview](https://aws.amazon.com/bedrock/)
