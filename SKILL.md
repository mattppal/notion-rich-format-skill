---
name: notion-rich-format
description: Apply rich formatting to Notion pages - toggles, callouts, headers, and styled text. Use when creating or formatting Notion documents for better readability and progressive disclosure.
allowed-tools: mcp__notion-personal__*, Read
---

# Notion rich format

Reference guide for creating and formatting Notion pages with rich block types and text styling via the Notion MCP.

## When to use this skill

- User asks to create a Notion page with formatting
- User wants to format or restructure an existing Notion page
- User wants to convert plain text or markdown into Notion content

## Block types

### Paragraph

```json
{
  "object": "block",
  "type": "paragraph",
  "paragraph": {
    "rich_text": [{ "type": "text", "text": { "content": "Text here" } }],
    "color": "default"
  }
}
```

### Headings

Available types: `heading_1`, `heading_2`, `heading_3`

```json
{
  "object": "block",
  "type": "heading_2",
  "heading_2": {
    "rich_text": [{ "type": "text", "text": { "content": "Section title" } }],
    "is_toggleable": true,
    "color": "default"
  }
}
```

Set `is_toggleable: true` to make the heading collapsible.

### Toggle

```json
{
  "object": "block",
  "type": "toggle",
  "toggle": {
    "rich_text": [{ "type": "text", "text": { "content": "Click to expand" } }],
    "color": "default",
    "children": [
      {
        "object": "block",
        "type": "paragraph",
        "paragraph": {
          "rich_text": [{ "type": "text", "text": { "content": "Hidden content" } }]
        }
      }
    ]
  }
}
```

### Bulleted list item

```json
{
  "object": "block",
  "type": "bulleted_list_item",
  "bulleted_list_item": {
    "rich_text": [{ "type": "text", "text": { "content": "List item" } }],
    "color": "default",
    "children": []
  }
}
```

### Numbered list item

```json
{
  "object": "block",
  "type": "numbered_list_item",
  "numbered_list_item": {
    "rich_text": [{ "type": "text", "text": { "content": "Step one" } }],
    "color": "default",
    "children": []
  }
}
```

### To-do

```json
{
  "object": "block",
  "type": "to_do",
  "to_do": {
    "rich_text": [{ "type": "text", "text": { "content": "Task" } }],
    "checked": false,
    "color": "default"
  }
}
```

### Callout

```json
{
  "object": "block",
  "type": "callout",
  "callout": {
    "rich_text": [{ "type": "text", "text": { "content": "Important note" } }],
    "icon": { "type": "emoji", "emoji": "💡" },
    "color": "gray_background"
  }
}
```

Icon can be emoji or external image:
```json
"icon": { "type": "external", "external": { "url": "https://..." } }
```

### Quote

```json
{
  "object": "block",
  "type": "quote",
  "quote": {
    "rich_text": [{ "type": "text", "text": { "content": "Quoted text" } }],
    "color": "default"
  }
}
```

### Code

```json
{
  "object": "block",
  "type": "code",
  "code": {
    "rich_text": [{ "type": "text", "text": { "content": "const x = 1;" } }],
    "language": "javascript",
    "caption": []
  }
}
```

Supported languages: `abap`, `arduino`, `bash`, `basic`, `c`, `clojure`, `coffeescript`, `cpp`, `csharp`, `css`, `dart`, `diff`, `docker`, `elixir`, `elm`, `erlang`, `flow`, `fortran`, `fsharp`, `gherkin`, `glsl`, `go`, `graphql`, `groovy`, `haskell`, `html`, `java`, `javascript`, `json`, `julia`, `kotlin`, `latex`, `less`, `lisp`, `livescript`, `lua`, `makefile`, `markdown`, `markup`, `matlab`, `mermaid`, `nix`, `objective-c`, `ocaml`, `pascal`, `perl`, `php`, `plain text`, `powershell`, `prolog`, `protobuf`, `python`, `r`, `reason`, `ruby`, `rust`, `sass`, `scala`, `scheme`, `scss`, `shell`, `sql`, `swift`, `typescript`, `vb.net`, `verilog`, `vhdl`, `visual basic`, `webassembly`, `xml`, `yaml`, `java/c/c++/c#`

### Divider

```json
{
  "object": "block",
  "type": "divider",
  "divider": {}
}
```

