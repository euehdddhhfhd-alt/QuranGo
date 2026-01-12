# AdSense Implementation Guide ✅

This guide shows where to paste AdSense ad unit code in your HTML and how to troubleshoot common issues.

> Tip: If you are not familiar with HTML, search for `HTML basics` or `HTML tutorial` before making changes.

## Before you begin
- Understand the difference between the AdSense library script (the `adsbygoogle.js` loader) and ad unit code (the `<ins>` block plus the `push()` call). Load the library once (preferably in `<head>`) and add ad units inside `<body>` where you want them to appear.

## Where to add ad unit code
- Paste your ad unit code between the `<body>` and `</body>` tags of each page where you want an ad to appear. If you paste the ad code outside the `<body>` tags it may prevent ads from rendering correctly.

Example (responsive ad recommended):

```html
<!-- Place once in the <head> -->
<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-2491298111552226" crossorigin="anonymous"></script>

<!-- Put the following inside <body> where you want the ad -->
<ins class="adsbygoogle"
     style="display:block"
     data-ad-client="ca-pub-2491298111552226"
     data-ad-slot="3364264934"
     data-ad-format="auto"
     data-full-width-responsive="true"></ins>
<script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
```

> Note: The example above is for demonstration — copy your own ad code from your AdSense account and paste it exactly.

---

## How to position ads on your site with HTML
Just like other elements (images, paragraphs), you can control ad placement with HTML containers (`<div>`, `<aside>`, etc.). Example to center an ad:

```html
<div align="center">
  <!-- ad unit here -->
</div>
```

For responsive behavior, prefer `data-ad-format="auto"` so the ad adapts to available width.

---

## Common issues with ad code
Ads might not appear on your site if you find any of the following problems with your ad code:
- Your ad code doesn't appear in its entirety (for example, there's a missing `<script>` or `<ins>` tag).
- Your ad code displays all on one line (line breaks lost during pasting or through an editor).
- Your ad code has extra HTML tags within it (editors sometimes insert wrappers or formatting).

If you notice any of these issues, replace the broken ad code with fresh ad code copied from the Ads page in your AdSense account. Also review the quick fixes below:

- Missing tags: ensure the `<script>`, `<ins>`, and the following `<script>(adsbygoogle...)</script>` appear exactly as copied.
- All-on-one-line code: preserve line breaks when pasting; some editors may collapse whitespace.
- Extra HTML inside the snippet: paste the snippet raw, without additional tags inside it.
- Ad blockers: disable AdBlock/privacy extensions when testing.
- Local `file://` loads: serve the site over HTTP(S) (e.g., `npx serve`) when testing Ads.
- Approval/status: confirm the domain/site is added and approved on your AdSense account; new units can take time.

---

## Use Chrome DevTools to troubleshoot (step-by-step)
1. Open the page that contains the ad code in your browser, then view your page's source (`Ctrl+U` in Chrome). Compare the ad code in the page source with the ad code in your AdSense account — they should match exactly.
2. Open DevTools (F12) → Console: look for errors like `adsbygoogle` or CSP/content blocking errors.
3. DevTools → Network: filter `pagead2.googlesyndication.com` and check that the Google script and ad requests return success (200/204).
4. DevTools → Elements: inspect the `ins.adsbygoogle` element — if it has no generated content or remains empty, the ad was not filled.

---

## Temporary debug helper (in repository)
- A small helper script has been added to `script.js` which waits a few seconds after page load and logs the status of `ins.adsbygoogle` elements:
  - Logs `info` when a slot has content.
  - Logs `warn` and adds a dashed red outline if an ad element appears empty.
- Remove this helper once you finish troubleshooting.

---

## WordPress quick notes
- WordPress users: use a plugin (e.g., *Ad Inserter*) or place ad code in template files (e.g., `header.php` / `footer.php`) inside the `<body>`.
- Keep the library script in the site head and add ad units in templates or widget areas.
- If you use WYSIWYG editors, consult the editor manual — some editors strip or modify script tags.

---

## Get more help
If you need further assistance, try these searches: `HTML guides`, `HTML reference`, `HTML tutorial`, `HTML help`, `AdSense implementation`, `AdSense troubleshoot`.
If you're using WYSIWYG or other HTML editing tools, check the product manual or contact their technical support for help.

---

If you'd like, I can also:
- Add the same responsive ad unit to other `.html` files in the repo.
- Add a small CSS rule for `.ads-debug-missing` to make the debug outline more visible.

Tell me which you'd like next. 🔧