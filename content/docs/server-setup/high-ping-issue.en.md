---
title: "Players Have High Ping — What to Do?"
description: "How to troubleshoot and fix high ping issues on a Minecraft server using WinMTR for network diagnostics"
weight: 30
---

## Problem

Are players experiencing high ping on your server? Don't worry — we'll help you diagnose and solve this issue.

## Common Causes

Before proceeding with diagnostics, check the following common causes of high ping:

- **Unloaded chunks** — ensure the server can handle chunk loading properly
- **Paper AntiXray in mode 2 or 3** — these modes can create additional load. Try switching to mode 1 or disabling it

If fixing these causes doesn't help, proceed to the next step.

## Diagnostics with WinMTR

### What is WinMTR?

{{< callout type="info" >}}
**WinMTR** is a free, open-source utility that combines the functionality of traceroute and ping, providing detailed information about network packet routing.
{{< /callout >}}

### Instructions for Players

Ask all players experiencing high ping to follow these steps:

#### 1. Download WinMTR

Download WinMTR from the official repository: [WinMTR Releases](https://github.com/White-Tiger/WinMTR/releases)

#### 2. Run the Trace

- **Important:** Disable all VPN, PROXY, and similar services before starting the trace
- In the **"Host"** field of WinMTR, enter **only the IP address** of your server, **without the port**
  
  **Example:** If the server address is `192.168.1.1:27015`, enter only `192.168.1.1`

#### 3. Collect Data

1. Click the **"Start"** button to begin the trace
2. Wait **2-3 minutes** to collect statistics for each node on the path to the server
3. Click the **"Stop"** button to stop the test
4. Save the results by clicking **"Export TXT"**

#### 4. Find Your External IP Address

{{< callout type="info" >}}
You can find your external IP address on any IP detection service, for example: [2ip.ru](https://2ip.ru/)
{{< /callout >}}

## Contacting Technical Support

After completing these steps, create a support ticket and provide the following data:

1. **WinMTR trace result** (.txt file)
2. **Player's IP address** corresponding to the trace result
3. Description of the issue and the time when high ping was observed

Our support team will analyze the data and help resolve the issue.

---

## Additional Tips

- Advise players to check the stability of their internet connection
- Verify that the server is not overloaded (CPU, RAM, disk)
- Ensure optimized plugins and settings are installed on the server
