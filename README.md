# Fiachra Matthews CV

This repository contains the LaTeX source files for generating a professional CV using the `moderncv` document class.

## Prerequisites

### LaTeX Distribution
You need a LaTeX distribution installed on your system. Choose one of the following:

- **macOS**: [MacTeX](https://www.tug.org/mactex/) (recommended for macOS)
- **Windows**: [MiKTeX](https://miktex.org/) or [TeX Live](https://www.tug.org/texlive/)
- **Linux**: Install via package manager (e.g., `sudo apt-get install texlive-full` on Ubuntu)

### Required LaTeX Packages
The following packages are required (usually included in full LaTeX distributions):
- `moderncv` - Modern CV template
- `geometry` - Page layout customization
- Standard LaTeX base packages

## Quick Start

### Compilation

#### Basic Compilation
To compile the CV to PDF, run the following command in the project directory:

```bash
pdflatex main.tex
```

This will generate `main.pdf` containing your compiled CV.

#### Clean Compilation (Recommended)
To avoid cluttering your directory with auxiliary files:

**Option 1: Use output directory**
```bash
mkdir -p build
pdflatex -output-directory=build main.tex
cp build/main.pdf .
```

**Option 2: Use auxiliary directory** 
```bash
mkdir -p aux  
pdflatex -aux-directory=aux main.tex
```

**Option 3: Compile and clean in one command**
```bash
pdflatex main.tex && rm -f *.aux *.log *.out *.fdb_latexmk *.fls *.synctex.gz
```

**Option 4: Use latexmk (most elegant)**
```bash
latexmk -pdf main.tex
latexmk -c  # Clean auxiliary files after compilation
```

#### Alternative LaTeX Engines
If you prefer other LaTeX engines:
```bash
# Using XeLaTeX (better Unicode support)
xelatex main.tex

# Using LuaLaTeX (modern LaTeX engine)  
lualatex main.tex
```

## File Structure

```
myCV/
├── main.tex                 # Main LaTeX file (compile this)
├── fiachraSquareSmall.png   # Profile photo
├── techskills.tex           # Technical skills section
├── industryex.tex           # Industry experience section  
├── teachingex.tex           # Teaching experience section
├── educationShort.tex       # Education section
├── interests.tex            # Interests section (commented out)
├── references.tex           # References section (commented out)
├── publications.tex         # Publications section (commented out)
├── coverletter.tex          # Cover letter (commented out)
├── picture.jpg              # Alternative profile photo
└── Legacy/                  # Previous versions and archives
```

## Customization

### Personal Information
Edit the personal data section in `main.tex` (lines 18-34):
```latex
\name{Your}{Name}
\title{Your Title}
\address{Your Address}{City}{Country}
\phone[mobile]{+xxx~xxx~xxx~xxx}
\email{your.email@example.com}
\social[linkedin]{yourlinkedin}
\photo[64pt][0.4pt]{your-photo-filename}
```

### Sections
To enable/disable sections, uncomment/comment the `\input{}` commands in `main.tex`:
```latex
\input{techskills.tex}        % Always included
\input{industryex.tex}        % Always included  
\input{teachingex.tex}        # Always included
\input{educationShort.tex}    % Always included
%\input{interests.tex}        % Currently commented out
%\input{references.tex}       % Currently commented out
```

### Styling
Modify the style and color in `main.tex`:
```latex
\moderncvstyle{casual}    % Options: casual, classic, oldstyle, banking
\moderncvcolor{blue}      % Options: blue, orange, green, red, purple, grey, black
```

### Content
Edit the individual `.tex` files to update your:
- Technical skills (`techskills.tex`)
- Work experience (`industryex.tex`) 
- Teaching experience (`teachingex.tex`)
- Education (`educationShort.tex`)
- And other sections as needed

## Troubleshooting

### Common Issues

1. **Missing moderncv package**:
   ```
   Install via: tlmgr install moderncv
   ```

2. **Photo file not found**:
   - Ensure `fiachraSquareSmall.png` exists in the main directory
   - Or update the `\photo{}` command with your image filename
   - Comment out the `\photo{}` line to compile without a photo

3. **Input files not found**:
   - Ensure all referenced `.tex` files exist in the main directory
   - Comment out any `\input{}` lines for missing files

4. **Compilation hangs**:
   - Try running `pdflatex main.tex` twice (needed for cross-references)
   - Clear auxiliary files: `rm *.aux *.log *.out *.toc`

### Build Automation
For convenience, you can create a build script:

**build.sh** (macOS/Linux) - Clean compilation:
```bash
#!/bin/bash
echo "Compiling CV..."

# Method 1: Using output directory (cleanest)
mkdir -p build
pdflatex -output-directory=build main.tex
pdflatex -output-directory=build main.tex  # Run twice for cross-references
cp build/main.pdf .
echo "CV compiled successfully to main.pdf"

# Method 2: Alternative using latexmk
# latexmk -pdf -pdflatex="pdflatex -interaction=nonstopmode" main.tex
# latexmk -c
```

**build.bat** (Windows) - Clean compilation:
```batch
@echo off
echo Compiling CV...

REM Method 1: Using output directory
if not exist build mkdir build
pdflatex -output-directory=build main.tex
pdflatex -output-directory=build main.tex
copy build\main.pdf . >nul
echo CV compiled successfully to main.pdf

REM Method 2: Alternative - compile and clean
REM pdflatex main.tex && pdflatex main.tex && del *.aux *.log *.out *.fdb_latexmk *.fls *.synctex.gz 2>nul
```

## Output

The compilation will produce:
- `main.pdf` - Your final CV
- Various auxiliary files (`.aux`, `.log`, `.out`) - Can be safely deleted

## Tips

- Keep backup copies before major changes
- Test compilation after any modifications
- The `Legacy/` folder contains previous versions for reference
- Consider version control (git) for tracking changes over time

## Support

For LaTeX-specific issues, consult:
- [LaTeX Documentation](https://www.latex-project.org/help/documentation/)
- [moderncv Documentation](https://ctan.org/pkg/moderncv)
- [TeX Stack Exchange](https://tex.stackexchange.com/)
