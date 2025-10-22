---
title: "EULA — Minecraft License Agreement"
description: "What is EULA and how to accept the license agreement to start a Minecraft server"
weight: 5
---

## What is EULA?

**EULA** ([End User License Agreement](https://www.minecraft.net/en-us/eula)) is an end-user license agreement between you and the Minecraft developer (Mojang Studios).

EULA describes:
- Rules for using the game
- User rights and responsibilities
- Restrictions on modifications and commercial use

{{< callout type="warning" >}}
**Warning!** Without accepting the EULA, starting a Minecraft server is impossible.
{{< /callout >}}

## How to Accept EULA?

There are two ways to accept the license agreement:

### Method 1: Through Console (Recommended)

1. Go to your server console in the control panel
2. Start the server
3. The server will automatically create an `eula.txt` file and stop
4. Follow the instructions in the console or use Method 2

### Method 2: Edit the eula.txt File

1. Open the control panel at panel.qwer-host.xyz and select your server
2. Go to the **"Files"** tab
3. Find and open the `eula.txt` file
4. Replace the file contents with:
   ```properties
   eula=true
   ```
5. Save the file
6. Start the server

After completing these steps, the server will start successfully.

---

## Important Information

- By accepting the EULA, you agree to comply with Mojang Studios' license agreement terms
- We recommend reading the full agreement at: [minecraft.net/eula](https://www.minecraft.net/en-us/eula)
- EULA applies to all Minecraft servers, regardless of hosting provider
