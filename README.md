# autough.com

Autough's one-page website. It's a single `index.html` with no scripts, no
cookies, no tracking and nothing loaded from other sites. It works on phones
and follows the visitor's light or dark setting.

**Why now:** autough.com is a GoDaddy parking page today. Anyone who looks us
up after a cold email lands on it, and spam filters notice parked domains.

GitHub Pages hosts it for free from this repo. The only step left is pointing
the domain here in GoDaddy, which needs the GoDaddy login (Matt).

## Matt: put it live (about 10 minutes)

**Don't touch the email records.** business@autough.com runs on Microsoft 365.
Leave every **MX**, **TXT**, **SRV** and email-related **CNAME** record exactly as
it is (autodiscover, enterpriseenrollment, lyncdiscover, sip, msoid and so on).
Only the website records below change.

1. Sign in to GoDaddy. Go to **My Products → autough.com → DNS** (Manage DNS).
2. **Turn off parking and forwarding.**
   - If **Forwarding** is on for the domain, delete it.
   - In the DNS records, delete the **A** record for `@` that points at GoDaddy's
     parking page. GoDaddy sometimes labels it "Parked".
3. **Add four A records**, each with Name `@`, TTL 1 hour:
   - `185.199.108.153`
   - `185.199.109.153`
   - `185.199.110.153`
   - `185.199.111.153`
4. **Optional, for IPv6:** add four AAAA records with Name `@`:
   - `2606:50c0:8000::153`
   - `2606:50c0:8001::153`
   - `2606:50c0:8002::153`
   - `2606:50c0:8003::153`
5. **Point www here.** Add (or change) a **CNAME** with Name `www` and Value
   `autough.github.io`. Do not add a wildcard (`*`) record.
6. **Wait, then turn on HTTPS.** Give DNS up to an hour (it can take as long as
   24). Then open this repo's **Settings → Pages**. It should say
   "Your site is live at https://autough.com". Tick **Enforce HTTPS**. HTTPS can
   take up to 24 hours to become available.
7. **Check it.** Open https://autough.com and https://www.autough.com on a phone
   and a laptop.

**Recommended, also about 5 minutes:** verify the domain with GitHub so nobody
else can claim it. Go to GitHub **Settings (your account) → Pages → Add a
domain**, enter `autough.com`, and add the TXT record GitHub shows you in
GoDaddy. It's a TXT record on its own `_github-pages-challenge-…` name, so it
doesn't affect email.

**Also on the GoDaddy account:** autough.com **expires on 2026-12-14**. Turn on
auto-renew, or renew now, so the domain and the email don't lapse.

Source for the IPs: GitHub's "Managing a custom domain for your GitHub Pages
site" (checked Oct 18, 2026).

## Editing the page

Everything is in `index.html`, with plain HTML and one `<style>` block. Commit
to `main` and GitHub Pages republishes within a minute or two.

Keep it true:
- no clients, results or testimonials until they're real and the client has
  agreed to be named;
- the offer wording matches what we say on calls and in emails.

`CNAME` holds the domain name and must stay. `lander/` sends the old parking
link (autough.com/lander) to the home page.
