# Product Requirements Document (PRD)
**Project Name:** Wada Sanzo Color Combinations Visualizer
**Document Status:** Draft

## 1. Product Overview
The Wada Sanzo Color Combinations Visualizer is a web application designed to help users interactively explore, analyze, and apply the 348 historic color palettes documented in Sanzo Wada's renowned *A Dictionary of Color Combinations*. This tool bridges early 20th-century color theory with modern digital workflows, enabling designers to find palettes, extract colors from their own assets, and mathematically determine the most versatile colors in the collection.

## 2. Target Audience
- Graphic designers, illustrators, and UI/UX designers looking for curated aesthetic palettes.
- Fashion and interior decorators.
- Color theory enthusiasts and historical design researchers.

## 3. Core Features

### 3.1. Color Exploration & Associated Combinations
* **Objective:** Allow users to browse individual colors and instantly discover all the established combinations they belong to.
* **Requirements:**
  * Present a searchable, filterable grid of all colors in the dictionary.
  * When a user selects a color, navigate to a detail view displaying all associated 2-color, 3-color, and 4-color palettes.
  * Display technical data (HEX, RGB, CMYK) and the original color name.
  * Allow easy copying of color codes to the clipboard.

### 3.2. Advanced Versatility Ranking Algorithm
* **Objective:** Enable users to sort the dictionary to find the "most versatile" colors using a weighted, multi-level scoring system.
* **Requirements:**
  * **Algorithm Definition:** The score should not merely rely on the immediate number of combinations a color has (1st-degree connections). It must calculate a weighted score based on the versatility of its connected colors (2nd-degree connections).
  * **Logic Example:** 
    * *Color A* connects to 10 colors, but each of those 10 colors only has 1 or 2 total combinations in the whole book.
    * *Color B* connects to 5 colors, but those 5 colors are highly versatile and average 20 combinations each.
    * *Result:* Color B receives a significantly higher versatility score than Color A.
  * **UI Implementation:** Provide a "Sort by Versatility" toggle in the main gallery, along with a visual indicator (like a score or badge) on the color's detail card.

### 3.3. Image Color Extraction & Matching
* **Objective:** Let users upload their own inspiration images to find matching Wada Sanzo palettes.
* **Requirements:**
  * Provide an upload zone for images (JPEG, PNG, WEBP).
  * Render the uploaded image onto an interactive canvas.
  * Implement an eyedropper/picker tool allowing the user to click anywhere on the image to sample a color pixel.
  * **Matching Logic:** Map the sampled color to the closest color present in the `colors.json` dataset (using a color distance algorithm like Euclidean distance in RGB or, preferably, Delta E in CIELAB color space).
  * Once the closest color is identified, instantly display the color and all its associated Wada Sanzo combinations.

### 3.4. Similar Colors / "Shades Off" Finder
* **Objective:** Provide alternative options when a user likes a color but wants it just a shade lighter, darker, or slightly different in hue.
* **Requirements:**
  * On the detail view of any selected color, display a "Similar Colors" section.
  * This section should query the dataset for the nearest neighbors in the color space.
  * Present 3-5 colors from the dictionary that are "a shade or two off" from the selected color.

## 4. Technical Architecture Notes
* **Data Source:** The primary source of truth will be the local `colors.json` file.
* **Frontend:** Modern JavaScript framework (e.g., React, Vue) with HTML5 Canvas for image processing.
* **Processing:** Image processing and color distance calculations should be handled client-side to ensure privacy and fast interactions without server lag.
* **Color Math:** Use libraries like `chroma.js` or `color-difference` to accurately handle RGB to CIELAB conversions and Delta E similarity calculations.

## 5. Success Metrics
* High user engagement with the "Image Upload" feature.
* Smooth performance of the color mapping and versatility sorting algorithms in the browser.
