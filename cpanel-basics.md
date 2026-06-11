# cPanel Basics

## Overview

cPanel is a web hosting control panel used to manage websites, domains, files, databases, email accounts, SSL certificates, backups, and other hosting features.

This document provides beginner-friendly cPanel notes for IT support, website support, small business web administration, and hosting troubleshooting.

## Purpose

This guide demonstrates practical knowledge of:

- cPanel navigation
- File Manager
- Domain management
- DNS basics
- Email accounts
- SSL certificates
- Backups
- Databases
- Common website support tasks

## What cPanel Is Used For

cPanel helps website owners and support technicians manage hosting tasks without needing to use only the command line.

Common cPanel tasks include:

- Uploading website files
- Managing domains and subdomains
- Creating email accounts
- Managing DNS records
- Installing SSL certificates
- Creating backups
- Managing MySQL databases
- Viewing website errors
- Checking storage and bandwidth usage

## Common cPanel Sections

| Section | Purpose |
|---|---|
| File Manager | Upload, edit, delete, and organize website files |
| Domains | Manage domains, subdomains, redirects, and document roots |
| Zone Editor | Manage DNS records |
| Email Accounts | Create and manage email mailboxes |
| SSL/TLS | Manage SSL certificates |
| Backup | Download website and database backups |
| MySQL Databases | Create and manage databases |
| phpMyAdmin | View and manage database tables |
| Metrics | View visitors, bandwidth, and errors |
| Security | Manage SSL, hotlink protection, IP blocker, and other tools |

## File Manager Basics

File Manager is used to manage website files.

Common website folder:

```text
public_html
```

For the main domain, website files are usually uploaded into:

```text
/public_html/
```

Common website files:

| File | Purpose |
|---|---|
| `index.html` | Main homepage for static websites |
| `index.php` | Main PHP homepage, common for WordPress |
| `style.css` | Website styling |
| `script.js` | Website JavaScript |
| `.htaccess` | Apache configuration rules |
| `wp-config.php` | WordPress database configuration |

## Uploading Website Files

Basic upload process:

1. Log in to cPanel.
2. Open **File Manager**.
3. Go to `public_html`.
4. Upload the website ZIP file.
5. Extract the ZIP file.
6. Confirm `index.html` or `index.php` is directly inside `public_html`.
7. Visit the domain in a browser.
8. Test pages, links, images, forms, and mobile layout.

## Common Upload Mistake

A common issue is uploading a folder inside `public_html` instead of the actual site files.

Incorrect:

```text
public_html/my-website/index.html
```

Correct for main domain:

```text
public_html/index.html
```

If the files are inside an extra folder, the website may not show properly at the main domain.

## Domain Management

cPanel may support:

- Primary domain
- Addon domains
- Subdomains
- Aliases
- Redirects

Example subdomain:

```text
support.example.com
```

Example document root:

```text
public_html/support
```

## DNS Zone Editor

The DNS Zone Editor is used to manage records such as:

| Record | Purpose |
|---|---|
| A | Points a domain to an IPv4 address |
| AAAA | Points a domain to an IPv6 address |
| CNAME | Points one hostname to another hostname |
| MX | Controls email delivery |
| TXT | Stores SPF, DKIM, DMARC, and verification records |

## Email Accounts

cPanel can create domain email accounts such as:

```text
info@example.com
support@example.com
admin@example.com
```

Common email settings:

| Protocol | Purpose |
|---|---|
| IMAP | Sync email across devices |
| POP3 | Download email to one device |
| SMTP | Send outgoing email |

## SSL/TLS

SSL secures website traffic using HTTPS.

A secure website starts with:

```text
https://
```

SSL issues may cause browser warnings such as:

```text
Your connection is not private
```

Common SSL tasks:

- Install SSL certificate
- Renew SSL certificate
- Force HTTPS
- Fix mixed content issues
- Confirm certificate matches domain

## Backup Basics

Backups are important before making website changes.

Common backup items:

- Website files
- Databases
- Email data
- DNS settings
- Configuration files

Before making major changes, download a full backup or at minimum back up `public_html` and databases.

## Database Basics

Dynamic websites like WordPress often use MySQL databases.

Common database tasks:

- Create database
- Create database user
- Assign user permissions
- Import database
- Export database
- Update configuration file

WordPress database connection file:

```text
wp-config.php
```

## Metrics and Logs

cPanel may provide:

- Visitors
- Bandwidth
- Raw access logs
- Error logs
- Resource usage
- Disk usage

These help troubleshoot:

- Website errors
- High traffic
- Missing files
- PHP errors
- Storage limits

## Common cPanel Support Issues

| Issue | Possible Cause | Basic Check |
|---|---|---|
| Website not loading | Files in wrong folder | Check `public_html` |
| 403 error | Permission or missing index file | Check file permissions and homepage file |
| 404 error | Missing file or wrong link | Confirm file path |
| SSL warning | Certificate issue or mixed content | Check SSL/TLS and HTTPS |
| Contact form not sending | SMTP or PHP mail issue | Check email settings |
| Email not working | MX/DNS issue | Check DNS and email account |
| Database error | Wrong credentials | Check database config |
| Site broken after upload | Missing files | Re-upload and verify structure |

## Best Practices

- Back up files before changes.
- Keep website files organized.
- Confirm the correct document root.
- Use HTTPS.
- Avoid editing live files without a backup.
- Use strong passwords.
- Do not share cPanel login details.
- Keep CMS platforms and plugins updated.
- Document DNS and website changes.
- Test website after every major change.

## Example Ticket Note

```text
User reported website showing default hosting page.
Logged in to cPanel and checked File Manager.
Confirmed website files were uploaded inside an extra folder under public_html.
Moved index.html, assets, CSS, and JS files directly into public_html.
Cleared browser cache and retested domain.
Website loaded successfully.
Ticket resolved.
```

## Skills Demonstrated

- cPanel navigation
- Website file management
- Domain and DNS awareness
- SSL support basics
- Email account awareness
- Backup awareness
- Website support documentation
