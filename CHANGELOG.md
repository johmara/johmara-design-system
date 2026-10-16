# Changelog

## 0.3.3

- Add `.ds-back-link--fixed` (pinned top-left, hidden in print).

## 0.3.2

- `.ds-back-link`: the mark is shown as-is (black) in light mode instead of blue-tinted. (0.3.0 shipped the tinted mark; 0.3.1 was never published.)

## 0.3.0

- Add `.ds-back-link` (arrow plus brand mark image, with `__arrow` and `__mark` parts). The arrow uses the text color; the mark is tinted to the primary color in light mode. In dark mode both are white.

## 0.2.0

- Add `.ds-btn--transparent` (transparent at rest, default hover fill) and `.ds-btn--round` (2.5rem circular button).
- `.ds-menu__item` is now a flex row with gap, so icons and labels line up.
- `.ds-chip` gets letter-spacing.

## 0.1.0

- Initial release: tokens (color, typography, spacing, radius, shadow, motion, z-index, breakpoints), base styles, and `ds-*` components extracted from johmara.github.io.
