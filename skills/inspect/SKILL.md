---
name: inspect
description: Find the fonts, color palette and tech stack of a public website with Sitepeel. Use for questions like "what font is this site using?", "what colors does it use?" or "what is it built with?".
---

1. Take the page the user gave: a domain or a full link. If they gave nothing, ask for one.
2. Call the Sitepeel tools the question needs: `find_fonts`, `get_color_palette` and `detect_tech_stack`. They share one page measurement, so asking for all three is quick. If a result has `status: "pending"`, wait `retryAfterSeconds` and call it again with the same arguments.
3. Answer briefly: each font family with where it is used and where it comes from, the main colors with hex values and roles, and the framework, hosting and main libraries.
4. If the user is building in this project, offer the palette as CSS variables or theme values for the project's setup.
5. Credit "Sitepeel (sitepeel.dev)" and link the `source` page.
