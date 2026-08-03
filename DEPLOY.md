# Deploying to Cloudflare Pages

One-time setup to get this repo live at `7talents.io` via Cloudflare Pages.

## 1. Push this repo to GitHub

```bash
cd 7talents-site
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/7talents-site.git
git push -u origin main
```

## 2. Create a Cloudflare account (free)

Go to [dash.cloudflare.com/sign-up](https://dash.cloudflare.com/sign-up) and sign up if you don't already have an account.

## 3. Connect the repo to Cloudflare Pages

1. In the Cloudflare dashboard, go to **Workers & Pages** → **Create** → **Pages** → **Connect to Git**
2. Authorize Cloudflare to access your GitHub account, then select the `7talents-site` repository
3. Build settings:
   - **Framework preset:** None
   - **Build command:** *(leave blank)*
   - **Build output directory:** `/`
4. Click **Save and Deploy**

Cloudflare will deploy the site and give you a live URL like `7talents-site.pages.dev` within a minute or two. Confirm it looks right before moving to the domain step.

## 4. Move the domain to Cloudflare

Cloudflare Pages requires your domain's nameservers to point to Cloudflare in order to attach a custom domain (this is different from Netlify, which can work with external DNS).

1. In Cloudflare, go to **Websites** → **Add a site** → enter `7talents.io`
2. Choose the **Free** plan
3. Cloudflare will scan your existing DNS records and show you a summary — review it (it should pick up whatever records currently exist, e.g. any email records)
4. Cloudflare will give you two nameservers, e.g.:
   ```
   ada.ns.cloudflare.com
   rex.ns.cloudflare.com
   ```
5. Go to your current domain registrar (wherever `7talents.io` is registered/managed today) → domain settings → **Nameservers** → replace the existing nameservers with the two Cloudflare gave you
6. Save. Cloudflare will email you once it detects the change (usually within a few hours, occasionally up to 24)

## 5. Attach the domain to your Pages project

Once Cloudflare shows the domain as **Active**:

1. Go back to **Workers & Pages** → your `7talents-site` project → **Custom domains**
2. Click **Set up a custom domain** → enter `7talents.io` → follow the prompts
3. Repeat for `www.7talents.io` if you want the www version to work too (Cloudflare will offer to set up a redirect automatically)

Cloudflare auto-provisions SSL — no separate certificate step needed.

## 6. Verify

- Visit `https://7talents.io` and confirm it loads with a valid padlock/HTTPS
- Check `https://www.7talents.io` redirects correctly
- Test on mobile

## After initial setup

Every push to `main` on GitHub automatically triggers a new deploy — no manual steps needed going forward. Cloudflare Pages also creates a preview URL for any other branch or pull request, useful if you want to test changes before merging to `main`.
