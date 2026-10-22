# BML Traffic

An interactive simulator of the Biham–Middleton–Levine traffic model, in a single HTML file with no dependencies.

![Four patterns running side by side: random start, packed block, checkerboard and crossroads](bml-demo.gif)

**[Live demo →](https://dmitrymdd.github.io/bml-traffic/)**

## The model

Cars sit on a square grid whose edges wrap around. There are two kinds: cars that move right and cars that move down. Each tick, every right-moving car steps one cell at once, then every down-moving car does. A car moves only if the cell in front of it is empty.

At low density the cars sort themselves into diagonal stripes and never block each other again. At high density one jam wraps around the whole grid. In between, jams and free flow can live side by side for a very long time.

## Features

- Grids from 32×32 to 1024×1024, plus multiples of 3 for the exact 2/3 pattern
- Seeded random starts
- Patterns - choose one of the scenarios
- Paint and erase cars with the mouse, creating your own pattern
- Step one tick at a time, or hold Step (or →) to fast-forward
- Exact outcome detection - free flow, gridlock, or a loop
- A chart of moving cars per tick, with past runs kept for comparison
- Phase diagram - a sweep over densities that runs in a Web Worker
- Export as PNG, animated GIF (with a built-in encoder) or CSV
- Car colors are customizable, and the interface accents follow them
- Both in English and Russian

## How outcomes are detected

- **Free flow**: every car moved for N ticks in a row. Each car is then back where it started, so the grid repeats forever.
- **Gridlock**: no car moved in a tick.
- **Loop**: the exact grid came back. Each grid state is hashed with Zobrist-style keys, updated incrementally as cars move, and Brent's algorithm finds the repeat while storing only one checkpoint. A matching hash is confirmed cell by cell.

## References

- O. Biham, A. A. Middleton, D. Levine. *Self-organization and a dynamical transition in traffic-flow models.* Phys. Rev. A 46, R6124 (1992).
- O. Angel, A. E. Holroyd, J. B. Martin. *The jammed phase of the Biham–Middleton–Levine traffic model.* Electron. Commun. Probab. 10, 167–178 (2005).
- R. M. D'Souza. *Coexisting phases and lattice dependence of a cellular automaton model for traffic flow.* Phys. Rev. E 71, 066112 (2005).
- T. Austin, I. Benjamini. *For what number of cars must self organization occur in the Biham–Middleton–Levine traffic model from any possible starting configuration?* arXiv:math/0607759 (2006).

## License

MIT, see [LICENSE](LICENSE).

The font is Pixar One © Vasily Shishkin, 2012 ([shishkin.ru](https://shishkin.ru)). It is used under the author's licence, free for personal and commercial use, and is not covered by the MIT License.