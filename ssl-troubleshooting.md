# SSL Troubleshooting

## Overview

SSL certificates secure websites by enabling HTTPS. SSL issues can cause browser warnings, broken trust, failed form submissions, SEO problems, and user confidence issues.

This guide explains common SSL problems and practical troubleshooting steps for cPanel-hosted websites.

## Purpose

This document demonstrates knowledge of:

- HTTPS and SSL basics
- cPanel SSL/TLS tools
- AutoSSL
- Certificate coverage
- Mixed content issues
- DNS-related SSL problems
- Safe troubleshooting steps

## What SSL Does

SSL/TLS encrypts traffic between the visitor's browser and the website.

A secure website uses:

```text
https://example.com
```

A website without SSL uses:

```text
http://example.com
```

## Common SSL Symptoms

Users may report:

- Browser says connection is not private
- HTTPS does not work
- Website loads with HTTP only
- SSL certificate expired
- SSL certificate name mismatch
- Padlock missing
- Images or scripts blocked
- Contact form fails on HTTPS
- Mixed content warnings
- AutoSSL failed

## Common Browser Warnings

Examples:

```text
Your connection is not private
NET::ERR_CERT_DATE_INVALID
NET::ERR_CERT_COMMON_NAME_INVALID
Mixed content warning
```

## Step 1: Confirm the Exact URL

Test both versions:

```text
http://example.com
https://example.com
http://www.example.com
https://www.example.com
```

Check whether SSL works on:

- Root domain
- WWW version
- Subdomains
- Addon domains

## Step 2: Check DNS

SSL issuance usually requires the domain to point to the correct hosting server.

Check DNS:

```cmd
nslookup example.com
nslookup www.example.com
```

If the domain points to the wrong IP address, SSL may fail.

## Step 3: Check cPanel SSL/TLS Status

In cPanel:

1. Open **SSL/TLS Status**.
2. Select the domain.
3. Check certificate status.
4. Run AutoSSL if available.
5. Confirm certificate covers:
   - `example.com`
   - `www.example.com`
   - required subdomains

## Step 4: Check Certificate Expiration

If SSL certificate is expired:

- Run AutoSSL
- Renew certificate
- Confirm domain DNS points correctly
- Check hosting provider SSL tools
- Escalate if renewal fails

## Step 5: Check Certificate Name Mismatch

A mismatch happens when the certificate does not match the domain.

Example:

```text
Certificate issued to olddomain.com
User visits newdomain.com
```

Fix:

- Install certificate for correct domain
- Confirm domain is added to hosting account
- Confirm DNS points to correct server
- Run AutoSSL again

## Step 6: Force HTTPS

If SSL works but site still loads HTTP, force HTTPS.

Common `.htaccess` redirect example:

```apache
RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
```

Before editing `.htaccess`, back it up.

## Step 7: Check Mixed Content

Mixed content happens when an HTTPS page loads HTTP resources.

Example:

```text
Page: https://example.com
Image: http://example.com/image.jpg
```

Fix:

- Update links from `http://` to `https://`
- Use relative paths
- Update CMS site URL settings
- Replace old database URLs if needed
- Clear cache

Common affected resources:

- Images
- CSS files
- JavaScript files
- Fonts
- Embedded videos
- Tracking scripts

## Step 8: Check WordPress SSL Settings

For WordPress:

- Confirm WordPress Address uses HTTPS
- Confirm Site Address uses HTTPS
- Update mixed content URLs
- Clear cache plugin
- Check `.htaccess`
- Confirm SSL plugin settings if used

WordPress settings:

```text
Settings > General
WordPress Address (URL): https://example.com
Site Address (URL): https://example.com
```

## Step 9: Check AutoSSL Failure Causes

AutoSSL may fail if:

- Domain points to wrong server
- DNS has not propagated
- Domain is blocked by CAA record
- HTTP validation file cannot be reached
- Website has redirect loop
- Domain is not added to cPanel
- Rate limit is reached
- Firewall blocks validation

## Useful Commands

### Check domain DNS

```cmd
nslookup example.com
nslookup www.example.com
```

### Linux/macOS DNS check

```bash
dig example.com
dig www.example.com
```

### Test HTTPS with curl

```bash
curl -I https://example.com
```

### Check HTTP redirect

```bash
curl -I http://example.com
```

## Common SSL Issues and Fixes

| Issue | Possible Cause | Fix |
|---|---|---|
| SSL expired | Certificate not renewed | Run AutoSSL or renew cert |
| Name mismatch | Certificate for wrong domain | Install correct certificate |
| HTTPS not forcing | No redirect | Add HTTPS redirect |
| Mixed content | HTTP resources on HTTPS page | Update URLs to HTTPS |
| AutoSSL fails | DNS points wrong | Fix DNS and rerun AutoSSL |
| WWW not secure | Certificate missing WWW | Include www in certificate |
| Subdomain not secure | Subdomain not covered | Issue certificate for subdomain |

## SSL Testing Checklist

| Check | Status |
|---|---|
| Root domain DNS points correctly | Pending |
| WWW DNS points correctly | Pending |
| SSL certificate installed | Pending |
| Certificate not expired | Pending |
| Certificate covers root domain | Pending |
| Certificate covers www | Pending |
| HTTPS loads | Pending |
| HTTP redirects to HTTPS | Pending |
| No mixed content warnings | Pending |
| Contact form works over HTTPS | Pending |

## Example Ticket Note

```text
User reported browser warning on website.
Tested https://example.com and confirmed SSL certificate name mismatch.
Checked cPanel SSL/TLS Status and found certificate did not include www version.
Confirmed DNS for www pointed to correct hosting server.
Ran AutoSSL and issued certificate covering example.com and www.example.com.
Tested HTTPS on both versions and confirmed browser padlock displayed.
Ticket resolved.
```

## Escalation Criteria

Escalate if:

- AutoSSL repeatedly fails
- DNS changes are required
- Certificate authority errors appear
- CAA record blocks certificate issuance
- Website has redirect loop
- Mixed content requires database changes
- Production checkout/payment pages are affected
- Hosting provider support is required

## Skills Demonstrated

- SSL troubleshooting
- cPanel AutoSSL awareness
- DNS validation checks
- HTTPS redirect configuration
- Mixed content troubleshooting
- Website support documentation
