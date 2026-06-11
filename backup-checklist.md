# Website Backup Checklist

## Overview

Website backups are essential before making changes to a website, updating files, editing DNS, changing databases, installing plugins, or migrating hosting.

This checklist explains what to back up in a cPanel hosting environment and how to document backup activity.

## Purpose

This document demonstrates knowledge of:

- Website file backups
- Database backups
- cPanel backup tools
- Email backup awareness
- Backup verification
- Safe change preparation
- Recovery planning

## Why Backups Matter

Backups protect against:

- Accidental file deletion
- Broken website updates
- Malware or compromise
- Failed plugin/theme updates
- Database corruption
- Hosting migration issues
- User error
- DNS or configuration mistakes

## Backup Types

| Backup Type | Description |
|---|---|
| Full account backup | Includes website files, databases, email, DNS, and account settings |
| Home directory backup | Includes website files and account files |
| Database backup | Includes MySQL database content |
| Email backup | Includes mailboxes or email data |
| Manual file backup | ZIP copy of selected website folders |
| Offsite backup | Backup stored outside hosting account |

## Before Making Changes

Back up before:

- Uploading a new website
- Editing `public_html`
- Updating WordPress
- Updating plugins or themes
- Changing DNS records
- Editing `.htaccess`
- Changing PHP version
- Editing database
- Migrating website
- Installing SSL or redirect rules

## cPanel Full Backup

In cPanel:

1. Open **Backup** or **Backup Wizard**.
2. Select **Full Backup**.
3. Choose backup destination.
4. Generate backup.
5. Download backup when ready.
6. Store backup securely.

Suggested naming:

```text
full-backup-example.com-YYYY-MM-DD.tar.gz
```

## Manual File Backup

To back up website files:

1. Open **File Manager**.
2. Go to `public_html`.
3. Select website files and folders.
4. Click **Compress**.
5. Create ZIP archive.
6. Download ZIP file.

Suggested name:

```text
public_html-backup-YYYY-MM-DD.zip
```

## Database Backup

Dynamic websites such as WordPress usually need database backups.

In cPanel:

1. Open **Backup**.
2. Download MySQL database backup.

Or use phpMyAdmin:

1. Open **phpMyAdmin**.
2. Select database.
3. Click **Export**.
4. Choose Quick or Custom export.
5. Download `.sql` file.

Suggested name:

```text
database-backup-YYYY-MM-DD.sql
```

## WordPress Backup Items

For WordPress, back up:

| Item | Purpose |
|---|---|
| `wp-content` | Themes, plugins, uploads |
| `wp-config.php` | Database connection settings |
| Database | Posts, pages, users, settings |
| `.htaccess` | Rewrite and redirect rules |
| Custom code | Theme edits or snippets |

## Email Backup Awareness

If cPanel email is used, consider email data.

Important email items:

- Mailboxes
- Forwarders
- Filters
- Autoresponders
- MX records
- SPF/DKIM/DMARC records

Email backup methods vary by hosting provider.

## DNS Backup

Before changing DNS records, record current values.

DNS documentation example:

```text
Domain: example.com
Record: A
Host: @
Value: 192.0.2.10
TTL: 14400
Date recorded: YYYY-MM-DD
```

Take screenshots or copy records into a change document.

## Backup Verification

A backup is only useful if it can be restored.

Verify:

- Backup file downloaded successfully
- File size looks reasonable
- ZIP or archive opens
- Database `.sql` file is not empty
- Backup stored outside live website folder
- Backup date is documented
- Restore process is understood

## Backup Storage Best Practices

Store backups:

- On a secure local drive
- In approved cloud storage
- In an external backup system
- Outside the live `public_html` folder

Avoid:

- Leaving backup ZIP files publicly accessible
- Storing passwords inside public folders
- Uploading sensitive backups to public GitHub repositories
- Keeping only one backup copy

## Backup Security

Backups may contain sensitive information such as:

- Customer form submissions
- User accounts
- Database credentials
- Email data
- Configuration files
- API keys

Protect backups with:

- Strong access controls
- Secure storage
- Encryption if required
- Limited sharing
- Regular cleanup of old backups

## Backup Checklist

| Check | Status |
|---|---|
| Full cPanel backup generated | Pending |
| Website files backed up | Pending |
| Database exported | Pending |
| `.htaccess` backed up | Pending |
| `wp-config.php` backed up, if WordPress | Pending |
| DNS records documented | Pending |
| Email settings documented | Pending |
| Backup downloaded | Pending |
| Backup file opens successfully | Pending |
| Backup stored securely | Pending |
| Old public backup files removed | Pending |

## Restore Planning

Before making changes, know how to restore:

- Website files
- Database
- DNS records
- Email settings
- SSL settings
- `.htaccess`

A restore plan should answer:

```text
What will be restored?
Where is the backup stored?
Who has access?
How long will restore take?
What business impact is expected?
```

## Common Backup Issues

| Issue | Possible Cause | Fix |
|---|---|---|
| Backup file too large | Large uploads/email/database | Use partial backups |
| Backup download fails | Browser or hosting timeout | Try smaller backup sections |
| Database export empty | Wrong database selected | Confirm database name |
| Backup left in public folder | Security risk | Move or delete public copy |
| No recent backup | Backup process missing | Create manual backup before change |
| Restore fails | Corrupt backup | Test backup archive before change |

## Example Ticket Note

```text
Created website backup before uploading new site files.
Compressed current public_html folder and downloaded ZIP backup.
Exported MySQL database from phpMyAdmin.
Documented current DNS records and saved screenshot.
Verified backup files opened successfully.
Stored backup securely outside public_html.
Proceeding with website update.
```

## Escalation Criteria

Escalate if:

- Full account backup fails
- Website contains sensitive customer data
- Database export fails
- Restore is needed for production outage
- Malware is suspected
- Hosting storage is full
- Email backup is required
- Migration requires DNS and database coordination

## Skills Demonstrated

- cPanel backup process
- Website file backup
- Database export awareness
- DNS documentation
- Restore planning
- Security-focused backup handling
- Technical documentation
