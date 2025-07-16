# Web Research Artifacts

This directory contains original web content and research artifacts collected during device documentation research.

## Directory Structure

```
web/
├── {device-name}/
│   ├── specs/              # Technical specifications from web
│   ├── manuals/            # Downloaded manual PDFs
│   ├── reviews/            # Product reviews and analyses
│   ├── official-pages/     # Manufacturer web pages
│   └── research-sources/   # Original source material
└── README.md (this file)
```

## Collection Tool: jina.ai_reader

`jina.ai_reader` wrapper around `jina.ai` API: <https://github.com/CLIAI/handy_scripts_CLIAI/> .

### Basic Usage
```bash
# Download and process web content in multiple formats
jina.ai_reader -u "https://example.com/device-specs" -o auto -A all

# Save specific formats
jina.ai_reader -u "https://manufacturer.com/product-manual.pdf" -o auto -A json,markdown,content

# Extract specific fields
jina.ai_reader -u "https://example.com/specs" -f content -o device-specs-content.txt
jina.ai_reader -u "https://example.com/specs" -f description -o device-description.txt
```

### Key Options
- **-u, --url**: Target URL to fetch
- **-o, --output**: Output file path or 'auto' for automatic naming
- **-A, --save-all**: Save multiple formats (json,content,title,description,links,images,markdown,html)
- **-f, --field**: Extract specific field (content,links,images,title,description)
- **-F, --return-format**: Response format (markdown,html,text,screenshot,pageshot)
- **--download-images**: Download actual image files when saving images

### Output Formats Available
- **json**: Complete structured response
- **content**: Extracted main content
- **title**: Page title
- **description**: Page description
- **links**: All page links
- **images**: All page images
- **markdown**: Markdown formatted content
- **html**: HTML formatted content
- **text**: Plain text content

### Directory Organization Example
```
web/
├── sony-icd-px470/
│   ├── specs/
│   │   ├── sony-official-specs.json
│   │   ├── sony-official-specs.md
│   │   └── technical-datasheet.pdf
│   ├── manuals/
│   │   ├── user-manual-web.json
│   │   ├── user-manual-web.md
│   │   └── quick-start-guide.pdf
│   └── reviews/
│       ├── professional-review-site.json
│       └── professional-review-site.md
└── brostrend-n300-bridge/
    ├── specs/
    │   ├── amazon-listing.json
    │   ├── amazon-listing.md
    │   └── technical-specs.pdf
    └── official-pages/
        ├── manufacturer-page.json
        └── manufacturer-page.md
```

## Collection Guidelines

### For Each Device
1. **Create device subdirectory**: `web/{device-name}/`
2. **Organize by content type**: specs, manuals, reviews, official-pages
3. **Use jina.ai_reader** for consistent format collection
4. **Maintain source attribution** in filenames and metadata

### Naming Conventions
- **Device directories**: lowercase with hyphens (e.g., `sony-icd-px470`)
- **Content files**: `source-description.{format}` (e.g., `amazon-listing.json`)
- **PDF artifacts**: Original filename preserved when possible

### Research Workflow
1. Identify target URLs for device documentation
2. Create device subdirectory: `mkdir -p web/{device-name}/{specs,manuals,reviews,official-pages}`
3. Use jina.ai_reader to extract content:
   ```bash
   # For comprehensive extraction
   jina.ai_reader -u "https://manufacturer.com/device-specs" -o auto -A all
   
   # For specific content types
   jina.ai_reader -u "https://support.manufacturer.com/manual" -f content -o device-manual-content.txt
   jina.ai_reader -u "https://reviews.site.com/device-review" -A json,markdown -o review-analysis
   ```
4. Organize extracted content by type (specs, manuals, reviews, official-pages)
5. Create cross-references in main device documentation
6. Update research source tracking documents

## Integration with Main Documentation

Web artifacts complement the main device documentation structure:
- **Main docs**: `/device-name/` - Processed and organized information
- **Web artifacts**: `/web/device-name/` - Original source material and references

This separation allows for:
- **Traceability**: Original sources preserved for verification
- **Updates**: Easy re-processing of source material
- **Validation**: Cross-reference between processed and original data
- **Compliance**: Source attribution and research provenance
