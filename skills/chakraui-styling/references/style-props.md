# Style Props Reference

Complete reference for Chakra UI v3 style props.

## Spacing

| Prop | Description |
|------|-------------|
| `p` | Padding all sides |
| `px` | Padding horizontal (left + right) |
| `py` | Padding vertical (top + bottom) |
| `pt`, `pb`, `pl`, `pr` | Padding top, bottom, left, right |
| `ps`, `pe` | Padding start/end (RTL-safe logical properties) |
| `m`, `mx`, `my`, `mt`, `mb`, `ml`, `mr` | Same pattern for margin |
| `ms`, `me` | Margin start/end (RTL-safe) |
| `spaceX`, `spaceY` | Spacing between child elements |

```tsx
<Box p="4" px="6" py="2" ps="4" pe="4" />
<Box m="4" mx="auto" my="2" />
<HStack spaceX="4">...</HStack>  // Gap between items
```

## Sizing

| Prop | Description |
|------|-------------|
| `w`, `width` | Width |
| `h`, `height` | Height |
| `minW`, `maxW` | Min/max width |
| `minH`, `maxH` | Min/max height |
| `boxSize` | Width = Height (sets both) |

```tsx
<Box w="100%" h="100vh" />
<Box w="full" h="full" />
<Box minW="0" maxW="container.lg" />
<Box boxSize="16" />  // 16 units (4rem)
```

### Fractional Values
```tsx
<Box w="1/2" />   // 50%
<Box w="1/3" />   // 33.333%
<Box w="2/3" />   // 66.666%
<Box w="1/4" />   // 25%
<Box w="3/4" />   // 75%
```

## Typography

```tsx
<Text
  fontSize="lg"
  fontWeight="semibold"
  fontFamily="heading"
  lineHeight="tall"
  letterSpacing="wide"
  textAlign="center"
  textTransform="uppercase"
  textDecoration="underline"
  textDecorationColor="blue.500"
  textShadow="sm"
  truncate          // Single line truncation
  lineClamp={3}     // Multi-line truncation
/>
```

## Background

```tsx
<Box
  bg="blue.500"
  bgColor="blue.500"
  bgImage="url(...)"
  bgSize="cover"
  bgPosition="center"
  bgRepeat="no-repeat"
  bgAttachment="fixed"
  bgClip="border-box"
  bgBlendMode="multiply"
/>
```

### Gradients
```tsx
<Box
  bgGradient="to-r"
  gradientFrom="red.200"
  gradientTo="pink.500"
  gradientVia="purple.200"
/>

// Text gradient
<Text
  textGradient="to-r"
  gradientFrom="blue.400"
  gradientTo="purple.500"
/>
```

## Border

### Border Radius
```tsx
<Box rounded="md" />              // All corners
<Box roundedTop="lg" />           // Top corners
<Box roundedBottom="lg" />        // Bottom corners
<Box roundedStart="md" />         // Logical (RTL-safe)
<Box roundedEnd="md" />           // Logical (RTL-safe)
<Box roundedTopLeft="xl" />       // Specific corner
<Box roundedStartStart="md" />    // Logical corner
```

### Border Width & Color
```tsx
<Box
  border="1px solid"
  borderWidth="2px"
  borderColor="gray.200"
  borderTopWidth="4px"
  borderStartWidth="4px"    // Logical property
/>
```

### Divide (Borders between children)
```tsx
<VStack divideY="1px" divideColor="gray.200" divideStyle="dashed">
  <Box>Item 1</Box>
  <Box>Item 2</Box>
</VStack>

<HStack divideX="1px" divideColor="gray.200">
  <Box>Item 1</Box>
  <Box>Item 2</Box>
</HStack>
```

## Layout

```tsx
<Box
  display="flex"
  position="relative"          // absolute, fixed, sticky
  pos="relative"               // Shorthand
  top="0"
  right="0"
  bottom="0"
  left="0"
  inset="0"                    // All sides at once
  insetStart="4"               // Logical property
  insetEnd="4"                 // Logical property
  zIndex="modal"
  overflow="hidden"
  overscrollBehavior="contain"
/>
```

## Flex & Grid

### Flex
```tsx
<Flex
  flex="1"
  flexDir="column"             // flexDirection
  flexWrap="wrap"
  flexGrow="1"
  flexShrink="0"
  flexBasis="50%"
  justifyContent="center"      // or `justify`
  alignItems="center"          // or `align`
  alignContent="center"
  alignSelf="stretch"
  gap="4"
/>
```

