# Layout Components

## Box

The universal wrapper component that provides access to all style props.

```tsx
import { Box } from "@chakra-ui/react"

// Basic usage
<Box bg="tomato" w="100%" p="4" color="white">
  This is the Box
</Box>

// With pseudo props
<Box bg="tomato" _hover={{ bg: "green" }}>
  Hover me
</Box>

// With border
<Box p="4" borderWidth="1px" borderColor="border.disabled">
  Bordered box
</Box>

// Render as different element
<Box as="section">Rendered as section</Box>

// With shadow
<Box bg="bg" shadow="md" borderRadius="md">
  Box with shadow
</Box>
```

### Props
- All CSS properties as props
- `as` - Render as different element
- Pseudo props (`_hover`, `_focus`, `_active`, etc.)

---

## Flex

A container for flexbox layouts.

```tsx
import { Flex, Spacer } from "@chakra-ui/react"

// Basic flex
<Flex gap="4">
  <Box h="10" />
  <Box h="10" />
</Flex>

// Direction
<Flex direction="column" gap="4">
  <Box />
  <Box />
</Flex>

// Alignment
<Flex align="center" gap="4">
  <Box h="4" />
  <Box h="8" />
</Flex>

// Justify content
<Flex justify="space-between">
  <Box />
  <Box />
</Flex>

// With spacer
<Flex>
  <Box>Left</Box>
  <Spacer />
  <Box>Right</Box>
</Flex>

// Auto margin
<Flex justify="space-between">
  <Box marginEnd="auto" />
  <Box />
</Flex>
```

### Props
- `direction` / `flexDirection` - `row`, `column`, `row-reverse`, `column-reverse`
- `align` / `alignItems` - `flex-start`, `center`, `flex-end`, `stretch`, `baseline`
- `justify` / `justifyContent` - `flex-start`, `center`, `flex-end`, `space-between`, `space-around`
- `wrap` / `flexWrap` - `nowrap`, `wrap`, `wrap-reverse`
- `gap` - Spacing between items

---

## Stack

Layout component for consistent spacing between children.

```tsx
import { Stack, HStack, VStack, StackSeparator } from "@chakra-ui/react"

// Vertical stack (default)
<Stack gap="4">
  <Box />
  <Box />
</Stack>

// Horizontal stack
<HStack gap="4">
  <Box />
  <Box />
</HStack>

// Vertical stack with alignment
<VStack align="stretch" gap="4">
  <Box />
  <Box />
</VStack>

// With separator
<Stack separator={<StackSeparator />}>
  <Box />
  <Box />
</Stack>

// Responsive direction
<Stack direction={{ base: "column", md: "row" }} gap="10">
  <Box />
  <Box />
</Stack>
```

### Props
- `direction` - `row`, `column`
- `gap` - Spacing between items
- `align` - Cross-axis alignment
- `justify` - Main-axis alignment
- `separator` - Element to render between items

---

## Grid

CSS Grid layout component.

```tsx
import { Grid, GridItem } from "@chakra-ui/react"

// Basic grid
<Grid templateColumns="repeat(3, 1fr)" gap="6">
  <Box />
  <Box />
  <Box />
</Grid>

// Column spanning
<Grid templateColumns="repeat(4, 1fr)" gap="6">
  <GridItem colSpan={2}>
    <Box>Spans 2 columns</Box>
  </GridItem>
  <GridItem colSpan={1}>
    <Box>Spans 1 column</Box>
  </GridItem>
</Grid>

// Row and column spanning
<Grid templateRows="repeat(2, 1fr)" templateColumns="repeat(5, 1fr)" gap={4}>
  <GridItem rowSpan={2} colSpan={1}>
    <Box>Spans 2 rows</Box>
  </GridItem>
  <GridItem colSpan={4}>
    <Box>Spans 4 columns</Box>
  </GridItem>
</Grid>
```

### Props
- `templateColumns` - Grid column template
- `templateRows` - Grid row template
- `templateAreas` - Named grid areas
- `gap` - Gap between items
- `autoFlow` - Grid auto flow
- `autoRows` - Auto row size
- `autoColumns` - Auto column size

---

## SimpleGrid

Simplified grid with responsive column counts.

