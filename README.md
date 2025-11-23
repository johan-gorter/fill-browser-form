# Browser Form Filler Skill

A Claude Skill that helps automate web form filling using browser DevTools console JavaScript.

## What This Skill Does

This Skill guides Claude to help users:

- Extract HTML structure from web pages
- Analyze form fields and their structure
- Generate JavaScript snippets that automate form filling
- Handle dynamic content, timing, and event triggering properly

## How to Use

1. Upload this skill to Claude via the Skills interface
2. Ask Claude to help you fill a web form
3. Claude will guide you through:
   - Extracting the page HTML using a DevTools snippet
   - Analyzing the structure
   - Generating a custom script for your specific form
   - Running the script in your browser

## Installation

### Quick Install

1. Download [fill-browser-form.zip](https://github.com/johan-gorter/fill-browser-form/releases/latest/download/fill-browser-form.zip)
2. Go to Claude → Settings → Capabilities → Skills
3. Upload the ZIP file
4. Enable the skill

### Manual Installation (for development)

From the **parent directory** (e.g., `d:\github`), run:

**Python (recommended - works on all platforms):**

```bash
cd .. && python -c "
import zipfile
import os

if os.path.exists('fill-browser-form.zip'):
    os.remove('fill-browser-form.zip')

files = [
    'fill-browser-form/CONTRIBUTING.md',
    'fill-browser-form/LICENSE',
    'fill-browser-form/README.md',
    'fill-browser-form/Skill.md'
]

with zipfile.ZipFile('fill-browser-form.zip', 'w', zipfile.ZIP_DEFLATED) as zf:
    for file in files:
        arcname = file.replace(os.sep, '/')
        zf.write(file, arcname)

print('Created fill-browser-form.zip')
" && cd fill-browser-form
```

**Bash/sh (Linux/Mac):**

```bash
cd .. && zip -r fill-browser-form.zip fill-browser-form -x "fill-browser-form/.git/*" && cd fill-browser-form
```

**Important:** Do not use PowerShell's `Compress-Archive` as it creates backslashes in paths which causes "invalid path characters" errors in Claude Skills. Use the Python method above for Windows.

This creates a ZIP with the correct structure where `fill-browser-form/` is the root folder containing `Skill.md` and other files with forward-slash separators.

Then upload the generated `fill-browser-form.zip` to Claude at Settings > Capabilities > Skills

## Example Use Case

"Help me fill the following table with data into a form in my browser."

Claude will then use this skill to guide you through the process of creating a custom automation script.

## Requirements

- Web browser with DevTools (Chrome, Edge, Firefox, etc.)
- Access to paste content into Claude
- Basic understanding of running JavaScript in browser console

## Contributing

Contributions are welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## Version

1.0.1

## License

MIT - see [LICENSE](LICENSE) file for details
