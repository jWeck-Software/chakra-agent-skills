# Slot Recipes

Slot recipes apply style variations to multiple parts (slots) of a component.

## Slot Recipe Structure

- `className`: CSS class prefix for component slots
- `slots`: Array of component parts to style
- `base`: Base styles per slot
- `variants`: Visual styles for each slot
- `defaultVariants`: Default variant values
- `compoundVariants`: Styles for variant combinations per slot

## Defining a Slot Recipe

```tsx
import { defineSlotRecipe } from "@chakra-ui/react"

export const checkboxSlotRecipe = defineSlotRecipe({
  slots: ["root", "control", "label"],
  base: {
    root: { display: "flex", alignItems: "center", gap: "2" },
    control: { borderWidth: "1px", borderRadius: "sm" },
    label: { marginStart: "2" },
  },
  variants: {
    size: {
      sm: {
        control: { width: "4", height: "4" },
        label: { fontSize: "sm" },
      },
      md: {
        control: { width: "5", height: "5" },
        label: { fontSize: "md" },
      },
    },
    variant: {
      outline: {
        control: { borderColor: "gray.200" },
      },
      filled: {
        control: { bg: "gray.100" },
      },
    },
  },
  defaultVariants: {
    size: "md",
    variant: "outline",
  },
})
```

## Using Slot Recipes

### Method 1: useSlotRecipe Hook

```tsx
"use client"

import { chakra, useSlotRecipe } from "@chakra-ui/react"
import { checkboxSlotRecipe } from "./checkbox.recipe"

export const Checkbox = (props) => {
  const { size, ...restProps } = props

  const recipe = useSlotRecipe({ recipe: checkboxSlotRecipe })
  const [recipeProps, restProps] = recipe.splitVariantProps(props)
  const styles = recipe(recipeProps)

  return (
    <chakra.label css={styles.root}>
      <chakra.input type="checkbox" css={styles.control} {...restProps} />
      <chakra.span css={styles.label}>Checkbox Label</chakra.span>
    </chakra.label>
  )
}
```

### Method 2: createSlotRecipeContext (Recommended)

Create compound components that share the same context:

```tsx
"use client"

import { createSlotRecipeContext } from "@chakra-ui/react"
import { checkboxSlotRecipe } from "./checkbox.recipe"

const { withProvider, withContext } = createSlotRecipeContext({
  recipe: checkboxSlotRecipe,
})

// Root component (uses withProvider)
interface CheckboxRootProps extends HTMLChakraProps<"label", RecipeVariantProps<typeof checkboxSlotRecipe>> {}
export const CheckboxRoot = withProvider<HTMLLabelElement, CheckboxRootProps>("label", "root")

// Control component (uses withContext)
interface CheckboxControlProps extends HTMLChakraProps<"input"> {}
export const CheckboxControl = withContext<HTMLInputElement, CheckboxControlProps>("input", "control")

// Label component (uses withContext)
interface CheckboxLabelProps extends HTMLChakraProps<"span"> {}
export const CheckboxLabel = withContext<HTMLSpanElement, CheckboxLabelProps>("span", "label")
```

Usage:
```tsx
<CheckboxRoot size="md" variant="outline">
  <CheckboxControl />
  <CheckboxLabel>Checkbox Label</CheckboxLabel>
</CheckboxRoot>
```

### unstyled Prop

Remove recipe styles with `unstyled` prop:

```tsx
<CheckboxRoot unstyled>
  <CheckboxControl />
  <CheckboxLabel />
</CheckboxRoot>
```

## Compound Variants

Apply styles based on variant combinations:

```tsx
const checkboxRecipe = defineSlotRecipe({
  slots: ["root", "control", "label"],
  base: {},
  variants: {
    size: { sm: {}, md: {} },
    visual: { contained: {}, outline: {} },
  },
  compoundVariants: [
    {
      size: "sm",
      visual: "outline",
      css: {
        control: { borderWidth: "1px" },
        label: { color: "green.500" },
      },
    },
  ],
})
```

## Targeting Slots by ClassName

Use `className` config for slot-specific targeting:

```tsx
const checkboxRecipe = defineSlotRecipe({
  className: "checkbox",
  slots: ["root", "control", "label"],
  base: {
    root: {
      bg: "blue.500",
      _hover: {
        "& .checkbox__label": { color: "white" },
      },
    },
  },
})
```

Naming convention: `${className}__${slot}` (e.g., `checkbox__label`)

## Theme Usage

Add slot recipe to theme:

```tsx
const config = defineConfig({
  theme: {
    slotRecipes: {
      checkbox: checkboxSlotRecipe,
    },
  },
})

export default createSystem(defaultConfig, config)
```

Then use by key:
```tsx
const recipe = useSlotRecipe({ key: "checkbox" })
```

Or with createSlotRecipeContext:
```tsx
const { withProvider, withContext } = createSlotRecipeContext({
  key: "checkbox",
})
```

## Extending Existing Slot Recipes

### Adding New Size Variant

```tsx
import { alertAnatomy } from "@chakra-ui/react/anatomy"

const alertSlotRecipe = defineSlotRecipe({
  slots: alertAnatomy.keys(),
  variants: {
    size: {
      xl: {
        root: {
          fontSize: "lg",
          px: "6",
          py: "3",
        },
      },
    },
  },
})
```

Usage:
```tsx
<Alert size="xl" title="..." />
```

### Adding New Variant

```tsx
const alertSlotRecipe = defineSlotRecipe({
  slots: alertAnatomy.keys(),
  variants: {
    shape: {
      rounded: {
        root: { borderRadius: "full" },
      },
    },
  },
})
```

Usage:
```tsx
<Alert shape="rounded" title="..." />
```

## Custom Slot Recipe

Define a completely new slot recipe:

```tsx
const navbarSlotRecipe = defineSlotRecipe({
  slots: ["root", "badge", "icon"],
  base: {
    root: {
      bg: "blue.500",
      color: "white",
      px: "4",
      py: "2",
    },
    badge: {
      borderRadius: "full",
      px: "2",
      py: "1",
    },
    icon: {
      fontSize: "lg",
    },
  },
})

const config = defineConfig({
  theme: {
    slotRecipes: {
      navbar: navbarSlotRecipe,
    },
  },
})
```

Usage:
```tsx
const Navbar = (props) => {
  const recipe = useSlotRecipe({ key: "navbar" })
  const styles = recipe()
  
  return (
    <Box css={styles.root}>
      {props.children}
      <Box css={styles.badge} />
      <Box css={styles.icon} />
    </Box>
  )
}
```

## TypeScript

### RecipeVariantProps Type

```tsx
import type { RecipeVariantProps, UnstyledProp } from "@chakra-ui/react"
import { checkboxSlotRecipe } from "./checkbox.recipe"

type CheckboxVariantProps = RecipeVariantProps<typeof checkboxSlotRecipe>

export interface CheckboxProps
  extends React.PropsWithChildren<CheckboxVariantProps>, UnstyledProp {}
```

### SlotRecipeProps Type (from theme)

```tsx
import type { SlotRecipeProps, UnstyledProp } from "@chakra-ui/react"

export interface CheckboxProps
  extends SlotRecipeProps<"checkbox">, UnstyledProp {}
```

### Type Generation

```bash
npx @chakra-ui/cli typegen ./theme.ts
```

## Best Practices

1. **Use anatomy imports** for existing components (e.g., `alertAnatomy.keys()`)
2. **Create compound components** with `createSlotRecipeContext` for better DX
3. **Apply variant props to root** component (the one using `withProvider`)
4. **Support `unstyled` prop** for style reset capability
5. **Run typegen** after slot recipe changes
