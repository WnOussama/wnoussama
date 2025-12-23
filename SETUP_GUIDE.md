# Setup Guide for GitHub Stats

This repository includes an automated GitHub stats generation system powered by [jstrieb/github-stats](https://github.com/jstrieb/github-stats).

## Initial Setup

Follow these steps to enable the stats generation:

### 1. Create a Personal Access Token

1. Go to GitHub Settings → Developer settings → Personal access tokens → Tokens (classic)
2. Click "Generate new token (classic)"
3. Give it a descriptive name (e.g., "GitHub Stats")
4. Select the following scopes:
   - `read:user` - Read user profile data
   - `repo` - Full control of repositories (needed to read private repo stats)
5. Click "Generate token"
6. **Copy the token immediately** - you won't be able to see it again!

### 2. Add the Token as a Repository Secret

1. Go to your repository settings
2. Navigate to "Secrets and variables" → "Actions"
3. Click "New repository secret"
4. Name: `ACCESS_TOKEN`
5. Value: Paste your personal access token
6. Click "Add secret"

### 3. Run the Workflow

1. Go to the "Actions" tab in your repository
2. Click on "Generate Stats Images" workflow
3. Click "Run workflow" dropdown
4. Click the green "Run workflow" button
5. Wait for the workflow to complete (usually takes 1-2 minutes)

### 4. View Your Stats

Once the workflow completes successfully:
- Check the `generated/` folder for the SVG files
- Your profile README will automatically display the stats
- Stats will update automatically every day at 00:05 UTC

## Optional Configuration

### Exclude Specific Repositories

If you want to exclude certain repositories from the stats:

1. Go to repository settings → Secrets and variables → Actions
2. Create a new secret named `EXCLUDED`
3. Value: Comma-separated list of repos in `owner/name` format
   - Example: `WnOussama/test-repo,WnOussama/another-repo`

### Exclude Specific Languages

To exclude certain programming languages:

1. Create a new secret named `EXCLUDED_LANGS`
2. Value: Comma-separated list of languages
   - Example: `html,css,tex`

## Troubleshooting

### Workflow Fails

- Check that your `ACCESS_TOKEN` is valid and has the correct permissions
- Make sure the token isn't expired
- Check the workflow logs in the Actions tab for specific errors

### Stats Not Showing

- Ensure the workflow has run successfully at least once
- Check that the SVG files exist in the `generated/` folder
- Verify the image URLs in README.md point to the correct branch (`master` or `main`)

### Need Help?

- Check the [original project documentation](https://github.com/jstrieb/github-stats)
- Review the [GitHub Actions documentation](https://docs.github.com/en/actions)

## How It Works

1. The GitHub Actions workflow runs daily (or manually)
2. Python scripts query the GitHub API using your personal access token
3. Statistics are collected about your repositories, contributions, and languages
4. SVG images are generated from templates
5. The generated images are committed back to the repository
6. Your README displays these images

## Credits

Stats generation powered by [jstrieb/github-stats](https://github.com/jstrieb/github-stats)
