# How to Publish Your Updated Website

Your site **https://summerzhao618.github.io** is published by **GitHub Pages**, not by the "Scrape Talk Locations" workflow. Pages rebuilds the site whenever you push to the **branch set as the publishing source** (often `master`).

## Step 1: Commit and push your changes (on `revision_v1`)

Run these in your repo folder (PowerShell or Git Bash):

```powershell
cd "c:\Users\zhaox\Documents\GitHub\summerzhao618.github.io"

# Stage all website updates (exclude PubliscationList.docx if you don't want it in the repo)
git add _pages/ _publications/
git status

# Commit
git commit -m "Update about page, education, research experience; sync publications with Google Scholar and add paper links"

# Push to your branch
git push origin revision_v1
```

If you also want to include the 404 change:
```powershell
git add _pages/404.md
```

To **exclude** `PubliscationList.docx` from the commit, don’t run `git add .`; only add the paths above.

---

## Step 2: Get the updates onto the branch that GitHub Pages uses

1. **Check the Pages source**
   - On GitHub: open **summerzhao618/summerzhao618.github.io** → **Settings** → **Pages**.
   - Under **Build and deployment** → **Source**, see which **branch** (and folder) is selected (e.g. `master` or `main`).

2. **If the source is `master` (or `main`)**  
   Your updates are on `revision_v1`. To publish them:

   **Option A – Merge on GitHub (simplest)**  
   - Go to the repo → **Pull requests** → **New pull request**.  
   - Base: `master`, Compare: `revision_v1`.  
   - Create the PR, then **Merge pull request**.  
   - GitHub Pages will build and publish from `master` after the merge.

   **Option B – Merge locally and push**  
   ```powershell
   git checkout master
   git pull origin master
   git merge revision_v1 -m "Merge revision_v1: about page and publications update"
   git push origin master
   ```

3. **If the source is `revision_v1`**  
   After Step 1, you’re done. Pages will deploy from `revision_v1` automatically.

---

## Step 3: Confirm the site updated

- **Settings** → **Pages**: see the last deployment time and link.
- **Actions** tab: if “Pages build and deployment” (or similar) runs, wait for it to finish.
- Open **https://summerzhao618.github.io** and check the About and Publications pages.

---

## Summary

| Goal                         | What to do |
|-----------------------------|------------|
| Save and push your work     | Step 1 (commit + push `revision_v1`) |
| Publish the live site       | Step 2 (merge into the Pages branch or set source to `revision_v1`) |
| Check it worked             | Step 3 (Settings → Pages, then open the site) |

The **Scrape Talk Locations** workflow only runs when `talks/`, `_talks/`, or `talkmap.ipynb` change; it does not control publishing. Publishing is done by **GitHub Pages** when you push to the branch set under **Settings → Pages**.
