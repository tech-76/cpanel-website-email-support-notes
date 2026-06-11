# SMTP Website Email Setup

## Overview

SMTP is commonly used to send email from websites reliably. Contact forms, booking forms, password reset emails, order confirmations, and notification emails often require SMTP configuration.

Using authenticated SMTP is usually more reliable than basic PHP mail because it allows messages to be sent through a real mailbox or email provider.

## Purpose

This guide demonstrates knowledge of:

- SMTP website email setup
- Contact form email configuration
- cPanel email accounts
- SMTP ports and encryption
- SPF/DKIM/DMARC awareness
- Testing and troubleshooting website email

## Why SMTP Is Important

A website may need to send emails for:

- Contact form submissions
- Booking confirmations
- Customer inquiries
- Password reset messages
- Order confirmations
- Admin notifications
- Client onboarding forms

Without proper SMTP setup, emails may:

- Fail to send
- Go to spam
- Be rejected by recipient servers
- Show as spoofed
- Be blocked by the hosting provider

## SMTP vs PHP Mail

| Method | Description | Reliability |
|---|---|---|
| PHP mail | Basic server mail function | Less reliable |
| SMTP | Authenticated mail sending | More reliable |

SMTP is preferred because it authenticates with an email account or email service.

## Required SMTP Information

Before setup, collect:

| Setting | Example |
|---|---|
| SMTP Host | `mail.example.com` |
| SMTP Username | `info@example.com` |
| SMTP Password | mailbox password |
| SMTP Port | `465` or `587` |
| Encryption | SSL/TLS or STARTTLS |
| From Email | `info@example.com` |
| From Name | Company Name |
| To Email | `support@example.com` |

## Common SMTP Ports

| Port | Encryption | Common Use |
|---|---|---|
| 25 | None or STARTTLS | Server-to-server mail, often blocked |
| 465 | SSL/TLS | Secure SMTP |
| 587 | STARTTLS | Authenticated mail submission |

For websites, port `587` with STARTTLS or port `465` with SSL/TLS are commonly used.

## Step 1: Create or Confirm Email Account

In cPanel:

1. Open **Email Accounts**.
2. Create or confirm the mailbox.

Example:

```text
info@example.com
```

3. Set a strong password.
4. Confirm mailbox storage quota.
5. Test login through webmail.

## Step 2: Get SMTP Settings from cPanel

In cPanel:

1. Open **Email Accounts**.
2. Locate the mailbox.
3. Select **Connect Devices**.
4. Copy SMTP settings.

Example:

```text
SMTP Server: mail.example.com
SMTP Port: 465
Encryption: SSL/TLS
Username: info@example.com
Password: mailbox password
```

## Step 3: Configure Website Form

Depending on the website, SMTP may be configured in:

- WordPress SMTP plugin
- PHP mailer script
- Contact form plugin
- Website admin dashboard
- Environment variables
- Config file

Example configuration:

```text
SMTP Host: mail.example.com
SMTP Username: info@example.com
SMTP Password: ********
SMTP Port: 465
Encryption: SSL/TLS
From Email: info@example.com
From Name: Example Company
```

## Step 4: Test SMTP Authentication

After saving settings, send a test email.

Confirm:

- Test email sends successfully
- Email arrives in inbox
- Email does not go to spam
- From address is correct
- Reply-to address is correct
- Contact form submissions arrive

## Step 5: Check DNS Email Records

Good DNS records improve deliverability.

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

## SPF Example

Example SPF for cPanel-hosted email may look like:

```text
v=spf1 a mx include:example.com ~all
```

The exact SPF record depends on the mail provider and hosting environment.

## DKIM and DMARC

In cPanel, check:

```text
Email Deliverability
```

This may show whether SPF and DKIM are valid.

DMARC example:

```text
v=DMARC1; p=none; rua=mailto:dmarc@example.com
```

Use monitoring first before strict enforcement unless an administrator confirms the setup.

## Common SMTP Errors

| Error | Possible Cause | Fix |
|---|---|---|
| Authentication failed | Wrong username or password | Confirm mailbox login |
| Connection timed out | Port blocked or wrong host | Try approved port |
| SSL error | Wrong encryption setting | Match port with SSL/TLS or STARTTLS |
| Sender rejected | From address mismatch | Use authenticated mailbox as sender |
| Message sent but not received | Spam or DNS issue | Check spam, SPF, DKIM, DMARC |
| SMTP disabled | Provider restriction | Enable SMTP or use approved provider |

## Security Best Practices

- Do not hardcode passwords in public repositories.
- Use environment variables for credentials.
- Never commit real SMTP passwords to GitHub.
- Use a dedicated mailbox for website sending.
- Use strong mailbox passwords.
- Rotate credentials if exposed.
- Limit sending volume to prevent spam flags.
- Use CAPTCHA and validation on public forms.
- Keep plugins and scripts updated.

## Example Environment Variable Setup

Example `.env` style values:

```text
SMTP_HOST=mail.example.com
SMTP_PORT=465
SMTP_USER=info@example.com
SMTP_PASS=your-password-here
SMTP_ENCRYPTION=ssl
```

Do not upload real `.env` files with passwords to GitHub.

Use a sample file instead:

```text
.env.example
```

## Testing Checklist

| Check | Status |
|---|---|
| Mailbox created | Pending |
| Webmail login tested | Pending |
| SMTP host confirmed | Pending |
| SMTP port confirmed | Pending |
| Encryption confirmed | Pending |
| Website form configured | Pending |
| Test email sent | Pending |
| Contact form tested | Pending |
| SPF checked | Pending |
| DKIM checked | Pending |
| DMARC checked | Pending |

## Example Ticket Note

```text
Configured website contact form to send email using authenticated SMTP.
Created and tested info@example.com mailbox in cPanel.
Copied SMTP settings from cPanel Connect Devices page.
Updated website SMTP settings using mail.example.com, SSL/TLS, and approved SMTP port.
Sent test message and confirmed delivery to support mailbox.
Checked spam folder and verified message arrived in inbox.
Ticket resolved.
```

## Escalation Criteria

Escalate if:

- SMTP authentication fails after password reset
- Hosting provider blocks SMTP ports
- DNS records need updates
- Mail deliverability remains poor
- Website code requires developer changes
- Mailbox credentials are unavailable
- Microsoft 365 or Google Workspace SMTP policies apply
- Suspicious form spam is detected

## Skills Demonstrated

- SMTP website email setup
- cPanel email configuration
- Contact form support
- Email authentication awareness
- DNS mail record testing
- Security-focused documentation
