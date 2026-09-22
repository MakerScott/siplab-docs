---
icon: apple-whole
---

# Nutrition

The panel on a drink is an estimate for one serving, built after the ingredient amounts are locked. It is not a lab test, and it is not medical advice. [Claude Sonnet](models.md) writes the numbers. Code checks them, rounds them the way a label would, and overwrites coffee and tea caffeine.

{% hint style="warning" %}
Check the ingredient list for allergens. Use your own judgment before you make or drink anything.
{% endhint %}

## How the Panel Is Built

{% stepper %}
{% step %}
### Amounts lock first

Nutrition waits on the finished recipe. The model sees the same kitchen amounts you will measure — cups, shots, tablespoons — not a new pour invented for the label. If you wrote “2 shots” or “1 cup oat milk,” those numbers are still there. Cups are also written as fluid ounces so “½ cup” is not read as half an ounce.
{% endstep %}

{% step %}
### The model sums the list

We give it the category, the serving count, the finished glass size, and USDA-style anchors for dairy, fruit juice, and caffeine. Glass size is context only. Ice and headspace explain a taller drink. They do not add calories, and they are not a reason to scale the milk.

It has to sum the listed ingredients. An unsweetened latte should look like milk sugar, not a mocha. A ¼ cup of pineapple juice should look like pineapple juice, not a lemon squeeze.
{% endstep %}

{% step %}
### One serving, not the pitcher

The ingredient list is the full recipe. The panel is one serving. If servings is 1, the panel is the whole list. If you asked for two or three, the totals are divided. Servings snap to ½, 1, 2, or 3 before this step, so the math stays a home pour.
{% endstep %}

{% step %}
### We check it is usable

Every field has to come back. An all-zero panel is allowed when the drink is really just ice, water, or unsweetened tea or coffee. If the list has milk, juice, fruit, syrup, yogurt, or another caloric ingredient and the panel is empty, we try once more.

If the second attempt is still missing pieces or fails, we do not invent a fake label. The recipe still goes live. Nutrition can be estimated again later.
{% endstep %}

{% step %}
### Code rounds and sets caffeine

The model’s raw numbers are rounded the way a Nutrition Facts label would be. For coffee and tea, caffeine is then computed from the ingredient list in code and written over the model’s guess. That number is what you see on the drink.
{% endstep %}
{% endstepper %}

## What Is on the Panel

The drink card shows calories, protein, sugars, and either caffeine or carbs. Open the full panel for the rest. Daily Value percents use a 2,000 calorie diet.

<table data-search="false">
  <thead>
    <tr>
      <th>On the panel</th>
      <th>Unit</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Calories</td>
      <td>kcal</td>
    </tr>
    <tr>
      <td>Total fat, saturated fat, trans fat</td>
      <td>g</td>
    </tr>
    <tr>
      <td>Cholesterol, sodium, calcium, potassium, caffeine</td>
      <td>mg</td>
    </tr>
    <tr>
      <td>Total carbs, fiber, total sugars, added sugars, protein</td>
      <td>g</td>
    </tr>
    <tr>
      <td>Iron</td>
      <td>mg</td>
    </tr>
    <tr>
      <td>Vitamin D</td>
      <td>mcg</td>
    </tr>
  </tbody>
</table>

Total sugars include the sugar already in fruit, juice, milk, and yogurt. Added sugars are only sweeteners you poured in — syrup, honey, maple, agave, sugar, sweetened condensed milk.

Caffeine on the card is for coffee and tea drinks. Other categories show carbs in that slot. The full panel still stores caffeine when the recipe has coffee, tea, or matcha.

## Kitchen Amounts Are Literal

The model is told to keep the listed amounts and not rescale them to the glass. We also spell out the kitchen math in the prompt:

- 1 cup = 8 fl oz
- ½ cup = 4 fl oz
- ¼ cup = 2 fl oz
- 1 tbsp = 0.5 fl oz

Dairy milk uses USDA dairy numbers, not almond-milk calories. Skim is not treated like almond milk. Hazelnut syrup is syrup, not hazelnuts. Chocolate syrup is syrup, not a bar. Lemon or lime juice in tablespoons is tart citrus, not a cup of sweet juice.

Ice, water, and unsweetened tea or coffee add almost nothing. Ice cream is not ice.

## Caffeine Comes From Code

The model may draft a caffeine number. For coffee and tea we replace it with a sum from the locked list. Decaf and herbal teas — chamomile, hibiscus, rooibos, tulsi, and similar — stay at 0.

<table data-search="false">
  <thead>
    <tr>
      <th>Ingredient</th>
      <th>How we count it</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Espresso or ristretto</td>
      <td>63 mg per shot</td>
    </tr>
    <tr>
      <td>Brewed coffee</td>
      <td>12 mg per fl oz</td>
    </tr>
    <tr>
      <td>Cold brew</td>
      <td>15 mg per fl oz, or 25 mg if it is concentrate</td>
    </tr>
    <tr>
      <td>Black tea or chai</td>
      <td>6 mg per fl oz</td>
    </tr>
    <tr>
      <td>Green tea</td>
      <td>3.5 mg per fl oz</td>
    </tr>
    <tr>
      <td>Matcha</td>
      <td>35 mg per gram, or 70 mg per teaspoon</td>
    </tr>
    <tr>
      <td>Cocoa or cacao</td>
      <td>A small amount from the powder or spoon</td>
    </tr>
    <tr>
      <td>Decaf or herbal tea</td>
      <td>0</td>
    </tr>
  </tbody>
</table>

A juice or smoothie only gets caffeine if coffee, tea, or matcha is actually in the recipe.

## How We Round

We round after the estimate, not before. Small amounts can become zero on the label. That is the same pattern a packaged drink uses.

<table data-search="false">
  <thead>
    <tr>
      <th>Nutrient</th>
      <th>Rounding</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Calories</td>
      <td>Under 5 becomes 0. Up to 50, nearest 5. After that, nearest 10.</td>
    </tr>
    <tr>
      <td>Fat</td>
      <td>Under 0.5 g becomes 0. Under 5 g, nearest 0.5 g. After that, nearest gram.</td>
    </tr>
    <tr>
      <td>Protein, carbs, sugars, fiber</td>
      <td>Under 0.5 g becomes 0. Otherwise nearest gram.</td>
    </tr>
    <tr>
      <td>Sodium, potassium, caffeine</td>
      <td>Under 5 mg becomes 0. Up to 140 mg, nearest 5. After that, nearest 10.</td>
    </tr>
    <tr>
      <td>Cholesterol</td>
      <td>Under 2 mg becomes 0. Otherwise nearest 5 mg.</td>
    </tr>
  </tbody>
</table>

## Tags That Read the Panel

Some tags are assigned from these numbers, not by the model. We skip them when the panel is empty so a missing estimate does not mark a drink low-calorie.

- **High protein** — 15 g of protein or more in a serving
- **Low sugar** — 8 g of total sugars or less
- **Low calorie** — about 10 calories per fluid ounce of glass size
- **Caffeine-free** — the panel and the code estimate are both 0

Vegan, dairy-free, and the rest still come from the ingredient list.

## After It Is on the Drink

A second model [reviews](README.md#a-second-model-reviews-it) the recipe and glances at the panel. It is not a calorie audit. It only flags a panel that cannot be true — zero calories with cream and syrup, or a huge sugar number on unsweetened espresso and milk. That can trigger one rewrite.

If you own the drink, you can ask us to estimate nutrition again from the current ingredient list. The recipe does not wait on this step to go live.
