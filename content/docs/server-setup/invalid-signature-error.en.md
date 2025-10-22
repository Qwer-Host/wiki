---
title: "Invalid signature for profile public key — How to Fix?"
description: "How to fix the Invalid signature for profile public key error when connecting to a Minecraft server"
weight: 28
---

## Problem Description

If you encounter this error when trying to connect to a server:

```
Invalid signature for profile public key.
Try restarting your game.
agj$a: Missing profile public key.
This server requires secure profiles.
```

This is related to secure profile verification in newer Minecraft versions. Here's the solution!

## Solution

You need to change a setting in the server configuration file `server.properties`.

### Step-by-Step Instructions

1. Open the control panel at panel.qwer-host.xyz and select your server.
2. Go to the **"Files"** tab and find the `server.properties` file.
3. Open the file for editing.
4. Find the line:
   ```properties
   enforce-secure-profile=true
   ```
5. Change the value to `false`:
   ```properties
   enforce-secure-profile=false
   ```
6. Save the file.
7. Restart the server.

After the restart, try connecting again — the error should be gone.
