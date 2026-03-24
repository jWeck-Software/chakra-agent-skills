# Common Patterns for This Project

## Chakra Factory

Create supercharged JSX components that accept style props:

### JSX Element Syntax
```tsx
import { chakra } from "@chakra-ui/react"

// Use chakra.<element> syntax
<chakra.button bg="blue.500" color="white" py="2" px="4" rounded="md">
  Click me
</chakra.button>
```

### Factory Function
```tsx
// Convert native elements
const Link = chakra("a")

// With base styles
const Card = chakra("div", {
  base: {
    shadow: "lg",
    rounded: "lg",
    bg: "white",
  },
})

// With variants
const Card = chakra("div", {
  base: { shadow: "lg", rounded: "lg" },
  variants: {
    variant: {
      outline: { border: "1px solid", borderColor: "gray.200" },
      solid: { bg: "gray.800", color: "white" },
    },
  },
})
```

### Polymorphism
```tsx
// Use `as` prop to change element
<Button as="a" href="https://example.com">
  Link Button
</Button>

// Use `asChild` for composition
<Button asChild>
  <a href="https://example.com">Link Button</a>
</Button>
```

## Color Opacity Modifier

Apply opacity to any color using `{color}/{opacity}` syntax:

```tsx
<Box bg="red.300/40" />                    // 40% opacity
<Box borderColor="blue.500/20" />          // 20% opacity
<Box shadow="lg" shadowColor="black/30" /> // 30% opacity
```

### In CSS Variables
```tsx
<Box css={{ "--bg": "{colors.red.400/40}" }}>
  <Box bg="var(--bg)" />
</Box>
```

## Virtual Color (colorPalette)

Create themeable components with virtual colors:

```tsx
// Basic usage
<Box colorPalette="blue" bg="colorPalette.100">
  Light blue background
</Box>

// With hover states
<Box
  colorPalette="green"
  bg="colorPalette.500"
  _hover={{ bg: "colorPalette.600" }}
>
  Green button
</Box>

// With dark mode
<Box
  colorPalette="blue"
  bg={{ base: "colorPalette.600", _dark: "colorPalette.400" }}
>
  Adapts to color mode
</Box>

// Semantic tokens
<Box bg="colorPalette.solid" color="colorPalette.contrast">
  Uses semantic tokens
</Box>
```

### Color Palette Scale
```tsx
<Box colorPalette="blue">
  <Box bg="colorPalette.50">Lightest</Box>
  <Box bg="colorPalette.100">Lighter</Box>
  <Box bg="colorPalette.300">Light</Box>
  <Box bg="colorPalette.500">Base</Box>
  <Box bg="colorPalette.700">Dark</Box>
  <Box bg="colorPalette.900">Darker</Box>
  <Box bg="colorPalette.950">Darkest</Box>
</Box>
```

## Text Styles

Define reusable typography styles:

```tsx
// Using built-in text styles
<Heading textStyle="2xl">Large heading</Heading>
<Text textStyle="lg">Large text</Text>
<Text textStyle="sm">Small text</Text>
<Text textStyle="xs">Extra small text</Text>
```

### Defining Custom Text Styles
```tsx
// In theme.ts
import { defineTextStyles } from "@chakra-ui/react"

const textStyles = defineTextStyles({
  heading1: {
    value: {
      fontFamily: "heading",
      fontWeight: "bold",
      fontSize: "4xl",
      lineHeight: "1.2",
    },
  },
  body: {
    value: {
      fontFamily: "body",
      fontSize: "md",
      lineHeight: "tall",
    },
  },
})
```

## Layer Styles

Define reusable container styles:

```tsx
// Using layer styles
<Box layerStyle="card">Card content</Box>
<Box layerStyle="section">Section content</Box>
```

### Defining Custom Layer Styles
```tsx
// In theme.ts
import { defineLayerStyles } from "@chakra-ui/react"

const layerStyles = defineLayerStyles({
  card: {
    value: {
      bg: "white",
      shadow: "md",
      rounded: "xl",
      p: "6",
      border: "1px solid",
      borderColor: "gray.100",
    },
  },
  section: {
    value: {
      py: "8",
      px: "6",
      maxW: "container.xl",
      mx: "auto",
    },
  },
})
```

## Animation Styles

Define reusable animations:

```tsx
// In theme.ts
import { defineAnimationStyles } from "@chakra-ui/react"

const animationStyles = defineAnimationStyles({
  "slide-fade-in": {
    value: {
      animationName: "slide-in, fade-in",
      animationDuration: "0.3s",
      animationTimingFunction: "ease-out",
    },
  },
})

// Usage
<Box animationStyle="slide-fade-in">Animated content</Box>

// With state-based animations
<Box
  data-state="open"
  animationDuration="slow"
  animationStyle={{ _open: "slide-fade-in", _closed: "slide-fade-out" }}
>
  Animated based on state
</Box>
```

## Dashboard Cards

```tsx
<Box
  p="6"
  rounded="xl"
  bg="white"
  shadow="md"
  border="1px solid"
  borderColor="gray.100"
  _dark={{ bg: "gray.800", borderColor: "gray.700" }}
  transition="all 0.2s"
  _hover={{ shadow: "lg", transform: "translateY(-2px)" }}
>
  <Heading size="md" mb="2">Card Title</Heading>
  <Text color="gray.600" _dark={{ color: "gray.400" }}>
    Card content
  </Text>
</Box>
```

