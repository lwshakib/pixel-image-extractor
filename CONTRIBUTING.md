## Contributing to Pixel — Image Extractor

First off, **thank you** for your interest in contributing to Pixel — Image Extractor!  
This project is maintained by [`@lwshakib`](https://github.com/lwshakib) and is open to issues, bug reports, feature requests, and pull requests.

The goal of this document is to explain **how to work on the project**, **what is expected**, and **how to get your contribution reviewed and merged**.

---

### Project overview

Pixel — Image Extractor is a **Chrome side panel extension** built with:

- **React 19 + TypeScript**
- **Vite + CRXJS** for extension tooling
- **Tailwind CSS** and **shadcn/ui / Radix UI** components

It scans the current page, extracts image URLs from multiple sources (`<img>`, `<picture>`, inline background images, SVG `<image>` tags, etc.), deduplicates them, and lets the user:

- Filter by **size** and **format**
- Sort by **file size, width, height, mimetype, or dimensions**
- **Bulk select** images
- **Download**, **copy URLs**, or **open in a new tab**

The main UI lives in `src/sidepanel/`, the background script in `src/background.ts`, and extension metadata in `manifest.config.ts`.

---

### How to set up the project locally

1. **Fork** the repository on GitHub to your own account.
2. **Clone** your fork:

```bash
git clone https://github.com/<your-username>/pixel-image-extractor.git
cd pixel-image-extractor
```

3. **Install dependencies** (Node 18+ recommended):

```bash
npm install
```

4. **Start the development server**:

```bash
npm run dev
```

5. **Load the extension in Chrome**:

- Run `npm run build` once to generate the `dist` directory, or use CRXJS dev workflow if you have it configured.
- Open `chrome://extensions/`.
- Enable **Developer mode** (top-right).
- Click **Load unpacked** and select the `dist` folder.

When you make changes to the source and rebuild, refresh the extension in `chrome://extensions/`.

---

### Branching and workflow

- **main**: stable, releasable branch.
- For any change, create a **feature branch** from `main`:

```bash
git checkout main
git pull origin main
git checkout -b feature/short-description
```

Use clear, descriptive branch names such as:

- `feature/add-size-filtering`
- `fix/sidepanel-scroll-bug`
- `chore/update-deps`

---

### Coding style and guidelines

- Use **TypeScript** everywhere possible.
- Prefer **functional React components** and **hooks**.
- Keep components **small and focused**; extract UI pieces into reusable components under `src/components/`.
- Use existing **shadcn/ui** patterns for new UI elements.
- Follow the established **Tailwind and class-variance-authority** patterns for styling.
- Maintain **strict TypeScript settings** – do not weaken `tsconfig` just to pass a build.

Before opening a PR:

1. Ensure the project **builds cleanly**:

```bash
npm run build
```

2. Manually smoke-test the extension:
   - Load a few diverse websites (image-heavy pages, dashboards, etc.).
   - Confirm the side panel loads, images are detected, filters/sorting work, and downloads/links behave correctly.

---

### Commit messages

Write **clear, descriptive commit messages** that explain the _why_, not only the _what_.

Good examples:

- `fix: handle images from picture srcset correctly`
- `feat: add size-based filtering presets`
- `chore: bump vite and tailwind versions`

Avoid messages like `update`, `fix`, or `misc changes`.

---

### Opening issues

If you find a bug or have an idea:

- **Search existing issues** first to avoid duplicates.
- If none exist, open a **new issue** and include:
  - A **clear title**
  - **Steps to reproduce** (for bugs)
  - **Expected vs actual behavior**
  - Browser and OS information
  - Screenshots or screen recordings if helpful

Feature requests should explain the **use case** and why it benefits most users.

---

### Pull request guidelines

When you are ready to submit your changes:

1. **Sync with main**:

```bash
git fetch origin
git rebase origin/main
```

2. Push your branch:

```bash
git push -u origin feature/short-description
```

3. Open a **Pull Request** against `main` on GitHub:

- Provide a **summary of the change**.
- List **any UI or behavior changes**.
- Mention **how you tested** the change.
- If it closes an issue, link it (e.g. `Closes #12`).

4. Be responsive to review comments and be open to making follow‑up changes.

All contributions are expected to follow the project’s  
**[Code of Conduct](./CODE_OF_CONDUCT.md)**.

---

### Ways to contribute (beyond code)

- Improve or extend the **documentation** (README, usage examples, screenshots).
- Help **triage issues** and answer questions.
- Propose or refine **UX improvements** in the side panel.
- Suggest **new extraction strategies** for modern web image patterns.

If you are unsure whether an idea fits, feel free to open an issue and discuss it first.

---

### Getting help

If you need clarification or guidance:

- Open a **discussion or issue** on GitHub in the [`lwshakib/pixel-image-extractor`](https://github.com/lwshakib/pixel-image-extractor) repository.

We appreciate every contribution, no matter how small.  
Thank you for helping make Pixel — Image Extractor better for everyone!
