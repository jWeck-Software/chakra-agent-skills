# Design Tokens

Design tokens are platform-agnostic key-value pairs that describe fundamental visual styles.

## Token Structure

Each token consists of:
- `value`: The CSS value (required)
- `description`: Optional description

```tsx
tokens: {
  colors: {
    primary: { value: "#3b82f6", description: "Primary brand color" },
  },
}
```

## Token Types

### Colors

```tsx
tokens: {
  colors: {
    brand: {
      50: { value: "#eff6ff" },
      100: { value: "#dbeafe" },
      // ... 200-900
      950: { value: "#172554" },
    },
  },
}
```

**Default Color Palette**: `gray`, `red`, `orange`, `yellow`, `green`, `teal`, `blue`, `cyan`, `purple`, `pink` (each with 50-950 shades)

### Spacing

```tsx
tokens: {
  spacing: {
    gutter: { value: "12px" },
    "128": { value: "32rem" },
  },
}
```

**Default Spacing**: `0.5` (2px), `1` (4px), `1.5` (6px), `2` (8px), `2.5` (10px), `3` (12px), `3.5` (14px), `4` (16px), `5` (20px), `6` (24px), `7` (28px), `8` (32px), `9` (36px), `10` (40px), `11` (44px), `12` (48px), `14` (56px), `16` (64px), `20` (80px), `24` (96px), `28` (112px), `32` (128px), `36` (144px), `40` (160px), `44` (176px), `48` (192px), `52` (208px), `56` (224px), `60` (240px), `64` (256px), `72` (288px), `80` (320px), `96` (384px)

### Sizes

```tsx
tokens: {
  sizes: {
    sm: { value: "12px" },
    "1/7": { value: "14.285%" },
  },
}
```

Used for: `width`, `height`, `minWidth`, `maxWidth`, `minHeight`, `maxHeight`

### Fonts

```tsx
tokens: {
  fonts: {
    body: { value: "Inter, sans-serif" },
    heading: { value: ["Poppins", "sans-serif"] },
    mono: { value: "Fira Code, monospace" },
  },
}
```

**Default Fonts**: `heading`, `body`, `mono`

### Font Sizes

```tsx
tokens: {
  fontSizes: {
    sm: { value: "12px" },
  },
}
```

**Default Font Sizes**: `2xs` (10px), `xs` (12px), `sm` (14px), `md` (16px), `lg` (18px), `xl` (20px), `2xl` (24px), `3xl` (30px), `4xl` (36px), `5xl` (48px), `6xl` (60px), `7xl` (72px), `8xl` (96px), `9xl` (128px)

### Font Weights

```tsx
tokens: {
  fontWeights: {
    bold: { value: "700" },
  },
}
```

**Default Font Weights**: `thin` (100), `extralight` (200), `light` (300), `normal` (400), `medium` (500), `semibold` (600), `bold` (700), `extrabold` (800), `black` (900)

### Line Heights

```tsx
tokens: {
  lineHeights: {
    normal: { value: "1.5" },
  },
}
```

**Default Line Heights**: `shorter` (1.25), `short` (1.375), `moderate` (1.5), `tall` (1.625), `taller` (2)

### Letter Spacings

```tsx
tokens: {
  letterSpacings: {
    wide: { value: "0.1em" },
  },
}
```

**Default Letter Spacings**: `tighter` (-0.05em), `tight` (-0.025em), `wide` (0.025em), `wider` (0.05em), `widest` (0.1em)

### Radii (Border Radius)

```tsx
tokens: {
  radii: {
    sm: { value: "4px" },
  },
}
```

**Default Radii**: `none` (0), `2xs` (1px), `xs` (2px), `sm` (4px), `md` (6px), `lg` (8px), `xl` (12px), `2xl` (16px), `3xl` (24px), `4xl` (32px), `full` (9999px), `l1` (2px), `l2` (4px), `l3` (6px)

### Borders

```tsx
tokens: {
  borders: {
    subtle: { value: "1px solid red" },
    danger: { value: "1px solid {colors.red.400}" }, // with reference
    accent: { value: { width: "1px", color: "red", style: "solid" } }, // composite
  },
}
```

### Shadows

