# Feedback Components

## Alert

Display contextual feedback messages.

```tsx
import { Alert } from "@chakra-ui/react"

// Basic alert
<Alert.Root>
  <Alert.Indicator />
  <Alert.Title>This is an alert</Alert.Title>
</Alert.Root>

// With description
<Alert.Root status="error">
  <Alert.Indicator />
  <Alert.Content>
    <Alert.Title>Invalid Fields</Alert.Title>
    <Alert.Description>
      Your form has some errors. Please fix them and try again.
    </Alert.Description>
  </Alert.Content>
</Alert.Root>

// Status types
<Alert.Root status="error">
  <Alert.Indicator />
  <Alert.Title>Error alert</Alert.Title>
</Alert.Root>

<Alert.Root status="success">
  <Alert.Indicator />
  <Alert.Title>Success alert</Alert.Title>
</Alert.Root>

<Alert.Root status="warning">
  <Alert.Indicator />
  <Alert.Title>Warning alert</Alert.Title>
</Alert.Root>

<Alert.Root status="info">
  <Alert.Indicator />
  <Alert.Title>Info alert</Alert.Title>
</Alert.Root>

// Variants
<Alert.Root variant="subtle">...</Alert.Root>
<Alert.Root variant="solid">...</Alert.Root>
<Alert.Root variant="outline">...</Alert.Root>
<Alert.Root variant="surface">...</Alert.Root>

// With close button
<Alert.Root>
  <Alert.Indicator />
  <Alert.Content>
    <Alert.Title>Success!</Alert.Title>
    <Alert.Description>Your application has been received.</Alert.Description>
  </Alert.Content>
  <CloseButton pos="relative" top="-2" insetEnd="-2" />
</Alert.Root>

// With spinner (loading state)
<Alert.Root borderStartWidth="3px" borderStartColor="colorPalette.600">
  <Alert.Indicator>
    <Spinner size="sm" />
  </Alert.Indicator>
  <Alert.Title>We are loading something</Alert.Title>
</Alert.Root>

// With custom icon
<Alert.Root status="success">
  <Alert.Indicator>
    <LuCheckCircle />
  </Alert.Indicator>
  <Alert.Title>Operation successful</Alert.Title>
</Alert.Root>
```

### Props
- `status` - `error`, `success`, `warning`, `info`
- `variant` - `subtle`, `solid`, `outline`, `surface`
- `title` - Alert title (optional)

---

## Spinner

Loading spinner indicator.

```tsx
import { Spinner } from "@chakra-ui/react"

// Basic spinner
<Spinner />

// Sizes
<Spinner size="xs" />
<Spinner size="sm" />
<Spinner size="md" />
<Spinner size="lg" />
<Spinner size="xl" />

// Colors
<Spinner colorPalette="blue" />
<Spinner colorPalette="teal" />
<Spinner colorPalette="purple" />

// Custom color
<Spinner color="teal.500" size="lg" />

// Custom track color
<Spinner
  color="red.500"
  css={{ "--spinner-track-color": "colors.gray.200" }}
/>

// Custom speed
<Spinner color="blue.500" animationDuration="0.8s" />

// With label (accessibility)
<Spinner aria-label="Loading..." />

// In button
<Button loading>
  <Spinner size="sm" />
  Loading
</Button>

// Centered overlay
<Center position="absolute" inset="0">
  <Spinner size="xl" />
</Center>
```

### Props
- `size` - `xs`, `sm`, `md`, `lg`, `xl`
- `colorPalette` - Color theme
- `color` - Custom color
- `animationDuration` - Spin speed (default: "0.75s")

---

## Skeleton

Placeholder for loading content.

```tsx
import { Skeleton, SkeletonCircle, SkeletonText } from "@chakra-ui/react"

// Basic skeleton
<Skeleton height="20px" />

// Circle skeleton (for avatars)
<SkeletonCircle size="12" />

// Text skeleton
<SkeletonText noOfLines={3} gap="4" />

// Feed skeleton pattern
<Stack gap="6" maxW="xs">
  <HStack width="full">
    <SkeletonCircle size="10" />
    <SkeletonText noOfLines={2} />
  </HStack>
  <Skeleton height="200px" />
</Stack>

// Variants
<Skeleton variant="pulse" height="5" />  // Default
<Skeleton variant="shine" height="5" />
<Skeleton variant="none" height="5" />

// With children (conditional loading)
<Skeleton loading={isLoading}>
  <Badge>Select</Badge>
</Skeleton>

// Toggle loading state
const [loading, setLoading] = useState(true)
<Skeleton height="6" loading={loading}>
  <Text>Content loaded</Text>
</Skeleton>

// Custom colors
<Skeleton
  variant="shine"
  width="full"
  height="5"
  css={{
    "--start-color": "colors.pink.500",
    "--end-color": "colors.orange.500",
  }}
/>

// Card skeleton
<Card.Root>
  <Card.Body>
    <SkeletonCircle size="16" mb="4" />
    <Skeleton height="6" mb="2" />
    <SkeletonText noOfLines={3} />
  </Card.Body>
</Card.Root>
```

