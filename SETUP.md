# 🛠️ GitHub Profile Setup Guide

A quick-start guide to get all auto-updating features working.

---

## 1. Required GitHub Token Permissions

### `GITHUB_TOKEN` (auto-provided — no setup needed)
Used by: `snake.yml`, `update-readme.yml`

GitHub automatically injects this token for every workflow run. You just need to ensure **Actions are enabled** on the repo (see step 3).

### `METRICS_TOKEN` (optional — only if using `metrics.yml`)
Used by: `metrics.yml` (lowlighter/metrics)

1. Go to **GitHub → Settings → Developer Settings → Personal Access Tokens → Tokens (classic)**
2. Click **Generate new token (classic)**
3. Set expiration (e.g. 1 year), and select scopes:
   - `read:user`
   - `repo` (if you want private repo stats)
   - `read:org` (optional, for org data)
4. Copy the generated token
5. In your `hashirahmad806/hashirahmad806` repo → **Settings → Secrets and variables → Actions**
6. Click **New repository secret**, name it `METRICS_TOKEN`, paste the value

---

## 2. Enable GitHub Actions Write Permissions

The snake workflow needs to push to the `output` branch.

1. In your repo: **Settings → Actions → General**
2. Scroll to **Workflow permissions**
3. Select **Read and write permissions**
4. Click **Save**

---

## 3. Enable GitHub Actions

1. Go to your `hashirahmad806/hashirahmad806` repo
2. Click the **Actions** tab
3. If prompted, click **"I understand my workflows, go ahead and enable them"**

---

## 4. Create the `output` Branch (first run)

The snake SVG is pushed to a branch called `output`. On first run it's created automatically.
But you can also create it manually:

```bash
git checkout --orphan output
git rm -rf .
git commit --allow-empty -m "init output branch"
git push origin output
git checkout main
```

---

## 5. Run the Workflows Manually (First Time)

After enabling Actions:

1. Go to **Actions tab** in your repo
2. Click **"🐍 Generate Contribution Snake"** → **Run workflow** → **Run**
3. Wait ~1 min for it to complete
4. The snake SVG will appear in the `output` branch
5. The README snake section will now show the animation ✅

Repeat for **"📰 Update README Recent Activity"** to populate the recent activity section.

---

## 6. Customizing Placeholders in README.md

Open `README.md` and search for `<!-- REPLACE -->` to find all placeholder sections:

| Placeholder | What to add |
|-------------|------------|
| Project rows with 🔧 | Your real project name, description, tech stack, live URL, repo URL |
| Education/Experience code block | Your internships, roles, GPA, graduation year |

---

## 7. Accent Color

The current accent color is **Sky Blue `#38BDF8`** with a secondary of **Purple `#7C3AED`**.
To change it, find-and-replace `38BDF8` and `7C3AED` in `README.md`.

---

## Workflow Schedule Summary

| Workflow | Schedule | Trigger |
|----------|----------|---------|
| 🐍 Snake animation | Every 6 hours | Cron + manual |
| 📰 Recent activity | Every 6 hours | Cron + manual |
| 📊 Metrics (optional) | Daily at midnight UTC | Cron + manual |
