# Publishing Guide

## First-Time Setup

Before the automatic publishing workflow can work, you need to authenticate with GitHub Packages:

1. Users who want to install the package need to authenticate with GitHub Packages by creating a Personal Access Token (PAT) with the `read:packages` scope.

2. Add the following to your `~/.npmrc` file (replace `OWNER` with the repository owner, e.g., `PackmindHub`):
   ```
   @OWNER:registry=https://npm.pkg.github.com
   //npm.pkg.github.com/:_authToken=YOUR_GITHUB_TOKEN
   ```

## Publishing a New Version

To publish a new version to GitHub Packages:

1. Update the version in `package.json`:
   ```bash
   npm version patch  # or minor, major
   ```

2. Create and push the version tag:
   ```bash
   git push origin main
   git push origin --tags
   ```

3. The GitHub Actions workflow will automatically:
   - Install dependencies
   - Run linter
   - Build the TypeScript code
   - Update the package name with the repository owner
   - Publish to GitHub Packages

## Manual Trigger

You can also manually trigger the workflow from the GitHub Actions tab:
1. Go to Actions → Publish to GitHub Packages
2. Click "Run workflow"
3. Select the branch and click "Run workflow"

## Using the Published Package

Once published, users can install it with (replace `OWNER` with the repository owner):

```bash
npx @OWNER/packmind-mcp-server
```

For the official PackmindHub repository:

```bash
npx @PackmindHub/packmind-mcp-server
```

For use in VS Code or Cursor, users should configure their MCP settings as described in the README.md.

## Troubleshooting

If the workflow fails:
- Check the Actions tab for error logs
- Ensure the `GITHUB_TOKEN` has the correct permissions
- Verify that the repository allows GitHub Packages
- Make sure the package.json version has been incremented
