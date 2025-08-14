This README gives you a **complete workflow** for local updates, GitHub pushes, and Cloudflare Pages deployment — plus a quick daily checklist for fast updates.

````markdown
# Static Site Deployment Cheat Sheet

This README provides a complete guide to managing a static site exported from WordPress, using GitHub for version control and Cloudflare Pages for hosting.

---

## 1️⃣ Initial Git Setup

1. Navigate to your static site folder:

```bash
cd /path/to/your/static-export
````

2. Initialize Git (if not already done):

```bash
git init
```

3. Add all files and commit:

```bash
git add -A
git commit -m "Initial static export"
```

4. Add your GitHub repo as the remote:

* Using **HTTPS**:

```bash
git remote add origin https://github.com/YOURUSER/YOURREPO.git
```

* If the remote already exists but points to the wrong URL:

```bash
git remote set-url origin https://github.com/YOURUSER/YOURREPO.git
```

5. Push to GitHub:

```bash
git push -u origin main
```

> ⚠️ Make sure the GitHub repo exists. For HTTPS, use a **Personal Access Token** if prompted.

---

## 2️⃣ Updating Your Site

After making changes:

```bash
git add -A
git commit -m "Update site"
git push
```

**Single-line shortcut:**

```bash
git add -A && git commit -m "Update site" && git push
```

**Optional alias** (add to `~/.zshrc` or `~/.bashrc`):

```bash
alias sitepush='git add -A && git commit -m "Update site" && git push'
```

Then run:

```bash
sitepush
```

---

## 3️⃣ Moving Your Repo

* ✅ Move the **entire folder** (including the hidden `.git` folder).
* ❌ Do **not** move only the static files.

Check for `.git` in Terminal:

```bash
ls -a
```

---

## 4️⃣ Cloudflare Pages Setup

1. Go to [Cloudflare Pages](https://pages.cloudflare.com/) and log in.
2. Click **Create a project** → connect your GitHub account.
3. Select your repository.
4. Set the build settings:

   * **Framework preset**: None (for pre-built static files)
   * **Build command**: Leave empty
   * **Build output directory**: The root folder of your static files (usually `/`)
5. Click **Deploy**.

> Cloudflare Pages automatically redeploys every time you `git push` to the connected branch.

---

## 5️⃣ Troubleshooting Common Git Issues

| Error                                          | Cause                                     | Fix                                                                  |
| ---------------------------------------------- | ----------------------------------------- | -------------------------------------------------------------------- |
| `fatal: Could not read from remote repository` | Wrong remote URL or SSH not set up        | `git remote set-url origin https://github.com/YOURUSER/YOURREPO.git` |
| `remote origin already exists`                 | Trying to add a remote that’s already set | Use `git remote set-url origin <URL>` instead of `git remote add`    |
| Push prompts for password                      | GitHub no longer allows password auth     | Use a **Personal Access Token** as your password                     |

---

## 6️⃣ Quick Tips

* Use `Command + Shift + .` in Finder to view hidden files like `.git`.
* Keep commits small and descriptive (`"Update homepage"`, `"Fix broken links"`).
* Always move the **entire repo folder** to keep Git tracking intact.
* Cloudflare Pages automatically deploys when you push to the connected branch.

---

## 7️⃣ Daily Update Workflow (2-Minute Checklist)

1. Make changes to your static site files.
2. Open Terminal and navigate to your repo:

```bash
cd /path/to/your/static-export
```

3. Stage and commit all changes:

```bash
git add -A
git commit -m "Update site"
```

4. Push to GitHub:

```bash
git push
```

> Cloudflare Pages will redeploy automatically. Your site is now live with the latest updates!

**Optional:** Use the alias `sitepush` for a single-command update:

```bash
sitepush
```

---

```
