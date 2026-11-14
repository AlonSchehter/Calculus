# Surface rendering

The November 14, 2026 rendering update covers geometric concepts, surfaces,
translation, function types, level curves, parametric surfaces, function
composition (including its embedded function-types document), and limits.

Each page embeds the same `SurfaceQuality` helper to retain offline operation.
It provides two-sided camera-space directional lighting, a restrained specular
highlight, and vertex normals that smooth neighboring faces without crossing
sharp creases. Existing blue-gray, warm neutral, and instructional color roles
are retained. Rasterized custom surfaces interpolate normals per pixel;
Canvas triangle renderers interpolate lighting across each face.

Custom parametric/Cartesian meshes and limits meshes increase resolution in
bounded steps with zoom. Analytic sphere/cone/cylinder/paraboloid rendering
retains its ray-intersection geometry and uses the same lighting. The older
triangle-rendered activities use increased tessellation and less washed-out
surface fills. Limits retains its user-controlled transparency and colored
curves, including the thin paths at z = 0.

Current authoring and regression files are in
`C:/Users/user/Documents/Codex/2026-11-13/new-chat-2/work/`:

- `surface-quality.js`: source of the embedded helper.
- `upgrade-surfaces.cjs`: updates the seven pre-existing activity pages from
  the retained `render-base` snapshot. Do not rerun against future HTML without
  reconciling newer changes into that source snapshot.
- `limits-app.js`, `limits-core.js`, `limits-template.html`, `build-limits.cjs`:
  current limits authoring sources.
- `test-surface-quality.cjs`, `test-limits.cjs`, `test-limits-ui.cjs`:
  mathematical, rendering, syntax, and simulated-DOM interaction checks.

No finite mesh resolves arbitrarily rapid oscillations at a singularity.
The limits surface preview was inspected from the actual raster output;
full browser layout and interaction were not visually verified in this update.

The agreed rendering convention applies to all calculus activities and future mathematical apps: use continuous smooth shading, interpolated camera-space normals, no visible triangulation or triangle strokes, clean transparency without overlapping-face seams, and depth-aware instructional curves and shaded point markers. Preserve derivative color roles and stable axes. Reuse SurfaceQuality lighting. Partial derivatives now uses that same lighting with screen coordinates converted consistently to camera coordinates before computing normals; its transparent raster coat is composited once. These requirements are also persisted in the global AGENTS.md and calculus-app skill.

