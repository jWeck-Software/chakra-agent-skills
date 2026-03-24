# Semantic Tokens

Semantic tokens are context-aware tokens that can change based on conditions like color mode (light/dark).

## Basic Structure

```tsx
semanticTokens: {
  colors: {
    danger: { value: "{colors.red.500}" },
  },
}
```

## Token Reference Syntax

Use `{}` to reference existing tokens:

```tsx
semanticTokens: {
  colors: {
    danger: { value: "{colors.red}" },
    success: { value: "{colors.green}" },
  },
}
```

## Conditional Tokens (Light/Dark Mode)

Semantic tokens can change based on conditions:

```tsx
semanticTokens: {
  colors: {
    danger: {
      value: { 
        base: "{colors.red.500}", 
        _dark: "{colors.red.300}" 
      },
    },
    success: {
      value: { 
        base: "{colors.green}", 
        _dark: "{colors.darkgreen}" 
      },
    },
  },
}
```

**Note**: Conditions must be at-rules or parent selector conditions (like `_dark`, `_light`).

## Nested Semantic Tokens

Use `DEFAULT` for the default nested value:

```tsx
semanticTokens: {
  colors: {
    bg: {
      DEFAULT: { value: "{colors.gray.100}" },
      primary: { value: "{colors.teal.100}" },
      secondary: { value: "{colors.gray.100}" },
    },
  },
}
```

Usage:
```tsx
<Box bg="bg" />           // uses DEFAULT
<Box bg="bg.primary" />   // uses nested value
<Box bg="bg.secondary" /> // uses nested value
```

## Built-in Semantic Tokens

### Background Tokens

| Token | Usage |
|-------|-------|
| `bg` | `<Box bg="bg" />` |
| `bg.subtle` | `<Box bg="bg.subtle" />` |
| `bg.muted` | `<Box bg="bg.muted" />` |
| `bg.emphasized` | `<Box bg="bg.emphasized" />` |
| `bg.inverted` | `<Box bg="bg.inverted" />` |
| `bg.panel` | `<Box bg="bg.panel" />` |
| `bg.error` | `<Box bg="bg.error" />` |
| `bg.warning` | `<Box bg="bg.warning" />` |
| `bg.success` | `<Box bg="bg.success" />` |
| `bg.info` | `<Box bg="bg.info" />` |

### Text/Foreground Tokens

| Token | Usage |
|-------|-------|
| `fg` | `<Box color="fg" />` |
| `fg.muted` | `<Box color="fg.muted" />` |
| `fg.subtle` | `<Box color="fg.subtle" />` |
| `fg.inverted` | `<Box color="fg.inverted" />` |
| `fg.error` | `<Box color="fg.error" />` |
| `fg.warning` | `<Box color="fg.warning" />` |
| `fg.success` | `<Box color="fg.success" />` |
| `fg.info` | `<Box color="fg.info" />` |

### Border Tokens

| Token | Usage |
|-------|-------|
| `border` | `<Box borderColor="border" />` |
| `border.muted` | `<Box borderColor="border.muted" />` |
| `border.subtle` | `<Box borderColor="border.subtle" />` |
| `border.emphasized` | `<Box borderColor="border.emphasized" />` |
| `border.inverted` | `<Box borderColor="border.inverted" />` |
| `border.error` | `<Box borderColor="border.error" />` |
| `border.warning` | `<Box borderColor="border.warning" />` |
| `border.success` | `<Box borderColor="border.success" />` |
| `border.info` | `<Box borderColor="border.info" />` |

### Shadow Tokens

| Token | Usage |
|-------|-------|
| `xs` | `<Box shadow="xs" />` |
| `sm` | `<Box shadow="sm" />` |
| `md` | `<Box shadow="md" />` |
| `lg` | `<Box shadow="lg" />` |
| `xl` | `<Box shadow="xl" />` |
| `2xl` | `<Box shadow="2xl" />` |
| `inner` | `<Box shadow="inner" />` |
| `inset` | `<Box shadow="inset" />` |

## Color Palette (for colorPalette prop)

When using the `colorPalette` prop, define these semantic tokens for each brand color:

```tsx
semanticTokens: {
  colors: {
    brand: {
      solid: { value: "{colors.brand.500}" },       // Bold fill color
      contrast: { value: "{colors.white}" },        // Text on solid color
      fg: { value: "{colors.brand.700}" },          // Foreground (text, icons)
      muted: { value: "{colors.brand.100}" },       // Muted variant
      subtle: { value: "{colors.brand.200}" },      // Subtle variant
      emphasized: { value: "{colors.brand.300}" },  // Emphasized subtle
      focusRing: { value: "{colors.brand.500}" },   // Focus ring color
    },
  },
}
```

Usage with `colorPalette`:
```tsx
<Button colorPalette="brand">Click me</Button>
<Box colorPalette="brand" bg="colorPalette.solid" color="colorPalette.contrast">
  Themed content
</Box>
```

## Custom Semantic Tokens

Define custom semantic tokens for specific use cases:

```tsx
semanticTokens: {
  colors: {
    "checkbox-border": {
      value: { _light: "gray.200", _dark: "gray.800" },
    },
  },
}
```

Usage:
```tsx
<Square size="4" borderColor="checkbox-border">
  <LuCheck />
</Square>
```

## Using in Recipes

Semantic tokens are available in recipe definitions:

```tsx
const cardRecipe = defineRecipe({
  base: {
    bg: "bg.subtle",      // semantic token
    color: "fg",          // semantic token
    borderColor: "border", // semantic token
  },
})
```

## TypeScript Integration

After defining semantic tokens, run typegen:

```bash
npx @chakra-ui/cli typegen ./theme.ts
```

This provides autocompletion for semantic tokens in your editor.

## Best Practices

1. **Use semantic tokens over raw colors** - They adapt to color mode automatically
2. **Create color palettes** for brand colors to enable `colorPalette` prop
3. **Use built-in semantic tokens** (`bg`, `fg`, `border`) for consistent theming
4. **Leverage conditional values** for light/dark mode support
5. **Group related tokens** using nesting with `DEFAULT` key
