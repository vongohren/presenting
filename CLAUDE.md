# Presenting

Encrypted HTML presentations hosted on GitHub Pages.

## How It Works

1. Create HTML files in `source/` (unencrypted, human-readable)
2. Encrypt with StatiCrypt and output to `public/<name>/index.html`
3. Push to `main` — GitHub Actions deploys `public/` to Pages
4. Viewers need a password to decrypt in-browser (AES-256, client-side only)

## Encrypt a file

```bash
npx staticrypt source/my-file.html -p 'PASSWORD' -d public/my-file/ --template-title "My Title"
```

The encrypted file replaces the original filename with `index.html` in the output dir.

## Structure

- `source/` — Unencrypted HTML source files (committed for editing)
- `public/` — Encrypted HTML served by GitHub Pages
- `public/index.html` — Landing page (unencrypted, just links)

## Adding a new presentation

1. Create `source/my-topic.html` (self-contained HTML)
2. Run: `npx staticrypt source/my-topic.html -p 'PASSWORD' -d public/my-topic/ --template-title "My Topic"`
3. Add a link in `public/index.html`
4. Commit and push

## Notes

- Images can use external URLs (loaded by browser after decryption)
- For fully offline presentations, inline images as base64 data URIs
- `.staticrypt.json` is gitignored (generated salt file)
