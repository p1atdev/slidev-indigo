# JiT presentation sources

Used by `theme/example.md`. Checked on 2026-11-03.

## Paper

Tianhong Li and Kaiming He. **Back to Basics: Let Denoising Generative Models Denoise.** arXiv:2511.13720, 2025. Version 2, revised 2026-01-07. Technical report, MIT.

- Version: <https://arxiv.org/abs/2511.13720v2>
- PDF: <https://arxiv.org/pdf/2511.13720v2>
- DOI: <https://doi.org/10.48550/arXiv.2511.13720>
- License: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/), linked from the arXiv record and HTML.

## Figures

All figures are by Li and He, from the paper above, licensed CC BY 4.0. They were rendered from the v2 PDF at 4× scale and cropped to the figure region. Original panels, axes, labels and values are retained; captions are supplied on the slides. No content was synthesized or retouched. Crop coordinates are PDF points `(left, top, right, bottom)`.

| File | Source | PDF page | Crop | Slide |
| --- | --- | ---: | --- | ---: |
| `fig1-manifold.png` | Figure 1 | 1 | (340,216,553,339) | 4 |
| `fig2-toy.png` | Figure 2 | 4 | (316,171,554,353) | 17 |
| `fig3-architecture.png` | Figure 3 | 5 | (360,70,510,247) | 5 |
| `fig4-bottleneck.png` | Figure 4 | 6 | (327,188,551,293) | 9 |
| `fig5-selected.png` | Figure 5 | 8 | (61,79,292,357) | 2 |

Tables are editable reconstructions or excerpts of paper Tables 2, 4–9. These are paper values, not locally reproduced experiment results. Sources and evaluation conditions are shown on the slides.

## Code

Official PyTorch/GPU reimplementation: <https://github.com/LTH14/JiT>

Inspected revision: [`cbc743a2ada5e9762697da2c83f8c4f8379e8c17`](https://github.com/LTH14/JiT/tree/cbc743a2ada5e9762697da2c83f8c4f8379e8c17), 2025-12-08.

- `denoiser.py`: image output, velocity conversion, clipped denominators, loss, Euler/Heun, interval CFG.
- `model_jit.py`: patch embedding, blocks, conditioning, B/L/H with patch sizes 16/32.
- `README.md`: metadata, JAX/TPU origin, PyTorch/GPU reimplementation, examples tested on 8 H200 GPUs.

Code excerpt on slide 16 is under the repository's [MIT License](https://github.com/LTH14/JiT/blob/cbc743a2ada5e9762697da2c83f8c4f8379e8c17/LICENSE). Retain its notice when redistributing:

```text
MIT License

Copyright (c) 2025 Tianhong Li

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