```tsx
tokens: {
  shadows: {
    subtle: { value: "0 1px 2px 0 rgba(0, 0, 0, 0.05)" },
    accent: { value: { offsetX: 0, offsetY: 4, blur: 4, spread: 0, color: "rgba(0, 0, 0, 0.1)" } },
    realistic: { value: ["0 1px 2px 0 rgba(0, 0, 0, 0.05)", "0 1px 4px 0 rgba(0, 0, 0, 0.1)"] },
  },
}
```

**Default Shadows**: `xs`, `sm`, `md`, `lg`, `xl`, `2xl`, `inner`, `inset`

### Z-Index

```tsx
tokens: {
  zIndex: {
    modal: { value: 1000 },
  },
}
```

**Default Z-Index**: `hide` (-1), `base` (0), `docked` (10), `dropdown` (1000), `sticky` (1100), `banner` (1200), `overlay` (1300), `modal` (1400), `popover` (1500), `skipNav` (1600), `toast` (1700), `tooltip` (1800), `max` (2147483647)

### Opacity

```tsx
tokens: {
  opacity: {
    50: { value: 0.5 },
  },
}
```

### Easings

```tsx
tokens: {
  easings: {
    easeIn: { value: "cubic-bezier(0.4, 0, 0.2, 1)" },
    easeOut: { value: [0.4, 0, 0.2, 1] }, // array value
  },
}
```

### Durations

```tsx
tokens: {
  durations: {
    fast: { value: "100ms" },
  },
}
```

**Default Durations**: `slowest` (500ms), `slower` (400ms), `slow` (300ms), `moderate` (200ms), `fast` (150ms), `faster` (100ms), `fastest` (50ms)

### Animations

```tsx
tokens: {
  animations: {
    spin: { value: "spin 1s linear infinite" },
  },
}
```

**Default Keyframes**: `spin`, `pulse`, `ping`, `bounce`, `bg-position`, `position`, `circular-progress`, `expand-height`, `collapse-height`, `expand-width`, `collapse-width`, `fade-in`, `fade-out`, `slide-from-left-full`, `slide-from-right-full`, `slide-from-top-full`, `slide-from-bottom-full`, `slide-to-left-full`, `slide-to-right-full`, `slide-to-top-full`, `slide-to-bottom-full`, `slide-from-top`, `slide-from-bottom`, `slide-from-left`, `slide-from-right`, `slide-to-top`, `slide-to-bottom`, `slide-to-left`, `slide-to-right`, `scale-in`, `scale-out`, `marqueeX`, `marqueeY`

### Aspect Ratios

```tsx
tokens: {
  aspectRatios: {
    "1:1": { value: "1 / 1" },
    "16:9": { value: "16 / 9" },
  },
}
```

**Default Aspect Ratios**: `square` (1/1), `landscape` (4/3), `portrait` (3/4), `wide` (16/9), `ultrawide` (18/5), `golden` (1.618/1)

### Gradients

```tsx
tokens: {
  gradients: {
    simple: { value: "linear-gradient(to right, red, blue)" },
    primary: { value: { type: "linear", placement: "to right", stops: ["red", "blue"] } },
  },
}
```

### Assets

```tsx
tokens: {
  assets: {
    logo: { value: { type: "url", value: "/static/logo.png" } },
    checkmark: { value: { type: "svg", value: "<svg>...</svg>" } },
  },
}
```

### Cursors

```tsx
tokens: {
  cursor: {
    button: { value: "pointer" },
  },
}
```

**Default Cursors**: `button` (pointer), `checkbox` (default), `disabled` (not-allowed), `menuitem` (default), `option` (default), `radio` (default), `slider` (default), `switch` (pointer)

## Token Nesting

Use `DEFAULT` key for default value of nested tokens:

```tsx
tokens: {
  colors: {
    red: {
      DEFAULT: { value: "#EE0F0F" },
      100: { value: "#fee2e2" },
    },
  },
}
```

Usage:
```tsx
<Box bg="red" />        // uses DEFAULT
<Box bg="red.100" />    // uses nested value
```

## Token Reference Syntax

Reference tokens in composite values using `{path.to.token}`:

```tsx
<Box
  border="1px solid {colors.red.300}"
  p="{spacing.4} {spacing.6}"
  boxShadow="{spacing.4} {spacing.2} {spacing.2} {colors.red.300}"
/>
```

## Usage

After defining tokens, run typegen for autocompletion:

```bash
npx @chakra-ui/cli typegen ./theme.ts
```

Then use in components:
```tsx
<Box color="brand.500" fontFamily="body" fontSize="lg">
  Hello World
</Box>
```
