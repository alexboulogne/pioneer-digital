# Deploy to Vercel with GitHub

This is a static HTML landing page. Follow these steps to put it on GitHub and deploy with Vercel.

## 1. Initialize Git and push to GitHub

In your project folder, run:

```bash
cd "/Users/alexboulogne/Desktop/Cursor/Client Ascension "

git init
git add index.html favicon.svg Images/ .gitignore DEPLOY.md
git commit -m "Landing page for digital marketing agency"
```

Then create the repo on GitHub: **pioneer-digital**, **Public**, leave **Add README / .gitignore / license** all off (empty repo). Click **Create repository**. Then run:

```bash
git remote add origin https://github.com/alexboulogne/pioneer-digital.git
git branch -M main
git push -u origin main
```

**Check:** Open `https://github.com/YOUR_USERNAME/pioneer-digital` — you should see `index.html`, `favicon.svg`, `Images/`, etc. If the repo is empty, Vercel will show "repository does not contain the requested branch or commit".

## 2. Deploy on Vercel

1. Go to [vercel.com](https://vercel.com) and sign in (use “Continue with GitHub” if you like).
2. Click **Add New…** → **Project**.
3. Import your GitHub repo (select the repo you just pushed).
4. Leave the defaults:
   - **Framework Preset:** Other
   - **Root Directory:** . (leave blank)
   - **Build Command:** leave empty
   - **Output Directory:** leave empty
5. Click **Deploy**.

Vercel will build and deploy your site. It will detect the root `index.html` and serve it at the root URL. You’ll get a URL like `https://your-project.vercel.app`.

## 3. Custom domain (optional)

In the Vercel project: **Settings** → **Domains** → add your domain and follow the DNS instructions.

## Editing the site

Edit `index.html` and push to `main`; Vercel will redeploy automatically. Save and refresh **http://localhost:8080** to preview locally.

All assets (Tailwind, fonts, images) are loaded from CDNs, so no build step is required.

## Troubleshooting: "Repository does not contain the requested branch or commit"

This usually means the GitHub repo has no code on the `main` branch. Fix it:

1. Open Terminal and go to the project folder:
   ```bash
   cd "/Users/alexboulogne/Desktop/Cursor/Client Ascension "
   ```
2. If you haven’t set up Git yet:
   ```bash
   git init
   git add index.html favicon.svg Images/ .gitignore DEPLOY.md
   git commit -m "Landing page for digital marketing agency"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/pioneer-digital.git
   git push -u origin main
   ```
3. If you already ran `git init` and `git commit` but the repo on GitHub is still empty, check the remote and push again:
   ```bash
   git remote -v
   git branch -M main
   git push -u origin main
   ```
4. On GitHub, confirm the **pioneer-digital** repo shows files and the branch is **main**. Then in Vercel, import the project again (or redeploy) and choose branch **main**.
