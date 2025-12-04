# GitHub Secrets Setup Guide

## The Error You're Seeing

The workflow is failing because GitHub secrets are not set. The error shows:
```
VERCEL_TOKEN: (empty)
VERCEL_ORG_ID: (empty)
VERCEL_PROJECT_ID: (empty)
```

## Solution: Set GitHub Secrets

### Step 1: Get Your Vercel Credentials

1. **VERCEL_TOKEN:**
   - Go to [Vercel Dashboard](https://vercel.com/account/tokens)
   - Click **"Create Token"**
   - Give it a name (e.g., "GitHub Actions")
   - Copy the token (you won't see it again!)

2. **VERCEL_ORG_ID:**
   - Go to your Vercel project
   - Settings → General
   - Scroll to **"Organization ID"**
   - Copy the value

3. **VERCEL_PROJECT_ID:**
   - Same page (Settings → General)
   - Scroll to **"Project ID"**
   - Copy the value

### Step 2: Add Secrets to GitHub

1. Go to your GitHub repository
2. Click **Settings** → **Secrets and variables** → **Actions**
3. Click **"New repository secret"**
4. Add each secret:
   - **Name:** `VERCEL_TOKEN` → **Value:** [your token]
   - **Name:** `VERCEL_ORG_ID` → **Value:** [your org ID]
   - **Name:** `VERCEL_PROJECT_ID` → **Value:** [your project ID]

### Step 3: Verify

After adding secrets, push a new commit or re-run the workflow. The workflow now includes validation that will show clear error messages if secrets are missing.

## Alternative: Use Vercel's Built-in GitHub Integration

If you prefer not to use GitHub Actions, you can use Vercel's built-in GitHub integration:

1. Go to Vercel Dashboard
2. Import your GitHub repository
3. Vercel will automatically deploy on every push
4. No GitHub Actions needed!

This is simpler and recommended for most use cases.

## What I Fixed in the Workflow

1. ✅ Added quotes around token: `--token="${{ secrets.VERCEL_TOKEN }}"`
2. ✅ Added validation step to check if secrets are set
3. ✅ Better error messages if secrets are missing

The workflow code is now correct - you just need to add the secrets to GitHub!

