# Publishing to GitHub Packages (npm)

This repo is configured to publish the package to GitHub Packages (npm) under the scope `@srikanthlogic`.

Local publish (manual):

1. Create a Personal Access Token (PAT) with `write:packages` and `read:packages` scopes (and `repo` if the repo is private).
2. Create or update your `~/.npmrc` with the following lines:

   ```text
   @srikanthlogic:registry=https://npm.pkg.github.com/
   //npm.pkg.github.com/:_authToken=YOUR_PAT_TOKEN
   ```

3. Update package version and then run:

   ```bash
   npm publish --access public
   ```

CI publish via GitHub Actions (automatic):

- A workflow is included at `.github/workflows/publish.yml` that publishes on GitHub release events.
- The workflow uses the repository `GITHUB_TOKEN` with `packages: write` permissions to authenticate (no extra secret required for the GitHub Action to publish on releases).

Notes:
- The package name has been scoped to `@srikanthlogic/google-play-scraper` in `package.json`.
- Consumers should now install with `npm install @srikanthlogic/google-play-scraper`.
