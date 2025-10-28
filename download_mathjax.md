# Download MathJax v3 for Offline Use (CORRECT VERSION)

## ⚠️ Important: You need MathJax v3, NOT v4!

Sphinx's `sphinx.ext.mathjax` expects MathJax v3. The v4 you downloaded earlier is not compatible.

## Quick Fix Steps:

### Step 1: Remove MathJax v4

Delete these folders:
- `c:\Users\tomvanwoudenbe\git\test_mathjax\MathJax-4.0.0\`
- `c:\Users\tomvanwoudenbe\git\test_mathjax\book\figures\mathjax\`

### Step 2: Download MathJax v3

**Manual Download (Easiest):**

1. Go to: https://github.com/mathjax/MathJax/releases/tag/3.2.2
2. Download: `Source code (zip)` 
3. Extract the zip file
4. Navigate to the extracted folder: `MathJax-3.2.2/es5/`
5. Copy the entire `es5` folder
6. Paste it as: `c:\Users\tomvanwoudenbe\git\test_mathjax\book\figures\mathjax\`
7. The file `book\figures\mathjax\tex-mml-chtml.js` should now exist

### Step 3: Update Config

In `book\_config.yml`, uncomment these lines (remove the `#`):

```yaml
mathjax_path: mathjax/tex-mml-chtml.js
```

And comment out or remove the CDN URL if present.

## Verify Installation

Your directory structure should look like:

```
book/
├── figures/
│   ├── mathjax/
│   │   ├── tex-mml-chtml.js     ← Main file (from es5 folder)
│   │   ├── input/                ← From es5 folder
│   │   ├── output/               ← From es5 folder
│   │   ├── adaptors/             ← From es5 folder
│   │   └── ... (other files from es5 folder)
│   └── (other figure files)
└── _config.yml
```

## Alternative: Use CDN (Online Only)

If you want the book to work online for now, just leave the config as is (with mathjax_path commented out). It will use the default CDN: `https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js`

## Why v3 and not v4?

- Sphinx's `sphinx.ext.mathjax` extension is designed for MathJax v3
- MathJax v4 has a different API and initialization system
- The default `mathjax_path` in Sphinx points to v3 on the CDN
- Using v4 requires custom JavaScript which Sphinx doesn't provide by default

