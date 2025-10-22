---
title: "Allowing Offline (Cracked) Clients"
description: "How to enable offline-mode for cracked clients and required security measures."
weight: 27
---

If you intentionally want to allow cracked/offline clients to connect, follow these steps. Remember: this increases security risks and can let malicious users impersonate admins — follow the steps carefully.

1. Open panel.qwer-host.xyz and select your server.
2. Go to the "Files" tab and open `server.properties`.
3. Find the line `online-mode=true` and change it to `online-mode=false`.
   ![files-server-properties](/images/docs/help-servers/files-server-properties.png)
4. Save the file.
   ![open-files-server-proporties](/images/docs/help-servers/open-files-server-proporties.png)
5. Restart the server.

IMPORTANT:

- YOU MUST INSTALL AN AUTHENTICATION PLUGIN (e.g., AuthMe, xAuth or another trusted plugin). Without it, anyone can join with any nickname — including admin names — and perform any actions.
- Use a whitelist and manage permissions via trusted permission plugins (such as LuckPerms).
- Make backups before making changes.

While this setting allows non-premium players to join, we strongly recommend purchasing legitimate licenses for all players and using offline-mode only when absolutely necessary.
