# Web Scheduler - HTML Generator Tool

A powerful web-based HTML generator that creates multiple HTML pages from templates and data files. Perfect for batch generating landing pages, schedules, or any HTML content with variable data.

## Overview

**web_generator.html** is the main tool that allows you to:
- Create multiple HTML files from a single template
- Use CSV or XLSX files as data sources
- Replace template variables with actual data
- Download generated files individually or as a ZIP archive

## Features

- 🎨 **Template-based generation**: Use HTML templates with variable placeholders
- 📊 **Multiple data formats**: Supports both CSV and XLSX (Excel) files
- 🔄 **Batch processing**: Generate hundreds of HTML files in seconds
- 💾 **Flexible download options**: Download individual files or all files as a ZIP
- 🌐 **Browser-based**: No installation required, runs entirely in your browser
- 🚀 **Client-side processing**: All processing happens locally, your data stays private

## Getting Started

### Quick Start

1. Open `web_generator.html` in your web browser
2. Paste your HTML template in the template area
3. Upload your data file (CSV or XLSX)
4. Click "Generate HTML"
5. Download individual files or all files as a ZIP

### Template Syntax

Use the following format for variables in your template: `_VARIABLE_NAME_`

The generator will replace these placeholders with corresponding column values from your data file.

**Example:**
```html
<!DOCTYPE html>
<html>
<head>
    <title>_COMPANY_NAME_ | _PAGE_TITLE_</title>
</head>
<body>
    <h1>_HERO_HEADLINE_</h1>
    <p>_HERO_SUBHEAD_</p>
    <a href="_CTA_LINK_">_CTA_TEXT_</a>
</body>
</html>
```

### Data File Format

Your CSV or XLSX file should have:
- **Header row**: Column names matching your template variables (without underscores)
- **Data rows**: One row for each HTML file you want to generate
- **JUDUL column** (optional): Used as the filename (will be sanitized)

**Example CSV:**
```csv
JUDUL,COMPANY_NAME,PAGE_TITLE,HERO_HEADLINE,HERO_SUBHEAD,CTA_LINK,CTA_TEXT
product-1,Acme Corp,Product One,Welcome to Product One,The best solution,https://example.com/buy,Buy Now
product-2,Acme Corp,Product Two,Welcome to Product Two,Another great product,https://example.com/buy2,Get Started
```

## Example Files

The repository includes example files to help you get started:

- **`template.html`**: A sample HTML template with various variable placeholders
- **`_JUDUL_.html`**: An example of generated output
- **`_JUDUL__files/`**: Supporting assets for the example output

## How It Works

1. **Template Parsing**: The tool scans your template for variables in the format `_VARIABLE_NAME_`
2. **Data Loading**: Reads your CSV or XLSX file using PapaParse and SheetJS libraries
3. **Variable Replacement**: For each row in your data file:
   - Creates a copy of the template
   - Replaces all variables with corresponding values from that row
   - Generates a unique filename (based on JUDUL column or row index)
4. **File Generation**: Creates downloadable HTML files for each row
5. **ZIP Archive**: Optionally packages all files into a single ZIP for easy download

## Technical Details

### Dependencies (loaded via CDN)

- **Tailwind CSS**: For the UI styling
- **PapaParse**: CSV parsing library
- **SheetJS (xlsx)**: Excel file parsing
- **JSZip**: ZIP file creation
- **FileSaver.js**: File download functionality

### Browser Compatibility

Works in all modern browsers that support:
- FileReader API
- Blob API
- ES6 JavaScript

### Privacy & Security

- All processing is done client-side in your browser
- No data is uploaded to any server
- Your templates and data remain completely private

## Use Cases

- 📄 **Landing Pages**: Generate multiple landing pages for different products or campaigns
- 🎫 **Event Schedules**: Create individual schedule pages for different events or dates
- 🏢 **Directory Pages**: Build directory listings with individual profile pages
- 📧 **Email Templates**: Generate personalized HTML email content
- 🌍 **Localized Content**: Create the same page in multiple languages

## Tips & Best practices

1. **Test with small datasets first**: Try with 2-3 rows before processing large files
2. **Use descriptive column names**: Match them to your template variables exactly (case-sensitive)
3. **Include a JUDUL column**: For meaningful filenames instead of generic "file1.html"
4. **Sanitize your data**: Ensure URLs and special characters are properly formatted
5. **Keep templates organized**: Comment your variable placeholders for easier maintenance

## Troubleshooting

**Variables not being replaced?**
- Check that column names in your data file match the variable names in the template (without underscores)
- Ensure variables in the template use the format `_VARIABLE_NAME_` with underscores on both sides

**Files not generating?**
- Verify your data file is valid CSV or XLSX format
- Check that the file has a header row with column names
- Ensure your template is valid HTML

**Download not working?**
- Make sure you've generated files first by clicking "Generate HTML"
- Check your browser's pop-up blocker settings
