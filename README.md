# Zotero HTML Report Parser

A Python script that extracts bibliographic information from Zotero collection report HTML files and converts them to clean, structured JSON format.

## What it does

This tool takes a Zotero collection report (HTML format) and extracts key bibliographic information into a JSON file with the following structure:

```json
[
  {
    "title": "Article Title",
    "author(s)": "LastName and SecondLastName", 
    "year": "2023",
    "journal": "Journal Name",
    "abstract": "Article abstract text..."
  }
]
```

## Features

- 📄 Parses HTML collection reports from Zotero
- 👥 Smart author formatting (last names only, "et al" for >2 authors)
- 📅 Extracts year from various date formats
- 🧹 Removes line breaks and cleans text
- 📚 Handles multiple publication types (articles, books, conference papers)
- ⚡ Fast and reliable HTML parsing

## Prerequisites

- Python 3.6 or higher
- Zotero desktop application

## Installation

1. **Clone this repository:**
   ```bash
   git clone https://github.com/yourusername/zotero-html-parser.git
   cd zotero-html-parser
   ```

2. **Install required Python packages:**
   ```bash
   pip install beautifulsoup4
   ```

## Usage

### Step 1: Generate HTML Report from Zotero

1. Open Zotero desktop application
2. Select the collection you want to export
3. Right-click on the collection → **"Generate Report from Collection"**
4. Zotero will open a new window/tab with the report

### Step 2: Save Report as HTML

1. In the report window, save the page as HTML:
   - **Windows/Linux:** Press `Ctrl + S`
   - **Mac:** Press `Cmd + S`
2. In the save dialog:
   - Choose "Web Page, HTML Only" or "HTML File" format
   - Save as `"Zotero Report 1.html"` (or update the filename in the script)
   - Remember the location where you saved it

### Step 3: Run the Parser

1. **Place the HTML file** in the same directory as `zotero_parser.py`

2. **Run the script:**
   ```bash
   python zotero_parser.py
   ```

3. **Output:** The script will create `zotero_literature.json` with your parsed bibliography

## Example Output

```json
[
  {
    "title": "Simulation in Logistics: A Review of Present Practice and a Look to the Future",
    "author(s)": "Bowersox and Closs",
    "year": "1989",
    "journal": "Journal of Business Logistics",
    "abstract": "Simulation is a widely used methodology in logistics planning. This article compares simulation technology..."
  },
  {
    "title": "Verification and validation of simulation models",
    "author(s)": "Kleijnen",
    "year": "1995",
    "journal": "European Journal of Operational Research",
    "abstract": "This paper surveys verification and validation of models, especially simulation models in operations research..."
  }
]
```

## Author Formatting Rules

- **1 author:** `"Smith"`
- **2 authors:** `"Smith and Jones"`
- **3+ authors:** `"Smith et al"`

## Customization

### Change Input/Output Files

Edit these variables in `zotero_parser.py`:

```python
html_path = "Your Report Name.html"    # Input HTML file
output_path = "your_output.json"       # Output JSON file
```

### Add More Fields

To extract additional fields, modify the `parse_article()` function. Look for field names in the HTML table structure.

## Troubleshooting

### "File not found" error
- Ensure the HTML file is in the same directory as the script
- Check that the filename matches exactly (case-sensitive)

### No articles found
- Verify you saved the report as HTML format (not PDF)
- Make sure you're using a Zotero collection report, not an individual item

### Missing abstracts/fields
- Some Zotero entries may not have all fields - this is normal
- Check your original Zotero entries to see what data is available

## Requirements

The script requires:
- `beautifulsoup4` - for HTML parsing
- `json` - for output formatting (built-in)
- `re` - for text processing (built-in)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## Support

If you encounter any issues:
1. Check that your HTML report was generated correctly from Zotero
2. Ensure you're using the latest version of the script
3. Open an issue on GitHub with your error message and steps to reproduce

---

**Note:** This tool is designed specifically for Zotero HTML collection reports. It may not work with other bibliography management tools or different export formats.
