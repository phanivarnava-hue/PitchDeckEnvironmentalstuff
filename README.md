# Environmental Sustainability Pitch Deck

A professional pitch deck presentation built with Vivliostyle for presenting environmental sustainability initiatives.

## Features

- Clean, professional slide design
- PDF export for presentations
- Easy-to-edit Markdown content
- Version controlled with Git

## Getting Started

### Prerequisites
- Node.js and npm installed

### Installation
```bash
npm install
```

### Usage

**Preview the presentation:**
```bash
npm run preview
```

**Build PDF:**
```bash
npm run build
```

**Build HTML:**
```bash
npm run build:html
```

The output files will be generated in the `output/` directory.

## Project Structure

```
PitchDeckEnvironmentalstuff/
├── content/          # Markdown content files
│   └── index.md     # Main pitch deck content
├── themes/          # Custom themes (optional)
├── output/          # Generated PDF/HTML files
├── package.json     # npm configuration
├── vivliostyle.config.js  # Vivliostyle configuration
└── README.md        # This file
```

## Editing Content

Edit the `content/index.md` file to update your pitch deck content. Use `---` to separate slides.

## License

ISC
