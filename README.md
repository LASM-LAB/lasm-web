# lasm-web

LASM Lab homepage static export.

This folder contains only the homepage and the assets it needs. It is ready to push to:

https://github.com/LASM-LAB/lasm-web

## Push to GitHub

```bash
git init
git branch -M main
git remote add origin https://github.com/LASM-LAB/lasm-web.git
git add .
git commit -m "Deploy homepage"
git push -u origin main
```

## Preview Locally

Run the preview server from the parent `dist` directory:

```bash
cd ..
python3 -m http.server 8765
```

Then open:

http://127.0.0.1:8765/lasm-web/

## GitHub Pages

In the GitHub repository, enable Pages from the `main` branch root.
