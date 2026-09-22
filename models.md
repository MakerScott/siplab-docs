---
icon: microchip
---

# Models

No single model does everything. A stronger one writes the recipe. Smaller ones handle quick checks. Image, video, and voice models handle the rest.

<table data-search="false">
  <thead>
    <tr>
      <th>Job</th>
      <th>Model</th>
      <th>Why this one</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Write the recipe</td>
      <td>Claude Sonnet</td>
      <td>Strong at turning a loose idea into a complete, structured recipe.</td>
    </tr>
    <tr>
      <td>Estimate nutrition</td>
      <td>Claude Sonnet</td>
      <td>Same careful reasoning, with standard food references. See [Nutrition](nutrition.md).</td>
    </tr>
    <tr>
      <td>Check the idea</td>
      <td>GPT-4o mini</td>
      <td>Fast. It only needs to decide if this is a drink.</td>
    </tr>
    <tr>
      <td>Suggest ingredients</td>
      <td>GPT-4o mini</td>
      <td>Quick ideas while you are still building the drink.</td>
    </tr>
    <tr>
      <td>Review the recipe</td>
      <td>GPT-4o mini</td>
      <td>A second pair of eyes, without writing the whole recipe again.</td>
    </tr>
    <tr>
      <td>Take the photo</td>
      <td>Gemini Flash Image</td>
      <td>Good at still-life drink photos from a detailed description.</td>
    </tr>
    <tr>
      <td>Make a video</td>
      <td>Seedance 2.0</td>
      <td>Turns the finished photo into a short pour video. See [Videos](video.md).</td>
    </tr>
    <tr>
      <td>Read the recipe aloud</td>
      <td>Grok Voice</td>
      <td>Calm barista pacing, with pauses built into the script.</td>
    </tr>
    <tr>
      <td>Find similar drinks</td>
      <td>text-embedding-3-small</td>
      <td>Turns a recipe into a fingerprint we can compare.</td>
    </tr>
  </tbody>
</table>

Model IDs, as configured today:

<table data-search="false">
  <thead>
    <tr>
      <th>Job</th>
      <th>ID</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Write the recipe</td>
      <td>anthropic/claude-sonnet-5</td>
    </tr>
    <tr>
      <td>Estimate nutrition</td>
      <td>anthropic/claude-sonnet-5</td>
    </tr>
    <tr>
      <td>Check the idea</td>
      <td>openai/gpt-4o-mini</td>
    </tr>
    <tr>
      <td>Suggest ingredients</td>
      <td>openai/gpt-4o-mini</td>
    </tr>
    <tr>
      <td>Review the recipe</td>
      <td>openai/gpt-4o-mini</td>
    </tr>
    <tr>
      <td>Take the photo</td>
      <td>google/gemini-3.1-flash-image</td>
    </tr>
    <tr>
      <td>Make a video</td>
      <td>bytedance/seedance-2.0</td>
    </tr>
    <tr>
      <td>Read the recipe aloud</td>
      <td>x-ai/grok-voice-tts-1.0</td>
    </tr>
    <tr>
      <td>Find similar drinks</td>
      <td>openai/text-embedding-3-small</td>
    </tr>
  </tbody>
</table>

We may swap models as better ones show up. This is what we use today.
