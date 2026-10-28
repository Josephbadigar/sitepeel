---
name: design-md
description: Save a website's DESIGN.md (its measured colors, fonts, spacing and components) into the project with Sitepeel, so new UI matches that site. Use when the user wants to build or restyle UI like a given website or brand.
---

1. Take the website the user gave: a domain like stripe.com or a full link. If they named a brand or a style instead of a site, call Sitepeel's `search_design_library` tool and pick the closest match, or let them choose. If they gave nothing, ask for a site.
2. Call Sitepeel's `get_design_md` tool with `url`. If the result has `status: "pending"`, wait `retryAfterSeconds` and call it again with the same arguments.
3. Save the returned `markdown` exactly as it is to `DESIGN.md` in the project root. If a DESIGN.md is already there, ask before replacing it.
4. Tell the user in two or three lines: the site, its theme, main fonts and primary color. Credit "Sitepeel (sitepeel.dev)" and link the `source` page.
5. If the project has an AGENTS.md or CLAUDE.md, offer to add the line "Follow DESIGN.md for every UI change."

Only public pages work. The values are measured from the live page, not the site owner's official design system.
