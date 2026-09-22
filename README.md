# How it works

You bring an idea. We write a recipe you can make at home — with kitchen amounts, steps, tags, nutrition, and a photo. Here is exactly how that happens, and which models do which jobs.

## From idea to recipe

A drink is published as soon as the recipe is ready. The photo follows a moment later.

1. **You describe the drink**\
   Name a category, list ingredients, write a vibe, or mix all three. “Oat milk latte with maple” is enough.
2. **We check it is a drink**\
   A small model reads the prompt and turns away anything that is not a beverage.
3. **We write the recipe**\
   A model names it, lists ingredients with kitchen amounts, picks a glass size, and writes the steps.
4. **Code does the kitchen work**\
   We lock the amounts you typed, add a missing espresso or tea base, size the glass (4–24 fl oz), and put the steps in a makeable order.
5. **We estimate nutrition**\
   A model adds calories, macros, and the rest of the panel. Coffee and tea caffeine is checked again in code.
6. **A second model reviews it**\
   A second model looks for real problems. If something is off, we rewrite the recipe once and keep the result.
7. **It goes live**\
   The drink is live with a unique name. Tags, an embedding for similar drinks, and the photo job start right away.

## The models

No single model does everything. A stronger one writes the recipe. Smaller ones handle quick checks. Image, video, and voice models handle the rest.

| Job | Model | Why this one |
| --- | --- | --- |
| Write the recipe | Claude Sonnet | Strong at turning a loose idea into a complete, structured recipe. |
| Estimate nutrition | Claude Sonnet | Same careful reasoning, with USDA-style references in the prompt. |
| Check the prompt | GPT-4o mini | Fast and cheap. It only needs to decide if this is a drink. |
| Suggest ingredients | GPT-4o mini | Quick ideas while you are still building the drink. |
| Review the recipe | GPT-4o mini | A second pair of eyes, without spending another full recipe call. |
| Take the photo | Gemini Flash Image | Good at still-life drink photos from a detailed prompt. |
| Make a video | Seedance 2.0 | Turns the finished photo into a short pour video. |
| Read the recipe aloud | Grok Voice | Calm barista pacing, with pauses built into the script. |
| Find similar drinks | text-embedding-3-small | Turns a recipe into a fingerprint we can compare. |

Model IDs, as configured today:

| Job | ID |
| --- | --- |
| Write the recipe | `anthropic/claude-sonnet-5` |
| Estimate nutrition | `anthropic/claude-sonnet-5` |
| Check the prompt | `openai/gpt-4o-mini` |
| Suggest ingredients | `openai/gpt-4o-mini` |
| Review the recipe | `openai/gpt-4o-mini` |
| Take the photo | `google/gemini-3.1-flash-image` |
| Make a video | `bytedance/seedance-2.0` |
| Read the recipe aloud | `x-ai/grok-voice-tts-1.0` |
| Find similar drinks | `openai/text-embedding-3-small` |

We may swap models as better ones show up. This is what we use today.

## Who does what

AI drafts. Code keeps the kitchen honest. You stay in charge of the idea.

### You

* Pick a category and hot or cold
* List ingredients or write a short prompt
* Save, remix, or rewrite a drink you own

### AI

* Write the name, ingredients, and steps
* Estimate the nutrition panel
* Suggest the next ingredient while you type
* Review the finished recipe once
* Generate the photo, video, and voice

### Our code

* Keep the amounts you typed
* Size the glass and add a missing coffee or tea base
* Assign tags and round nutrition
* Publish the drink and find similar ones

## What a recipe includes

Every published drink has the same parts. Some are written by a model. Some are decided by code.

| On the drink | How it is made |
| --- | --- |
| Name and description | The model drafts these. We tidy repeated words in the name and keep the description short. |
| Ingredients | Kitchen units — cups, shots, tablespoons — not raw grams unless that is how you buy it. Your listed amounts win. |
| Steps | Written by the model, then reordered and filled in so every ingredient is used. |
| Servings and size | Servings snap to ½, 1, 2, or 3. Glass size stays between 4 and 24 fl oz. |
| Equipment | Inferred from the method: blender, kettle, espresso machine, and so on. |
| Tags | Assigned by rules, not a model — vegan, dairy-free, low sugar, seasonal, and similar. |
| Nutrition | Estimated by a model, rounded the way a label would be. Caffeine for coffee and tea is also computed in code. |
| Photo | Generated after the recipe is already public. Some catalog drinks also get a short video from the photo. |

## Amounts you write stay put

If you write “2 shots” or “1 cup oat milk,” we keep those amounts. After the model drafts the recipe, our code reads your lines again and puts your numbers back. The model does not get the last word.

## Nutrition is an estimate

Nutrition is an estimate, not a lab test. We give the model USDA-style anchors, then check that the panel is complete and sane. For coffee and tea, caffeine is also calculated in code. This is not medical advice.

## After it goes live

The recipe is public as soon as it is written. A few things keep happening in the background.

### The photo shows up next

A still life is painted from a long list of rules: the right glass, hot or cold, no logos, garnish that matches the drink.

### Similar drinks

An embedding turns the recipe into a fingerprint. We only compare drinks in the same category and the same hot or cold.

### Listen to it

The spoken script is written in code, then a voice reads it like a calm barista, with pauses after the name, each ingredient, and each step.

### Make it yours

Remix is a preview. It skips the review step and does not save until you publish a new drink.

## How a video is made

Not every drink gets a video. When one does, it is built from the finished photo and the recipe — not filmed in a kitchen.

1. **Start from the photo**\
   The still image is the first frame. If there is no photo yet, we wait.
2. **Write the shot list**\
   Code turns the recipe into a shot list: every ingredient in its measured amount, every step in order, the same glass from the first pour to the last garnish.
3. **Match the author’s hands**\
   If hands appear, they match the creator’s skin tone and jewelry from their profile. No faces, and no switching people mid-clip.
4. **Pick a length**\
   Clips run about 10 to 15 seconds, phone-tall. More steps or ingredients get a little more time.
5. **Animate the still**\
   A video model animates the photo into a short make. Sound is close-up kitchen noise for the action on screen — a pour, a shot, a blender — then it stops. No music, no talking.
6. **Keep the glass continuous**\
   Once liquid is in the glass, it stays. Later add-ins go into that same drink. The last seconds keep moving: steam, ice, or a quiet settle — never a freeze-frame.
7. **Attach the clip**\
   We save the finished clip on the drink so it can play on the recipe.
