# GitHub Pages Guide

Use GitHub Pages to give recruiters a clickable project page.

## What To Upload

Upload the contents of this folder:

```text
ai-customer-support-triage-desk
```

Do not upload:

```text
.env
```

The `.gitignore` already excludes `.env` if you use Git, but be careful when uploading through the GitHub website.

## Enable GitHub Pages

1. Open the GitHub repository.
2. Go to **Settings**.
3. Go to **Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Branch: `main`.
6. Folder: `/root`.
7. Click **Save**.

GitHub will give you a URL like:

```text
https://YOUR_USERNAME.github.io/ai-customer-support-triage-desk/
```

That is the recruiter-facing link to share.

## What The Page Shows

The public page is `index.html`. It explains:

- what the project does
- workflow stages
- architecture
- stack
- operational outcomes
- sanitized workflow exports
- setup documentation

## What Not To Share

Do not share a live n8n editor URL publicly. The editor can expose workflow internals and connected credentials.

For recruiters, share:

```text
GitHub Pages link + GitHub repository link
```

