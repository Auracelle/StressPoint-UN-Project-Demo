# Auracelle StressPoint — Public Site

Public-facing site for **Auracelle StressPoint**: AI Governance Ecosystem Asynchronous Wargame Stress-Testing.

StressPoint takes a real document — a policy, treaty, standard or legal instrument — and tests whether it holds. It returns a quantified Policy Stress-Test Outcome Assessment (PSTOA) alongside a qualitative read against existing policy and treaty precedent, then names the gaps that open when the document is challenged at a contested negotiation table.

Developed from the Accelerated Governance Policy Optimization research methodology, as part of Grace-Alice Evans' doctoral research at Bath Spa University, supervised by Dr. John Curry.

## Live site

Served from `index.html` at the repository root via GitHub Pages.

## What's in here

| Path | Purpose |
| --- | --- |
| `index.html` | Deployed build. Single self-contained file — fonts, runtime, three.js and the 3D module are inlined, so it works fully offline. |
| `src/StressPoint-Public.dc.html` | Page source. Edit this, not `index.html`. |
| `src/stress-lattice.js` | The `<stress-lattice>` 3D web component (three.js). |
| `src/lattice-boot.js` | Offline loader that wires three.js and OrbitControls into the lattice module in the compiled build. |
| `src/support.js` | Runtime required to open the source file directly in a browser. |
| `.github/workflows/pages.yml` | Deploys the repository root to GitHub Pages on push to `main`. |

## The 3D model

`src/stress-lattice.js` defines a `<stress-lattice>` custom element: a deformable lattice representing a governance structure under load, sectioned into six frontier-technology domains — AI, Quantum, BioTech, Cybersecurity, Nuclear, 5G/6G.

- A dim flat grid is the instrument **as written**; the lattice above it is the same structure under pressure.
- Struts and nodes recolour by computed strain: steel → amber → red at the failure threshold.
- Six radial seams partition the plane into domain sectors, each reporting live strain.
- Stressing one domain propagates strain across the seams into adjacent domains — no domain is governed in isolation.

Attributes:

| Attribute | Values | Effect |
| --- | --- | --- |
| `pressure` | number, ~0.5–1.8 | Applied load. Higher values drive the origin sector past the failure threshold. |
| `epicenter` | `AI`, `Quantum`, `BioTech`, `Cybersecurity`, `Nuclear`, `5G/6G` | Which sector is the stress origin. |
| `autorotate` | `true` / `false` | Slow orbit until the user drags. Drag always takes over. |

Honours `prefers-reduced-motion`. Zoom is disabled so page scroll is never captured. Degrades to an empty frame without WebGL.

## Local development

No build step and no dependencies to install.

```bash
python3 -m http.server 8000
# source page:    http://localhost:8000/src/StressPoint-Public.dc.html
# deployed build: http://localhost:8000/
```

Open `src/StressPoint-Public.dc.html` to work on copy and layout. `index.html` is a compiled artifact — regenerate it rather than editing it by hand. Hand-editing the compiled file can corrupt its inlined payload.

## Deployment

Push to `main`. The Pages workflow publishes the repository root.

In repository settings, set **Pages → Build and deployment → Source** to **GitHub Actions**.

## Scope

This site describes StressPoint at the capability level. Detailed analytical methods, scoring logic, learning architecture, implementation methods and framework documentation are intentionally not published here. Figures shown in the lattice model are illustrative.

## Contact

Log-in access, research collaboration, demonstrations and institutional use:
**EvansAGrace@gmail.com**

Research environment: <https://auracelle.github.io/Auracelle-Charlie-BSU-Research-Workshop-June2026/>

## License

© 2026 Grace-Alice Evans. All rights reserved. See [LICENSE](LICENSE).
