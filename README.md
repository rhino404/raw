# Roots and Wings WNC

A lightweight, one-page static website for **Roots and Wings WNC** — an outdoor, faith-based, kid-friendly organization in Western North Carolina.

🌐 **Domain:** [rootsandwingswnc.com](https://rootsandwingswnc.com)  
📧 **Email:** <rootsandwingswnc@gmail.com>

---

## Site Structure

Single-page design with anchor navigation:

| Section | Anchor       | Purpose                                        |
|---------|--------------|------------------------------------------------|
| Hero    | `#`          | Welcome message + primary CTA                  |
| About   | `#about`     | Mission, values, what we do                    |
| FAQ     | `#faq`       | Common questions and answers                   |
| Connect | `#subscribe` | Contact info, social links & newsletter signup |

---

## Tech Stack

- **HTML5 + CSS3** — No framework, minimal footprint
- **Mailchimp Embedded Form** — Newsletter signup with double opt-in
- **GitHub Pages** — Static hosting with apex domain

---

## Local Development

```bash
cd web
python -m http.server 8000
```

Then open [http://localhost:8000](http://localhost:8000)

---

## Mailchimp Setup

1. Log into [Mailchimp](https://mailchimp.com)
2. Create an **Audience** for Roots and Wings WNC
3. Go to **Audience → Signup forms → Embedded forms**
4. Enable **Double opt-in** under Audience settings
5. Copy the generated embed code
6. Replace the placeholder in `web/index.html` inside the `#subscribe` section

> **Note:** The Mailchimp embed has been trimmed to the minimal required markup (form fields, honeypot, response containers, `mc-validate.js`, and field name registration). All SMS/country-code logic has been removed. Site-owned CSS overrides style the form to match the design system, and a lightweight script handles loading states, double-submit prevention, and auto-dismissing success messages.

---

## Deployment (GitHub Pages + Apex Domain)

### 1. Enable GitHub Pages (Automated via GitHub Actions)

The repository includes a GitHub Actions workflow (`.github/workflows/deploy.yml`) that automatically deploys the `/web` folder to GitHub Pages when you push changes.

**One-time setup:**

1. Go to repo **Settings → Pages**
2. Set **Source** to `GitHub Actions`
3. Push your code to the `main` branch
4. The workflow will automatically build and deploy

**Manual deployment (if needed):**

- Go to **Actions** tab → **Deploy to GitHub Pages** → **Run workflow**

### 2. Configure Custom Domain

1. In **Settings → Pages → Custom domain**, enter: `rootsandwingswnc.com`
2. Check **Enforce HTTPS** (after DNS propagates)

### 3. Set DNS Records (at your registrar)

| Type  | Host | Value                        |
|-------|------|------------------------------|
| A     | @    | 185.199.108.153              |
| A     | @    | 185.199.109.153              |
| A     | @    | 185.199.110.153              |
| A     | @    | 185.199.111.153              |

> These are GitHub Pages' current IPs. Verify at [GitHub Docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site).

### 4. Verify

- Wait for DNS propagation (up to 48h, usually faster)
- Visit <https://rootsandwingswnc.com>
.github/
└── workflows/
    └── deploy.yml    # GitHub Actions deployment workflow
- Confirm HTTPS lock icon appears

---

## File Structure

```text
web/
├── index.html                # One-page site with all sections
├── styles.css                # Modern responsive styles
├── liability-waiver.html     # Liability waiver & assumption of risk
├── payment-policy.html       # Payment policy (Venmo, fees, refunds)
├── medical-authorization.html # Medical & emergency authorization
├── photo-consent.html        # Photo & media consent (optional)
├── robots.txt                # Search engine directives
├── sitemap.xml               # SEO sitemap
├── CNAME                     # GitHub Pages custom domain
└── favicon.svg               # Site icon
```

---

## Privacy Note (Subscribe Section)

Minimal privacy copy included near the form:

> "Your email is used to send updates via Mailchimp. You can unsubscribe anytime."

---

## Registration & Policies

Registration is handled through a Google Form. During registration, parents/guardians review and acknowledge four site-hosted policy documents:

| Document                     | Page                        | Required?       |
|------------------------------|-----------------------------|-----------------|
| Liability Waiver             | `liability-waiver.html`     | Yes             |
| Payment Policy               | `payment-policy.html`       | Yes             |
| Medical & Emergency Auth     | `medical-authorization.html`| Yes             |
| Photo & Media Consent        | `photo-consent.html`        | Optional        |

- **Payment:** $80 per family per 8-week session (≈$10/class) via Venmo (@rootsandwingswnc)
- **Jurisdiction:** North Carolina
- **Important:** Have the waiver/release language reviewed by a North Carolina attorney before relying on it operationally.

> "Your email is used to send updates via Mailchimp. You can unsubscribe anytime."

---

## License

© 2026 Roots and Wings WNC. All rights reserved.
