# Notion Rich Format Skill

An Agent Skill for creating and formatting Notion pages with rich block types and text styling.

## What is this?

This is a reference skill that provides comprehensive documentation for Notion's block and rich text formatting API. Use it when creating or formatting Notion documents via the [Notion MCP server](https://github.com/makenotion/notion-mcp-server).

## What are Agent Skills?

[Agent Skills](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) are an open standard published by Anthropic for packaging domain expertise into composable resources that agents can discover and load dynamically. Skills work across multiple platforms:

- **Claude.ai** - Upload as a zip file via Settings > Features
- **Claude Code** - Place in `~/.claude/skills/` (personal) or `.claude/skills/` (project)
- **Claude Agent SDK** - Place in `.claude/skills/` directory
- **Claude API** - Upload via the Skills API (`/v1/skills` endpoints)

## Features

This skill covers all Notion block types and formatting options:

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

### Claude.ai

1. Zip the `formatting-notion-pages` directory
2. Go to Settings > Capabilities > Skills
3. Click '+ Add' button
4. Upload the zip file

### Claude Code

```bash
# Personal (available in all projects)
cp -r formatting-notion-pages ~/.claude/skills/

# Or project-specific
cp -r formatting-notion-pages .claude/skills/
```

### Claude Agent SDK

```bash
cp -r formatting-notion-pages .claude/skills/
```

Then include `"Skill"` in your `allowed_tools` configuration.

### Claude API

Upload the `formatting-notion-pages` directory via the Skills API endpoints. See [Skills API documentation](https://docs.anthropic.com/en/build-with-claude/skills-guide).

## Requirements

- [Notion MCP server](https://github.com/makenotion/notion-mcp-server) configured with your Notion integration token

## Usage

Once installed, Claude automatically uses this skill when you ask it to:

- Create a Notion page with formatting
- Format or restructure an existing Notion page
- Convert plain text or markdown into Notion content

Example prompts:
- "Create a Notion page with a table comparing these options"
- "Format this content for Notion with toggles and callouts"
- "Add a two-column layout to my Notion page"

## Learn more

- [Agent Skills announcement](https://www.anthropic.com/news/skills)
- [Agent Skills engineering blog](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills)
- [Agent Skills documentation](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)
- [Awesome Claude Skills](https://github.com/travisvn/awesome-claude-skills) - Community curated list

## License

MIT
