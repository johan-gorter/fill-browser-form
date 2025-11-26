# Browser Form Filler Skill

A prompt that helps automate web form filling using browser DevTools console. Can be used as a Claude skill.

## How to use:

### Quickest way to try (Works with ChatGPT and Claude)

Paste your data and then use this prompt: "Fill in this data using this method: https://raw.githubusercontent.com/johan-gorter/fill-browser-form/refs/heads/main/Skill.md"

### Quickest way with Gemini 3:

Paste your data and then use the prompt: "Fill in this data" then copy-past the content of [Skill.md](https://raw.githubusercontent.com/johan-gorter/fill-browser-form/refs/heads/main/Skill.md).

### Permanent installation in Claude:

1. Download the latest release ZIP from [here](https://github.com/johan-gorter/fill-browser-form/releases/latest/download/fill-browser-form.zip)
2. Go to Claude → Settings → Capabilities → Skills → Upload Skill
3. Upload the ZIP file
4. Enable the skill
5. Use a prompt like: "Fill in this data in my browser"

## What This Skill Does

This Skill guides Claude to help users:

- Extract HTML structure from web pages
- Analyze form fields and their structure
- Generate JavaScript snippets that automate form filling

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
- Basic understanding of running JavaScript in browser console

## Contributing

Contributions are welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## Version

1.0.1

## License

MIT - see [LICENSE](LICENSE) file for details