### Grid
```tsx
<Box
  display="grid"
  gridTemplateColumns="repeat(3, 1fr)"
  gridTemplateRows="auto"
  gridAutoFlow="row"
  gridAutoColumns="1fr"
  gridAutoRows="minmax(100px, auto)"
  gridColumn="span 2"
  gridRow="1 / 3"
  gridColumnStart="1"
  gridColumnEnd="3"
/>
```

### Alignment
```tsx
<Box
  justifyContent="center"      // Main axis
  alignItems="center"          // Cross axis
  alignContent="center"        // Multi-line
  placeContent="center"        // Both at once
  placeItems="center"
  placeSelf="center"
/>
```

## Effects

```tsx
<Box
  shadow="md"                  // boxShadow
  shadowColor="black/20"       // With opacity
  opacity="0.8"
  mixBlendMode="multiply"
/>
```

## Filters

Requires `filter="auto"` for individual filter props:

```tsx
<Box filter="blur(4px)" />
<Box filter="auto" blur="sm" />
<Box filter="auto" contrast="0.8" />
<Box filter="auto" grayscale="50%" />
<Box filter="auto" hueRotate="90deg" />
<Box filter="auto" invert="100%" />
<Box filter="auto" saturate="150%" />
<Box filter="auto" sepia="100%" />
<Box filter="auto" dropShadow="0px 4px 8px rgba(0,0,0,0.2)" />
```

### Backdrop Filters
```tsx
<Box backdropFilter="blur(8px)" />
<Box backdropFilter="auto" backdropBlur="sm" />
<Box backdropFilter="auto" backdropContrast="0.8" />
<Box backdropFilter="auto" backdropGrayscale="50%" />
<Box backdropFilter="auto" backdropOpacity="0.5" />
```

## Transforms

```tsx
<Box
  transform="rotate(45deg)"
  transformOrigin="center"
  scale="1.1"
  scaleX="1.5"
  scaleY="0.8"
  rotate="45deg"
  rotateX="180deg"
  rotateY="180deg"
  translateX="10px"
  translateY="20px"
/>
```

## Transitions & Animation

```tsx
<Box
  transition="all 0.2s"
  transitionDuration="slow"
  transitionTimingFunction="ease-in-out"
  transitionDelay="100ms"
  animation="spin 1s linear infinite"
  animationName="bounce"
  animationDuration="1s"
  animationTimingFunction="ease"
  animationDelay="0.5s"
  animationIterationCount="infinite"
  animationDirection="alternate"
  animationFillMode="forwards"
  animationPlayState="paused"
/>
```

## Interactivity

```tsx
<Box
  cursor="pointer"
  pointerEvents="none"
  userSelect="none"
  resize="none"
  accentColor="blue.500"
  caretColor="blue.500"
  touchAction="pan-y"
  scrollBehavior="smooth"
  scrollMargin="4"
  scrollPadding="4"
  scrollSnapType="x mandatory"
  willChange="transform"
/>
```

## Lists

```tsx
<Box
  listStyleType="disc"
  listStylePosition="inside"
  listStyleImage="url(...)"
/>
```

## Tables

```tsx
<Box
  borderSpacing="4"
  borderCollapse="collapse"
  captionSide="top"
/>
```

## SVG

```tsx
<Icon
  fill="blue.500"
  stroke="currentColor"
  strokeWidth="2px"
/>
```

## Position

```tsx
<Box
  position="absolute"          // or pos
  top="0"
  right="0"
  bottom="0"
  left="0"
  inset="0"                    // All sides
  insetX="4"                   // Left + Right
  insetY="4"                   // Top + Bottom
  insetStart="4"               // Logical
  insetEnd="4"                 // Logical
/>
```

## Display

```tsx
<Box display="flex" />
<Box display="grid" />
<Box display="none" />
<Box display={{ base: "none", md: "flex" }} />
<Box hideFrom="md" />          // Hide from breakpoint
<Box hideBelow="md" />         // Hide below breakpoint
```

## Aspect Ratio

```tsx
<Box aspectRatio="16/9" />
<Box aspectRatio="1" />        // Square
<Box aspectRatio="4/3" />
```

## Object Fit

```tsx
<Image objectFit="cover" objectPosition="center" />
```

## Isolation

```tsx
<Box isolation="isolate" />    // Create stacking context
```