### Table of contents

```json
{
  "object": "block",
  "type": "table_of_contents",
  "table_of_contents": {
    "color": "default"
  }
}
```

### Table

Tables require a `table` block with `table_row` children.

```json
{
  "object": "block",
  "type": "table",
  "table": {
    "table_width": 3,
    "has_column_header": true,
    "has_row_header": false,
    "children": [
      {
        "object": "block",
        "type": "table_row",
        "table_row": {
          "cells": [
            [{ "type": "text", "text": { "content": "Column 1" } }],
            [{ "type": "text", "text": { "content": "Column 2" } }],
            [{ "type": "text", "text": { "content": "Column 3" } }]
          ]
        }
      },
      {
        "object": "block",
        "type": "table_row",
        "table_row": {
          "cells": [
            [{ "type": "text", "text": { "content": "Data 1" } }],
            [{ "type": "text", "text": { "content": "Data 2" } }],
            [{ "type": "text", "text": { "content": "Data 3" } }]
          ]
        }
      }
    ]
  }
}
```

- `table_width`: Number of columns
- `has_column_header`: First row is header
- `has_row_header`: First column is header
- Each cell is an array of rich_text objects

### Column list and columns

For side-by-side layouts:

```json
{
  "object": "block",
  "type": "column_list",
  "column_list": {
    "children": [
      {
        "object": "block",
        "type": "column",
        "column": {
          "children": [
            {
              "object": "block",
              "type": "paragraph",
              "paragraph": {
                "rich_text": [{ "type": "text", "text": { "content": "Left column" } }]
              }
            }
          ]
        }
      },
      {
        "object": "block",
        "type": "column",
        "column": {
          "children": [
            {
              "object": "block",
              "type": "paragraph",
              "paragraph": {
                "rich_text": [{ "type": "text", "text": { "content": "Right column" } }]
              }
            }
          ]
        }
      }
    ]
  }
}
```

### Image

```json
{
  "object": "block",
  "type": "image",
  "image": {
    "type": "external",
    "external": {
      "url": "https://example.com/image.png"
    },
    "caption": [{ "type": "text", "text": { "content": "Image caption" } }]
  }
}
```

### Bookmark

```json
{
  "object": "block",
  "type": "bookmark",
  "bookmark": {
    "url": "https://example.com",
    "caption": []
  }
}
```

### Embed

```json
{
  "object": "block",
  "type": "embed",
  "embed": {
    "url": "https://twitter.com/user/status/123",
    "caption": []
  }
}
```

### Video

```json
{
  "object": "block",
  "type": "video",
  "video": {
    "type": "external",
    "external": {
      "url": "https://youtube.com/watch?v=..."
    },
    "caption": []
  }
}
```

### PDF

```json
{
  "object": "block",
  "type": "pdf",
  "pdf": {
    "type": "external",
    "external": {
      "url": "https://example.com/file.pdf"
    },
    "caption": []
  }
}
```

### File

```json
{
  "object": "block",
  "type": "file",
  "file": {
    "type": "external",
    "external": {
      "url": "https://example.com/file.zip"
    },
    "caption": [],
    "name": "file.zip"
  }
}
```

### Equation

```json
{
  "object": "block",
  "type": "equation",
  "equation": {
    "expression": "E = mc^2"
  }
}
```

### Synced block

```json
{
  "object": "block",
  "type": "synced_block",
  "synced_block": {
    "synced_from": null,
    "children": [
      {
        "object": "block",
        "type": "paragraph",
        "paragraph": {
          "rich_text": [{ "type": "text", "text": { "content": "Synced content" } }]
        }
      }
    ]
  }
}
```

To reference existing synced block:
```json
"synced_from": { "block_id": "original-block-uuid" }
```

### Template button

```json
{
  "object": "block",
  "type": "template",
  "template": {
    "rich_text": [{ "type": "text", "text": { "content": "Add new item" } }],
    "children": [
      {
        "object": "block",
        "type": "to_do",
        "to_do": {
          "rich_text": [{ "type": "text", "text": { "content": "New task" } }],
          "checked": false
        }
      }
    ]
  }
}
```

### Link to page

```json
{
  "object": "block",
  "type": "link_to_page",
  "link_to_page": {
    "type": "page_id",
    "page_id": "page-uuid-here"
  }
}
```

