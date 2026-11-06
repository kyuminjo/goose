---
title: PopNow Extension
description: Add the PopNow MCP Server as a goose Extension to Create Images, Videos, Music and Speech
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';
import GooseDesktopInstaller from '@site/src/components/GooseDesktopInstaller';
import CLIExtensionInstructions from '@site/src/components/CLIExtensionInstructions';

This tutorial covers how to add the [PopNow MCP Server](https://github.com/popnow-ai/popnow-api-mcp) as a goose extension so goose can create images, videos, music and speech with models such as Nano Banana, GPT Image, Seedream, Kling, Seedance, MiniMax, Veo and Suno. Every paid tool quotes its price in USD first and only runs after you approve, so goose never spends without asking.

## Configuration

:::tip Quick Install
<Tabs groupId="interface">
  <TabItem value="ui" label="goose Desktop" default>
  [Launch the installer](goose://extension?type=streamable_http&url=https%3A%2F%2Fapi.popnow.ai%2Fapi%2Fv1%2Fmcp&id=popnow-mcp&name=PopNow&description=Create%20images%2C%20videos%2C%20music%20and%20speech%20with%20top%20AI%20models%2C%20priced%20before%20every%20run&header=Authorization%3DBearer%20YOUR_POPNOW_API_KEY)
  </TabItem>
  <TabItem value="cli" label="goose CLI">
  Add a `Remote Extension (Streamable HTTP)` extension type with:

  **Endpoint URL**
  ```
  https://api.popnow.ai/api/v1/mcp
  ```
  </TabItem>
</Tabs>

  **Custom Request Header**
  ```
  Authorization: Bearer <YOUR_POPNOW_API_KEY>
  ```
:::

<Tabs groupId="interface">
  <TabItem value="ui" label="goose Desktop" default>
    <GooseDesktopInstaller
      extensionId="popnow-mcp"
      extensionName="PopNow"
      description="Create images, videos, music and speech with top AI models, priced before every run"
      type="http"
      url="https://api.popnow.ai/api/v1/mcp"
      envVars={[
        { name: "Authorization", label: "Bearer YOUR_POPNOW_API_KEY" }
      ]}
      apiKeyLink="https://popnow.ai/api/console/keys"
      apiKeyLinkText="PopNow API key"
    />
  </TabItem>

  <TabItem value="cli" label="goose CLI">
    <CLIExtensionInstructions
      name="PopNow"
      description="Create images, videos, music and speech with top AI models, priced before every run"
      type="http"
      url="https://api.popnow.ai/api/v1/mcp"
      timeout={300}
      envVars={[
        { key: "Authorization", value: "Bearer sk-popnow-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" }
      ]}
      infoNote={
        <>
          Create a <a href="https://popnow.ai/api/console/keys" target="_blank" rel="noopener noreferrer">PopNow API key</a> and paste it in as the <code>Bearer</code> token. Paid tools spend your PopNow API balance in USD; add funds in the API console first. A key with a low daily spend cap is a good fit for agents.
        </>
      }
    />
  </TabItem>
</Tabs>

## Example Usage

Let's ask goose for a product image. PopNow tools return a price first, goose asks you to approve it, and the task runs once you do.

### goose Prompt

```
Create a square product photo of a paper boat on a rainy window sill, soft morning light.
Tell me the price before you run it.
```

### goose Output

```
[create_image: prompt="A paper boat on a rainy window sill, soft morning light"]
Needs confirmation, nothing started yet. This costs $0.048 USD.

The image will cost $0.048 with Nano Banana 2.1 at 1K. Shall I go ahead?

> yes

[create_image: ..., max_usd="0.048"]
✓ Image ready

Here's your paper boat. You can download it from the link above; ask me for a
5-second video of the same scene if you want to animate it.
```

## Tools

| Tool | What it does |
|---|---|
| `create_image`, `edit_image` | Create a picture from a description, or change a photo with words |
| `create_video`, `extend_video`, `create_video_from_references` | Text or image to video, continue a clip, keep subjects from reference pictures |
| `create_music`, `create_speech`, `create_sound_effects` | Songs, voiceovers and sound effects |
| `upscale`, `remove_background`, `erase_object`, `expand_image` | Common photo and video fixes |
| `create_task` | Run any PopNow model by its exact API ID with the model's own inputs |
| `list_models`, `get_task`, `list_tasks`, `check_balance` | Free reading tools |

The full list with default models and typical prices is in the [PopNow developer MCP docs](https://popnow.ai/docs/mcp).

## Links

- **Website**: [popnow.ai/api](https://popnow.ai/api)
- **Docs**: [popnow.ai/docs/mcp](https://popnow.ai/docs/mcp)
- **GitHub**: [popnow-ai/popnow-api-mcp](https://github.com/popnow-ai/popnow-api-mcp)
- **npm (stdio bridge)**: [`@popnow/mcp`](https://www.npmjs.com/package/@popnow/mcp)
