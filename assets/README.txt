Put your files here:

  mariem.jpg       -> your photo, next to your name at the top (square crop is best)

Demo media, one per project in the Work section:

  labelling-demo.mp4      -> Automated annotation pipeline  (20s silent loop)
  tta-demo.mp4            -> Test-Time Adaptation project
  robotics-demo.mp4       -> Vision-guided pick-and-place   (simulation capture)
  meeting-assistant.jpg   -> Meeting assistant UI  (still image, data-type="image")

Optional cover images shown before each video plays:

  labelling-poster.jpg
  tta-poster.jpg
  robotics-poster.jpg

Long-form video for the labelling.html project page:

  labelling-walkthrough.mp4         -> 75s walkthrough, has controls, loads on click
  labelling-walkthrough-poster.jpg

Names must match exactly (lowercase). If a file is missing, the page
shows a placeholder instead of breaking.

Encoding recipe for the homepage loops — keep them short and small,
they autoplay on page load and three of them share the bandwidth:

  ffmpeg -ss <start> -t 20 -i source.webm -an \
    -vf "fps=24,scale=1440:900:flags=lanczos" \
    -c:v libx264 -crf 29 -preset slow -pix_fmt yuv420p \
    -movflags +faststart out.mp4

16:10 (1440x900) matches the .media slot. Aim for under 1 MB.

If a source is a different aspect ratio, pad it to 16:10 rather than letting
object-fit:cover crop it — robotics-demo.mp4 is a 2.67:1 side-by-side that
would otherwise lose its right-hand panel:

  -vf "scale=1280:-2,pad=1280:800:(ow-iw)/2:(oh-ih)/2:black"