```tsx
import { SimpleGrid, GridItem } from "@chakra-ui/react"

// Fixed columns
<SimpleGrid columns={2} gap="40px">
  <Box />
  <Box />
</SimpleGrid>

// Responsive columns
<SimpleGrid columns={[2, null, 3]} gap="40px">
  <Box />
  <Box />
</SimpleGrid>

// Auto-responsive with min width
<SimpleGrid minChildWidth="sm" gap="40px">
  <Box />
  <Box />
</SimpleGrid>

// With column span
<SimpleGrid columns={{ base: 2, md: 4 }} gap={{ base: "24px", md: "40px" }}>
  <GridItem colSpan={{ base: 1, md: 3 }}>
    <Box />
  </GridItem>
</SimpleGrid>

// Separate row and column gap
<SimpleGrid columns={2} columnGap="2" rowGap="4">
  <Box />
  <Box />
</SimpleGrid>
```

### Props
- `columns` - Number of columns (responsive)
- `minChildWidth` - Minimum width for auto-fit
- `gap` - Gap between items
- `columnGap` - Horizontal gap
- `rowGap` - Vertical gap

---

## Center

Center content horizontally and vertically.

```tsx
import { Center, Circle, Square } from "@chakra-ui/react"

// Basic center
<Center bg="bg.emphasized" h="100px">
  <Box>Centered content</Box>
</Center>

// Inline center
<Link href="#">
  <Center inline gap="4">
    <Box>Visit Chakra UI</Box>
    <LuArrowRight />
  </Center>
</Link>

// Square (equal width/height)
<Square size="10" bg="purple.700" color="white">
  <LuPhoneForwarded />
</Square>

// Circle (rounded square)
<Circle size="10" bg="blue.700" color="white">
  <LuPhoneForwarded />
</Circle>
```

### Props
- `inline` - Use inline-flex instead of flex

---

## AbsoluteCenter

Center content using absolute positioning.

```tsx
import { AbsoluteCenter, Box } from "@chakra-ui/react"

// Requires parent with position: relative
<Box position="relative" h="100px">
  <AbsoluteCenter>Centered Content</AbsoluteCenter>
</Box>

// Axis control
<AbsoluteCenter axis="horizontal">Horizontal only</AbsoluteCenter>
<AbsoluteCenter axis="vertical">Vertical only</AbsoluteCenter>
<AbsoluteCenter axis="both">Both axes (default)</AbsoluteCenter>

// Overlay pattern
<AbsoluteCenter bg="bg/80" backdropFilter="blur(2px)">
  <HStack gap="3">
    <Spinner size="sm" />
    <Text>Loading...</Text>
  </HStack>
</AbsoluteCenter>
```

### Props
- `axis` - `horizontal`, `vertical`, or `both` (default)

---

## Container

Center content with max width.

```tsx
import { Container } from "@chakra-ui/react"

<Container maxW="container.lg">
  <Box>Content constrained to container width</Box>
</Container>

// Fluid container
<Container fluid>
  <Box>Full width with horizontal padding</Box>
</Container>
```

### Props
- `maxW` - Maximum width
- `fluid` - Remove max-width constraint
- `centerContent` - Center content horizontally

---

## Wrap

Flex container that wraps children.

```tsx
import { Wrap, WrapItem } from "@chakra-ui/react"

<Wrap gap="4">
  <WrapItem>
    <Tag>Tag 1</Tag>
  </WrapItem>
  <WrapItem>
    <Tag>Tag 2</Tag>
  </WrapItem>
  <WrapItem>
    <Tag>Tag 3</Tag>
  </WrapItem>
</Wrap>
```

### Props
- `gap` - Spacing between items
- `justify` - Main axis alignment
- `align` - Cross axis alignment
- `direction` - `row` or `column`

---

## Bleed

Extend content beyond container boundaries.

```tsx
import { Bleed, Container } from "@chakra-ui/react"

<Container>
  <Bleed inline="4" block="2">
    <Box>Content that bleeds outside container</Box>
  </Bleed>
</Container>
```

### Props
- `inline` - Horizontal bleed
- `block` - Vertical bleed
- `inlineStart` - Start edge bleed
- `inlineEnd` - End edge bleed

---

## Float

Float element outside normal flow.

```tsx
import { Float } from "@chakra-ui/react"

<Box position="relative">
  <Float>X</Float>
  <Box>Content with floating element</Box>
</Box>
```

### Props
- `placement` - Position of floated element
- `offset` - Offset from edge
