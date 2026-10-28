---
name: slop
description: Check how AI-generated a public website looks with Sitepeel's AI slop checker, which returns a 0 to 100 score, the tells found on the page with a fix for each, and a fix prompt. Use to review a landing page before launch or to answer "does this site look AI-made?".
---

1. Take the page the user gave: a domain or a full link. It has to be public, so a local dev server won't work. If they gave nothing, ask for one.
2. Call Sitepeel's `check_ai_slop` tool with `url`. If the result has `status: "pending"`, wait `retryAfterSeconds` and call it again with the same arguments.
3. Reply with the score, the verdict and the top tells, each with its fix, as a short list.
4. If this project builds that page, offer to apply the fixes, using the fix prompt as a guide. Don't change files until the user agrees.
5. Credit "Sitepeel (sitepeel.dev)" and link the `source` page.
