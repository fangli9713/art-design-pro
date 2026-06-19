# AGENTS.MD

## Project Direction

This project is based on Art Design Pro, a Vue 3, TypeScript, Vite, Element Plus, Pinia, and SCSS admin template. The preferred UI direction is **Modern SaaS Console**: clean, calm, readable, and suitable for long daily use.

Agents working in this repository should prioritize a cohesive admin product experience over decorative effects.

## UI Principles

- Build real admin interfaces, not landing pages.
- Prefer clarity, hierarchy, and scanability over visual spectacle.
- Keep surfaces simple. Avoid stacking many cards, shadows, borders, gradients, and glass effects in the same area.
- Use restrained color. A neutral base plus one primary brand color is usually enough.
- Tables, forms, search panels, and settings screens are data-work areas. They should be stable, readable, and low-noise.
- Decorative effects such as liquid glass, glow, mesh gradients, or large hero sections should be used only when they support the product context.

## Visual Style

### Recommended Direction

Use a clean SaaS dashboard style:

- Light mode: soft gray page background, white or near-white panels, strong readable text.
- Dark mode: deep blue-gray surfaces, not pure black.
- Borders: subtle and consistent.
- Shadows: light, soft, and rare. Prefer borders and spacing for hierarchy.
- Radius: usually `6px-12px` for admin UI. Avoid overly rounded cards unless the component is intentionally decorative.
- Spacing: predictable 4px/8px rhythm. Do not use large marketing-style whitespace inside dense tools.

### Avoid

- Global liquid glass as the primary theme.
- Multiple overlapping translucent layers.
- Weak light-gray text on light backgrounds.
- Purple/blue gradients as the default visual answer.
- Excessive dashboard hero sections that push useful content down.
- Card-inside-card layouts unless the inner card is a repeated item or an intentional floating control.

## Color & Theme Tokens

Prefer semantic CSS variables over hardcoded colors.

Use and extend existing project tokens:

- `--default-bg-color`: page background.
- `--default-box-color`: primary panel/card surface.
- `--art-card-border`: card border.
- `--default-border`: component border.
- `--art-gray-*`: text and neutral UI scale.
- `--theme-color`: brand/action color.
- Element Plus variables such as `--el-bg-color`, `--el-text-color-*`, `--el-border-color`, and table variables.

When adding new visual systems, define tokens first, then consume them from components.

## Text Contrast

- Light mode primary text should be dark enough for comfortable reading.
- Do not use very light gray for body text, table text, labels, or navigation.
- Secondary text should still meet practical contrast expectations.
- Use reduced contrast only for metadata, hints, disabled states, or decorative copy.

## Layout Rules

- A page should usually have one main content surface, not many competing containers.
- Search/filter panels should visually belong to the table or list they control.
- Avoid making every section a floating card. Use full-width content bands or simple grouped regions where appropriate.
- Keep dashboard sections balanced: metrics first, operational data next, secondary charts lower.
- Do not let decorative content take priority over primary workflows.

## Tables & Forms

Tables and forms are core admin surfaces.

- Tables should use a stable solid or near-solid surface, not heavy transparency.
- Table headers should have a clear but subtle background.
- Row hover should be visible but not loud.
- Borders should be soft and consistent.
- Numeric columns should use `font-variant-numeric: tabular-nums` when practical.
- Long cell content must truncate, wrap, or clamp intentionally.
- Form controls must have clear labels and focus states.
- Avoid low-contrast placeholders as the only clue.

## Dark Mode

- Never use pure black for primary panels unless intentionally designing an OLED mode.
- Prefer deep blue-gray or neutral-gray surfaces.
- Ensure Element Plus variables are aligned with project theme tokens.
- Check tables, popovers, dialogs, dropdowns, inputs, and scrollbars in dark mode after theme changes.
- Dark mode should feel like the same product, not a separate skin.

## Motion

- Motion should clarify state changes, not entertain.
- Animate only explicit properties such as `transform`, `opacity`, `box-shadow`, `border-color`, or `background-color`.
- Do not use `transition: all`.
- Honor `prefers-reduced-motion` for decorative animations.
- Avoid layout-shifting animations in tables, forms, and dense settings panels.

## Accessibility & Interaction

- Icon-only controls must have an accessible name, usually `aria-label`.
- Use `button` for actions and router links or anchors for navigation.
- Avoid clickable `div` elements. If unavoidable, add keyboard support and focus styles.
- Interactive elements need visible `:focus-visible` states.
- Do not remove outlines without replacing them.
- Images need `alt` text, or empty `alt=""` when decorative.

## Implementation Guidance

- Prefer existing project patterns, components, hooks, stores, SCSS, and Element Plus customization points.
- Do not introduce a new UI library only for visual polish.
- Keep visual changes token-driven and centralized.
- Before large visual rewrites, inspect:
  - `src/assets/styles/index.scss`
  - `src/assets/styles/core/tailwind.css`
  - `src/assets/styles/core/el-ui.scss`
  - `src/assets/styles/core/dark.scss`
  - layout components under `src/components/core/layouts`
  - table components under `src/components/core/tables`
- Run `pnpm build` before claiming UI/theme changes are complete.

## Recommended Upgrade Path

1. Define or adjust theme tokens.
2. Fix typography and text contrast.
3. Simplify page surfaces and layout hierarchy.
4. Tune Element Plus tables, forms, dialogs, popovers, and dropdowns.
5. Refine dashboard composition.
6. Add decorative accents only after the core UI is coherent.
