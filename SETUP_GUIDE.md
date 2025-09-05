# CI/CD Setup Guide

## GitHub Secrets Configuration

You need to add the following secrets to your GitHub repository:

### 1. Get Vercel Token
```bash
npx vercel tokens create personal-website-ci
```
Copy the token and add it as `VERCEL_TOKEN` in GitHub Secrets.

### 2. Add Project IDs
Add these values from your `.vercel/project.json`:
- `VERCEL_ORG_ID`: team_xKGi93onow6tB8gPVuF1s4zK
- `VERCEL_PROJECT_ID`: prj_LYKS9HG5pxuedYipr7CekX2u8ncM
- `VERCEL_SCOPE`: mikerowans-projects

### 3. How to Add Secrets
1. Go to https://github.com/mikerowan/personal-website/settings/secrets/actions
2. Click "New repository secret"
3. Add each secret with its name and value

## Branch Protection Rules

To enable automatic testing before merging:

1. Go to https://github.com/mikerowan/personal-website/settings/branches
2. Click "Add rule"
3. Set branch name pattern: `main`
4. Enable these protections:
   - ✅ Require a pull request before merging
   - ✅ Require status checks to pass before merging
   - ✅ Require branches to be up to date before merging
   - Select required status checks: `test`
5. Click "Create" or "Save changes"

## Workflow

### Making Changes
1. Create a new branch:
   ```bash
   git checkout -b feature/my-change
   ```

2. Make your changes and commit:
   ```bash
   git add .
   git commit -m "Description of changes"
   ```

3. Push to GitHub:
   ```bash
   git push origin feature/my-change
   ```

4. A Pull Request will be automatically created
5. Tests will run automatically
6. Preview deployment will be created on Vercel
7. Once tests pass and you approve, merge to main
8. Production deployment happens automatically

## What Gets Tested

- **HTML Validation**: Checks for valid HTML structure
- **Link Checking**: Ensures no broken links
- **Lighthouse**: Performance and accessibility checks
- **Vercel Preview**: Every PR gets a preview URL

## Automatic Features

- ✅ Auto PR creation from feature branches
- ✅ Automated testing on every PR
- ✅ Preview deployments for PRs
- ✅ Auto-deploy to production when merged to main
- ✅ Branch protection to prevent direct pushes to main