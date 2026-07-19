# praveen.cloud — Portfolio Website

A single-file portfolio (`index.html`) for **Praveen Kumar S — Azure Cloud Engineer**.
Everything (styles, scripts, your photo) is embedded in that one file, so it can be hosted anywhere with zero build steps.

**Sections:** animated welcome loader → hero with hanging ID-badge photo & typing effect → About Me → Certifications (AZ-900, AZ-104) → Portfolio with Projects/Skills tabs and project detail pop-ups → Contact form + direct links (email, phone, WhatsApp, GitHub, LinkedIn, Instagram).

---

## 1. Make the contact form deliver to your Gmail (2 minutes, free)

The form is wired to [Web3Forms](https://web3forms.com) — a free service that forwards form submissions to your email. No account or backend needed.

1. Open **https://web3forms.com** and enter `praveenkumar.sankar08@gmail.com` → click **Create Access Key**.
2. The key arrives in your Gmail instantly. Copy it.
3. Open `index.html`, find this line near the bottom (inside `<script>`):
   ```js
   const WEB3FORMS_ACCESS_KEY = "YOUR_ACCESS_KEY_HERE";
   ```
   and paste your key between the quotes. Save. Done — every "Send Message" now lands in your inbox.

> Until you add the key, the form still works: it opens the visitor's email app with the message pre-filled, addressed to you.

---

## 2. Deploy it

### Option A — GitHub Pages (fastest, free)
1. Create a repo named `praveenk-cloud.github.io` under your GitHub account.
2. Upload `index.html` to it (root of the repo).
3. Repo → **Settings → Pages** → Source: `main` branch → Save.
4. Your site is live at **https://praveenk-cloud.github.io** within a minute.

### Option B — Azure Static Web Apps (free tier — great talking point in interviews)
1. Push `index.html` to any GitHub repo (e.g. `portfolio`).
2. Azure Portal → **Create a resource → Static Web App** → Free plan.
3. Sign in with GitHub, pick the repo/branch, app location `/`, leave build presets as **Custom**, output location empty.
4. Azure creates a GitHub Actions workflow and deploys automatically. You get a URL like `https://<name>.azurestaticapps.net`, with free SSL. Every future `git push` redeploys.

### Option C — Azure Storage static website (this is literally an AZ-104 skill)
1. Create a Storage Account → **Data management → Static website → Enabled**, index document: `index.html`.
2. Upload `index.html` to the auto-created `$web` container.
3. Site is live at the "Primary endpoint" URL. (Add Azure CDN/Front Door later for HTTPS on a custom domain.)

Mentioning on your resume that your portfolio *itself* runs on Azure is a nice bonus signal for a fresher.

---

## 3. Customize

- **Project GitHub links:** in `index.html`, search for `const PROJECTS` — each project has a `repo:` field currently pointing to your profile (`https://github.com/praveenk-cloud`). Replace each with the exact repository URL.
- **Typing phrases:** edit the `PHRASES` array in the same script block.
- **Colors:** all theme colors are CSS variables at the top of the file under `:root` (`--cyan`, `--azure`, `--grad`, etc.).
- **Photo:** the image is embedded as base64. To swap it, replace the two `data:image/jpeg;base64,...` values in the `src` attributes (one in the hero ID card, one in About).
- **Custom domain:** if you buy `praveen.cloud` or similar, both GitHub Pages and Azure Static Web Apps let you attach it for free.
