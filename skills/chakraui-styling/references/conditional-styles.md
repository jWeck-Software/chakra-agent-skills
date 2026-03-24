# Conditional Styles

## Pseudo Classes

### Hover, Active, Focus, Disabled
```tsx
<Button
  _hover={{ bg: "blue.600", transform: "scale(1.02)" }}
  _active={{ bg: "blue.700" }}
  _focus={{ ring: "2px", ringColor: "blue.300" }}
  _disabled={{ opacity: "0.5", cursor: "not-allowed" }}
>
```

### First, Last, Odd, Even
```tsx
<VStack>
  {items.map((item) => (
    <Box
      key={item}
      _first={{ pt: "0" }}
      _last={{ borderBottom: "none" }}
      _even={{ bg: "gray.50" }}
      _odd={{ bg: "white" }}
    >
      {item}
    </Box>
  ))}
</VStack>
```

### Nested Conditions
```tsx
// Nested conditions for complex selectors
<Box bg={{ base: "red.500", _hover: { _focus: "red.700" } }}>
  Hover & Focus me
</Box>
```

## Pseudo Elements

### Before and After
```tsx
<Box
  _before={{
    content: '""',
    position: "absolute",
    inset: "0",
    bg: "red.500"
  }}
  _after={{
    content: '"🎉"'
  }}
/>
```

### Placeholder
```tsx
<Input
  placeholder="Enter your name"
  _placeholder={{ color: "gray.500" }}
/>
```

### File Input Button
```tsx
<chakra.input
  type="file"
  _file={{ bg: "gray.500", px: "4", py: "2", marginEnd: "3" }}
/>
```

### Marker (List markers)
```tsx
<Box _marker={{ color: "blue.500" }}>
  List item
</Box>
```

## Dark Mode

```tsx
// Inline dark mode
<Box
  bg="white"
  color="gray.900"
  _dark={{ bg: "gray.800", color: "gray.100" }}
>

// Nested in value
<Box bg={{ base: "white", _dark: "gray.800" }}>
```

### Force Dark Mode
```tsx
// Force dark mode on element
<Box bg="black" className="dark">
  <Box bg="bg.subtle">Always dark</Box>
</Box>

// Force light mode
<Box bg="white" className="light">
  <Box bg="bg.subtle">Always light</Box>
</Box>
```

## Group Selectors

Style children based on parent state:

```tsx
<Box className="group">
  <Box _groupHover={{ opacity: 1 }} opacity="0.5">
    Visible on parent hover
  </Box>
  <Box _groupFocus={{ bg: "blue.100" }}>
    Styled on parent focus
  </Box>
  <Box _groupActive={{ color: "red.500" }}>
    Styled on parent active
  </Box>
  <Box _groupDisabled={{ opacity: 0.5 }}>
    Styled when parent disabled
  </Box>
</Box>
```

## Peer Selectors

Style siblings based on sibling state (peer must be a previous sibling):

```tsx
<Box>
  <p className="peer">Hover me</p>
  <Box _peerHover={{ bg: "red.500" }}>
    I'll change my bg
  </Box>
</Box>
```

## Media Queries

### Motion Preference
```tsx
<Box _motionSafe={{ transition: "all 0.3s" }}>
  Animated only when user allows motion
</Box>
<Box _motionReduce={{ transition: "none" }}>
  No animation when user prefers reduced motion
</Box>
```

### Color Scheme (OS Level)
```tsx
<Box bg={{ base: "white", _osDark: "black" }}>
  Responds to system color scheme
</Box>
```

### Color Contrast
```tsx
<Box bg={{ base: "white", _highContrast: "black" }}>
  Responds to contrast preference
</Box>
```

### Orientation
```tsx
<Box pb="4" _portrait={{ pb: "8" }} _landscape={{ pb: "2" }}>
  Responds to device orientation
</Box>
```

## Data Attributes

