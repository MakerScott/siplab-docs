# How It Works

You bring an idea. We write a recipe you can make at home — with kitchen amounts, steps, tags, nutrition, and a photo. The recipe is public as soon as it is written. The photo follows a moment later. Some drinks also get a short [video](video.md).

The [models](models.md) that do each job are listed separately. This page is the path from your idea to a drink you can make.

## From Idea to Recipe

{% stepper %}
{% step %}
### You describe the drink

Name a category, list ingredients, write a vibe, or mix all three. “Oat milk latte with maple” is enough. You can also pick hot or cold and start typing ingredients one at a time — we will suggest the next one while you build.

You do not have to specify every amount. If you do write amounts, we keep them later. If you only write a feeling, the recipe model fills in the kitchen work.
{% endstep %}

{% step %}
### We check it is a drink

A small model reads the prompt, the category, and any ingredient list. It only answers one question: is this a homemade drink? Anything that is not a beverage is turned away before we spend a full recipe call.
{% endstep %}

{% step %}
### We write the recipe

A stronger model names the drink, writes a short description, lists ingredients in kitchen units, picks a glass size, and writes the steps. It infers equipment from the method — blender, kettle, espresso machine — and drafts a nutrition panel.

The name has to be unique on Siplab. If that name is already taken, we adjust the slug so the drink still has its own URL.
{% endstep %}

{% step %}
### Code does the kitchen work

After the draft, our code reads the recipe again. It locks the amounts you typed, adds a missing espresso or tea base when the category needs one, sizes the glass between 4 and 24 fl oz, and snaps servings to ½, 1, 2, or 3.

Steps are put in a makeable order and checked so every ingredient is used. For blender drinks, whole fruit is cut — and peeled when it needs it — before it goes in. Milk pours are sized to the glass when the model left them vague. Tags are assigned by rules, not by the model: vegan, dairy-free, low sugar, seasonal, and similar.
{% endstep %}

{% step %}
### We estimate nutrition

A model builds a Nutrition Facts panel for one serving from the locked ingredient list. We give it USDA-style anchors and the finished glass size, then ask it to use the listed amounts as recipe totals — not to invent a new pour.

If servings is more than one, the panel is the totals divided by servings. Coffee and tea caffeine is also calculated in code. If the panel is incomplete or not sane, we try once more. This is an estimate, not a lab test, and not medical advice.
{% endstep %}

{% step %}
### A second model reviews it

A smaller model looks for real problems: missing steps, leftover ingredients, a glass that cannot hold the pour, or a method that would not work at home. If something is off, it writes a short edit brief and we regenerate the recipe once.

We do not loop. If the second attempt is still imperfect, we keep that attempt and publish. The review step is a second pair of eyes, not a veto that can stall the drink forever.
{% endstep %}

{% step %}
### It goes live

The drink is public with a unique name. An embedding job starts so we can find similar drinks. If a photo was requested, that job starts too. The recipe does not wait on the picture.
{% endstep %}
{% endstepper %}

## What a Recipe Includes

Every published drink has the same parts. Some are written by a model. Some are decided by code. The table is the map. The sections below are the parts that need more than a line.

<table data-search="false">
  <thead>
    <tr>
      <th>On the drink</th>
      <th>How it is made</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Name and description</td>
      <td>The model drafts these. We tidy repeated words in the name and keep the description short.</td>
    </tr>
    <tr>
      <td>Ingredients</td>
      <td>Kitchen units — cups, shots, tablespoons — not raw grams unless that is how you buy it. Your listed amounts win.</td>
    </tr>
    <tr>
      <td>Steps</td>
      <td>Written by the model, then reordered and filled in so every ingredient is used.</td>
    </tr>
    <tr>
      <td>Servings and size</td>
      <td>Servings snap to ½, 1, 2, or 3. Glass size stays between 4 and 24 fl oz.</td>
    </tr>
    <tr>
      <td>Equipment</td>
      <td>Inferred from the method: blender, kettle, espresso machine, and so on.</td>
    </tr>
    <tr>
      <td>Tags</td>
      <td>Assigned by rules, not a model — vegan, dairy-free, low sugar, seasonal, and similar.</td>
    </tr>
    <tr>
      <td>Nutrition</td>
      <td>Estimated by a model, rounded the way a label would be. Caffeine for coffee and tea is also computed in code.</td>
    </tr>
    <tr>
      <td>Photo</td>
      <td>Generated after the recipe is already public. Some drinks also get a short [video](video.md) from the photo.</td>
    </tr>
  </tbody>
</table>

## Amounts You Write Stay Put

If you write “2 shots” or “1 cup oat milk,” we keep those amounts. After the model drafts the recipe, our code reads your lines again and puts your numbers back. The model does not get the last word.

We only fill in amounts you left blank. A missing espresso or tea base can be added when the category needs one. Milk that was listed without a pour can be sized to the glass. We do not scale your teaspoons up for the camera or the photo, and we do not rewrite “2 shots” as a different volume because the model preferred a bigger drink.

Glass size stays between 4 and 24 fl oz. If you asked for a size in that range, we use it. Servings snap to ½, 1, 2, or 3 so the recipe stays a home pour, not a batch.

## Nutrition Is an Estimate

Nutrition is not a lab test. We give the model USDA-style references, the locked ingredient list, the serving count, and the finished glass size. It estimates calories, macros, and the rest of a standard panel, then we round the way a label would.

The amounts on the ingredient list are the full recipe. The panel is one serving. If you asked for two servings, the numbers are divided. For coffee and tea, caffeine is also computed in code from the recipe, not left entirely to the model.

If the first panel is missing pieces or does not make sense next to the ingredients, we try once more. If it still fails, we do not invent a fake label. This is not medical advice.

## After It Goes Live

The recipe is public as soon as it is written. A few things keep happening in the background.

### The Photo Shows Up Next

A still life is painted from the finished recipe: the right unbranded glass, hot or cold, the liquid color those ingredients would actually mix, and only the garnish the method called for.

The drink fills the frame. There are no people, logos, straws, or store bottles. Kitchen and leftover ingredients stay soft at the edges. Hot drinks stay in an opaque ceramic mug. Cold drinks stay in glass — not a mug with a handle. Some drinks also get a short [video](video.md) from this still.

### Similar Drinks

An embedding turns the recipe into a fingerprint — name, ingredients, steps, and tags, not the photo. We only compare drinks in the same category and the same hot or cold, then keep the closest matches. A latte is not ranked against a juice.

### Listen to It

The spoken script is written in code, not improvised by a model. It reads the name, the servings if you asked for more than one, each ingredient in spoken kitchen amounts, then each step.

A voice reads it like a calm barista. There is a pause after the name, after each ingredient, and after each step, so you can measure while it talks.
