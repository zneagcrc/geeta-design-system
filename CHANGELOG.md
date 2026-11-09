# Changelog

Before 1.0, a new minor version (0.x.0) can rename or remove classes and tokens; a patch version (0.1.x) won't.

## 0.2.0 (November 2026)

Matches the updated Figma file.

- New components: Button (`.button`, `--secondary`, `--delete`), Icon Button (`.icon-button`, `--delete`), Button small (`.button-small`), Object list (`.object-list` and its parts), Form/Inputs/Button group (`.button-group-field`), and the layout helpers Containers/Content (`.container-content`) and Spacers/1em (`.spacer-1em`).
- Text style classes for the Figma Heading 1–5 and Paragraph styles (`.heading-1` to `.heading-5`, `.paragraph`), with `--font-size-heading-*` and `--font-size-paragraph` tokens.
- Fields: description and error text (`.field-description`, `.field-error`), an Error state (`--error` modifier or `aria-invalid="true"`), and a Read only state for input and date fields (`readonly`, plus `--read-only` for an italic description). **The gap between label and control is now 6px, not 8px**, as in Figma.
- Tokens: the four Figma neutral variables (`--neutral-dark`, `--neutral-mid`, `--neutral-mid-light`, `--neutral-light`), the 20 Figma semantic colours (`--text-primary`, `--status-error`, `--brand-deep`...) and `--radius-pill`. Semantic aliases are `var()` references in CSS.
- Deprecated: `--text-strong`, `--text-muted`, `--border-field`, `--border-rule` and `--surface-white`. They still work (as aliases of `--text-primary`, `--text-secondary`, `--neutral-mid`, `--border-section` and `--surface-field`) and will be removed in a later 0.x version.
- **Breaking (TypeScript tokens only):** `tokens.neutral.borderDivider` is now `tokens.semantic.borderDivider`.
- Icons: `edit`, `add`, `add-green`, `delete`, `delete-red`, `delete-green` and `delete-white`.

## 0.1.0 (November 2026)

First version, extracted from location-info-tool (pinpoint) and the design system Figma file.

- Tokens: the 15 Figma colour variables, neutrals, fonts, font sizes, spacing, corner radii and the panel shadow, as CSS, SCSS and TypeScript.
- Components: top bar, panel, panel message (default, loading, warning, error, success), data list, button group, select box, input field, date picker field, file field, map layer, modal and small print.
- JUST Sans Regular and ExBold, 13 icons and the zneag logo.
- Reference page.
