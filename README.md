# Text to PDF Converter

A Python script that converts code or text files into syntax-highlighted PDF documents.

## Features

- **Syntax Highlighting** using [Pygments](https://pygments.org/) for various programming languages.
- **Multiple Columns**: Use `--columns` to split the output into multiple columns.
- **Customizable Styles**: Specify a color style with `--style` (any supported Pygments style).
- **Headless Chrome**: Renders HTML to PDF, ensuring consistent appearance across platforms.

## Requirements

- **Python 3+**, with the following Python libraries:
    - `pygments`
    - `get-chrome-paths`
- **Chrome, Chromium, or Microsoft Edge**  
   - A headless Chrome executable must be installed and discoverable.  
   - If Chrome is not auto-detected, provide its path with `--chrome-path`.

## Installation

- Download or clone this repository.

```
git clone https://github.com/jifengwu2k/txt2pdf.git
cd txt2pdf
```

- Install Chrome, Chromium, or Microsoft Edge if not already available.
- Install Python 3+ if not already available.
- Install Python packages using `pip` or your preferred installer:

```
pip install pygments get-chrome-paths
```

You can also use the bundled versions:

```
pip install --no-index --find-links=. pygments get-chrome-paths
```

## Usage

```
# Basic single-file conversion
python txt2pdf.py file1.py

# Multiple files at once
python txt2pdf.py script.sh code.c

# Specify columns
python txt2pdf.py --columns=2 code.c

# Override default syntax style (e.g., 'friendly')
python txt2pdf.py --style=friendly script.sh

# Specify a custom Chrome path (if auto-detection fails)
python txt2pdf.py --chrome-path="/usr/bin/google-chrome" file1.py
```

## How It Works

1. Read the Source File: The script reads each file's content.
2. Apply Syntax Highlighting: Uses Pygments to convert code into HTML with inline styles.
3. Generate Temporary HTML: Wraps the highlighted code in an HTML template and saves it to a temporary HTML file.
4. Convert HTML to PDF: Launches headless Chrome (via the `--headless` flag) to produce a PDF, respecting multi-column CSS.
5. Cleanup: Deletes any temporary HTML files upon completion. Logs successes and failures.

## License

This script is released under the [MIT License](LICENSE).

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you'd like to change.