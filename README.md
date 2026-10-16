# @johmara/design-system

Design tokens and CSS/SCSS components extracted from johmara.github.io. Framework-agnostic, no runtime dependencies.

## Install

Published to GitHub Packages. Add to the consuming repo's `.npmrc`:

```
@johmara:registry=https://npm.pkg.github.com
//npm.pkg.github.com/:_authToken=${NODE_AUTH_TOKEN}
```

`NODE_AUTH_TOKEN` needs `read:packages` (a PAT locally; in GitHub Actions use `actions/setup-node` with `registry-url: https://npm.pkg.github.com` and pass a token). Never commit the token.

```
npm install @johmara/design-system
```

## Use

Full CSS (tokens, base styles, components). In Angular add to `angular.json` `styles`:

```json
"styles": ["node_modules/@johmara/design-system/dist/design-system.css", "src/styles.scss"]
```

Tokens only:

```json
"styles": ["node_modules/@johmara/design-system/dist/tokens.css"]
```

Sass API (breakpoints and mixins, no CSS output):

```scss
// Node package importer (Sass >= 1.71; Angular builders may need stylePreprocessorOptions.includePaths
// ["node_modules"] and the explicit path form: @use '@johmara/design-system/src/index' as ds;)
@use 'pkg:@johmara/design-system' as ds;

.card {
  @include ds.down(ds.$bp-sm) { padding: 0.5rem; }
  @include ds.lift;
}
```

Dark mode: add `.dark-mode` (or `data-theme="dark"`) to `<html>`.

## Contents

| Area | Names |
|---|---|
| Colors | `--ds-color-{bg,bg-subtle,text,text-muted,heading,primary,primary-light,success,hint,code-bg,overlay}` |
| Type | `--ds-font-{sans,mono}`, `--ds-text-{2xs..2xl}`, `--ds-weight-*`, `--ds-leading-*` |
| Spacing / radius / shadow | `--ds-space-1..7`, `--ds-radius-{sm,md,lg,xl,pill,round}`, `--ds-shadow-{sm,md,lg,xl}` |
| Motion / z-index | `--ds-duration-{fast,base,slow}`, `--ds-z-*`, keyframes `ds-fade-in`, `ds-slide-up`, `ds-slide-down`, `ds-drop-down` |
| Breakpoints (Sass) | `$bp-sm` 768px, `$bp-md` 1024px, `$bp-lg` 1250px, mixins `up()`, `down()` |
| Components | `.ds-btn` (`--outline --solid --link --icon --ghost --transparent --round --sm`), `.ds-pill`, `.ds-badge`, `.ds-chip`, `.ds-card`, `.ds-kbd`, `.ds-section-heading`, `.ds-popover`, `.ds-menu`, `.ds-modal`, `.ds-code`, `.ds-segmented`, `.ds-input`, `.ds-table`, `.ds-footer`, `.ds-back-link` (`--fixed`) |

Legacy variable names from the site (`--accent-color-2`, `--background-color`, ...) are kept as aliases of the `--ds-*` tokens.

## Develop

```
npm install
npm run build      # dist/design-system.css, .min.css, tokens.css
open docs/index.html
```

## Release

Bump `version` in `package.json`, update `CHANGELOG.md`, commit, then publish a GitHub release tagged `vX.Y.Z`. The `publish` workflow builds and publishes to GitHub Packages.
