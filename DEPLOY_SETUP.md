# Setting Up Your Vercel Deploy Button

This guide will help you set up the "Deploy with Vercel" button in your repository so you can quickly deploy your Community OS project.

## Step-by-Step Setup

### Step 1: Create Your GitHub Repository

1. Go to GitHub and create a new repository
2. Name it something like `ai-sync-day-community-os` or `techsapiens-vibe-starter`
3. Make it **public** (required for the deploy button to work)
4. Copy your repository URL (e.g., `https://github.com/yourusername/your-repo-name`)

### Step 2: URL-Encode Your Repository URL

The deploy button needs your repository URL to be URL-encoded. Here's how:

**Option A: Use an Online Tool (Easiest)**
1. Go to https://www.urlencoder.org/
2. Paste your GitHub repository URL
3. Click "Encode"
4. Copy the encoded result

**Option B: Use Command Line**

```bash
# Using Python
python3 -c "import urllib.parse; print(urllib.parse.quote('https://github.com/yourusername/your-repo-name', safe=''))"

# Using Node.js
node -e "console.log(encodeURIComponent('https://github.com/yourusername/your-repo-name'))"
```

**Option C: Manual Encoding**
Replace these characters:
- `:` → `%3A`
- `/` → `%2F`
- `#` → `%23`
- `?` → `%3F`
- `&` → `%26`

**Example:**
- Original: `https://github.com/username/repo-name`
- Encoded: `https%3A%2F%2Fgithub.com%2Fusername%2Frepo-name`

### Step 3: Update Your README.md

1. Open your `README.md` file
2. Find this line:
   ```markdown
   [![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=YOUR_GITHUB_REPO_URL&env=NEXT_PUBLIC_SUPABASE_URL,NEXT_PUBLIC_SUPABASE_ANON_KEY)
   ```

3. Replace `YOUR_GITHUB_REPO_URL` with your **URL-encoded** repository URL

4. The final line should look like:
   ```markdown
   [![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fyourusername%2Fyour-repo-name&env=NEXT_PUBLIC_SUPABASE_URL,NEXT_PUBLIC_SUPABASE_ANON_KEY)
   ```

### Step 4: Test Your Deploy Button

1. Commit and push your changes to GitHub
2. View your README on GitHub
3. Click the "Deploy with Vercel" button
4. You should be redirected to Vercel where you can:
   - Connect your GitHub account
   - Set up Supabase environment variables
   - Deploy your project

## Complete Example

Let's say your repository is:
```
https://github.com/johndoe/ai-sync-community-os
```

**Step 1:** URL-encode it:
```
https%3A%2F%2Fgithub.com%2Fjohndoe%2Fai-sync-community-os
```

**Step 2:** Update your README.md:
```markdown
[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fjohndoe%2Fai-sync-community-os&env=NEXT_PUBLIC_SUPABASE_URL,NEXT_PUBLIC_SUPABASE_ANON_KEY)
```

**Step 3:** Commit and push:
```bash
git add README.md
git commit -m "Update deploy button with my repo URL"
git push
```

**Step 4:** Click the button in your GitHub README and deploy! 🚀

## Troubleshooting

### The button doesn't work

- ✅ **Check URL encoding:** Make sure your repository URL is properly encoded
- ✅ **Repository visibility:** Ensure your repository is **public** (or you're logged into GitHub)
- ✅ **URL correctness:** Double-check for typos in your repository URL
- ✅ **GitHub access:** Make sure the repository exists and you have access to it

### Environment variables not showing

The deploy button includes `&env=NEXT_PUBLIC_SUPABASE_URL,NEXT_PUBLIC_SUPABASE_ANON_KEY` which tells Vercel to prompt for these variables. If they don't show up:
- Make sure the `&env=...` part is included in your URL
- Variables should be comma-separated (no spaces)
- You can add them manually in Vercel dashboard after deployment

### Repository not found error

- Verify the repository exists on GitHub
- Check that the repository name matches exactly (case-sensitive)
- Ensure you're using the full URL: `https://github.com/username/repo-name`
- Try accessing the repository URL directly in your browser

### Deploy fails

- Make sure your repository has all necessary files
- Check that `package.json` exists with proper scripts
- Verify environment variables are set correctly in Vercel
- Check Vercel deployment logs for specific errors

## Quick Reference

**Template:**
```markdown
[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=YOUR_ENCODED_REPO_URL&env=NEXT_PUBLIC_SUPABASE_URL,NEXT_PUBLIC_SUPABASE_ANON_KEY)
```

**URL Encoder:**
- Online: https://www.urlencoder.org/
- Python: `python3 -c "import urllib.parse; print(urllib.parse.quote('YOUR_URL', safe=''))"`
- Node: `node -e "console.log(encodeURIComponent('YOUR_URL'))"`

## Need Help?

If you're stuck:
1. Check the main [README.md](./README.md) for project setup
2. Review [DATA_WORKFLOW.md](./DATA_WORKFLOW.md) for data handling
3. Ask in the hackathon chat or Discord
4. Check Vercel's official docs: https://vercel.com/docs/deploy-button

---

**Pro Tip:** Once your deploy button works, you can share it with your team members or use it to quickly deploy to different Vercel projects for testing!
