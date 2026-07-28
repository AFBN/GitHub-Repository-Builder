# GitHub-Repository-Builder

A single‑page, self‑contained HTML application that lets you create fully‑configured GitHub repositories right from your browser.   Authenticate with a Personal Access Token, edit branding files, add custom files, upload binary assets, and publish everything in one click – no server, no build tools, no external dependencies.

## Getting Started

Open `index.html` in your browser. No build tools required.

## License

MIT © 2026 AFBN

# GitHub Repository Publisher

A single‑page, self‑contained HTML application that lets you create fully‑configured GitHub repositories right from your browser.  
Authenticate with a Personal Access Token, edit branding files, add custom files, upload binary assets, and publish everything in one click – no server, no build tools, no external dependencies.

---

## Features

- **Token‑based authentication** – Connect your GitHub account with a classic Personal Access Token (scope: `repo`). The token is kept **only in browser memory** and never sent anywhere except the official GitHub API.
- **Create new repositories** – Set name, description, and visibility (public / private).
- **Branding file editor** – Built‑in code editor for `README.md`, `index.html`, `style.css`, and `script.js` with live placeholder replacement (`GitHub-Repository-Builder`, `A single‑page, self‑contained HTML application that lets you create fully‑configured GitHub repositories right from your browser.   Authenticate with a Personal Access Token, edit branding files, add custom files, upload binary assets, and publish everything in one click – no server, no build tools, no external dependencies.`, `2026`, `AFBN`).
- **Load files from disk** – Populate any branding textarea by importing a local `.txt` file.
- **Remove unwanted branding files** – Each branding file has a red ✕ button to remove it from the publish list. Removed files appear in a restore list so you can bring them back.
- **Custom text files** – Add any text file with an arbitrary extension via a modal. Choose a language type (JavaScript, Python, HTML, CSS, Markdown, JSON, plain text, or other) – the extension is applied automatically. Edit or remove previously added custom files.
- **Additional binary files** – Upload `.txt`, `.docx`, or `.pdf` files via drag‑and‑drop or file picker. Conflict checks prevent overwriting reserved names.
- **One‑click publish** – All visible branding files, custom text files, and additional binary files are committed to the new repository in a single operation.
- **WordPress‑safe** – Nuclear CSS overrides hide theme headers/footers when embedded in a WordPress custom HTML block. Works perfectly in sandboxed environments.
- **No server required** – Just open `index.html` in any modern browser.

---

## Quick Start

1. **Get a GitHub Personal Access Token (classic)**  
   Go to [github.com/settings/tokens](https://github.com/settings/tokens/new?scopes=repo&description=GitHub%20Repository%20Publisher) and create a token with the `repo` scope. Copy it.

2. **Open the tool**  
   Download or clone this repository, then open `index.html` in your browser. Alternatively, paste the entire HTML into a WordPress custom HTML block or any static file host.

3. **Connect your GitHub account**  
   Paste the token into the “Personal Access Token” field and click **Connect GitHub Account**.

4. **Configure your new repository**  
   - Enter a repository name (required) and an optional description.
   - Toggle the switch between **Private** and **Public**.

5. **Edit branding files**  
   Use the text areas for `README.md`, `index.html`, `style.css`, and `script.js`. The placeholders `GitHub-Repository-Builder`, `A single‑page, self‑contained HTML application that lets you create fully‑configured GitHub repositories right from your browser.   Authenticate with a Personal Access Token, edit branding files, add custom files, upload binary assets, and publish everything in one click – no server, no build tools, no external dependencies.`, `2026`, and `AFBN` are replaced automatically when you publish.

   - **Load from File** replaces the content of a textarea with the contents of a local `.txt` file.
   - **Remove** (red ✕) hides a file from the publish list. Removed files appear in a restore panel below the editors.

6. **Add custom text files (optional)**  
   Click **Add File** under “Custom Text Files”.  
   - Enter a file name (e.g., `app.py`) and choose a language type – the extension is auto‑filled.  
   - Write the content and click **Add File**.  
   - Use the **Edit** button on any existing custom file to change its name, language type, or content.

7. **Add additional binary files (optional)**  
   Drag & drop `.txt`, `.docx`, or `.pdf` files onto the upload area, or use the **Select Files** button. Remove individual files or clear all with the **Clear All** button.

8. **Publish**  
   Click **Publish to GitHub**. The tool will:
   - Create the repository (private or public).
   - Upload all active branding files (placeholders replaced).
   - Upload all custom text files.
   - Upload all additional binary files.

   A success banner with a link to the new repository will appear, and all form fields are cleared.

---

## File Structure

The entire application is contained in a single HTML file. No external JavaScript, CSS, or images are required.

```
index.html        # The complete application
README.md         # This file
```

---

## How It Works

- **Authentication** – The GitHub token is stored in session storage (or memory fallback) and attached to every API request via the `Authorization` header.
- **Repository creation** – A `POST` to `/user/repos` creates the repository without initializing it (`auto_init: false`).
- **File uploads** – Each file is uploaded individually using the [GitHub Contents API](https://docs.github.com/en/rest/repos/contents). Text files are Base64‑encoded, and binary files are read as data URLs before encoding.
- **All API calls** are made directly from the browser to `api.github.com`. No third‑party proxy or server is involved.

---

## Security

- The Personal Access Token is **never** stored permanently. It is kept in `sessionStorage` (cleared when the tab is closed) or in an in‑memory fallback when `sessionStorage` is not available (e.g., sandboxed WordPress environments).
- The token is only sent to `https://api.github.com` – no other domains.
- No client secret, OAuth redirect, or external proxy is used, eliminating the risk of token leakage to third parties.

---

## Compatibility

- **Modern browsers** – Chrome, Firefox, Safari, Edge.
- **WordPress custom HTML blocks** – Extensive CSS overrides hide theme headers, footers, and other unwanted elements. The layout remains fully functional inside any sandboxed environment.
- **Static file hosting** – Works from any local or remote server.

---

## Customisation

All styling is embedded in the `<style>` block and uses CSS custom properties (`--bg`, `--surface`, `--accent`, etc.). Adjust these variables to match your brand.

The default branding file templates can be edited directly in the textareas. If you want to change the initial content permanently, modify the `<textarea>` elements inside `index.html`.

---

## License

MIT © 2025

Feel free to use, modify, and distribute this tool as you wish.

---

## Contributing

Contributions, bug reports, and feature requests are welcome!  
Open an issue or submit a pull request with your improvements.

---

## Acknowledgements

- Built with vanilla HTML, CSS, and JavaScript – no frameworks.
- Inspired by the need for a frictionless way to spin up branded repositories directly from a browser.