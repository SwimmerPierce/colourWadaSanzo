# Wada Sanzo · A Dictionary of Color Combinations Visualizer

An interactive web application for exploring, analyzing, and applying the 348 historic color palettes documented by Sanzo Wada in the early 20th century.

## 🎨 Overview

This tool bridges early 20th-century Japanese color theory with modern digital workflows. It allows designers and artists to interact with the palettes from Sanzo Wada's seminal work, *A Dictionary of Color Combinations*, providing technical data (HEX, RGB, CMYK), advanced versatility analysis, and image-based color matching.

## ✨ Key Features

### 1. Color Exploration & Detail
- **Searchable Gallery:** Browse the full collection of 157 colors by name, hex code, or index number.
- **Technical Specs:** View and copy HEX, RGB, and CMYK values for any color.
- **Combination Mapping:** Instantly see every palette (2-color, 3-color, or 4-color) that a specific color belongs to.

### 2. Advanced Versatility Ranking
Find the most "versatile" colors in the dictionary using a multi-pass weighted algorithm. The system doesn't just count immediate combinations; it weights colors based on the versatility of their connected neighbors (2nd-degree connections), identifying the most functionally useful colors in the entire collection.

### 3. Image Color Extraction (Eyedropper)
- **Upload Inspiration:** Drag and drop or upload any image (JPEG, PNG, WEBP).
- **Interactive Sampling:** Click anywhere on your image to sample a color.
- **Intelligent Matching:** The app uses Delta E (CIELAB) color distance math to find the closest matching Wada Sanzo color and its associated palettes.

### 4. Similar Colors ("Shades Off")
Each color detail view includes a "Similar Colors" section, suggesting 5 alternatives from the dictionary that are "a shade or two off" in the color space.

## 🚀 Getting Started

The application is built with standard web technologies and requires no build step.

1. Clone this repository:
   ```bash
   git clone https://github.com/SwimmerPierce/colourWadaSanzo.git
   ```
2. Open `index.html` in a modern web browser.
   *Note: Due to browser security policies regarding local JSON fetching, you may need to serve the directory via a local server (e.g., `python -m http.server` or VS Code Live Server).*

## 📜 Historical Context

**Sanzo Wada (1883–1967)** was a pioneering Japanese artist and costume designer who played a crucial role in shaping modern Japanese color theory. His original masterwork, *Haishoku Soukan* (1933-1934), is the foundation for this digital adaptation. His work remains a primary influence for designers worldwide, blending traditional Japanese aesthetics with early modern color science.

## 🛠️ Technical Architecture

- **Frontend:** Vanilla HTML5, CSS3, and JavaScript.
- **Data:** `colors.json` serves as the primary source of truth.
- **Color Science:** Custom implementations for RGB to CIELAB conversion and Delta E similarity calculations.
- **Performance:** All processing (image sampling, similarity matching, versatility calculation) is handled client-side for speed and privacy.

---
*Based on the 348 palettes originally documented by Sanzo Wada.*
