# Theme Customization

Complete guide to customizing the Chakra UI theming system.

## Configuration Overview

### Config Hierarchy

- `defaultBaseConfig`: Conditions and style properties only (no tokens/recipes)
- `defaultConfig`: Everything from `defaultBaseConfig` plus built-in tokens and recipes
- `defaultSystem`: Uses `defaultConfig` by default

### Basic Setup

```tsx
import { createSystem, defaultConfig, defineConfig } from "@chakra-ui/react"

const config = defineConfig({
  // configuration options
})

export const system = createSystem(defaultConfig, config)
```

### Provider Setup

```tsx
import { ChakraProvider } from "@chakra-ui/react"
import { system } from "./theme"

export function Provider(props: { children: React.ReactNode }) {
  return (
    <ChakraProvider value={system}>
      {props.children}
    </ChakraProvider>
  )
}
```

## Config Options

### cssVarsRoot

Root element where token CSS variables are applied:

```tsx
const config = defineConfig({
  cssVarsRoot: ":where(:root, :host)",
})
```

### cssVarsPrefix

Prefix for CSS variables:

```tsx
const config = defineConfig({
  cssVarsPrefix: "sui",
})

// Results in: --sui-colors-gray-100
```

### globalCss

Apply global styles:

```tsx
const config = defineConfig({
  globalCss: {
    "html, body": {
      margin: 0,
      padding: 0,
    },
    "*::placeholder": {
      opacity: 1,
      color: "fg.subtle",
    },
    "*::selection": {
      bg: "green.200",
    },
    html: {
      fontFamily: "Roboto, sans-serif",
    },
  },
})
```

### preflight

CSS reset configuration:

```tsx
// Disable CSS reset
const config = defineConfig({
  preflight: false,
})

// Scope CSS reset
const config = defineConfig({
  preflight: {
    scope: ".chakra-reset",
  },
})
```

### strictTokens

Enforce token-only values (TS error for raw values):

```tsx
const config = defineConfig({
  strictTokens: true,
})

// ❌ TS error
<Box color="#4f343e">Hello World</Box>

// ✅ Works
<Box color="red.400">Hello World</Box>
```

### conditions

Define custom selectors and media query conditions:

```tsx
const config = defineConfig({
  conditions: {
    cqSm: "@container(min-width: 320px)",
    child: "& > *",
    off: "&:is([data-state=off])",
    on: "&:is([data-state=on])",
  },
})
```

Usage:
```tsx
<Box mt="40px" _cqSm={{ mt: "0px" }}>
  <Text>Hello World</Text>
</Box>

<Box data-state="off" _off={{ bg: "red.500" }} />
<Box data-state="on" _on={{ bg: "green.500" }} />
```

## Theme Properties

### breakpoints

Custom responsive breakpoints:

```tsx
const config = defineConfig({
  theme: {
    breakpoints: {
      tablet: "992px",
      desktop: "1200px",
      wide: "1400px",
    },
  },
})
```

Usage:
```tsx
<Box fontSize={{ base: "16px", tablet: "18px", desktop: "20px" }}>Hello</Box>
```

**Default Breakpoints**: `sm` (480px), `md` (768px), `lg` (992px), `xl` (1280px), `2xl` (1536px)

### keyframes

CSS animation keyframes:

```tsx
const config = defineConfig({
  theme: {
    keyframes: {
      shakeX: {
        "0%, 100%": { transform: "translateX(-100%)" },
        "50%": { transform: "translateX(100%)" },
      },
      fadeIn: {
        "0%": { opacity: "0" },
        "100%": { opacity: "1" },
      },
    },
  },
})
```

### tokens

Design tokens (see [tokens.md](tokens.md)):

```tsx
const config = defineConfig({
  theme: {
    tokens: {
      colors: {
        brand: {
          500: { value: "#3b82f6" },
        },
      },
      spacing: {
        gutter: { value: "12px" },
      },
    },
  },
})
```

### semanticTokens

Context-aware tokens (see [semantic-tokens.md](semantic-tokens.md)):

```tsx
const config = defineConfig({
  theme: {
    semanticTokens: {
      colors: {
        danger: {
          value: { base: "{colors.red.500}", _dark: "{colors.red.300}" },
        },
      },
    },
  },
})
```

### textStyles

Typography style presets:

```tsx
const config = defineConfig({
  theme: {
    textStyles: {
      heading: {
        fontSize: "2xl",
        fontWeight: "bold",
        lineHeight: "shorter",
      },
      caption: {
        fontSize: "sm",
        color: "fg.muted",
      },
    },
  },
})
```

### layerStyles

Layer/container style presets:

```tsx
const config = defineConfig({
  theme: {
    layerStyles: {
      card: {
        bg: "white",
        shadow: "md",
        borderRadius: "lg",
        p: "6",
      },
      panel: {
        bg: "bg.subtle",
        border: "1px solid",
        borderColor: "border",
        borderRadius: "md",
      },
    },
  },
})
```

