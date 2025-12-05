# Vercel Deploy Button Setup Guide

## Quick Setup

To make the "Deploy with Vercel" button work in your repository, you need to:

### 1. Create Your GitHub Repository

First, create a repository on GitHub (e.g., `techsapiens-vibe-starter`)

### 2. URL-Encode Your Repository URL

Your repository URL needs to be URL-encoded for the deploy button to work.

**Original URL:**
```
https://github.com/username/repo-name
```

**URL-Encoded:**
```
https%3A%2F%2Fgithub.com%2Fusername%2Frepo-name
```

### 3. Update the Deploy Button in README.md

Replace this line in your README.md:

```markdown
[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=YOUR_GITHUB_REPO_URL&env=NEXT_PUBLIC_SUPABASE_URL,NEXT_PUBLIC_SUPABASE_ANON_KEY)
```

With your actual repository URL (URL-encoded):

```markdown
[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fusername%2Frepo-name&env=NEXT_PUBLIC_SUPABASE_URL,NEXT_PUBLIC_SUPABASE_ANON_KEY)
```

### 4. Quick URL Encoding

You can use any of these methods:

**Online Tool:**
- Visit https://www.urlencoder.org/
- Paste your GitHub repo URL
- Copy the encoded result

**Command Line:**
```bash
# Using Python
python3 -c "import urllib.parse; print(urllib.parse.quote('https://github.com/username/repo-name', safe=''))"

# Using Node.js
node -e "console.log(encodeURIComponent('https://github.com/username/repo-name'))"
```

**Manual Encoding:**
- `:` becomes `%3A`
- `/` becomes `%2F`
- `#` becomes `%23`
- `?` becomes `%3F`
- `&` becomes `%26`

### 5. Example

If your repository is:
```
https://github.com/techsapiens/ai-sync-day-starter
```

The deploy button URL should be:
```
https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Ftechsapiens%2Fai-sync-day-starter&env=NEXT_PUBLIC_SUPABASE_URL,NEXT_PUBLIC_SUPABASE_ANON_KEY
```

### 6. Test the Button

After updating, click the deploy button in your README. It should:
1. Redirect to Vercel
2. Show your repository in the clone dialog
3. Allow you to set up Supabase environment variables
4. Deploy your project

## Troubleshooting

**Button doesn't work:**
- Check that the URL is properly encoded
- Ensure the repository is public (or you're logged in to GitHub)
- Verify the repository URL is correct

**Environment variables not showing:**
- The `&env=...` part tells Vercel which environment variables to prompt for
- Make sure they're comma-separated: `NEXT_PUBLIC_SUPABASE_URL,NEXT_PUBLIC_SUPABASE_ANON_KEY`

**Repository not found:**
- Ensure the repository exists and is accessible
- Check for typos in the URL
- Verify the repository name matches exactly

## For Hackathon Organizers

If you're providing a starter kit template:

1. **Option A:** Create a template repository and use its URL in the starter kit README
2. **Option B:** Leave it as `YOUR_GITHUB_REPO_URL` and instruct participants to replace it (as we've done)
3. **Option C:** Create a script that auto-generates the deploy button URL for each participant

The current approach (Option B) gives participants flexibility to use their own repositories.