### State-based
```tsx
<Box data-loading _loading={{ bg: "gray.500" }}>
  Loading state
</Box>

<Box data-active _active={{ bg: "green.500" }}>
  Active state
</Box>

<Box data-disabled _disabled={{ opacity: 0.5 }}>
  Disabled state
</Box>

<Box data-invalid _invalid={{ borderColor: "red.500" }}>
  Invalid state
</Box>

<Box data-valid _valid={{ borderColor: "green.500" }}>
  Valid state
</Box>
```

### LTR/RTL
```tsx
<div dir="ltr">
  <Box _ltr={{ ml: "3" }} _rtl={{ mr: "3" }}>
    Direction-aware spacing
  </Box>
</div>
```

### Orientation
```tsx
<Box
  data-orientation="horizontal"
  _horizontal={{ bg: "red.500" }}
  _vertical={{ bg: "blue.500" }}
>
  Orientation-aware styling
</Box>
```

### Open/Closed State
```tsx
<Box
  data-state="open"
  _open={{ bg: "blue.100" }}
  _closed={{ bg: "gray.100" }}
>
  State-aware styling
</Box>
```

## ARIA Attributes

```tsx
<Box aria-expanded="true" _expanded={{ bg: "gray.500" }}>
  Expanded state
</Box>

<Box aria-selected="true" _selected={{ bg: "blue.500" }}>
  Selected state
</Box>
```

## At-Rules

### Container Queries
```tsx
<Box
  css={{
    "@container (min-width: 10px)": {
      color: "green.300",
    },
  }}
>
  Container query
</Box>
```

### Media Queries (Custom)
```tsx
<Box
  css={{
    "@media (min-width: 768px)": {
      fontSize: "24px",
    },
  }}
>
  Custom media query
</Box>
```

### Supports
```tsx
<Box
  css={{
    "@supports (backdrop-filter: blur(8px))": {
      backdropFilter: "blur(8px)",
    },
  }}
>
  Feature detection
</Box>
```

## Arbitrary Selectors

```tsx
// Custom data attribute selector
<Box css={{ "&[data-state=closed]": { color: "red.300" } }} />

// Child selector
<Box css={{ "& > *": { margin: "2" } }} />

// Nested descendant
<Box css={{ "& .nested-class": { color: "blue.500" } }} />
```

## CSS Variables

### Basic Usage
```tsx
<Box css={{ "--font-size": "18px" }}>
  <h3 style={{ fontSize: "calc(var(--font-size) * 2)" }}>Hello</h3>
</Box>
```

### Access Tokens
```tsx
<Box css={{ "--color": "colors.red.500" }}>
  <p style={{ color: "var(--color)" }}>Hello</p>
</Box>
```

### Responsive CSS Variables
```tsx
<Box css={{ "--font-size": { base: "18px", lg: "24px" } }}>
  Responsive variable
</Box>
```

### With Opacity Modifier
```tsx
<Box css={{ "--color": "{colors.red.500/40}" }}>
  <p style={{ color: "var(--color)" }}>Semi-transparent</p>
</Box>
```

### Virtual Color in Variables
```tsx
<Box colorPalette="blue" css={{ "--color": "colors.colorPalette.400" }}>
  <p style={{ color: "var(--color)" }}>Theme-aware variable</p>
</Box>
```

## Focus Ring

```tsx
// Focus ring styles
<chakra.button px="4" py="2" focusRing="outside">
  Click me
</chakra.button>

// Focus visible (keyboard only)
<chakra.button px="4" py="2" focusVisibleRing="outside">
  Click me
</chakra.button>

// Customization
<Button focusRingColor="red.500">Click me</Button>
<Button focusRingWidth="2px">Click me</Button>
<Button focusRingStyle="dashed">Click me</Button>
```

### Focus Ring Values
- `"outside"` - Ring outside the element
- `"inside"` - Ring inside the element
- `"mixed"` - Combination of inside and outside