### animationStyles

Animation style presets:

```tsx
const config = defineConfig({
  theme: {
    animationStyles: {
      "fade-in": {
        animation: "fade-in 0.3s ease-out",
      },
      "slide-in": {
        animation: "slide-from-bottom 0.3s ease-out",
      },
    },
  },
})
```

### recipes

Component recipes (see [recipes.md](recipes.md)):

```tsx
const config = defineConfig({
  theme: {
    recipes: {
      button: buttonRecipe,
      title: titleRecipe,
    },
  },
})
```

### slotRecipes

Multi-slot component recipes (see [slot-recipes.md](slot-recipes.md)):

```tsx
const config = defineConfig({
  theme: {
    slotRecipes: {
      checkbox: checkboxSlotRecipe,
      alert: alertSlotRecipe,
    },
  },
})
```

## Utilities

### Creating Custom Utilities

```tsx
const config = defineConfig({
  utilities: {
    extend: {
      br: {
        values: "radii",
        transform(value) {
          return { borderRadius: value }
        },
      },
    },
  },
})
```

Usage:
```tsx
<Box br="sm" />
```

### Using Enum Values

```tsx
const config = defineConfig({
  utilities: {
    extend: {
      borderX: {
        values: ["1px", "2px", "4px"],
        shorthand: "bx",
        transform(value, { token }) {
          return {
            borderInlineWidth: value,
            borderColor: token("colors.red.200"),
          }
        },
      },
    },
  },
})
```

Usage:
```tsx
<Box borderX="1px" />
<Box bx="2px" />
```

### Using Mapped Values

```tsx
const config = defineConfig({
  utilities: {
    extend: {
      borderX: {
        values: { small: "2px", medium: "5px" },
        shorthand: "bx",
        transform(value, { token }) {
          return {
            borderTopWidth: value,
            borderTopColor: token("colors.gray.400"),
          }
        },
      },
    },
  },
})
```

## System API

### token

Get raw token value or CSS variable:

```tsx
const system = createSystem(defaultConfig, config)

// Raw token
system.token("colors.red.200") // => "#EE0F0F"

// Token with fallback
system.token("colors.pink.240", "#000") // => "#000"

// CSS variable
system.token.var("colors.red.200") // => "var(--chakra-colors-red-200)"

// Semantic tokens always return CSS variable
system.token("colors.danger") // => "var(--chakra-colors-danger)"
```

### tokens

```tsx
system.tokens.getVar("colors.red.200")
// => "var(--chakra-colors-red-200)"

system.tokens.expandReferenceInValue("3px solid {colors.red.200}")
// => "3px solid var(--chakra-colors-red-200)"
```

### css

Convert Chakra style objects to CSS:

```tsx
system.css({
  color: "red.200",
  bg: "blue.200",
})
// => { color: "var(--chakra-colors-red-200)", background: "var(--chakra-colors-blue-200)" }
```

### cva

Create component recipes:

```tsx
const button = system.cva({
  base: { color: "white", bg: "blue.500" },
  variants: {
    outline: { color: "blue.500", bg: "transparent", border: "1px solid" },
  },
})

button({ variant: "outline" })
// => { color: "blue.500", bg: "transparent", border: "1px solid" }
```

### sva

Create slot recipes:

```tsx
const alert = system.sva({
  slots: ["title", "description", "icon"],
  base: {
    title: { color: "white" },
    description: { color: "white" },
    icon: { color: "white" },
  },
  variants: {
    status: {
      info: {
        title: { color: "blue.500" },
      },
    },
  },
})

alert({ status: "info" })
// => { title: { color: "blue.500" }, ... }
```

### breakpoints

Query breakpoints:

```tsx
system.breakpoints.up("sm")    // => "@media (min-width: 320px)"
system.breakpoints.down("sm")  // => "@media (max-width: 319px)"
system.breakpoints.only("md")  // => "@media (min-width: 320px) and (max-width: 768px)"
system.breakpoints.keys()      // => ["sm", "md", "lg", "xl"]
```

### splitCssProps

Split CSS props from non-CSS props:

```tsx
system.splitCssProps({
  color: "red.200",
  bg: "blue.200",
  "aria-label": "Hello World",
})
// => [{ color: "red.200", bg: "blue.200" }, { "aria-label": "Hello World" }]
```

## TypeScript

### Type Generation

Run after theme changes:

```bash
npx @chakra-ui/cli typegen ./theme.ts
```

### Complete Ejection

Scaffold all default tokens and recipes:

```bash
npx @chakra-ui/cli eject --outdir ./theme
```

## Best Practices

1. **Extend defaultConfig** unless you need complete control
2. **Run typegen** after any theme changes
3. **Use semantic tokens** for color mode support
4. **Create color palettes** for brand colors
5. **Organize theme files** by concern (tokens, recipes, etc.)
6. **Use globalCss** for base styles, not individual components
