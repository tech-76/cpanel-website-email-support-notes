# Contact Form Troubleshooting

## Overview

Contact forms are used on websites to collect messages, quote requests, bookings, support requests, and customer inquiries. A contact form may fail because of code errors, SMTP issues, spam filtering, incorrect recipient settings, hosting mail restrictions, DNS problems, or form validation issues.

This guide explains a practical troubleshooting process for website contact forms.

## Purpose

This document demonstrates knowledge of:

- Contact form testing
- Form validation checks
- SMTP configuration
- PHP mail limitations
- Spam filtering
- DNS email records
- cPanel hosting checks
- Ticket documentation

## Common Contact Form Issues

Users may report:

- Form does not submit
- Form shows error after submit
- Form says sent but no email arrives
- Emails go to spam
- User receives no confirmation email
- Required fields do not work
- CAPTCHA fails
- Attachments do not send
- Form works on desktop but not mobile
- Form stopped working after website migration

## Step 1: Reproduce the Issue

Test the form yourself.

Check:

- Name field
- Email field
- Phone field
- Message field
- Required fields
- Submit button
- Confirmation message
- Error message
- Mobile view
- Browser console errors

Document the exact behavior.

## Step 2: Confirm Form Destination

Check where the form is supposed to send messages.

Examples:

```text
info@example.com
support@example.com
sales@example.com
```

Confirm:

- Recipient email is correct
- Mailbox exists
- Mailbox is not full
- Email is not going to spam
- Forwarding rules are not moving messages

## Step 3: Check Front-End Form Code

For static websites, check the HTML form.

Example:

```html
<form action="contact.php" method="POST">
```

Check:

- `action` points to the correct script
- `method` is correct
- Required fields have `name` attributes
- Submit button works
- JavaScript does not block submission

Example required field:

```html
<input type="email" name="email" required>
```

## Step 4: Check Server-Side Script

If using PHP, confirm the processing file exists.

Example:

```text
contact.php
```

Check:

- File is uploaded to correct folder
- File permissions are correct
- Recipient email is correct
- Error reporting/logging is reviewed
- Server supports PHP mail or SMTP library
- Script redirects or displays confirmation properly

## Step 5: PHP Mail vs SMTP

Many hosting providers limit or block basic PHP mail because it can be abused for spam.

More reliable option:

```text
Use authenticated SMTP
```

SMTP usually requires:

- SMTP server
- SMTP username
- SMTP password
- SMTP port
- Encryption type
- From address
- Authentication

## Step 6: Check SMTP Settings

Common SMTP settings:

| Setting | Example |
|---|---|
| SMTP Server | `mail.example.com` |
| Username | `info@example.com` |
| Password | mailbox password |
| Port | `465` or `587` |
| Encryption | SSL/TLS or STARTTLS |
| From Email | `info@example.com` |
| To Email | `support@example.com` |

If using Microsoft 365, Google Workspace, or another provider, confirm their SMTP requirements.

## Step 7: Check Spam and Junk Folders

If the form says sent but email is missing:

- Check Junk/Spam
- Check quarantine
- Check mailbox rules
- Check forwarding
- Check cPanel webmail
- Check recipient mailbox storage
- Send test to another address

## Step 8: Check DNS Email Records

Poor email authentication can cause form emails to go to spam.

Check:

```cmd
nslookup -type=mx example.com
nslookup -type=txt example.com
nslookup -type=txt _dmarc.example.com
```

Important records:

- MX
- SPF
- DKIM
- DMARC

## Step 9: Check cPanel Email Deliverability

In cPanel, look for:

- Email Deliverability
- Track Delivery
- Email Accounts
- Forwarders
- Default Address
- Spam Filters

These tools can help identify whether messages are being accepted, rejected, or flagged.

## Step 10: Check Hosting Error Logs

In cPanel:

1. Open **Metrics**.
2. Open **Errors**.
3. Review recent errors.

Also check application logs if available.

Look for:

- PHP errors
- Missing files
- Permission errors
- SMTP authentication errors
- 500 server errors

## Common Contact Form Problems and Fixes

| Issue | Possible Cause | Fix |
|---|---|---|
| Form does not submit | JavaScript or validation error | Check browser console and form fields |
| 404 after submit | Wrong form action path | Correct script path |
| 500 error | PHP/server error | Check error logs |
| Says sent but no email | PHP mail blocked or spam | Use SMTP and check spam |
| SMTP auth failed | Wrong username/password | Confirm mailbox credentials |
| Emails go to spam | Missing SPF/DKIM/DMARC | Fix email authentication |
| CAPTCHA fails | Site key or secret key issue | Verify CAPTCHA setup |
| Attachments fail | File size or script restriction | Check upload limits |

## Testing Checklist

| Test | Status |
|---|---|
| Submit form with valid information | Pending |
| Required fields block empty submission | Pending |
| Invalid email is rejected | Pending |
| Confirmation message appears | Pending |
| Email arrives in inbox | Pending |
| Email does not go to spam | Pending |
| Mobile form works | Pending |
| SMTP authentication works | Pending |
| Error logs are clean | Pending |

## Example Ticket Note

```text
User reported website contact form showed success message but emails were not received.
Tested form and confirmed success message appeared.
Checked recipient mailbox, spam folder, and cPanel webmail.
Reviewed cPanel Track Delivery and found messages were not being sent through authenticated SMTP.
Updated form configuration to use SMTP with the domain mailbox.
Submitted test form and confirmed email arrived in inbox.
Ticket resolved.
```

## Escalation Criteria

Escalate if:

- SMTP credentials are unavailable
- Mail provider blocks SMTP authentication
- Server-side code requires developer changes
- DNS records need updating
- Website has security concerns
- Multiple forms fail after migration
- Hosting provider blocks outbound mail
- CAPTCHA keys need admin access

## Skills Demonstrated

- Website form troubleshooting
- SMTP configuration awareness
- cPanel email tools
- DNS email record checks
- PHP mail awareness
- Web support documentation
