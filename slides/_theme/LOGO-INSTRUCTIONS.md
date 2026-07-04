# Adding the IU Trident Logo to Slides

The slide templates have been configured to display the IU trident logo on the title slide. You just need to add the logo image file.

## How to Get the Logo

**Option 1: Download from IU Brand**
Visit: https://brand.iu.edu/apply/downloads.html

Look for the "Trident" downloads and get the PNG version (preferably crimson or white trident).

**Option 2: Use IU's Direct Asset Link**
The trident is available at IU's brand assets:
- https://assets.iu.edu/brand/3.2.x/trident-large.png

**Option 3: Get from IU Marketing**
Contact IU's marketing or communications office for official logo files.

## Where to Put the Logo

Save the logo file as:
```
~/Library/CloudStorage/OneDrive-IndianaUniversity/Teaching/IU Courses/503 - IPE/ipe-summer2026/slides/iu-trident.png
```

The filename must be exactly `iu-trident.png` for the slides to find it.

## Logo Configuration in Slides

The slides are configured with these settings:

```yaml
logo: iu-trident.png
title-slide-attributes:
  data-background-image: iu-trident.png
  data-background-size: 15%
  data-background-position: 98% 2%
```

This will:
- Display a small logo in the upper right corner of the title slide (15% size)
- Use the same logo file for all slides (in the footer/corner)

## Adjusting Logo Size or Position

If you want to change where the logo appears or how big it is, modify these values:

**Size:** Change `15%` to make it larger or smaller
- `10%` = smaller
- `20%` = larger

**Position:** Change `98% 2%` (horizontal, vertical)
- `98% 2%` = top right (current setting)
- `50% 2%` = top center  
- `2% 2%` = top left
- `50% 50%` = centered

## Logo Format Tips

**Best practices:**
- Use PNG format with transparent background
- Recommended size: 500-1000px width
- The crimson version of the trident works best with our slide theme
- Make sure you have permission to use IU logos (you should as IU faculty)

## Testing

After adding the logo file:

1. Open Terminal in the slides folder
2. Render a slide deck:
   ```bash
   quarto render day01-chapter01.qmd
   ```
3. Open the resulting HTML file in a browser to verify the logo appears correctly

## If the Logo Doesn't Appear

Check:
1. File is named exactly `iu-trident.png` (case-sensitive)
2. File is in the same folder as the .qmd slides
3. File is actually a PNG (not renamed from .jpg)
4. Try rendering again after clearing cache: `quarto render day01-chapter01.qmd --no-cache`

## Alternative: Different Logo Per Deck

If you want different logos for different presentations, you can change the `logo:` line in individual .qmd files to point to different files:

```yaml
logo: my-custom-logo.png
```
