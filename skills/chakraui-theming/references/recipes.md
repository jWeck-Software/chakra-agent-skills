# Component Recipes

Recipes define multi-variant styles with a type-safe runtime API for single-slot components.

## Recipe Structure

- `className`: CSS class to attach to the component
- `base`: Base styles for the component
- `variants`: Different style variations
- `compoundVariants`: Styles for variant combinations
- `defaultVariants`: Default variant values

## Defining a Recipe

```tsx
import { defineRecipe } from "@chakra-ui/react"

export const buttonRecipe = defineRecipe({
  base: {
    display: "flex",
    alignItems: "center",
    justifyContent: "center",
  },
  variants: {
    variant: {
      solid: { bg: "blue.500", color: "white" },
      outline: { borderWidth: "1px", borderColor: "blue.500", bg: "transparent" },
      ghost: { bg: "transparent", _hover: { bg: "gray.100" } },
    },
    size: {
      sm: { padding: "2", fontSize: "sm" },
      md: { padding: "3", fontSize: "md" },
      lg: { padding: "4", fontSize: "lg" },
    },
  },
  defaultVariants: {
    variant: "solid",
    size: "md",
  },
})
```

## Using Recipes

### Method 1: useRecipe Hook

```tsx
"use client"

import { chakra, useRecipe } from "@chakra-ui/react"
import { buttonRecipe } from "./button.recipe"

export const Button = (props) => {
  const recipe = useRecipe({ recipe: buttonRecipe })
  const [recipeProps, restProps] = recipe.splitVariantProps(props)
  const styles = recipe(recipeProps)

  return <chakra.button css={styles} {...restProps} />
}
```

### Method 2: chakra Factory (Recommended)

```tsx
import { chakra } from "@chakra-ui/react"
import { buttonRecipe } from "./button.recipe"

export const Button = chakra("button", buttonRecipe)
```

Usage:
```tsx
<Button variant="solid" size="lg">Click Me</Button>
```

### Method 3: From Theme

First, add to theme:
```tsx
const config = defineConfig({
  theme: {
    recipes: {
      button: buttonRecipe,
    },
  },
})
```

Then use by key:
```tsx
const recipe = useRecipe({ key: "button" })
```

## Default Variants

Set default variant values:

```tsx
const buttonRecipe = defineRecipe({
  base: { display: "flex" },
  variants: {
    variant: {
      solid: { bg: "blue.500" },
      outline: { borderWidth: "1px" },
    },
    size: {
      sm: { padding: "2" },
      lg: { padding: "4" },
    },
  },
  defaultVariants: {
    variant: "solid",
    size: "lg",
  },
})
```

## Compound Variants

Apply styles based on variant combinations:

```tsx
const buttonRecipe = defineRecipe({
  base: { display: "flex" },
  variants: {
    variant: {
      solid: { bg: "blue.500" },
      outline: { borderWidth: "1px" },
    },
    size: {
      sm: { padding: "2" },
      lg: { padding: "4" },
    },
  },
  compoundVariants: [
    {
      size: "sm",
      variant: "outline",
      css: {
        borderWidth: "2px",
      },
    },
  ],
})
```

**Caveat**: Compound variants don't work with responsive values. Use hide/show with breakpoints instead.

## Using Semantic Tokens

```tsx
const buttonRecipe = defineRecipe({
  base: {
    bg: "bg.muted",           // semantic token
    color: "fg",              // semantic token
    borderRadius: "l2",       // semantic radius
  },
  variants: {
    variant: {
      primary: {
        bg: "colorPalette.solid",  // virtual color
        color: "colorPalette.contrast",
      },
    },
  },
})
```

## Extending Existing Recipes

### Adding New Size Variant

```tsx
const buttonRecipe = defineRecipe({
  variants: {
    size: {
      xl: {
        fontSize: "lg",
        px: "6",
        py: "3",
      },
    },
  },
})

const config = defineConfig({
  theme: {
    recipes: {
      button: buttonRecipe,
    },
  },
})
```

Usage:
```tsx
<Button size="xl">Click me</Button>
```

### Adding Boolean Variant

```tsx
const buttonRecipe = defineRecipe({
  variants: {
    raised: {
      true: {
        boxShadow: "md",
      },
    },
  },
})
```

Usage:
```tsx
<Button raised>Click me</Button>
```

## Custom Recipe

Define a completely new recipe:

```tsx
const titleRecipe = defineRecipe({
  base: {
    fontWeight: "bold",
    letterSpacing: "tight",
  },
  variants: {
    size: {
      md: { fontSize: "xl" },
      lg: { fontSize: "2xl" },
    },
  },
})

const config = defineConfig({
  theme: {
    recipes: {
      title: titleRecipe,
    },
  },
})
```

Usage:
```tsx
const Title = (props) => {
  const recipe = useRecipe({ key: "title" })
  const styles = recipe({ size: "lg" })
  return <Box as="h1" css={styles} {...props} />
}
```

## TypeScript

### RecipeVariantProps Type

```tsx
import type { RecipeVariantProps } from "@chakra-ui/react"
import { buttonRecipe } from "./button.recipe"

type ButtonVariantProps = RecipeVariantProps<typeof buttonRecipe>

export interface ButtonProps extends React.PropsWithChildren<ButtonVariantProps> {}
```

### Type Generation

Run CLI to generate types:

```bash
npx @chakra-ui/cli typegen ./theme.ts
```

## splitVariantProps

Automatically split recipe props from component props:

```tsx
export const Button = (props) => {
  const recipe = useRecipe({ recipe: buttonRecipe })
  const [recipeProps, restProps] = recipe.splitVariantProps(props)
  const styles = recipe(recipeProps)

  return <chakra.button css={styles} {...restProps} />
}
```

## Best Practices

1. **Use semantic tokens** in recipes for color mode support
2. **Leverage `colorPalette`** for themeable components
3. **Set sensible defaults** with `defaultVariants`
4. **Use `splitVariantProps`** to cleanly separate variant props from component props
5. **Run typegen** after recipe changes for TypeScript support