Can also link to database: `"type": "database_id"`

### Child page

```json
{
  "object": "block",
  "type": "child_page",
  "child_page": {
    "title": "Subpage title"
  }
}
```

### Child database

```json
{
  "object": "block",
  "type": "child_database",
  "child_database": {
    "title": "Database title"
  }
}
```

### Breadcrumb

```json
{
  "object": "block",
  "type": "breadcrumb",
  "breadcrumb": {}
}
```

## Rich text formatting

### Text object structure

```json
{
  "type": "text",
  "text": {
    "content": "styled text",
    "link": null
  },
  "annotations": {
    "bold": false,
    "italic": false,
    "strikethrough": false,
    "underline": false,
    "code": false,
    "color": "default"
  },
  "plain_text": "styled text",
  "href": null
}
```

### Annotations

| Property | Type | Description |
|----------|------|-------------|
| bold | boolean | Bold text |
| italic | boolean | Italic text |
| strikethrough | boolean | Strikethrough text |
| underline | boolean | Underlined text |
| code | boolean | Inline code style |
| color | string | Text or background color |

### Colors

**Text colors:** `default`, `gray`, `brown`, `orange`, `yellow`, `green`, `blue`, `purple`, `pink`, `red`

**Background colors:** `gray_background`, `brown_background`, `orange_background`, `yellow_background`, `green_background`, `blue_background`, `purple_background`, `pink_background`, `red_background`

### Links

External link:
```json
{
  "type": "text",
  "text": {
    "content": "Click here",
    "link": { "url": "https://example.com" }
  }
}
```

### Mentions

**Page mention:**
```json
{
  "type": "mention",
  "mention": {
    "type": "page",
    "page": { "id": "page-uuid" }
  }
}
```

**Database mention:**
```json
{
  "type": "mention",
  "mention": {
    "type": "database",
    "database": { "id": "database-uuid" }
  }
}
```

**User mention:**
```json
{
  "type": "mention",
  "mention": {
    "type": "user",
    "user": { "id": "user-uuid" }
  }
}
```

**Date mention:**
```json
{
  "type": "mention",
  "mention": {
    "type": "date",
    "date": {
      "start": "2026-01-11",
      "end": null,
      "time_zone": null
    }
  }
}
```

**Link preview:**
```json
{
  "type": "mention",
  "mention": {
    "type": "link_preview",
    "link_preview": { "url": "https://example.com" }
  }
}
```

### Inline equation

```json
{
  "type": "equation",
  "equation": {
    "expression": "x^2 + y^2 = z^2"
  }
}
```

### Mixed formatting example

Paragraph with multiple styles:
```json
{
  "object": "block",
  "type": "paragraph",
  "paragraph": {
    "rich_text": [
      { "type": "text", "text": { "content": "This is " } },
      {
        "type": "text",
        "text": { "content": "bold" },
        "annotations": { "bold": true }
      },
      { "type": "text", "text": { "content": " and " } },
      {
        "type": "text",
        "text": { "content": "highlighted" },
        "annotations": { "color": "yellow_background" }
      },
      { "type": "text", "text": { "content": " text." } }
    ]
  }
}
```

## MCP tool usage

### Fetch existing page

```
mcp__notion-personal__notion-fetch
id: "page-uuid-or-url"
```

### Create page with content

```
mcp__notion-personal__notion-create-pages
```

Request body:
```json
{
  "parent": { "page_id": "parent-page-uuid" },
  "properties": {
    "title": [{ "text": { "content": "Page Title" } }]
  },
  "children": [
    // Block objects
  ]
}
```

For database parent:
```json
{
  "parent": { "database_id": "database-uuid" },
  "properties": {
    "Name": {
      "title": [{ "text": { "content": "Page Title" } }]
    }
    // Other database properties
  },
  "children": []
}
```

### Update page properties

```
mcp__notion-personal__notion-update-page
```

Note: To add blocks to an existing page, you need the block append endpoint which may require direct API access.

## API constraints

- Maximum 100 blocks per request
- Nested blocks limited to 2 levels via API
- Some block types (synced blocks, databases) have additional restrictions
- Rich text arrays have a maximum of 100 elements
- Text content limited to 2000 characters per rich text object
