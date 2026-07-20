# Common Workflows

## Update Sales Data
1. Place new Excel file(s) in `data/`
2. Ask: "Process the new Excel files in data/ and update the embedded data in builds/bph_portal.html"
3. Claude reads Excels, merges with existing data, recompresses, replaces B64 string
4. Download from `builds/`, rename to `index.html`, deploy to Netlify

## Add a New Brand
1. Ask: "Add brand ANKER with PIN 5555 to the default brands in builds/bph_portal.html"
2. Claude edits the `/*BP_START*/` ... `/*BP_END*/` block
3. Download and redeploy

## Change a PIN
1. Ask: "Change UGREEN PIN to 8888 in the portal"
2. Claude updates the PIN in the BP_START/BP_END block
3. Download and redeploy

## Add a New Dashboard Feature
1. Describe the feature in detail
2. Claude reads context/architecture.md to understand the codebase
3. Claude edits builds/bph_portal.html
4. Always verify: balanced braces, balanced parens, file ends with </html>

## Fix a Bug
1. Describe the symptom (screenshot helps)
2. Reference context/known-issues.md for common patterns
3. Claude identifies the function, applies fix, verifies structure

## Update Branding
1. Place new logo file in the project root or context/
2. Ask: "Replace the login logo with the new logo file"
3. Claude base64-encodes the image and replaces the data URI in the HTML

## Deploy to Netlify
1. Download builds/bph_portal.html
2. Rename to index.html
3. Go to app.netlify.com → your site → Deploys → drag and drop
4. Same URL, updated content