## Metric Displays

```tsx
<VStack align="flex-start" gap="1">
  <Text textStyle="sm" color="gray.500">
    Metric Label
  </Text>
  <Heading size="2xl" colorPalette="green">
    $1,234.56
  </Heading>
  <HStack gap="1" color="green.500">
    <ArrowUpIcon />
    <Text fontWeight="medium">+12.5%</Text>
  </HStack>
</VStack>
```

## Sidebar Navigation Items

```tsx
<HStack
  px="4"
  py="3"
  rounded="md"
  cursor="pointer"
  transition="all 0.15s"
  color="gray.600"
  _hover={{ bg: "gray.100", color: "gray.900" }}
  _dark={{ color: "gray.400", _hover: { bg: "gray.700", color: "white" } }}
  _active={{ bg: "blue.500/10", color: "blue.400" }}
>
  <Icon as={DashboardIcon} />
  <Text fontWeight="medium">Dashboard</Text>
</HStack>
```

## Data Tables

```tsx
<Table.Root variant="line">
  <Table.Header>
    <Table.Row bg="gray.50" _dark={{ bg: "gray.800" }}>
      <Table.ColumnHeader py="3" px="4">Symbol</Table.ColumnHeader>
      <Table.ColumnHeader py="3" px="4" textAlign="right">Price</Table.ColumnHeader>
    </Table.Row>
  </Table.Header>
  <Table.Body>
    {data.map((row) => (
      <Table.Row
        key={row.id}
        _even={{ bg: "gray.50/50" }}
        _dark={{ _even: { bg: "gray.800/50" } }}
        _hover={{ bg: "gray.100" }}
        _dark={{ _hover: { bg: "gray.700" } }}
      >
        <Table.Cell py="3" px="4">{row.symbol}</Table.Cell>
        <Table.Cell py="3" px="4" textAlign="right">
          {row.price}
        </Table.Cell>
      </Table.Row>
    ))}
  </Table.Body>
</Table.Root>
```

## Status Badges

```tsx
<Badge
  colorPalette={status === 'success' ? 'green' : status === 'error' ? 'red' : 'yellow'}
  px="2"
  py="0.5"
  rounded="full"
  textTransform="uppercase"
  fontSize="xs"
  fontWeight="bold"
>
  {status}
</Badge>
```

## Form Fields

```tsx
<Field.Root invalid={hasError}>
  <Field.Label fontSize="sm" fontWeight="medium">
    Email Address
  </Field.Label>
  <Input
    placeholder="you@example.com"
    _placeholder={{ color: "gray.400" }}
  />
  <Field.ErrorText color="red.500" fontSize="sm">
    Please enter a valid email
  </Field.ErrorText>
  <Field.HelperText color="gray.500" fontSize="sm">
    We'll never share your email
  </Field.HelperText>
</Field.Root>
```

## Animation & Transitions

```tsx
<Box
  transition="all 0.2s"
  transitionTimingFunction="ease-in-out"
  _hover={{ transform: "scale(1.05)", bg: "blue.600" }}
>
  Hover me
</Box>
```

## Gradient Text

```tsx
<Text
  bgGradient="to-r"
  gradientFrom="blue.400"
  gradientTo="purple.500"
  bgClip="text"
  color="transparent"
>
  Gradient Text
</Text>
```

## Glass Effect (Frosted Glass)

```tsx
<Box
  bg="white/80"
  backdropFilter="blur(12px)"
  border="1px solid"
  borderColor="white/20"
  shadow="xl"
>
  Frosted glass effect
</Box>
```

## Scrollable Container

```tsx
<Box
  maxH="400px"
  overflowY="auto"
  scrollBehavior="smooth"
  scrollPadding="4"
  sx={{
    "&::-webkit-scrollbar": {
      width: "8px",
    },
    "&::-webkit-scrollbar-track": {
      bg: "gray.100",
    },
    "&::-webkit-scrollbar-thumb": {
      bg: "gray.300",
      rounded: "full",
    },
  }}
>
  Scrollable content
</Box>
```

## Truncation Patterns

```tsx
// Single line truncation
<Text truncate maxW="200px">
  This text will be truncated with ellipsis if too long
</Text>

// Multi-line truncation
<Text lineClamp={3}>
  This text will be truncated after 3 lines with ellipsis
</Text>
```

## Responsive Grid Layout

```tsx
<SimpleGrid
  columns={{ base: 1, sm: 2, lg: 3, xl: 4 }}
  gap={{ base: "4", md: "6" }}
>
  {items.map(item => (
    <Card key={item.id} {...item} />
  ))}
</SimpleGrid>
```

## Centered Container

```tsx
<Container
  maxW="container.xl"
  py={{ base: "4", md: "8" }}
  px={{ base: "4", md: "6" }}
>
  <Center minH="100vh">
    <VStack gap="8">
      Content
    </VStack>
  </Center>
</Container>
```

## Sticky Header

```tsx
<Box
  position="sticky"
  top="0"
  zIndex="sticky"
  bg="white"
  _dark={{ bg: "gray.900" }}
  borderBottom="1px solid"
  borderColor="gray.200"
  _dark={{ borderColor: "gray.700" }}
  backdropFilter="blur(8px)"
  bg="white/90"
  _dark={{ bg: "gray.900/90" }}
>
  <Container maxW="container.xl" py="4">
    Header content
  </Container>
</Box>
```
