# AdSense Implementation Guide ✅

This guide shows where to paste AdSense ad unit code in your HTML and how to troubleshoot common issues.

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

> Tip: Add the script in `<head>` **once** and then include `ins` + `push()` blocks where needed in the body.

---

## How to position ads on your site with HTML
You control placement with standard HTML containers (`<div>`, `<aside>`, etc.). Example to center:

```html
<div style="text-align:center">
  <!-- ad unit here -->
</div>
```

For responsive behavior, prefer `data-ad-format="auto"` so the ad adapts to available width.

---

## Common issues and quick fixes
- Missing tags: ensure the `<script>`, `<ins>`, and the following `<script>(adsbygoogle...)</script>` appear exactly as copied.
- All-on-one-line code: preserve line breaks when pasting; some editors may collapse whitespace.
- Extra HTML inside the snippet: paste the snippet raw, without additional tags inside it.
- Ad blockers: disable AdBlock/privacy extensions when testing.
- Local `file://` loads: serve the site over HTTP(S) (e.g., `npx serve`) when testing Ads.
- Approval/status: confirm the domain/site is added and approved on your AdSense account; new units can take time.

---

## Use Chrome DevTools to troubleshoot (quick checklist)
1. Open the page and press `Ctrl+U` to view page source; verify the ad code matches your AdSense code exactly.
2. Open DevTools (F12) → Console: look for errors like `adsbygoogle` or CSP errors.
3. DevTools → Network: filter `pagead2.googlesyndication.com` and check the Google script and ad requests succeed (200/204).
4. Inspect the `ins.adsbygoogle` element in Elements panel: does it have generated content? If empty, the ad was not filled.

---

## Temporary debug helper (in repository)
- A small helper script has been added to `script.js` which waits a few seconds after page load and logs the status of `ins.adsbygoogle` elements:
  - Logs `info` when slot has content.
  - Logs `warn` and adds a dashed red outline if an ad element appears empty.
- Remove this helper once you finish troubleshooting.

---

## WordPress quick notes
- Use a plugin (e.g., *Ad Inserter*) or insert ad code into template files (e.g., `header.php` or `footer.php`) inside `<body>` where needed.
- Keep the library script once in the site head and add ad units in templates or widget areas.

---

## More help
Search for: `HTML basics`, `AdSense implementation`, `AdSense troubleshoot` or see AdSense docs.

---

If you'd like, I can also:
- Add the same responsive ad unit to other `.html` files in the repo.
- Add a temporary visual indicator (CSS) to help spot empty ad slots during testing.

Tell me which you'd like next. 🔧