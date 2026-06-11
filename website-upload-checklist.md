# Website Upload Checklist

## Overview

This checklist explains how to upload a website to cPanel hosting using File Manager. It is useful for static HTML websites, small business websites, landing pages, and basic website support tasks.

## Purpose

This checklist demonstrates knowledge of:

- Preparing website files
- Uploading to cPanel
- Extracting ZIP files
- Checking folder structure
- Testing website pages
- Troubleshooting common upload issues

## Before Uploading

Confirm the website package includes:

- `index.html` or `index.php`
- CSS files
- JavaScript files
- Images
- Fonts, if used
- Assets folder
- Form files, if used
- `.htaccess`, if required
- Any required documentation

Example static website structure:

```text
website-project/
├── index.html
├── about.html
├── contact.html
├── css/
│   └── style.css
├── js/
│   └── script.js
└── images/
    └── logo.png
```

## Pre-Upload Checklist

| Check | Status |
|---|---|
| Website opens locally | Pending |
| Homepage file is named `index.html` or `index.php` | Pending |
| Images load correctly | Pending |
| CSS loads correctly | Pending |
| JavaScript works | Pending |
| Navigation links work | Pending |
| Contact form reviewed | Pending |
| ZIP file created | Pending |
| Backup of existing site completed | Pending |

## Step 1: Back Up Existing Website

Before uploading a new website, back up the current files.

In cPanel:

1. Open **File Manager**.
2. Go to `public_html`.
3. Select existing files.
4. Compress them into a ZIP file.
5. Download the backup.

Suggested backup name:

```text
website-backup-YYYY-MM-DD.zip
```

## Step 2: Log In to cPanel

1. Go to the hosting provider login page.
2. Open cPanel.
3. Open **File Manager**.

## Step 3: Open the Correct Folder

For the main domain, open:

```text
public_html
```

For an addon domain or subdomain, check the document root.

Examples:

```text
public_html
public_html/subdomain
public_html/addon-domain
```

## Step 4: Upload the ZIP File

1. Click **Upload**.
2. Select the website ZIP file.
3. Wait for upload to complete.
4. Return to File Manager.

## Step 5: Extract the ZIP File

1. Right-click the ZIP file.
2. Select **Extract**.
3. Confirm extraction location.
4. Open the extracted folder.

## Step 6: Confirm File Structure

The homepage file must be in the correct document root.

Correct:

```text
public_html/index.html
public_html/css/style.css
public_html/js/script.js
public_html/images/logo.png
```

Incorrect:

```text
public_html/website-project/index.html
```

If files are inside an extra folder, move the contents into `public_html`.

## Step 7: Set File Permissions

Common permissions:

| Item | Permission |
|---|---|
| Files | `644` |
| Folders | `755` |

Avoid using:

```text
777
```

unless specifically required in a controlled lab environment.

## Step 8: Test Website

Open the website in a browser.

Test:

- Homepage
- Navigation menu
- Mobile view
- Images
- Buttons
- Contact form
- Booking links
- External links
- Page speed
- HTTPS
- Footer links

## Step 9: Clear Cache

If old content appears:

- Clear browser cache
- Try private/incognito window
- Clear website cache if a CMS is used
- Clear CDN cache if Cloudflare or another CDN is used

## Step 10: Remove Upload ZIP

After confirming the website works:

1. Delete the uploaded ZIP file from `public_html`.
2. Keep a backup copy outside the live website folder.
3. Confirm no unnecessary files are publicly accessible.

## Common Upload Issues

| Issue | Possible Cause | Fix |
|---|---|---|
| Website shows old page | Browser or server cache | Clear cache |
| Website shows file list | Missing `index.html` or `index.php` | Add homepage file |
| CSS not loading | Wrong path | Check folder and file names |
| Images missing | Wrong path or case-sensitive filename | Confirm exact filename |
| 404 error | File missing or wrong URL | Check file path |
| 403 error | Permission issue or missing index file | Check permissions and homepage |
| Contact form not sending | SMTP/PHP mail issue | Configure SMTP |
| SSL warning | Certificate or mixed content issue | Check SSL and links |

## Post-Upload Checklist

| Check | Status |
|---|---|
| Website loads on main domain | Pending |
| HTTPS works | Pending |
| All pages open | Pending |
| Navigation works | Pending |
| Images display | Pending |
| Contact form tested | Pending |
| Mobile layout checked | Pending |
| Backup saved | Pending |
| Upload ZIP removed | Pending |
| Client/user notified | Pending |

## Example Ticket Note

```text
Uploaded new static website files to cPanel File Manager.
Backed up existing public_html folder before changes.
Uploaded and extracted website ZIP package.
Moved site files directly into public_html and confirmed index.html was present.
Tested homepage, navigation, images, mobile view, and contact page.
Removed upload ZIP after successful testing.
Website is live and working.
```

## Skills Demonstrated

- cPanel File Manager usage
- Website upload process
- File structure troubleshooting
- Website testing
- Backup awareness
- Technical documentation
