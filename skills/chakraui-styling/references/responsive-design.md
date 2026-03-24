# Responsive Design Patterns

## Breakpoints

Chakra UI uses a mobile-first breakpoint system with min-width media queries:

| Breakpoint | Min Width | Pixels |
|------------|-----------|--------|
| `base` | 0rem | 0px |
| `sm` | 30rem | ~480px |
| `md` | 48rem | ~768px |
| `lg` | 62rem | ~992px |
| `xl` | 80rem | ~1280px |
| `2xl` | 96rem | ~1536px |

## Object Syntax (Recommended)

Mobile-first approach - styles cascade up:

```tsx
<Box
  fontSize={{ base: "sm", md: "md", lg: "lg" }}
  p={{ base: "2", md: "4", lg: "8" }}
  flexDir={{ base: "column", md: "row" }}
/>
```

### Prop-based Modifier
```tsx
<Text fontWeight="medium" lg={{ fontWeight: "bold" }}>
  Text
</Text>
```

### Inline Base Value
```tsx
<Text fontWeight={{ base: "medium", lg: "bold" }}>Text</Text>
```

## Array Syntax

Index corresponds to breakpoint (0=base, 1=sm, 2=md, 3=lg, 4=xl, 5=2xl):

```tsx
<Box
  fontWeight={["medium", null, null, "bold"]}  // base=medium, lg=bold
  display={["none", "block", null, "flex"]}    // base=none, sm=block, lg=flex
/>
```

Use `null` to skip breakpoints.

## Breakpoint Targeting

### Range (`To` notation)
Apply styles between two breakpoints:

```tsx
<Text fontWeight={{ mdToXl: "bold" }}>Text</Text>
// Only bold from md to xl (not at base, sm, or 2xl)
```

### Single Breakpoint (`Only` notation)
Target only one breakpoint:

```tsx
<Text fontWeight={{ lgOnly: "bold" }}>Text</Text>
// Only bold at lg breakpoint
```

### Down (`Down` notation)
Target breakpoint and below:

```tsx
<Text fontWeight={{ smDown: "bold" }}>Text</Text>
// Bold from base up to and including sm
```

## Hide Utilities

### Hide From
Hide from a breakpoint and up:

```tsx
<Stack hideFrom="md">
  <Text>Hidden from md breakpoint and up</Text>
</Stack>
```

### Hide Below
Hide below a breakpoint:

```tsx
<Stack hideBelow="md">
  <Text>Hidden below md breakpoint</Text>
</Stack>
```

## Show/Hide Components

```tsx
import { Show, Hide } from "@chakra-ui/react"

<Show when={["md", "lg", "xl"]}>
  <DesktopNav />
</Show>

<Hide when={["md", "lg", "xl"]}>
  <MobileNav />
</Hide>
```

## Responsive Variants

For component variants, use explicit breakpoints instead of `base` to avoid style leaking:

```tsx
// ⚠️ Can lead to style leaking
<Button variant={{ base: "solid", md: "outline" }}>Button</Button>

// ✅ Better - clear boundaries
<Button variant={{ smDown: "solid", md: "outline" }}>Button</Button>
```

## Responsive CSS Variables

```tsx
<Box css={{ "--font-size": { base: "18px", lg: "24px" } }}>
  <h3 style={{ fontSize: "calc(var(--font-size) * 2)" }}>Hello</h3>
</Box>
```

## Common Patterns

### Responsive Layout
```tsx
<Grid
  templateColumns={{ base: "1fr", md: "repeat(2, 1fr)", lg: "repeat(4, 1fr)" }}
  gap={{ base: "4", md: "6", lg: "8" }}
>
  {items.map(item => <Card key={item.id} {...item} />)}
</Grid>
```

### Responsive Typography
```tsx
<Heading
  fontSize={{ base: "2xl", md: "3xl", lg: "4xl" }}
  lineHeight={{ base: "short", lg: "base" }}
>
  Responsive Title
</Heading>
```

### Responsive Spacing
```tsx
<Container
  py={{ base: "4", md: "8", lg: "12" }}
  px={{ base: "4", md: "6", lg: "8" }}
>
  Content
</Container>
```

### Responsive Visibility
```tsx
<HStack>
  <Box display={{ base: "none", md: "block" }}>
    Desktop Only
  </Box>
  <Box display={{ base: "block", md: "none" }}>
    Mobile Only
  </Box>
</HStack>
```

## Why rem for Breakpoints?

Breakpoints are converted to `rem` for accessibility:
- Respects user's browser font size settings
- Works correctly when user zooms
- Adapts to HTML font size changes
