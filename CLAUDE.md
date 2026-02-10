# Claude Code Instructions

## Deployment Flow
- Never push directly to `main`
- Push to `claude/*` branches only
- `.github/workflows/auto-merge-claude.yml` handles everything automatically:
  1. Merges the claude branch into main
  2. Deletes the claude branch
  3. Deploys to GitHub Pages
- The "Create a pull request" message in push output is just GitHub boilerplate — ignore it, the workflow handles merging automatically

## File Version Headers
Every file must have a version comment as the **first line**, using the appropriate comment syntax for that file type:
- HTML: `<!-- Version: 1.0 | Updated: 2026-02-10 -->`
- CSS: `/* Version: 1.0 | Updated: 2026-02-10 */`
- JS: `// Version: 1.0 | Updated: 2026-02-10`
- Python: `# Version: 1.0 | Updated: 2026-02-10`
- For any file type not listed above, use the HTML variant: `<!-- Version: 1.0 | Updated: 2026-02-10 -->`

Rules:
- Increment the version number each commit that modifies the file (1.0 → 1.1 → 1.2, etc.)
- Update the date to the current date
- New files start at version 1.0

## Build Version (Auto-Refresh)
HTML files have a `<meta name="build-version" content="TIMESTAMP">` tag in the `<head>`. This powers the auto-refresh system that polls every 10 seconds and reloads the page when a new version is detected.
- Before every commit, update the content value to the current Unix timestamp (`date +%s`)
- This is separate from the version header — both must be updated

