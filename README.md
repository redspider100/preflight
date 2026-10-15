# Exterior Preflight Study

A static, dependency-free study app containing all 89 slides and 184 independently revealable blue callouts. No build or account integration is required.

## Publish on GitHub Pages

1. Unzip the download.
2. Create a GitHub repository, then upload the CONTENTS of the `preflight` folder to its root. `index.html`, `assets`, `app.js`, and the other files must be alongside each other. Keep `.nojekyll` if your upload tool shows hidden files.
3. In the repository, open Settings → Pages. Under Build and deployment choose Deploy from a branch, then `main` and `/(root)`. Save.
4. Wait for the Pages deployment to finish, then open the website URL shown there. Its usual form is `https://YOUR-USERNAME.github.io/YOUR-REPOSITORY/`.
5. Keep the page open online until the header says **Ready for offline study**. All slides and callout covers are downloaded at this stage.

Source: [GitHub Pages publishing instructions](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site).

Do not just upload the ZIP. Do not open index.html by double-clicking: browser file restrictions prevent normal data loading and service-worker operation. For a local preview, serve this folder with a static web server (for example `python3 -m http.server 8000`) and visit `http://localhost:8000`.

## Add to iPhone or iPad Home Screen

Open the published HTTPS URL in Safari. Open Share (depending on Safari's layout, this may be inside its menu), choose Add to Home Screen, enable Open as Web App if offered, and tap Add. Open the new icon while online and wait for **Ready for offline study** before testing airplane mode. On iPad you can drag its Home Screen icon into the Dock if desired.

Source: [Apple's web-app instructions](https://support.apple.com/guide/iphone/iphea86e5236/ios).

Offline storage is local to each browser/device and may be cleared by storage cleanup or browser settings. Reopen online to restore it. The app retries incomplete downloads on the next visit. Browser installation itself is not proof that the slide download completed.

## Study controls

Tap a blank blue bubble to reveal its exact original lettering. Tap again to hide. Previous/Next and the slide selector preserve reveals during the current visit. Reveal all and Reset slide affect the current slide only. Reloading starts a fresh study session. Reference slides without blue callouts remain visible and their reveal/reset controls are disabled.

On a phone, use landscape orientation or choose Large / scroll for small labels. Pinch zoom remains enabled. Original proportional hit regions align with the slides, so small bubbles may need zooming.

Keyboard: Left/Right = previous/next, Home/End = first/last, A = reveal all, R = reset slide. Tab to controls or callouts, then Enter/Space to activate. Visible focus, pressed-state labels, live progress announcements, and reduced-motion support are included.

## Conversion and fidelity

The complete PPTX structure was inspected. Most study slides contain one flattened picture: photographs, arrows, bubbles, and lettering are baked together. One blue label on slide 74 is a separate editable PowerPoint shape. The app therefore uses full-slide raster renderings and matching blank covers over each blue callout, rather than reconstructing the aircraft photos or retyping labels. The angled callout on slide 23 and alternate blue styles on slides 64/74 were handled separately.

Revealing removes a cover and exposes the original rendered slide pixels, preserving wording, punctuation, line breaks, and embedded artwork. Rendered slide files use lossless WebP at 1600 × 900. The original image resolution still limits detail at large zoom. LibreOffice rendered the PPTX, so editable text/font rendering can differ slightly from Microsoft PowerPoint. PowerPoint animations/transitions are not reproduced. Blank covers approximate the blue fill and boundary; they do not recreate every compression artifact or original gradient.

Only blue callouts are hidden. Other colored labels (including slide 64), markings in photographs, red notes, and ordinary slide text remain visible. This follows the requested blue-callout scope.

## Text accessibility limitation

The answers remain original image pixels. A reliable automatic transcript could not be obtained in this environment, and none was invented. Screen readers can navigate and toggle numbered callouts, but cannot read their image-only answers or all image-only slide text. A fully text-accessible edition would require a verified manual transcription of the flattened slides. This limitation is also stated inside the app.

## Validation

All 89 slide renderings were visually reviewed in contact sheets, including hidden-state review. Automated app-logic checks passed for all slides and 184 callouts: existing assets, normalized region bounds, independent reveal/hide, reveal-all, reset, keyboard navigation, and disabled controls on reference slides. JavaScript syntax and manifest data were checked.

This environment blocked browser launch and local server binding, so actual Safari/iOS layout and service-worker offline behavior were not end-to-end tested. After publishing, test: open slide 7, reveal one bubble, confirm the others stay blank, use reveal/reset, then wait for offline-ready and reload in airplane mode. This is a documented verification gap, not a claimed browser-test pass.

## Updating later

When replacing app content, change `preflight-v1` to a new matching cache name in BOTH app.js and sw.js. Existing users may need to remove the site's stored data and reopen online to pick up a new edition. No external fonts, analytics, CDNs, or runtime dependencies are used.
