---
title: "Minecraft Server Cores"
description: "Complete guide to choosing Minecraft server cores in 2025"
weight: 20
---

In the era of Minecraft 1.21+ and beyond, choosing a server core isn't just a technical detail—it's a strategic decision that determines stability, performance, and the uniqueness of your world. 

But with an abundance of forks, proxies, and hybrids, it's easy to get confused. We'll break down key options by categories, based on current trends in 2025: from performance focus to mod support.

{{< callout type="info" >}}
**Recommendation Legend:**
- ✅ — Top choice for 2025
- ❓ — Experimental option
- ❌ — Not recommended
- 💀 — Outdated/abandoned
{{< /callout >}}

## Vanilla Cores: Foundation for Plugins and Optimizations

Vanilla cores are the foundation for Bukkit/Spigot API servers, ideal for multiplayer with plugins. They've evolved from simple Vanilla to high-performance forks like Paper. In 2025, the focus is on async improvements and compatibility with the latest Minecraft versions (1.21+).

{{< tabs items="Recommended,Outdated" >}}

{{< tab >}}
### Top Cores for 2025

| Core | Description | Recommendation | Key Features |
|------|-------------|----------------|--------------|
| **Paper** | Spigot fork with deep optimizations: async chunk processing, dupe fixes, and support for all Bukkit/Spigot/Paper plugins | ✅ | High stability, paper.yml configs for fine-tuning |
| **Pufferfish** | Paper fork with additional patches for large servers: improved entity handling and SIMD instructions | ✅ | Better than Paper for 100+ players; use `--add-modules=jdk.incubator.vector` flag |
| **Purpur** | Pufferfish/Paper fork focused on customization: thousands of options in purpur.yml for changing mechanics | ✅ | For serious projects; inherits all optimizations + "fun" options |
| **Leaf** | Experimental Purpur fork with patches from multiple sources | ❓ | Multithreaded entity processing, but may be unstable |

{{< /tab >}}

{{< tab >}}
### Outdated Options

| Core | Description | Recommendation | Why to Avoid |
|------|-------------|----------------|--------------|
| **Vanilla** | Original Mojang core without plugins | ❌ | No mod/plugin support; Paper is backward compatible |
| **CraftBukkit** | First core with Bukkit plugins | ❌ | Doesn't support modern plugins; replaced by Spigot |
| **Spigot** | CraftBukkit fork with basic optimizations | ❌ | Lags on large servers; Paper is drop-in replacement |

{{< /tab >}}

{{< /tabs >}}

{{< callout type="tip" >}}
**Tip:** Start with Paper — it's free, easy to install, and covers 90% of needs. For networks with 200+ players, move to Pufferfish/Purpur.
{{< /callout >}}

## Proxy Cores: For Server Networks and Protection

Proxy cores connect multiple servers into a network (e.g., hub + minigames), adding load balancing and anti-DDoS. In 2025, Velocity leads due to speed and security.

| Core | Description | Recommendation | Key Features |
|------|-------------|----------------|--------------|
| **Velocity** | Modern proxy from Paper team: high performance, built-in mod support | ✅ | Scalability for thousands of players; API for custom features |
| **NullCordX** | Paid Waterfall fork focused on antibot and DDoS protection | ✅ (paid) | Active updates, low ping; from $10/month |
| **BungeeCord** | Original proxy: basic but full of security holes | ❌ | Outdated; use Waterfall as replacement |
| **Waterfall** | BungeeCord fork with vulnerability fixes | 💀 | Support discontinued; migration to Velocity |

{{< callout type="warning" >}}
**Important:** Velocity is the #1 choice for 2025. It's 2-3x faster than Waterfall and supports modern features.
{{< /callout >}}

## Mod Cores: For Deep Customization with Mods

Mod loaders allow adding content: new blocks, biomes, mechanics. In 2025, Fabric leads in popularity thanks to fast updates.

{{< tabs items="Modern,Legacy" >}}

{{< tab >}}
### Current Loaders

| Core | Description | Recommendation | Features |
|------|-------------|----------------|----------|
| **Fabric** | Lightweight and fast modloader: quick adaptation to new versions | ✅ | Popular for 1.21+; easy installation, low overhead |
| **Quilt** | Fabric fork with improvements: more features for modders | ✅ | Compatible with Fabric mods; extended APIs |
| **NeoForge** | Forge fork without legacy mod support: focus on stability | ✅ | Faster than Forge; growing ecosystem |

{{< /tab >}}

{{< tab >}}
### Legacy Options

| Core | Description | Recommendation | Status |
|------|-------------|----------------|--------|
| **Forge** | Classic modloader with huge mod library | ❓ | Heavy and slow to update |

{{< /tab >}}

{{< /tabs >}}

{{< callout type="tip" >}}
**Tip:** Choose Fabric/Quilt for fresh modpacks — they're lighter and update faster. NeoForge — if you're a Forge mod fan.
{{< /callout >}}

## Hybrids: Mod and Plugin Combo

{{< callout type="warning" >}}
**Important Warning:** Plugins on hybrids work unstably; don't expect developer support. Risk of crashes and vulnerabilities is high.
{{< /callout >}}

| Core | Description | Recommendation | Status |
|------|-------------|----------------|--------|
| **Arclight** | Actively developed: supports Forge/NeoForge/Fabric mods + Bukkit plugins | ✅ | More stable than alternatives; for 1.21.1+ |
| **Ketting** | Based on Forge: supports Bukkit/Spigot/Paper plugins + Forge mods | ❓ | Active for new versions |
| **CatServer** | Similar to Ketting: Forge + limited versions with Bukkit plugins | ❓ | Limited version support |
| **Mohist** | Forge + Bukkit/Spigot/Paper plugins | 💀 | Outdated with security risks |

## Conclusion: Choose Core for Your Server

In 2025, recommendations are simple:

- **For plugin servers:** Paper → Pufferfish → Purpur (by increasing complexity)
- **For networks:** Velocity
- **For mods:** Fabric/Quilt for new projects, NeoForge for Forge legacy
- **For hybrids:** Arclight, Mohist with caution

{{< callout type="info" >}}
**Start with test server:** download from official sites (papermc.io, fabricmc.net, neoforged.net) and monitor with Spark plugin.
{{< /callout >}}

Avoid outdated ones like Spigot or BungeeCord — they're vulnerable and slow. If your project grows, invest in hosting with Aikar's JVM flags for +20% performance.

Now your server is ready to work! 🚀

## Useful Links

- [Paper MC](https://papermc.io/) - Official Paper website
- [Fabric MC](https://fabricmc.net/) - Official Fabric website  
- [NeoForged](https://neoforged.net/) - Official NeoForge website
- [Velocity](https://velocitypowered.com/) - Official Velocity website
