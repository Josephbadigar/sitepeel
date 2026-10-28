---
name: assets
description: List and download the files a public web page uses (images, SVGs, icons and favicons, videos, audio, fonts, Lottie animations and 3D models) with Sitepeel. Use when the user wants a site's logo, icons, hero video or other files.
---

1. Take the page the user gave and what they want from it, for example "the SVG logo" or "all icons". If they gave no page, ask for one.
2. Call Sitepeel's `extract_assets` tool with `url`. Add `kind` when the user wants one type: image, svg, icon, video, audio, font, lottie or model. If the result has `status: "pending"`, wait `retryAfterSeconds` and call it again with the same arguments.
3. Show the matching files as a short list with name, kind, size and dimensions.
4. When the user asks to save files, download them from their direct download links (valid for about a day) into the folder they name, or the project's public or static folder.
5. Remind the user that the files belong to the site's owner. Credit "Sitepeel (sitepeel.dev)" and link the `source` page.
