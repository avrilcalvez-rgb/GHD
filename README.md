# Gray Home Decor Estimator — External JSON (GitHub Pages)

This site ships with **no embedded prices**. Load pricing at runtime via JSON.

## Use it
1. Open **index.html** (or your GitHub Pages site URL).
2. Click **Import JSON** in the UI and select your pricing file (e.g., `ghd_estimator_data.json`).

## Publish on GitHub Pages
1. Create a new GitHub repository.
2. Upload all files in this folder.
3. In **Settings → Pages**, set **Source:** Deploy from branch, **Branch:** main, **Folder:** /(root).
4. Open the published URL.

## Optional: auto-load a PUBLIC JSON
Place your file at `pricing/ghd_estimator_data.json` and add this snippet **before `</body>`** in `index.html`:

```html
<script>
(async () => {
  try {
    const r = await fetch('./pricing/ghd_estimator_data.json', { cache: 'no-store' });
    if (!r.ok) return;
    const data = await r.json();
    localStorage.setItem('ghd_estimator_data', JSON.stringify(data));
    if (typeof window.renderMaster === 'function') renderMaster();
  } catch {}
})();
</script>
```
**Note:** Public JSON means anyone can view it.
