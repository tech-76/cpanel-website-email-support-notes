# Domain DNS Checklist

## Overview

DNS controls how a domain points to websites, email services, verification systems, and other online services. Incorrect DNS records can cause website outages, email delivery problems, SSL issues, and service connection failures.

This checklist provides a practical process for reviewing domain DNS settings.

## Purpose

This document demonstrates knowledge of:

- DNS record types
- Website DNS checks
- Email DNS checks
- cPanel DNS Zone Editor
- DNS propagation
- Basic troubleshooting commands
- Safe DNS change practices

## Common DNS Records

| Record Type | Purpose |
|---|---|
| A | Points a hostname to an IPv4 address |
| AAAA | Points a hostname to an IPv6 address |
| CNAME | Points a hostname to another hostname |
| MX | Controls email delivery |
| TXT | Stores verification, SPF, DKIM, and DMARC records |
| NS | Identifies authoritative nameservers |
| SRV | Used by some services for discovery |
| CAA | Controls which certificate authorities can issue SSL |

## Important DNS Terms

| Term | Meaning |
|---|---|
| Domain | Main name, such as `example.com` |
| Subdomain | Name before domain, such as `www.example.com` |
| Hostname | Full DNS name |
| TTL | Time To Live; how long DNS records are cached |
| Nameserver | Server that hosts DNS records |
| Propagation | Time for DNS changes to update globally |
| Zone File | Collection of DNS records for a domain |

## Website DNS Checklist

| Check | Example | Status |
|---|---|---|
| Domain has correct nameservers | `ns1.host.com` | Pending |
| Root domain has A record | `example.com -> 192.0.2.10` | Pending |
| WWW record exists | `www -> example.com` | Pending |
| Subdomains point correctly | `support.example.com` | Pending |
| Old duplicate records removed | Old A/CNAME records | Pending |
| TTL reviewed | 300 / 3600 / 14400 | Pending |

## Email DNS Checklist

| Check | Example | Status |
|---|---|---|
| MX record points to correct mail provider | Microsoft 365 / Google / cPanel | Pending |
| SPF TXT record exists | `v=spf1 ...` | Pending |
| DKIM records exist | selector records | Pending |
| DMARC record exists | `_dmarc.example.com` | Pending |
| Autodiscover record exists if using Microsoft 365 | `autodiscover` CNAME | Pending |
| No duplicate SPF records | Only one SPF TXT | Pending |

## SSL DNS Checklist

| Check | Status |
|---|---|
| Domain points to correct hosting server | Pending |
| WWW points correctly | Pending |
| DNS has propagated | Pending |
| SSL certificate covers root domain | Pending |
| SSL certificate covers WWW subdomain | Pending |
| CAA record does not block certificate issuer | Pending |

## cPanel DNS Zone Editor

In cPanel:

1. Open **Zone Editor**.
2. Select the domain.
3. Review records.
4. Confirm website records.
5. Confirm email records.
6. Document changes before editing.

Common records in cPanel:

```text
example.com        A       192.0.2.10
www                CNAME   example.com
example.com        MX      mail.example.com
example.com        TXT     v=spf1 include:example.com ~all
```

## DNS Commands

### Check A Record

```cmd
nslookup example.com
```

### Check WWW Record

```cmd
nslookup www.example.com
```

### Check MX Record

```cmd
nslookup -type=mx example.com
```

### Check TXT Records

```cmd
nslookup -type=txt example.com
```

### Check DMARC

```cmd
nslookup -type=txt _dmarc.example.com
```

### Linux/macOS dig Examples

```bash
dig example.com
dig www.example.com
dig MX example.com
dig TXT example.com
dig TXT _dmarc.example.com
```

## Common DNS Issues

| Issue | Possible Cause | Fix |
|---|---|---|
| Website not loading | Wrong A record | Point domain to correct hosting IP |
| WWW not working | Missing CNAME | Add or fix WWW record |
| Email not receiving | Wrong MX record | Update MX to correct provider |
| SPF fails | Missing sending provider | Update SPF carefully |
| DKIM fails | Missing selector record | Add provider DKIM record |
| DMARC missing | No DMARC TXT record | Add monitoring policy if approved |
| SSL cannot issue | DNS not pointing correctly | Fix A/CNAME records |
| DNS changes not visible | Propagation/cache | Wait for TTL and retest |

## Safe DNS Change Process

1. Identify the current record.
2. Confirm the required new value.
3. Take screenshot or copy existing record.
4. Lower TTL before planned migration if possible.
5. Make one change at a time.
6. Test after change.
7. Document old value, new value, date, and reason.
8. Escalate if unsure.

## DNS Change Documentation Example

```text
Date: YYYY-MM-DD
Domain: example.com
Record changed: www CNAME
Old value: old-host.example.net
New value: example.com
Reason: Point www to new cPanel website
Test result: www.example.com resolves successfully
```

## Escalation Criteria

Escalate if:

- Nameservers need to be changed
- DNS records are unclear
- Email is down for multiple users
- MX records need provider migration
- SPF/DKIM/DMARC changes affect deliverability
- SSL cannot validate
- Production website is down
- Domain registrar access is required

## Example Ticket Note

```text
User reported website working without www but failing with www.
Checked DNS records and confirmed root domain had correct A record.
Found missing www CNAME record.
Added www CNAME pointing to root domain after approval.
Tested DNS lookup and confirmed www.example.com resolved correctly.
Website loaded successfully using both root and www versions.
Ticket resolved.
```

## Skills Demonstrated

- DNS record review
- cPanel Zone Editor awareness
- Website DNS troubleshooting
- Email DNS troubleshooting
- SSL DNS checks
- Change documentation
