# Beam — turn any HTML file into a link

A single-file, no-backend web app. Drop in an `.html` file, preview it instantly,
and turn it into a shareable link. The file's content is base64-encoded and
packed straight into the URL's hash (`index.html#view=...`) — there's no
server, no database, and nothing ever gets uploaded anywhere. Anyone who opens
the link decodes and renders the page locally, in their own browser.

## Run it locally

Just open `index.html` in any browser. That's the whole app.

## Deploy — GitHub + Vercel

1. **Create a GitHub repo** and push these files (`index.html`, `README.md`) to it:
   ```bash
   git init
   git add .
   git commit -m "Beam: html to link"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```
2. **Go to [vercel.com](https://vercel.com)** → **Add New Project** → **Import** your
   GitHub repo.
3. Vercel will auto-detect it as a static site — no build command or output
   directory needed. Click **Deploy**.
4. You'll get a live URL (e.g. `https://your-project.vercel.app`) where the
   app is hosted. Shareable links generated inside the app will use that
   domain automatically.

## Notes

- Very long HTML files produce very long links. The app warns you once a
  link crosses roughly 2,000 characters (some older browsers/apps start
  truncating around there) and flags it more strongly past ~8,000.
- Uploaded HTML is sandboxed in an `<iframe>` (scripts run, but the frame
  can't navigate the parent page).
