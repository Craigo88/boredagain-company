# Domain Setup Guide for Bored Again Website

## Step 1: Purchase Domain

### Option A: .com Domain (Recommended - Most Universal)
- **Registrar**: Namecheap (you already have an account)
- **Domain**: `boredagain.com`
- **Cost**: ~$10-15/year
- **Purchase at**: https://www.namecheap.com/

### Option B: .com.au Domain (Australian Business)
- **Registrars**: VentraIP, Crazy Domains, NetRegistry
- **Domain**: `boredagain.com.au`
- **Cost**: ~$20-30/year
- **Requirement**: Must have ABN (which you have)

## Step 2: Configure DNS at Your Registrar

### If using Namecheap:

1. Log into Namecheap
2. Go to **Domain List** → Click **Manage** next to your domain
3. Go to **Advanced DNS** tab

#### Add A Records (for root domain - `boredagain.com`):
Click **Add New Record** and add these 4 A records:

| Type | Host | Value | TTL |
|------|------|-------|-----|
| A Record | @ | 185.199.108.153 | Automatic |
| A Record | @ | 185.199.109.153 | Automatic |
| A Record | @ | 185.199.110.153 | Automatic |
| A Record | @ | 185.199.111.153 | Automatic |

#### Add CNAME Record (for www subdomain):
Click **Add New Record**:

| Type | Host | Value | TTL |
|------|------|-------|-----|
| CNAME Record | www | craigo88.github.io | Automatic |

4. **Save** all changes

### If using other registrars:
- Follow the same DNS configuration pattern
- Add the 4 A records for root domain
- Add CNAME record for www subdomain

## Step 3: Configure Custom Domain in GitHub

1. Go to: https://github.com/Craigo88/boredagain-company/settings/pages
2. Scroll to **Custom domain** section
3. Enter your domain: `boredagain.com` (or `boredagain.com.au`)
4. Click **Save**
5. Wait a few minutes, then check **"Enforce HTTPS"** (will be available after DNS propagates)

## Step 4: Verify DNS Propagation

Wait 5 minutes to 2 hours, then verify:

```bash
# Check if DNS is configured correctly
dig boredagain.com
dig www.boredagain.com
```

Or use online tools:
- https://dnschecker.org/
- https://www.whatsmydns.net/

## Step 5: Test Your Website

Once DNS propagates:
- Visit: `https://boredagain.com` (or `https://boredagain.com.au`)
- Visit: `https://www.boredagain.com`

Both should show your website!

## Troubleshooting

### Domain not working after 24 hours?
- Verify DNS records are correct
- Check that GitHub Pages shows your custom domain
- Ensure "Enforce HTTPS" is checked (may take time to enable)

### SSL Certificate Issues?
- GitHub automatically provisions SSL certificates
- May take 24 hours after DNS propagation
- Keep "Enforce HTTPS" checked

## DNS Records Reference

**GitHub Pages IP Addresses** (for A records):
- 185.199.108.153
- 185.199.109.153
- 185.199.110.153
- 185.199.111.153

**GitHub Pages CNAME** (for www):
- craigo88.github.io