### Props
- `variant` - `pulse`, `shine`, `none`
- `loading` - Show skeleton state (default: true)
- `colorPalette` - Color theme (default: gray)
- `height` - Skeleton height
- `width` - Skeleton width
- `isLoaded` - Alias for `loading={false}`

---

## Collapsible

Expandable/collapsible content container.

```tsx
import { Collapsible } from "@chakra-ui/react"

// Basic collapsible
<Collapsible.Root>
  <Collapsible.Trigger>
    <Button>Toggle Content</Button>
  </Collapsible.Trigger>
  <Collapsible.Content>
    <Box p="4" bg="bg.muted">
      This content can be expanded or collapsed.
    </Box>
  </Collapsible.Content>
</Collapsible.Root>

// Controlled
const [open, setOpen] = useState(false)
<Collapsible.Root open={open} onOpenChange={(e) => setOpen(e.open)}>
  <Collapsible.Trigger>
    <Button>{open ? "Collapse" : "Expand"}</Button>
  </Collapsible.Trigger>
  <Collapsible.Content>
    Content here
  </Collapsible.Content>
</Collapsible.Root>

// Default open
<Collapsible.Root defaultOpen>
  ...
</Collapsible.Root>

// Disabled
<Collapsible.Root disabled>
  ...
</Collapsible.Root>

// With animation
<Collapsible.Root>
  <Collapsible.Trigger>
    <HStack justify="space-between">
      <Text>Click to expand</Text>
      <Icon>
        <LuChevronDown />
      </Icon>
    </HStack>
  </Collapsible.Trigger>
  <Collapsible.Content>
    <Box p="4">
      Animated content
    </Box>
  </Collapsible.Content>
</Collapsible.Root>

// Nested collapsibles
<Collapsible.Root>
  <Collapsible.Trigger>Parent</Collapsible.Trigger>
  <Collapsible.Content>
    <Collapsible.Root>
      <Collapsible.Trigger>Child</Collapsible.Trigger>
      <Collapsible.Content>
        Nested content
      </Collapsible.Content>
    </Collapsible.Root>
  </Collapsible.Content>
</Collapsible.Root>
```

### Props
- `defaultOpen` - Initial open state
- `open` - Controlled open state
- `onOpenChange` - Open state change callback
- `disabled` - Disable toggle

---

## EmptyState

Display when there's no content.

```tsx
import { EmptyState } from "@chakra-ui/react"

// Basic empty state
<EmptyState.Root>
  <EmptyState.Content>
    <EmptyState.Indicator>
      <LuInbox />
    </EmptyState.Indicator>
    <EmptyState.Title>No items found</EmptyState.Title>
    <EmptyState.Description>
      Try adjusting your search or filters
    </EmptyState.Description>
  </EmptyState.Content>
</EmptyState.Root>

// With action
<EmptyState.Root>
  <EmptyState.Content>
    <EmptyState.Indicator>
      <LuFileX />
    </EmptyState.Indicator>
    <EmptyState.Title>No documents</EmptyState.Title>
    <EmptyState.Description>
      Upload your first document to get started
    </EmptyState.Description>
    <Button mt="4">Upload Document</Button>
  </EmptyState.Content>
</EmptyState.Root>

// Sizes
<EmptyState.Root size="sm">...</EmptyState.Root>
<EmptyState.Root size="md">...</EmptyState.Root>
<EmptyState.Root size="lg">...</EmptyState.Root>
```

---

## Loading Spinner (Custom)

For custom loading states, use the Spinner with layout components:

```tsx
import { Spinner, Center, VStack, Text } from "@chakra-ui/react"

// Full page loading
<Center h="100vh">
  <VStack gap="4">
    <Spinner size="xl" colorPalette="blue" />
    <Text color="fg.muted">Loading...</Text>
  </VStack>
</Center>

// Inline loading
<HStack gap="2">
  <Spinner size="sm" />
  <Text>Saving changes...</Text>
</HStack>

// Button loading state
<Button loading loadingText="Submitting">
  Submit
</Button>

// Overlay loading
<Box position="relative" minH="200px">
  {isLoading && (
    <AbsoluteCenter bg="bg/80" backdropFilter="blur(2px)" rounded="md" p="4">
      <HStack gap="3">
        <Spinner size="sm" />
        <Text>Loading...</Text>
      </HStack>
    </AbsoluteCenter>
  )}
  <Content opacity={isLoading ? 0.5 : 1}>
    ...
  </Content>
</Box>
```
