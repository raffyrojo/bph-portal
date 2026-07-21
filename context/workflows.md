# Common Workflows

## Update Sales Data (in-app — no local file needed)
1. Open the live app: https://raffyrojo.github.io/bph-portal/
2. Log in to a brand, click **Upload**, drop the new CSV/Excel (Replace or Append)
3. Open **Admin Access** (admin PIN) → **Publish to GitHub (go live)**
4. Paste your GitHub token → **Publish live**
5. GitHub Pages redeploys in ~1 min. Works from any laptop.

Token: fine-grained GitHub PAT, scoped to only `raffyrojo/bph-portal`, Contents: Read and write. Held in the browser only, never written into the app file. Optional "remember on this browser" for your own laptop.

## Update Sales Data (with Claude — alternative)
1. Give Claude the new Excel (attach it, or place in `data/`)
2. Ask: "Merge the new Excel into the app data and publish it"
3. Claude rebuilds the embedded B64 and commits `index.html` + `bph_portal.html` to `main`
4. GitHub Pages redeploys in ~1 min

## Add a New Brand
1. In the app: **Admin Access** → Add New Brand (name + PIN) → **Publish to GitHub**
   (or ask Claude to edit the `/*BP_START*/` … `/*BP_END*/` block and publish)

## Change a PIN
1. In the app: **Admin Access** → edit the brand's PIN, or change the admin PIN → **Publish to GitHub**
   (or ask Claude to update it and publish)

## Add a New Dashboard Feature
1. Describe the feature in detail
2. Claude reads context/architecture.md to understand the codebase
3. Claude edits `index.html` (keeps `bph_portal.html` in sync) and commits to `main`
4. Always verify: balanced braces, balanced parens, `dc()` before every `new Chart()`, file ends with `</html>`

## Fix a Bug
1. Describe the symptom (screenshot helps)
2. Reference context/known-issues.md for common patterns
3. Claude identifies the function, applies the fix, verifies structure, commits

## Update Branding
1. Give Claude the new logo (attach or place in the project)
2. Ask: "Replace the login logo with the new logo file"
3. Claude base64-encodes the image, replaces the data URI, and publishes

## Deploy / Hosting
- Live on **GitHub Pages** at https://raffyrojo.github.io/bph-portal/ (source: `main`, root).
- Any commit to `main` — via the app's Publish, via Claude, or via GitHub's web editor — auto-redeploys in ~1 min.
- The app serves `index.html`; `bph_portal.html` is kept as an identical copy. Publishing updates both.
- Netlify is retired and no longer used.
