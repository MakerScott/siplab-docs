# The models

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
