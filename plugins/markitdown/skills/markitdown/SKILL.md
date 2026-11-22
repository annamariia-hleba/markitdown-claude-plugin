---
name: markitdown
description: Convert documents and media to Markdown with Microsoft MarkItDown. Use when the user wants to read, summarize, quote or extract text/tables from a PDF, .docx, .pptx, .xlsx/.xls, .csv, HTML page, EPUB, ZIP, image (OCR/EXIF), audio (transcription) or YouTube URL.
---

# MarkItDown

Use the `convert_to_markdown` tool from the `markitdown` MCP server. It takes a single `uri` argument:

- Local file: `file:///absolute/path/to/report.pdf` (always an absolute path)
- Web page or file on the web: `https://...`
- Inline data: `data:` URI

Tips:
- Convert first, then work with the Markdown (summarize, search, extract tables).
- For large documents, convert once and save the result to a `.md` file instead of converting repeatedly.
- If the MCP tool is unavailable, fall back to the CLI: `uvx --from 'markitdown[all]' markitdown <file> -o out.md`.
