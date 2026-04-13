# Deployment Instructions

## Step 1 — Upload to Cloudflare Pages

1. Go to [pages.cloudflare.com](https://pages.cloudflare.com) and sign up / log in (free)
2. Click **Create a project** → **Direct Upload**
3. Name it e.g. `kitchen-tea-towels`
4. Upload your entire `___AI Shop` folder
5. Click **Deploy** — you'll get a free URL like `kitchen-tea-towels.pages.dev`

---

## Step 2 — Point your domain (kitchenteatowels.co.uk)

1. In Cloudflare Pages → your project → **Custom domains**
2. Add `kitchenteatowels.co.uk`
3. Cloudflare will ask you to move your domain's nameservers to Cloudflare — do this with whoever you bought the domain from (your domain registrar)
4. SSL certificate is automatic and free

---

## Step 3 — Secure admin.html with Cloudflare Access

This replaces the browser password with a proper email-based one-time code login — no password to guess or hack.

1. In your Cloudflare dashboard → **Zero Trust** (free plan)
2. Go to **Access** → **Applications** → **Add an application**
3. Choose **Self-hosted**
4. Set the domain to `kitchenteatowels.co.uk` and path to `/admin.html`
5. Under **Policy**, set it to allow your email address only
6. Save

From then on, anyone visiting `/admin.html` is prompted to enter their email. Cloudflare sends a one-time code — only your email can get in.

---

## Notes

- Your **PayPal Client ID** in the code is safe to be public — it's designed for front-end use
- After any product changes via the admin panel, click **Save & Download products.js** and re-upload that file to Cloudflare Pages
- If product images ever look wrong in the browser, open the browser console (F12) and run:
  ```javascript
  localStorage.removeItem('ktt_products')
  ```
  Then refresh the page
