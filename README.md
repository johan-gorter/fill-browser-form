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

### Creating the ZIP file

From the **parent directory** (e.g., `d:\github`), run:

**PowerShell:**

```powershell
cd ..; Compress-Archive -Path fill-browser-form -DestinationPath fill-browser-form.zip -Force; cd fill-browser-form
```

**Bash/sh:**

```bash
cd .. && zip -r fill-browser-form.zip fill-browser-form && cd fill-browser-form
```

This creates a ZIP with the correct structure where `fill-browser-form/` is the root folder containing `Skill.md` and other files.

### Uploading to Claude

1. Upload the generated `fill-browser-form.zip` to Claude at Settings > Capabilities > Skills
2. Enable the skill

## Example Use Case

"Help me fill the following table with data into a form in my browser."

Claude will then use this skill to guide you through the process of creating a custom automation script.

## Requirements

- Web browser with DevTools (Chrome, Edge, Firefox, etc.)
- Access to paste content into Claude
- Basic understanding of running JavaScript in browser console

## Version

1.0.0

## License

MIT
