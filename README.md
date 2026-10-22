# Gozo Website Demo

A beginner-friendly static website for learning how to make small manual edits, commit them to GitHub, preview locally, and deploy manually on Cloudflare Workers. It is **a demo project, not a real client website**.

## Files

- `public/index.html` — page copy, links and structure.
- `public/styles.css` — fonts, colours, layout and mobile styling.
- `wrangler.jsonc` — Cloudflare Worker name and asset folder.

## Put it on GitHub (web method)

1. Extract the ZIP on your laptop.
2. GitHub > New repository > call it `gozo-website-demo` > Public or Private > Create repository. Don't initialise with a README because this ZIP already has one.
3. In the new repository, select **uploading an existing file** (or **Add file > Upload files**), drag the **contents** of the extracted folder (preserving `public/`), and Commit changes. Note: if dragging a folder doesn't work in your browser, use VS Code/Git instead.
4. Clone your new GitHub repo to your laptop via VS Code's **Clone Repository**, or PowerShell:

   ```powershell
   cd C:\Projects
   git clone https://github.com/YOUR-USERNAME/gozo-website-demo.git
   cd gozo-website-demo
   ```

## Preview locally

You need Node.js installed, which you already use for your other projects.

```powershell
npx wrangler dev
```

Accept the install prompt if Wrangler is not installed locally. Open the local URL that Wrangler displays (usually `http://localhost:8787`). Stop the server with `Ctrl+C`.

## Make three REAL edits for the video

1. In `public/index.html`, find `Good businesses deserve` and rewrite the headline. Save, then refresh the local preview.
2. In `public/styles.css`, change `--accent:#c9fc77` to `--accent:#9dcaff` (blue). Save and refresh.
3. In `public/index.html`, edit the `Thoughtful design` card heading and its paragraph. Save and refresh.

Show the editor and updated browser side-by-side or cut between them. You now have real before/after footage.

## Save changes to GitHub

```powershell
git add .
git commit -m "Update headline, accent colour and service copy"
git push
```

Use VS Code's Source Control panel instead if you prefer. **Pushing to GitHub does not itself deploy this demo Worker**, because this workflow deliberately does not connect Cloudflare Builds to the repository.

## Deploy manually to Cloudflare

In the repo directory in PowerShell:

```powershell
npx wrangler login
npx wrangler deploy
```

Wrangler opens Cloudflare login/authorisation if needed. It should display a `workers.dev` URL after a successful deployment. If your account has no active workers.dev subdomain, Cloudflare may prompt you to set one up.

To publish a later edit, repeat `npx wrangler deploy` from the same project directory. Keep this separate from your real dealership Worker.

## What to film

1. GitHub repository structure.
2. A manual HTML copy edit in VS Code.
3. A CSS colour change with the before/after preview.
4. PowerShell running `npx wrangler deploy`.
5. The live `workers.dev` demo site on your phone.

Do not expose Cloudflare credentials, private repository URLs, payment details or client credentials on screen.

## Why this is deliberately simple

No frameworks, paid APIs, hosting subscriptions, or build process. The `assets.directory` configuration tells Cloudflare to publish the files in `public` as static assets. Future production projects may need additional security, SEO, image optimisation, forms and testing.
