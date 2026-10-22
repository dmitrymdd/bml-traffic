# BML Traffic

An interactive simulator of the Biham–Middleton–Levine traffic model, in a single HTML file with no dependencies.

![30% density on a 128×128 grid, seed 1: jams form, dissolve, and the traffic sorts itself into diagonal stripes](bml-demo.gif)

**[Live demo →](https://YOUR-USERNAME.github.io/bml-traffic/)**

## The model

Cars sit on a square grid whose edges wrap around. There are two kinds: cars that move right and cars that move down. Each tick, every right-moving car steps one cell at once, then every down-moving car does. A car moves only if the cell in front of it is empty.

At low density the cars sort themselves into diagonal stripes and never block each other again. At high density one jam wraps around the whole grid. In between, jams and free flow can live side by side for a very long time.

## Features

- Grids from 32×32 to 1024×1024, plus multiples of 3 for the exact 2/3 pattern
- Seeded random starts, so any run can be reproduced
- Patterns: perfect flow at 66%, perfect flow plus one car, a staircase that never moves, a jam seed
- Paint and erase cars with the mouse: click a car color to pick it as the brush
- Step one tick at a time, or hold Step (or →) to fast-forward
- Exact outcome detection: free flow, gridlock, or a loop where the same grid repeats forever
- A chart of moving cars per tick, with past runs kept for comparison
- Phase diagram: a sweep over densities that runs in a Web Worker
- Export as PNG, animated GIF (with a built-in encoder) or CSV
- Car colors are customizable, and the interface accents follow them
- No dependencies: the pixel font (Pixar One) is embedded as a 13 KB subset
- English and Russian

## How outcomes are detected

- **Free flow**: every car moved for N ticks in a row. Each car is then back where it started, so the grid repeats forever.
- **Gridlock**: no car moved in a tick.
- **Loop**: the exact grid came back. Each grid state is hashed with Zobrist-style keys, updated incrementally as cars move, and Brent's algorithm finds the repeat while storing only one checkpoint. A matching hash is confirmed cell by cell.

## Running it

Open `index.html` in a browser. To host it, upload `index.html` to any static host, such as GitHub Pages.

## References

- O. Biham, A. A. Middleton, D. Levine. *Self-organization and a dynamical transition in traffic-flow models.* Phys. Rev. A 46, R6124 (1992).
- O. Angel, A. E. Holroyd, J. B. Martin. *The jammed phase of the Biham–Middleton–Levine traffic model.* Electron. Commun. Probab. 10, 167–178 (2005).
- R. M. D'Souza. *Coexisting phases and lattice dependence of a cellular automaton model for traffic flow.* Phys. Rev. E 71, 066112 (2005).
- T. Austin, I. Benjamini. *For what number of cars must self organization occur in the Biham–Middleton–Levine traffic model from any possible starting configuration?* arXiv:math/0607759 (2006).

## License

MIT, see [LICENSE](LICENSE).

The embedded pixel font is a subset of [Pixar One](https://shishkin.ru/pixar) by Vasily Shishkin (c) 2025, which its author distributes as free for personal and commercial use. It is not under the MIT license that covers the code.
