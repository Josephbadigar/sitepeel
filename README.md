<p align="center"><a href="https://sitepeel.dev"><img src="assets/sitepeel.png" alt="Sitepeel" width="96"></a></p>

<h1 align="center">Sitepeel for Claude Code and Codex</h1>

<p align="center">Give your coding agent any website's DESIGN.md, a clone prompt, an AI slop check, its files, fonts, colors and tech stack.</p>

<p align="center">
  <a href="https://sitepeel.dev">sitepeel.dev</a> ·
  <a href="https://sitepeel.dev/mcp/">MCP server</a> ·
  <a href="https://github.com/Josephbadigar/design-md">DESIGN.md library</a> ·
  <a href="https://sitepeel.dev/extension/">Chrome extension</a>
</p>

This is the Sitepeel plugin for Claude Code and OpenAI Codex. It connects your agent to [Sitepeel's MCP server](https://sitepeel.dev/mcp/), which opens public web pages in a real browser and measures them. Your agent can then save a site's DESIGN.md into your project, rebuild a page's layout, check a landing page for AI slop, pull a logo or icon set, or tell you which fonts, colors and framework a site uses. The plugin also adds five short commands for the common jobs.

![Sitepeel tools: clone prompt, AI slop checker, assets, fonts, colors and tech stack](assets/sitepeel-tools.png)

## Install in Claude Code

In a Claude Code session, add this repository as a marketplace and install the plugin:

```text
/plugin marketplace add Josephbadigar/sitepeel
/plugin install sitepeel@sitepeel
```

On Claude Code 2.1.275 or later, one line does both:

```text
/plugin install sitepeel --marketplace Josephbadigar/sitepeel
```

From your terminal instead:

```sh
claude plugin marketplace add Josephbadigar/sitepeel
claude plugin install sitepeel@sitepeel
```

Start a new session after installing. Run `/mcp` to see the Sitepeel server and its tools.

## Install in Codex

Add this repository as a plugin marketplace, then install the plugin:

```sh
codex plugin marketplace add Josephbadigar/sitepeel
codex plugin add sitepeel@sitepeel
```

You can also open `/plugins` inside Codex, pick the Sitepeel tab and install it from there. Start a new session afterwards so Codex loads the skills and tools.

## Sign in

The first time your agent uses Sitepeel, it opens the browser so you can sign in to Sitepeel (free). It stays connected after that. There is no API key to copy.

## Commands

In Claude Code, type these after installing. In Codex, the same skills are named `$sitepeel:design-md`, `$sitepeel:clone` and so on, or you can ask in plain words.

| Command | What it does |
| --- | --- |
| `/sitepeel:design-md stripe.com` | Saves the site's DESIGN.md in your project root, so new UI follows its colors, fonts and spacing |
| `/sitepeel:clone linear.app/pricing` | Rebuilds the page's look and layout in your project, with placeholders for the site's own text and images |
| `/sitepeel:slop example.com` | Scores how AI-generated the page looks (0 to 100) and lists each tell with a fix |
| `/sitepeel:assets vercel.com svg` | Lists the page's images, SVGs, icons, videos and other files, and downloads the ones you pick |
| `/sitepeel:inspect notion.com` | Finds the page's fonts, color palette and tech stack |

You don't have to use the commands. Once the plugin is installed you can just ask, for example "get the DESIGN.md of linear.app and restyle my settings page to match it".

## Tools

The plugin adds one remote MCP server, `https://sitepeel.dev/mcp`, with these tools:

| Tool | What it returns |
| --- | --- |
| `get_design_md` | A site's DESIGN.md in the Google Stitch format: colors, type, spacing, radii and components |
| `search_design_library` | Brands from the DESIGN.md library that match a name, font, color, style or category |
| `clone_prompt` | One prompt that rebuilds a page's look and layout |
| `check_ai_slop` | A 0 to 100 score, a verdict, the tells found with a fix for each, and a fix prompt |
| `extract_assets` | Images, SVGs, icons, videos, audio, fonts, Lottie and 3D files, with download links |
| `find_fonts` | Font families, where each is used, weights, sizes and the type scale |
| `get_color_palette` | The palette with roles, hex values and CSS variables |
| `detect_tech_stack` | Framework, CMS, hosting, libraries and analytics, with the evidence found |

More tools are on the way, such as full-page screenshots and responsive checks. They show up in the plugin on their own when they go live on the server, with no update needed.

Every result links to its page on sitepeel.dev. Please credit "Sitepeel (sitepeel.dev)" when you use one.

## Other apps

Any app that supports remote MCP servers can use Sitepeel without this plugin. Add `https://sitepeel.dev/mcp` as a Streamable HTTP server. For example:

```sh
claude mcp add --transport http sitepeel https://sitepeel.dev/mcp
codex mcp add sitepeel --url https://sitepeel.dev/mcp
```

Setup for Cursor, VS Code, Windsurf, Gemini CLI, Zed, Claude Desktop and claude.ai is on [sitepeel.dev/mcp](https://sitepeel.dev/mcp/).

## What the plugin does on your machine

The plugin has no code of its own. It holds:

- `.mcp.json`, which points your agent at `https://sitepeel.dev/mcp`
- five skills in `skills/`, plain instructions that tell the agent which Sitepeel tool to call
- the manifests for Claude Code (`.claude-plugin/`) and Codex (`.codex-plugin/`, `.agents/plugins/`)

When your agent calls a tool, it sends the page address you gave to sitepeel.dev, which opens that public page and sends back the result. Your project files are not sent. The skills only write to your project when you ask, for example to save DESIGN.md or download a file. See the [privacy policy](https://sitepeel.dev/privacy/) and [terms](https://sitepeel.dev/terms/).

## Good to know

- Only public pages work. For pages behind a login, use the [Sitepeel Chrome extension](https://sitepeel.dev/extension/), which reads the page open in your browser.
- A new page takes about 15 to 40 seconds to measure. If a tool answers "pending", the agent calls it again.
- Results are an independent measurement of the public page, not the site owner's official design system. A site's text, images and logos belong to its owner.
- Ready DESIGN.md files for more than 160 brands are in the [DESIGN.md library](https://github.com/Josephbadigar/design-md), with style guides at [sitepeel.dev/design-md/examples](https://sitepeel.dev/design-md/examples/).

## Support

Questions or problems: support@sitepeel.dev or [sitepeel.dev/contact](https://sitepeel.dev/contact/).

## License

The plugin files in this repository are under the [MIT License](LICENSE). The Sitepeel service at sitepeel.dev has its own [terms](https://sitepeel.dev/terms/).
