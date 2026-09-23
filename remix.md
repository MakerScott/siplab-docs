---
icon: wand-magic-sparkles
---

# Remix

You do not have to start from a blank description. On a drink you can **Remix** it into a new recipe of your own, or type a short request under **make it yours**. The published original stays as it was.

You need an account for both. If you are not signed in, we keep what you typed and send you to **Join Us**.

<table data-search="false">
  <thead>
    <tr>
      <th></th>
      <th>Remix</th>
      <th>Make it yours</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Where</td>
      <td>The Remix button on the drink</td>
      <td>The field under the ingredient list</td>
    </tr>
    <tr>
      <td>You give us</td>
      <td>An edited ingredient list, starting from theirs</td>
      <td>A short request, such as less sweet, extra protein, dairy free</td>
    </tr>
    <tr>
      <td>What we keep</td>
      <td>Category and hot or cold</td>
      <td>The same drink, except what the request asks to change</td>
    </tr>
    <tr>
      <td>What you get</td>
      <td>A new public drink under your name, with its own photo</td>
      <td>A rewritten recipe on this screen. It is not saved over theirs.</td>
    </tr>
    <tr>
      <td>Who can use it</td>
      <td>Anyone signed in</td>
      <td>Anyone signed in who does not already own the drink</td>
    </tr>
  </tbody>
</table>

{% tabs %}
{% tab title="Remix" %}
Remix is a new drink. We start from this one, then run the same [path](README.md#from-idea-to-recipe) we use when you create from scratch.

{% stepper %}
{% step %}
### Start from their list

**Remix** opens **Remix This Drink** with this drink’s ingredients already filled in, plus the category. The job is **Edit the ingredients**. You can keep the list, add a line, drop one, or change an amount.
{% endstep %}

{% step %}
### We check it is still a drink

[Jev](models.md) reads your list the same way it guards a new idea. If it is no longer a homemade drink, we stop before we write a full recipe.
{% endstep %}

{% step %}
### We write a new recipe

The recipe model treats your edited list like any other create. It names the drink, writes steps, sizes the glass, and estimates [nutrition](nutrition.md). We lock kitchen amounts, assign tags, and a second model reviews it once.

The name has to be unique. This is not a copy with the same page. It is a new drink you own.
{% endstep %}

{% step %}
### It goes live as yours

The remix is public under your handle. A photo job starts. The drink you remixed is unchanged: same name, same recipe, same picture.
{% endstep %}
{% endstepper %}
{% endtab %}

{% tab title="Make It Yours" %}
**make it yours** is for a drink that is not already yours. You keep the recipe on screen and tell us how it should change. Owners do not see this field.

{% stepper %}
{% step %}
### You write the request

The field sits under the ingredients. “Less sweet,” “extra protein,” or “dairy free” is enough. We treat that line as a hard constraint. If you asked to reduce something, we do not increase it.
{% endstep %}

{% step %}
### We start from this recipe

The model gets the current name, description, ingredients, amounts, steps, and glass size as the baseline. It is not a blank slate. It should keep the same drink unless you asked for a different one, and change only what the request requires.
{% endstep %}

{% step %}
### Your request wins the amounts

On a new create, amounts you typed stay put. Here the request is allowed to change them. If “less sweet” conflicts with two tablespoons of syrup, the syrup comes down. Vague add-ins such as “some marshmallows” stay a garnish: a tablespoon or two, not a cup.
{% endstep %}

{% step %}
### We estimate nutrition again

The rewritten list gets a new panel. Coffee and tea caffeine is counted the same way as on a new drink. We do not paint a new photo. You are looking at a rewritten recipe, not a newly published one.
{% endstep %}
{% endstepper %}

The original drink in the catalog is not overwritten. Refresh the page and theirs is still theirs. Use **Remix** if you want a public copy under your name.
{% endtab %}
{% endtabs %}

## What We Will Not Do

- Invent a different drink when you only asked for a tweak
- Reverse the request (sweeter when you said less sweet)
- Ignore the current list and start over
- Treat a handful of toppings like a main pour
- Keep a name that no longer fits, if the request really changed the drink

Ingredients stay in make order: coffee, tea, or espresso first, then water and milk, then produce, then sweeteners, then ice, then toppings last. On a smoothie, blender add-ins group by kind: liquids, yogurt, produce, syrups, powders, then seeds.
