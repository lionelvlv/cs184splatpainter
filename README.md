# Splat Painter

Interactive painting tools for **3D Gaussian splat scenes**: select splats with a freeform brush and recolor them, or project an image onto them. Built as a 4-person team final project for CS 184 (Computer Graphics) at UC Berkeley, Spring 2025, by extending [Viser](https://github.com/nerfstudio-project/viser), Nerfstudio's web-based 3D visualizer.

- **Final report:** https://lionelvlv.github.io/cs184splatpainter/finalreport.html
- **Video:** https://www.youtube.com/watch?v=KW4eVKy3m0Y
- **Code** (our Viser fork): https://github.com/palleet/viser-painter

This repo hosts the project website: the report, milestone and gallery pages.

## How it works
- **Brush selection.** The React frontend records the stroke as screen-space points. The Python backend projects every Gaussian center into normalized camera space and keeps the splats whose **distance to the stroke polyline** is within the brush radius. This gives smooth, painterly selection instead of rigid box selection.
- **Image mapping.** An uploaded image is loaded as an RGB array (Pillow + NumPy). Selected splats are projected to screen space, scaled to the image's dimensions, masked to the stroke area, and given the pixel color under them. That transfers a 2D image onto a 3D point cloud.
- **Color tools.** HSV adjustments, random recoloring, and rectangle select with filter options.

## My part (Lionel Verano)
- Implemented the **brush stroke tool** (the stroke event and the point-to-polyline projection selection) and **image mapping**.
- Environment setup and Windows/WSL debugging.
- Built this website and edited the video.

## Team
- **Patrick Le:** Viser debugging, initial setup, reported a Viser rendering bug upstream that Nerfstudio fixed the same day, rectangle select and filter options, extra UI.
- **Jordan Argel and Eric Lin:** report and presentation.
- **Everyone:** painting interactions, color transformations, UI tuning.
