# Notion Rich Format Skill

A Claude Code skill for creating and formatting Notion pages with rich block types and text styling.

## What is this?

This is a reference skill for [Claude Code](https://claude.ai/code) that provides comprehensive documentation for Notion's block and rich text formatting API. Use it when creating or formatting Notion documents via the [Notion MCP server](https://github.com/makenotion/notion-mcp-server).

## Features

The skill covers all Notion block types and formatting options:

- **Text blocks**: paragraphs, headings (with toggleable option), toggles, quotes
- **Lists**: bulleted, numbered, to-do items
- **Tables**: full table support with headers and rich text cells
- **Columns**: side-by-side layouts
- **Media**: images, videos, PDFs, files, embeds, bookmarks
- **Structure**: dividers, table of contents, breadcrumbs
- **Advanced**: callouts, code blocks, equations, synced blocks, templates, page links

Plus complete rich text formatting:
- Annotations (bold, italic, underline, strikethrough, code)
- Text and background colors
- Links and mentions (pages, databases, users, dates)
- Inline equations

## Installation

### With rulesync (recommended)

Copy the `SKILL.md` file to your rulesync skills directory:

```bash
mkdir -p .rulesync/skills/notion-rich-format
cp SKILL.md .rulesync/skills/notion-rich-format/
pnpm exec rulesync generate --targets claudecode
```

### Manual installation

Copy the `SKILL.md` file to your Claude Code skills directory:

```bash
mkdir -p .claude/skills/notion-rich-format
cp SKILL.md .claude/skills/notion-rich-format/
```

## Requirements

- [Claude Code](https://claude.ai/code)
- [Notion MCP server](https://github.com/makenotion/notion-mcp-server) configured with your Notion integration token

## Usage

Once installed, Claude Code will automatically use this skill when you ask it to:

- Create a Notion page with formatting
- Format or restructure an existing Notion page
- Convert plain text or markdown into Notion content

Example prompts:
- "Create a Notion page with a table comparing these options"
- "Format this content for Notion with toggles and callouts"
- "Add a two-column layout to my Notion page"

## License

MIT
