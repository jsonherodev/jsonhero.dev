<div align="center">

# jsonhero.dev

**A free online JSON viewer, formatter, validator, editor and diff tool that runs in your browser.**<br>
Format, minify, validate, search and compare JSON with no sign-up and no ads.<br>
Your JSON stays on your device unless you click Share.

### [Open the editor →][editor] &nbsp;·&nbsp; [Compare JSON →][diff]

[Features][features] · [Pricing][pricing] · [FAQ][faq] · [Privacy](PRIVACY.md) · [Changelog](CHANGELOG.md)

<br>

<a href="https://jsonhero.dev/?utm_source=github&utm_medium=referral&utm_campaign=repo&utm_content=readme-screenshot"><img src=".github/assets/screenshot.png" width="900" alt="The jsonhero.dev editor showing formatted JSON in a collapsible tree, with search matches highlighted"></a>

</div>

## Features

### Editor

- **Format and beautify.** Pretty-print with indentation and syntax highlighting, plus line numbers and bracket matching. Pasted JSON is formatted straight away, and a tolerant parser still gives you best-effort formatting when the JSON is malformed.
- **Validate.** Input is checked with `JSON.parse` when you format, and invalid JSON is flagged with a warning.
- **Minify.** Compact JSON to a single line.
- **Collapsible tree.** Fold any object or array, or collapse and expand everything in one click.
- **Search.** Real-time search with every match highlighted across the document.
- **Load JSON your way.** Paste it, drag and drop a `.json` file, or fetch it from a public URL that allows cross-origin requests (CORS).
- **Clipboard detection.** If the editor is empty when you open or return to the page, valid JSON on your clipboard is pasted in for you. Your browser may ask for permission first.
- **Extract JSON from logs.** Paste a log line or other text with JSON inside it, like `request: {…} response: {…}`, and the JSON is pulled out and formatted.
- **Unescape.** Escaped JSON strings like `{\"id\":1}` are detected and turned back into readable JSON.
- **Download.** Save the formatted or minified result as a text file.
- **Share links.** Send a teammate a short link like `jsonhero.dev/s/AbC123XyZ0` for any valid JSON. The link is copied for you, and you can add a name. See [how sharing works](#how-sharing-works).

### Compare JSON

<a href="https://jsonhero.dev/diff.html?utm_source=github&utm_medium=referral&utm_campaign=repo&utm_content=readme-diff-screenshot"><img src=".github/assets/json-diff-comparison.png" width="900" alt="The jsonhero.dev diff page comparing two JSON documents side by side, with added, removed and changed values highlighted and the list of changes below"></a>

Open the [diff page][diff], or click **Compare** in the editor to bring your document with you.

- **See what changed.** Added, removed and changed values, plus values that changed type (the number `42` becoming the string `"42"`), side by side or as a unified diff. Object key order is ignored.
- **Cut the noise.** Match array items by a key such as `id` so a reordered list doesn't read as one big change, or compare arrays as sets. Ignore paths like `$.**.updatedAt`, allow a number tolerance, and compare strings ignoring case or surrounding whitespace.
- **Spot breaking changes.** A compatibility report flags the changes most likely to break code that reads the data.
- **Find your way around.** Search both documents at once, filter the list of changes by path, and fold unchanged lines.
- **Load each side your way.** Paste it, drop or open a file, or fetch it from a URL.
- **Share a comparison.** One link opens both documents with your rules and the view you were on.
- **Export** a comparison as a JSON Patch, a unified diff or Markdown (Pro).

Works in current versions of Chrome, Firefox, Safari and Edge.

### Keyboard shortcuts

| Shortcut | Action |
|---|---|
| <kbd>Ctrl/Cmd</kbd> + <kbd>Shift</kbd> + <kbd>M</kbd> | Minify (editor) |
| <kbd>Ctrl/Cmd</kbd> + <kbd>F</kbd> | Jump to the search box (replaces the browser's find) |
| <kbd>Enter</kbd> / <kbd>Shift</kbd> + <kbd>Enter</kbd> | Next / previous search match |
| <kbd>Ctrl/Cmd</kbd> + <kbd>Enter</kbd> | Previous search match in the editor; run the comparison on the diff page |
| <kbd>Esc</kbd> | Close a dialog or menu |

## Privacy

Formatting, minifying, validating, searching, folding, unescaping, comparing and downloading all run as JavaScript in your browser. None of them upload your JSON or send it to analytics.

**Share is the one exception.** It uploads the editor contents, or both documents when you share a comparison, so the link has something to serve.

### How sharing works

- Anyone with the link can open it. Links aren't password-protected; their only protection is a random 10-character id.
- When a link is pasted into Slack, X, Discord or another app that unfurls links, the preview shows the start of your JSON, or for a comparison, the two names and the first few changes, values included.
- When someone opens a link, Google Analytics records the page title: the share's name or, if it has none, its summary (a document's top-level keys, or a comparison's names and change counts). The link itself is never sent.
- Shares are stored without your name or account, even when you're signed in.
- A link lasts 7 days on the free plan or 30 days on Pro. After that it stops working and the stored JSON is deleted.
- **Don't share credentials, access tokens or personal data.**

What's stored, what the analytics record, and how to check all of this yourself in DevTools: [PRIVACY.md](PRIVACY.md).

## Free and Pro

| | Free | Pro |
|---|---|---|
| Format, minify, validate, search, unescape, compare | ✓ | ✓ |
| Document size | 100 KB | 1 MB |
| Share link lifetime | 7 days | 30 days |
| New share links | 30 an hour, 100 a day | 100 an hour, 500 a day |
| Comparison rules | 1 match key, 3 ignored paths | 50 match keys, 200 ignored paths |
| Saved rule presets | – | Up to 20, in your browser |
| Export a comparison (JSON Patch, unified diff, Markdown) | – | ✓ |
| Support | Email | Priority email |
| Price | Free | ₹99/month or ₹999/year in India<br>$4.99/month or $49/year elsewhere |

Prices include taxes, and Pro needs an account. The size limit covers pasting, opening a file, fetching a URL, sharing and each side of a comparison. A share link someone sent you opens on any plan, whatever its size.

## Feedback and support

- **Found a bug?** [Open a bug report](https://github.com/jsonherodev/jsonhero.dev/issues/new?template=bug_report.yml).
- **Have an idea?** [Request a feature](https://github.com/jsonherodev/jsonhero.dev/issues/new?template=feature_request.yml).
- **Security issue?** Please report it privately. See [SECURITY.md](SECURITY.md).
- **Account, billing, or removing a share link early?** Email [hello@jsonhero.dev](mailto:hello@jsonhero.dev).

Issues here are public, so please don't paste private JSON or share links you want to keep private.

## About this repository

This is the public home of jsonhero.dev: documentation, the changelog and the issue tracker. The app's source code is not published here.

If jsonhero.dev saves you time, starring this repo helps other developers find it.

---

<sub>jsonhero.dev is an independent project built and run by Akash Kumar.</sub>

[editor]: https://jsonhero.dev/?utm_source=github&utm_medium=referral&utm_campaign=repo&utm_content=readme
[diff]: https://jsonhero.dev/diff.html?utm_source=github&utm_medium=referral&utm_campaign=repo&utm_content=readme
[features]: https://jsonhero.dev/features.html?utm_source=github&utm_medium=referral&utm_campaign=repo&utm_content=readme
[pricing]: https://jsonhero.dev/pricing.html?utm_source=github&utm_medium=referral&utm_campaign=repo&utm_content=readme
[faq]: https://jsonhero.dev/faq.html?utm_source=github&utm_medium=referral&utm_campaign=repo&utm_content=readme
