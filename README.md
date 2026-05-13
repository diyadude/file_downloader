# GitHub Actions File Downloader

Download any file from the internet directly into your GitHub repository — for free, no activation code, no size limits.

---

## Features

- Download files from any public URL into your repo
- Supports files of any size (auto-splits large files into 90MB zip parts)
- Optional zip password protection
- Two download modes: individual files or combine all into one archive
- Download multiple files at once (space-separated URLs)
- Reliable downloads with aria2c + curl fallback and automatic retries
- Files stored permanently in your GitHub repository
- One-click cleanup workflow to reset the downloads folder

---

## Setup

1. **Fork this repository** (click the Fork button at the top right)
2. In your fork, go to **Settings → Actions → General**
3. Under "Workflow permissions", select **Read and write permissions**
4. Click **Save**

That's it — no tokens, no secrets, no configuration needed.

---

## How to Download a File

1. Go to the **Actions** tab in your forked repo
2. Click **Download File** in the left sidebar
3. Click **Run workflow**
4. Fill in the fields:
   - **Download URLs**: Paste one or more file URLs (separate multiple URLs with spaces)
   - **Download mode**: Choose `normal` or `zip` (see below)
   - **Password**: Optional — leave blank for no encryption
5. Click **Run workflow** and wait for it to finish (up to 6 hours for very large files)

---

## Download Modes

| Mode | What it does |
|------|-------------|
| `normal` | Each file gets its own folder with a README containing its download link |
| `zip` | All files are combined into a single zip archive (with optional password) |

---

## Finding Your Downloaded Files

After the workflow completes:

1. Go to the **Code** tab of your repo
2. Open the `downloads/` folder
3. Each subfolder contains a `README.md` with direct download links for that file

For large files split into multiple parts, download all parts (`.zip`, `.z01`, `.z02`, ...) and open the `.zip` file with **7-Zip** or **WinRAR** — the parts combine automatically.

---

## How to Clean Up

To delete all downloaded files:

1. Go to **Actions** tab
2. Click **Clean Downloads** in the left sidebar
3. Click **Run workflow** → **Run workflow**

This resets the `downloads/` folder back to empty.

---

## Notes & Limits

- **Job timeout**: 6 hours maximum per run
- **File size**: No hard limit, but GitHub has a 100MB per-file limit — large files are automatically split into 90MB zip parts to work around this
- **Server compatibility**: Some servers block requests from GitHub Actions IPs (this is a server-side restriction, not a bug)
- **Private URLs**: URLs that require login or authentication cannot be downloaded

---

## Workflows

| Workflow | Purpose |
|----------|---------|
| Download File | Download files from URLs into `downloads/` |
| Clean Downloads | Delete all files in `downloads/` |
