# geeta design system

Shared fonts, colours, tokens and plain-CSS components for every geeta tool (location-info-tool, fullcam-calculator-tool, excel-bulk-processor, conversational-input, method-workbench, data-mapper...). Tools install it from GitHub at a pinned tag. See `README.md`.

- Figma is the source of truth: file `KRXa8aNV4VOdDUkcLbFQao` (pages Foundations, Controls and feedback, Data, panels and icons). Colour tokens use the Figma variable names; CSS classes use the Figma component names. Check Figma before adding or changing a token or component.
- Brand fonts: JUST Sans (display) and Arial (body). Don't add other fonts.
- Edit `src/` only, then `npm run build`. `dist/` is generated but committed (git dependencies aren't built on install).
- Plain CSS, no nesting or preprocessor, so tools without a build step can use it. React wrappers are deliberately not built yet; add them when the React tools migrate.
- Keep tool-specific styles (Mapbox controls, map layout) in the tools, not here.
- Any change a tool would notice goes in `CHANGELOG.md` with a version bump.
