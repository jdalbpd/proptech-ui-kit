# Proptech UI Kit

A design system and component library built with vanilla HTML, CSS, and JavaScript, driven by design tokens. It serves as both a learning exercise and a portable reference for future implementations in React or other frameworks.

> ⚠️ **Confidentiality note:** this repository is a practice project inspired by a real proptech (real estate platform) engagement. It does not contain any proprietary information, branding, or content from the original client. All tokens, naming, and content have been generalized.

---

## 📐 Philosophy

This project follows the principle of **"system before screens"**: components are not designed in isolation, but as pieces of a shared visual language defined through **design tokens**.

The architecture is layered, from lowest to highest level of abstraction:

```
Tokens → Base → Atomic components → Composite components → Layouts
```

Each layer depends only on the one below it. This means that when migrating to a framework like React, each CSS component maps directly to a component with props, without rewriting the visual logic from scratch.

---

## 🗂️ Repository structure

```
proptech-ui-kit/
├── tokens/
│   └── tokens.css              # Global variables: color, typography, spacing, radii, shadows
├── base/
│   ├── reset.css                # Browser default style normalization
│   └── typography.css           # Base typographic scales and text styles
├── components/
│   ├── button/
│   │   ├── button.css
│   │   └── button.html          # Playground with all variants
│   ├── input/
│   ├── badge/
│   ├── form-field/
│   └── step-indicator/
├── layouts/
│   └── wizard/                  # "New Listing" flow (real estate listing creation)
├── index.html                   # Kitchen sink: overview of all components
└── README.md
```

---

## 🎨 Design tokens

Tokens are the single source of truth for the system's visual values. They are defined as CSS variables (`:root`) in `tokens/tokens.css` and consumed by every component — never hardcoded.

| Category | Examples |
|---|---|
| **Color** | `--color-primary`, `--color-secondary`, `--color-neutral-700` |
| **Typography** | `--font-display`, `--font-body`, `--font-size-*` |
| **Spacing** | `--space-1` to `--space-8` (8pt scale) |
| **Radii** | `--radius-sm`, `--radius-md`, `--radius-full` |
| **Shadows** | `--shadow-sm`, `--shadow-md` |
| **Z-index** | `--z-modal`, `--z-dropdown`, `--z-tooltip` |

> Any branding or theme change is made by editing this single file, without touching the components.

---

## 🧩 Components

Each component lives in its own folder and follows this convention:

- `[component].css` → styles, using design tokens exclusively
- `[component].html` → playground with all variants, states, and sizes
- (when applicable) `[component].js` → interactive behavior

### Naming convention (BEM)

The **BEM** (Block, Element, Modifier) methodology is used to keep CSS predictable and scalable:

```css
.button { }                /* Block */
.button__icon { }           /* Element */
.button--primary { }        /* Modifier */
.button--disabled { }       /* State modifier */
```

This convention makes it straightforward to translate components into React, where each modifier becomes a prop (`variant="primary"`, `disabled`, etc.).

### Available components

- [x] Button (primary, secondary, ghost, danger · states: default, hover, active, disabled, focus · sizes: sm, md, lg)
- [ ] Input / Textarea
- [ ] Label, Helper Text, Error Message
- [ ] Form Field (composite)
- [ ] Select, Checkbox, Radio
- [ ] Badge
- [ ] Step Indicator

---

## 🧭 "New Listing" flow (Wizard)

The main practice layout is a multi-step wizard for publishing a real estate listing, with two flow variants:

- **Private user** — 6 steps
- **Agency** — 7 steps

Each step is built by combining the components defined in `/components`, demonstrating how the system scales from atom to full screen.

---

## 🚀 Usage

```bash
git clone https://github.com/<your-username>/proptech-ui-kit.git
cd proptech-ui-kit
```

No dependencies required: it's plain HTML/CSS/JS. To preview:

1. Open `index.html` in the browser to view the full kitchen sink
2. Or open any individual component's `.html` file inside `/components`

> Recommended: use VS Code's **Live Server** extension for auto-reload.

---

## 🔄 React migration roadmap

This system is designed to make a future migration straightforward:

| Vanilla CSS/HTML | React |
|---|---|
| Variables in `tokens.css` | Theme tokens (CSS variables or JS object) |
| BEM classes (`.button--primary`) | Props (`<Button variant="primary" />`) |
| State classes (`.is-disabled`) | Boolean props (`disabled`) |
| `button.html` (playground) | Storybook stories |
| Static HTML wizard | Stateful component (`useState`, `useReducer`) |

---

## 📌 Project status

🚧 **Actively in development** — personal practice project. Structure and components are being documented progressively as they are built.

---

## 📄 License

This project is distributed under the MIT License. See [LICENSE](./LICENSE) for details.