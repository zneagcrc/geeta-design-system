# geeta design system

Shared fonts, colours, tokens, components and icons for every geeta tool, so they all look and behave the same.

- **Figma is the source of truth.** The design system Figma file (formerly "pinpoint for geeta", key `KRXa8aNV4VOdDUkcLbFQao`) documents the foundations and components. Colour token names match the Figma colour variables, and CSS class names match the Figma component names.
- **Plain CSS**, so it works the same in plain HTML, plain TypeScript and React tools. React wrapper components will come when the React tools migrate.
- **Brand fonts:** JUST Sans for titles, headings and controls; Arial for data, labels and supporting text.

## Using it in a tool

Install a tagged version straight from GitHub (the repository is private, so you need access to `zneagcrc`):

```bash
npm install github:zneagcrc/geeta-design-system#v0.1.0
```

Import everything at once:

```ts
import '@zneagcrc/geeta-design-system/geeta.css';
```

Or only the parts you want:

```ts
import '@zneagcrc/geeta-design-system/fonts.css';      // JUST Sans @font-face rules
import '@zneagcrc/geeta-design-system/tokens.css';     // CSS custom properties (--paddock-green, --space-16...)
import '@zneagcrc/geeta-design-system/base.css';       // box-sizing, body font and colour
import '@zneagcrc/geeta-design-system/components.css'; // component classes
```

Sass and TypeScript can also read the tokens:

```scss
@use '@zneagcrc/geeta-design-system/tokens.scss' as geeta;
.thing { color: geeta.$paddock-green; }
```

```ts
import { tokens } from '@zneagcrc/geeta-design-system/tokens';
map.setPaintProperty('sites', 'fill-color', tokens.color.pastureGreen);
```

Icons, fonts and the zneag logo are in the package too. With Vite, import an icon to get its URL:

```ts
import infoIcon from '@zneagcrc/geeta-design-system/icons/info.svg';
```

A tool without a build step can copy `dist/` into its public folder and link `geeta.css`.

### Updating a tool to a new version

Change the tag in the tool's `package.json` (`#v0.1.0` to `#v0.2.0`), run `npm install`, and check the tool. Read `CHANGELOG.md` first: a new major version (or, before 1.0, a new minor version) can rename classes or tokens.

### Amplify builds

Amplify needs permission to fetch this private repository during `npm ci`. Add a read-only deploy key to this repository and give Amplify the private key, or ask an organisation owner to grant the Amplify GitHub app access to this repository as well as the tool's.

## What's in it

### Tokens (`src/tokens.json`)

| Group | CSS variables | Notes |
|---|---|---|
| Colour | `--harvest-green`, `--paddock-green`, `--pasture-green`, `--seedling-green`, `--fleece-white`, `--earth-red`, `--golden`, `--sunlit-fields`, `--harvest-glow`, `--yellow-light`, `--red-light`, `--green-light`, `--blue-light`, `--blue-mid`, `--blue-dark` | The 15 Figma colour variables |
| Neutral | `--text-strong`, `--text-muted`, `--border-field`, `--border-rule`, `--border-divider`, `--surface-white`, `--hover-tint` | Not Figma variables yet |
| Font | `--font-display` (JUST Sans), `--font-body` (Arial) | |
| Font size | `--font-size-brand` 24, `--font-size-panel-title` 22, `--font-size-section` 16, `--font-size-control` 14, `--font-size-data` 14, `--font-size-small` 12, `--font-size-fine` 11 | |
| Space | `--space-4`, `-8`, `-10`, `-12`, `-16`, `-32` | |
| Radius | `--radius-small` 4, `--radius-field` 6, `--radius-panel` 8 | |
| Shadow | `--shadow-panel` | Floating panels |

### Components (`src/components/`)

| Class | Figma component |
|---|---|
| `.top-bar`, `.brand`, `.brand__logo`, `.brand__name`, `.top-bar__org-logo` | Top bar |
| `.panel`, `.panel__header`, `.panel__title`, `.panel__toggle`, `.panel__close`, `.panel__body`, `.panel__subheader`, `.panel__content`, `.panel__text`, `.panel--collapsed` | Panel, Panel header, Panel subheader, Panel content holder |
| `.panel-message` with `--default`, `--loading`, `--warning`, `--error`, `--success` | Panel message (Figma's "Alert" variant is `--warning`) |
| `.data-list`, `.data-point`, `.data-point__label`, `.data-point__value` | Data list, Data point |
| `.button-group` (buttons get `.is-selected`) | Button group |
| `.select-box`, `.input-field`, `.date-picker-field`, each with `--inline`; `.file-field` | Select box, Input field, Date picker field |
| `.layer-list`, `.map-layer`, `.map-layer__text`, `.map-layer__name`, `.map-layer__description` | Map Controls/Map layer, Panel menu |
| `.modal` (on a `<dialog class="panel modal">`) | |
| `.small-print` | |

The reference page shows each one with its markup classes.

## Working on the design system

```bash
npm install
npm run build      # regenerate dist/ from src/
npm run reference  # open the reference page (reference/index.html)
npm run check      # build, then fail if dist/ differs from what's committed
```

- Edit `src/`, never `dist/`. `dist/` is generated but committed, because tools install this package from GitHub without building it.
- New components: design them in Figma first, then add `src/components/<name>.css` (named after the Figma component), add it to `COMPONENTS` in `scripts/build.mjs`, and add it to the reference page.
- Release: update `CHANGELOG.md`, bump `version` in `package.json`, run `npm run build`, commit, and tag (`git tag v0.2.0 && git push --tags`).

## Font licence

The JUST Sans files are in this repository, and every tool that uses it serves them publicly. Check the licence covers web use across all geeta tools before the repository or any tool is made public.
