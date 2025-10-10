---
title: "Linking Web Server to Domain"
description: "How to connect a Minecraft dynamic map or other web server to your domain via CloudFlare"
weight: 15
---

# How to Link a Dynamic Map/Other Web Server to a Domain?

If you have a web server (for example, a Minecraft dynamic map via Dynmap, BlueMap, or a server Panel), you can easily link it to your domain through Cloudflare. This takes literally **a couple of clicks**!

{{< callout type="info" >}}
**What can be linked to a domain:**
- 🗺️ Dynamic maps (Dynmap, BlueMap, Pl3xMap)
- 🎮 Server control panels (Pterodactyl, Multicraft)
- 🌐 Websites on your server
- 📊 Monitoring and statistics
- 🔧 Any other web service on your port
{{< /callout >}}

---

## How to Transfer Domain to Cloudflare?

If you don't have a domain on Cloudflare yet, you need to transfer it first:

### Quick Guide:

1. **Register on [Cloudflare](https://dash.cloudflare.com/sign-up)** (free)
2. **Add your domain** — click "Add Site" and enter your domain
3. **Choose a plan** — select the free plan (Free)
4. **Cloudflare will show your current DNS records** — review and confirm
5. **Change NS servers at your registrar** — Cloudflare will show 2 NS server addresses
6. **Log in to your registrar's website** (where you bought the domain) and replace NS servers with those provided by Cloudflare
7. **Wait** — DNS servers will update within 24-48 hours (usually faster)

{{< callout type="info" >}}
**Detailed domain transfer instructions:**
- [Official Cloudflare Documentation](https://developers.cloudflare.com/dns/zone-setups/full-setup/)
- [Video tutorial on YouTube](https://www.youtube.com/results?search_query=cloudflare+add+domain)
{{< /callout >}}

---

## Step-by-Step Web Server Linking Guide

### Step 1: Create an A Record with Proxying

1. Open Cloudflare dashboard
2. Select your domain
3. Go to **DNS** → **Records**
4. Click **Add record**

Fill in the fields:

| Field | Value | Description |
|-------|-------|-------------|
| **Type** | `A` | Record type |
| **Name** | `map` | Subdomain (you can choose any: `map`, `dynmap`, `web`, `panel`, etc.) |
| **IPv4 address** | `123.45.67.89` | Your server's IP address |
| **Proxy status** | 🟠 **ON** | Orange cloud must be **enabled**! |
| **TTL** | `Auto` | Leave unchanged |

{{< callout type="warning" >}}
**Important difference from Minecraft server setup:**

For a web server, Proxy Status (orange cloud) must be **ENABLED** (orange)!  
This allows using Cloudflare features, including port proxying.
{{< /callout >}}

**Configuration example:**

![A Record configuration with proxying](/images/docs/cloudflare/a-record-proxy.png)

Click **Save**.

---

### Step 2: Configure Origin Rules for Port Forwarding

Now you need to set up a rule that will redirect requests to the required port of your web server.

1. In Cloudflare dashboard, go to **Rules** → **Overview**
2. Click **Create rule**
3. Select **Origin rule**

![Menu Original Rules](/images/docs/cloudflare/rules-overview-original-rules.png)

#### Fill in the rule form:

**Rule name:**
```
Dynmap Port Forwarding
```
_(or any other name that makes sense to you)_

**When incoming requests match... (Condition):**

Select:
- **Field:** `URL Full`
- **Operator:** `wildcard`
- **Value:** `https://map.mhcore.xyz/*` _(your subdomain with A record)_

**Then... (Action):**

In the **Destination Port** section, select:
- **Rewrite to:** `25443` _(specify your web server's port)_

**Fill-in example:**

![Origin Rule configuration in Cloudflare](/images/docs/cloudflare/origin-rule.png)

---

### Step 3: Save and Deploy the Rule

1. Review all settings
2. Click **Deploy**
3. Cloudflare will apply the rule automatically

{{< callout type="success" >}}
**Done!** Now your web server is accessible at:
```
https://map.mhcore.xyz
```

Note: Cloudflare will automatically add **HTTPS** (SSL certificate), even if your server uses only HTTP!
{{< /callout >}}

---

## Step 4: Verify Functionality

1. Open a browser
2. Navigate to your subdomain address (e.g., `https://map.mhcore.xyz`)
3. You should see your dynamic map or web interface!

{{< callout type="info" >}}
**Please note:**
- First connection may take a few seconds
- SSL certificate is created automatically and for free
- Cloudflare will cache static files to speed up loading
{{< /callout >}}

---

## Multiple Web Services on One Domain

You can create multiple subdomains for different services:

### Structure Example:

| Subdomain | Service | Port | Origin Rule |
|-----------|---------|------|-------------|
| `map.mhcore.xyz` | Dynmap | 8123 | `URL Full wildcard map.mhcore.xyz` → Port `8123` |
| `bluemap.mhcore.xyz` | BlueMap | 8100 | `URL Full wildcard bluemap.mhcore.xyz` → Port `8100` |
| `panel.mhcore.xyz` | Pterodactyl | 8080 | `URL Full wildcard panel.mhcore.xyz` → Port `8080` |
| `stats.mhcore.xyz` | Statistics | 3000 | `URL Full wildcard stats.mhcore.xyz` → Port `3000` |

For each service:
1. Create a separate **A record** with proxying enabled
2. Create a separate **Origin Rule** with the corresponding port

---

## Benefits of Using Cloudflare

✅ **Free SSL** — automatic HTTPS for your site  
✅ **DDoS protection** — protection against attacks  
✅ **Caching** — faster loading of static files  
✅ **CDN** — your site will load faster worldwide  
✅ **IP hiding** — your server's real IP address will be hidden  
✅ **Analytics** — free visitor statistics

---

## Common Issues and Solutions

### ❌ Error 521 "Web server is down"

**Cause:** Cloudflare cannot connect to your server

**Solution:**
1. Check that the web server is running
2. Ensure the port is open in the firewall
3. Verify the IP address in the A record is correct
4. Make sure the port in Origin Rule is specified correctly

### ❌ Error 522 "Connection timed out"

**Cause:** Cloudflare cannot reach the server within the allotted time

**Solution:**
1. Check server accessibility from outside (via online port scanners)
2. Make sure the port is not blocked by the provider
3. Check firewall settings on the server

### ❌ Infinite loading or "Too many redirects"

**Cause:** Incorrect SSL/TLS settings

**Solution:**
1. Go to **SSL/TLS** → **Overview**
2. Set mode to **Flexible** (if your server doesn't use HTTPS)
3. Or set to **Full** (if your server uses a self-signed certificate)

### ❌ Page opens but styles/scripts don't load

**Cause:** Mixed Content — HTTPS page loading HTTP resources

**Solution:**
1. Go to **SSL/TLS** → **Edge Certificates**
2. Enable **Always Use HTTPS**
3. Enable **Automatic HTTPS Rewrites**

---

## SSL/TLS Configuration

For correct web server operation through Cloudflare, configure SSL:

1. Go to **SSL/TLS** → **Overview**
2. Choose the appropriate mode:

| Mode | When to Use |
|------|-------------|
| **Flexible** | Your server uses only HTTP (no SSL) |
| **Full** | Your server uses HTTPS with self-signed certificate |
| **Full (strict)** | Your server uses HTTPS with trusted certificate |

{{< callout type="info" >}}
**Recommendation:** For most cases (Dynmap, simple web servers), use **Flexible** mode.
{{< /callout >}}

---

## Usage Examples

### Example 1: Dynmap for Minecraft Server

```
Domain: map.mhcore.xyz
IP: 123.45.67.89
Dynmap Port: 8123

A Record:
- Name: map
- IP: 123.45.67.89
- Proxy: ON

Origin Rule:
- URL Full wildcard https://map.mhcore.xyz/*
- Rewrite to port 8123
```

Result: `https://map.mhcore.xyz` will show your Dynmap!

### Example 2: Pterodactyl Control Panel

```
Domain: panel.mhcore.xyz
IP: 123.45.67.89
Panel Port: 8080

A Record:
- Name: panel
- IP: 123.45.67.89
- Proxy: ON

Origin Rule:
- URL Full wildcard https://panel.mhcore.xyz/*
- Rewrite to port 8080
```

Result: `https://panel.mhcore.xyz` will open the control panel!

---

## Useful Links

- [Official Cloudflare Rules Documentation](https://developers.cloudflare.com/rules/)
- [Cloudflare SSL/TLS Configuration](https://developers.cloudflare.com/ssl/)
- [Troubleshooting Cloudflare Errors](https://developers.cloudflare.com/support/troubleshooting/)

{{< callout type="info" >}}
**Need help?**

If you encounter difficulties setting up a web server through Cloudflare, contact your hosting support or Cloudflare community forums.
{{< /callout >}}

---