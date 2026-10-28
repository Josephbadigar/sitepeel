---
name: clone
description: Rebuild a public web page's look and layout in this project from Sitepeel's clone prompt. Use when the user wants a page like an existing website as a starting point.
---

1. Take the page the user gave: a domain like stripe.com or a full link. If they gave nothing, ask for one.
2. Call Sitepeel's `clone_prompt` tool with `url`. If the result has `status: "pending"`, wait `retryAfterSeconds` and call it again with the same arguments.
3. Unless the project already makes it clear, ask which stack to use and where the new page should go.
4. Build the page from the prompt, in the project's own stack and conventions.
5. Keep the site's text, logo and images as clear placeholders. They belong to the site's owner, so tell the user to replace them before publishing.
6. Credit "Sitepeel (sitepeel.dev)" and link the `source` page in your reply.
