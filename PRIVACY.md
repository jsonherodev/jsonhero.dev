# How jsonhero.dev handles your data

This is a plain-English summary. The [privacy policy](https://jsonhero.dev/privacy.html) is the authoritative version, and if the two ever disagree, the policy wins.

**The short version: your JSON stays on your device unless you click Share.**

## What runs in your browser

Formatting, minifying, validating, searching, folding, unescaping, comparing and downloading are all done by JavaScript on your device. None of them upload the JSON you work on or send it to analytics. When you click **Compare** in the editor, your document is handed to the diff page through your browser's session storage, never through the URL.

**Load from URL** is fetched by your browser, directly from the address you enter. The request never passes through jsonhero.dev, and the site you fetch from has to allow cross-origin requests (CORS).

## What happens when you click Share

Sharing is the one action that uploads your JSON, because the link needs something to serve. Sharing a comparison uploads both documents, and is stored and deleted the same way.

**What's stored**

- the JSON text, in a private storage bucket; for a comparison, both documents with their names, your comparison rules and the view you shared from
- its size and a checksum
- a short preview snippet and an auto-generated summary, such as `JSON object · 3 keys: id, name, email`, or for a comparison, its names and change counts
- a preview image of its first few lines, or a comparison's first few changes, for link previews
- the name you give it, if any
- a view count
- the plan it was shared on, to apply that plan's limits
- a salted hash of your IP address, used only for rate limiting

**Who can see it.** Anyone who has the link. Links aren't password-protected; their only protection is a random 10-character id that is effectively unguessable. When a link is pasted into Slack, X, Discord or another app that unfurls links, the preview card shows the start of your JSON, or for a comparison, the two names and the first few changes, values included. Share pages are marked `noindex`, so search engines are asked not to list them, but a link posted somewhere public can still be opened by anyone who finds it. When someone opens a link, Google Analytics records the page title but never the link; see [Analytics](#accounts-analytics-and-payments).

**Who it's tied to.** No one. Shares are stored without your name or account, even when you're signed in.

**How long it lasts.** 7 days from upload on the free plan, or 30 days on Pro. After that the link stops working, and a daily cleanup job deletes the stored JSON and its preview image. To remove a link sooner, email [hello@jsonhero.dev](mailto:hello@jsonhero.dev).

**Don't share credentials, access tokens or personal data through a link.**

## Accounts, analytics and payments

- **Sign-in is optional.** You can use Google, GitHub, Microsoft or a code sent by email. Sign-in providers share your email, name and profile picture, never your password or wider account access.
- **Cookies.** Signing in sets a single HttpOnly, SameSite=Lax cookie that holds only random values. If you arrive from a link with campaign tags (`utm_`) or from another site, a first-party `jh_ref` cookie notes those tags, that site's name, the page you landed on and when. It lasts 90 days and is read only if you then create an account, which records how you found us. Google Analytics sets its own cookies.
- **Analytics.** Google Analytics runs on every page. It records page views, approximate region, device and browser type, and traffic source, plus a few actions: signing in or creating an account, creating a share link (and whether it's a document or a comparison), starting a checkout, and upgrading to Pro with the plan and price. It never receives your JSON. Page addresses reach it with share ids blanked out and every query parameter except campaign tags removed. On a share link it does record the page title: the share's name or, if it has none, its summary, such as `JSON object · 3 keys: id, name, email` or a comparison's names and change counts.
- **Hosting.** Hosting, storage, database, sign-in and email run on Amazon Web Services in the Asia Pacific (Mumbai) region.
- **Payments.** Paddle handles payments as Merchant of Record. Card numbers, UPI IDs and bank details are entered with Paddle and never reach jsonhero.dev.

## Check it yourself

You don't have to take any of this on trust.

1. Open [jsonhero.dev](https://jsonhero.dev), then open your browser's developer tools (<kbd>F12</kbd>, or <kbd>Cmd</kbd> + <kbd>Option</kbd> + <kbd>I</kbd> on a Mac) and switch to the **Network** tab.
2. Paste some JSON, then format, minify, search, fold and download it. The [diff page](https://jsonhero.dev/diff.html) passes the same test with two documents.
3. Watch the requests. Besides page assets and analytics, you'll see two small calls to jsonhero.dev: `GET /api/auth/session`, which checks whether you're signed in, and `POST /api/shares/reserve`, which sets aside a link id as soon as the editor has content so that Share can copy the link instantly. Open any of them and check the payload: your JSON isn't in it.
4. Now click **Share**. A `PUT /api/shares/<id>` request appears. That's the upload, and the one time your JSON leaves your device.
5. For the strongest proof, go offline. Leave the page open (don't reload it), set the Network tab's throttling to **Offline** or turn off Wi-Fi, and repeat step 2. Everything still works, because none of it needs the network. Only Share, sign-in and Load from URL stop.

## Questions

Email [hello@jsonhero.dev](mailto:hello@jsonhero.dev).
