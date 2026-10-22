# Ideas

Possible additions, roughly from most to least useful. None of these are planned or promised.

## Sharing and export
- **Shareable links.** Keep pattern, seed, density, car ratio and grid size in the URL hash, so a link reopens the exact same run.
- **Video export.** WebM through `MediaRecorder` on the grid canvas: much smaller than GIF for long runs.
- **Save and load drawings.** Export the grid as a small file or text string (for example run-length encoded) and import it later.
- **Link previews.** Open Graph and Twitter card tags with a preview image, so shared links show a picture and a description.

## Simulation and analysis
- **Faster phase sweeps.** Split a sweep across several workers, one per CPU core (`navigator.hardwareConcurrency`).
- **More statistics.** Number and size of jam clusters over time, and the share of cars stuck in the largest jam.
- **Phase diagram by grid size.** Plot sweeps for several N on one chart to show how the tipping point moves with grid size.
- **Speed on large grids.** Bit-packed rows or a WebGL step for 1024 x 1024 and above.

## Interface
- **Offline and installable.** A web app manifest and a service worker (this adds files, so the app would no longer be strictly a single file).
- **Accessibility.** A text summary of the grid state for screen readers, and less motion when "reduce motion" is on.
- **Theme switch.** A manual light / dark toggle; the CSS already supports `data-theme`.

## Project
- **Automated tests.** A headless-browser regression test (patterns, outcome detection, exports, both languages) to run before each release.
- **Smaller demo GIF.** Optimise `bml-demo.gif` (for example `gifsicle -O3 --lossy`) or offer an MP4 alongside it.
