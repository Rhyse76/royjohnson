# Handoff: maybe move royjohnson.info to Cloudflare

Written 2026-10-21 for the next Claude Code session. This note is on the `handoff` branch, not
`main`, so GitHub Pages doesn't publish it. Delete the branch when it's done or dropped.

**This is optional.** The owner said "maybe". Ask before starting.

## Where things stand (checked 2026-10-21)

- The site works: GitHub Pages builds from `main` (`CNAME` = royjohnson.info, HTTPS enforced).
- The domain is registered at Squarespace, and DNS is at Squarespace (A records point to GitHub
  Pages).
- **Email:** the domain receives mail through iCloud (MX `mx01`/`mx02.mail.icloud.com`). Any DNS
  move must keep the MX records and all of iCloud's TXT/CNAME records (SPF, DKIM
  `sig1._domainkey`, `apple-domain` verification). **Don't** add `v=spf1 -all`.

## If the owner wants it

The point would be to have all of the owner's domains in one Cloudflare account (like
hearthward.games and starrow.ai).

1. Add royjohnson.info to Cloudflare (Free plan). Check that the imported records include the
   GitHub Pages A records and every iCloud mail record, then move the nameservers at Squarespace
   (turn off DNSSEC first).
2. Choose: keep GitHub Pages with Cloudflare for DNS only (smallest change), or serve the repo
   from a Cloudflare Worker with static assets, the way `Rhyse76/Hearthward` does. Ask the owner.
3. Check the site, `resume.pdf`, www, HTTPS, and that email still arrives.
