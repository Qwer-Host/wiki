---
title: "Disabling Encrypted Client Hello (ECH)"
description: "Comprehensive guide to disabling ECH on CloudFlare's free tier via API"
weight: 10
---

# Disabling Encrypted Client Hello (ECH) on Cloudflare Free Tier via API

## Why Disable ECH?

Roskomnadzor (Russian telecommunications regulator) has blocked the **Encrypted Client Hello (ECH)** technology, causing issues for Cloudflare users in Russia. Moreover, Cloudflare has forcibly enabled this technology for all users, including those on the free tier.

This guide will show you how to disable ECH for your domain using the Cloudflare API.

{{< callout type="warning" >}}
**For users from Russia:** Disabling ECH may be necessary to ensure your website's accessibility for Russian users due to Roskomnadzor's blocking of this technology.
{{< /callout >}}

---

## Step 1: Check if ECH is Enabled

Before disabling ECH, verify whether it's enabled for your domain. You can do this using a Google Public DNS query:

1. Navigate to the following link, replacing `[YOUR_DOMAIN]` with your domain name:

```url
https://dns.google/resolve?name=[YOUR_DOMAIN]&type=HTTPS
```

2. If the results show that ECH is active, proceed to the next step.

{{< callout type="info" >}}
**Example:** For the domain `example.com`, the link would look like:
```
https://dns.google/resolve?name=example.com&type=HTTPS
```
{{< /callout >}}

---

## Step 2: Obtain Cloudflare API Credentials

To interact with the API, you'll need two key elements:

### Global API Key

1. Go to the [Cloudflare profile page](https://dash.cloudflare.com/profile/api-tokens)
2. Find the section with your **Global API Key** and copy the key

{{< callout type="warning" >}}
**Important:** The Global API Key provides full access to your account. Never share it with third parties and store it securely!
{{< /callout >}}

### Zone ID

1. Log in to your domain's Cloudflare dashboard
2. Scroll down the page in the right column
3. Copy the **Zone ID** value

{{< callout type="info" >}}
Zone ID is the unique identifier for your domain in the Cloudflare system.
{{< /callout >}}

---

## Step 3: Disable ECH via Cloudflare API

### Method 1: Using curl Command

To disable ECH, execute the following command in your terminal, replacing `{ID_ZONE}`, `{ACCOUNT_EMAIL}`, and `{GLOBAL_API_KEY}` with your data:

```bash
curl -X PATCH "https://api.cloudflare.com/client/v4/zones/{ID_ZONE}/settings/ech" \
     -H "X-Auth-Email: {ACCOUNT_EMAIL}" \
     -H "X-Auth-Key: {GLOBAL_API_KEY}" \
     -H "Content-Type: application/json" \
     --data '{"id":"ech","value":"off"}'
```

**Example:**
```bash
curl -X PATCH "https://api.cloudflare.com/client/v4/zones/abc123def456/settings/ech" \
     -H "X-Auth-Email: user@example.com" \
     -H "X-Auth-Key: c2547eb745079dac9320b638f5e225cf483cc5cfdda41" \
     -H "Content-Type: application/json" \
     --data '{"id":"ech","value":"off"}'
```

{{< callout type="success" >}}
Upon successful execution, you'll receive a JSON response confirming the setting change.
{{< /callout >}}

### Method 2: Using Postman

You can execute this request through **Postman** by following these instructions:

#### 1. Request Setup

- **Method:** `PATCH`
- **URL:**
```
https://api.cloudflare.com/client/v4/zones/{ID_ZONE}/settings/ech
```

#### 2. Headers Setup

In the **Headers** section, add the following fields:

| Key | Value |
|-----|-------|
| `X-Auth-Email` | your Cloudflare email address |
| `X-Auth-Key` | your Global API Key |
| `Content-Type` | `application/json` |

#### 3. Body Setup

In the **Body** section, select `raw` and `JSON`, then enter:

```json
{
  "id": "ech",
  "value": "off"
}
```

#### 4. Send Request

Click the **Send** button and wait for the server response.

---

## Method 3: For Paid Plans

If you're using a **paid Cloudflare plan**, you can disable ECH through the dashboard interface:

1. Navigate to the **SSL/TLS** section
2. Open the **Edge Certificates** tab
3. Find the **Encrypted ClientHello (ECH)** setting
4. Set the value to **Disabled**

{{< callout type="info" >}}
**Note:** This option is only available for paid plan users (Pro, Business, Enterprise).
{{< /callout >}}

---

## Verify the Results

After disabling ECH, it's recommended to verify the changes:

1. Wait 5-10 minutes for the settings to apply
2. Run the Google Public DNS check again (Step 1)
3. Check your website's accessibility for users from Russia

{{< callout type="success" >}}
**Done!** ECH is now disabled for your domain, and the site should be accessible to Russian users.
{{< /callout >}}

---

## Common Issues and Solutions

### Authentication Error

**Problem:** Receiving `Authentication error` or `Invalid credentials`

**Solution:**
- Verify your email address is correct
- Ensure you've copied the Global API Key completely
- Check that you haven't added extra spaces when copying

### Zone ID Error

**Problem:** Receiving `Zone not found` error

**Solution:**
- Make sure the Zone ID is copied correctly
- Verify you're using the Zone ID for the domain you want to modify

### ECH Doesn't Disable

**Problem:** After executing the command, ECH remains enabled

**Solution:**
- Wait 10-15 minutes for changes to apply
- Clear the DNS cache on your device
- Retry the API request

---

## Additional Resources

- [Official Cloudflare API Documentation](https://api.cloudflare.com/)
- [SSL/TLS Configuration Guide for Cloudflare](https://developers.cloudflare.com/ssl/)
- [Cloudflare Community](https://community.cloudflare.com/)

{{< callout type="info" >}}
**Need help?** If you encounter difficulties disabling ECH, contact Cloudflare support or community forums.
{{< /callout >}}
