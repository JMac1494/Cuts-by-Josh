# Cuts by Josh — Booking App

Two standalone HTML files. No build tools, no dependencies, no server needed.

---

## Files

| File | Purpose |
|---|---|
| `index.html` | Customer-facing booking app |
| `admin.html` | Your private admin panel |
| `CBJ_Logo.png` | Your logo — keep this in the same folder |

---

## Deploying to GitHub Pages (step by step)

### 1. Create a GitHub account
Go to [github.com](https://github.com) and sign up for a free account if you don't have one.

### 2. Create a new repository
- Click the **+** icon (top right) → **New repository**
- Name it something like `cuts-by-josh` or `cbj-booking`
- Set it to **Public** (required for free GitHub Pages)
- Click **Create repository**

### 3. Upload your files
- On your new repository page, click **Add file** → **Upload files**
- Drag and drop these three files:
  - `index.html`
  - `admin.html`
  - `CBJ_Logo.png`
- Click **Commit changes**

### 4. Enable GitHub Pages
- Go to your repository **Settings** tab
- Scroll down to **Pages** in the left sidebar
- Under **Source**, select **Deploy from a branch**
- Choose branch: `main` — folder: `/ (root)`
- Click **Save**

### 5. Your URLs (ready in ~2 minutes)
```
Booking app:  https://YOUR-USERNAME.github.io/cuts-by-josh/
Admin panel:  https://YOUR-USERNAME.github.io/cuts-by-josh/admin.html
```

Replace `YOUR-USERNAME` with your actual GitHub username.

---

## Changing the admin password

Open `admin.html` in a text editor and find this line near the top of the `<script>` section:

```javascript
const ADMIN_PASSWORD='josh2024';
```

Change `josh2024` to any password you like. Save and re-upload the file to GitHub.

> **Note:** This is a simple password for demo purposes. For a production app with real customer data, you'd want a proper login service (e.g. Supabase Auth). See the "Going live" section below.

---

## Keeping admin private

Your admin panel URL is technically public (anyone who knows the link can try to log in). The password gate stops casual visitors. For stronger protection:

**Option A — Rename the admin file**
Change `admin.html` to something obscure like `admin-j7x9k.html`. No one will guess it.

**Option B — Use Netlify instead of GitHub Pages**
Netlify (free tier) lets you password-protect specific pages without code. Takes 5 minutes to set up.

---

## Going live (real bookings that persist)

Right now bookings reset when the page refreshes. To make them permanent you need a database. Here's the simplest path:

### Supabase (free, takes ~1 hour to set up)
1. Sign up at [supabase.com](https://supabase.com) — free tier is plenty for a solo barber
2. Create a project and add two tables: `bookings` and `blocked_dates`
3. Replace the in-memory arrays in both HTML files with `fetch()` calls to your Supabase API
4. Supabase gives you a URL and an anon key — add those to your code

**Cost:** Free up to ~50,000 rows. You'd only pay (~£20/month) at very high volume.

### Email confirmations
- [Resend](https://resend.com) — free for up to 3,000 emails/month
- Add a webhook call after `confirm-btn` is clicked

### SMS reminders
- [Twilio](https://twilio.com) — approximately £0.04 per SMS in the UK
- Set up a scheduled job (Supabase has this built in) to send reminders 24 hours before each appointment

### Total running cost for a solo barber: ~£5–15/month

---

## Making changes

To update services, prices, or anything else:
1. Edit the HTML file in a text editor (Notepad works, VS Code is better)
2. Go to your GitHub repository
3. Click on the file → click the pencil (edit) icon → paste your changes → **Commit changes**

Changes go live within 1–2 minutes.

---

## Questions?
Ask Claude to help you with any of the above steps — just paste in the relevant section and describe what you need.
