# Typography Components

## Text

The primary component for rendering text content.

```tsx
import { Text } from "@chakra-ui/react"

// Basic usage
<Text>This is the text component</Text>

// Sizes (using textStyle)
<Text textStyle="xs">Extra small</Text>
<Text textStyle="sm">Small</Text>
<Text textStyle="md">Medium</Text>
<Text textStyle="lg">Large</Text>
<Text textStyle="xl">Extra large</Text>
<Text textStyle="2xl">2X Large</Text>
<Text textStyle="3xl">3X Large</Text>
<Text textStyle="4xl">4X Large</Text>
<Text textStyle="5xl">5X Large</Text>
<Text textStyle="6xl">6X Large</Text>
<Text textStyle="7xl">7X Large</Text>

// Font weights
<Text fontWeight="light">Light weight</Text>
<Text fontWeight="normal">Normal weight</Text>
<Text fontWeight="medium">Medium weight</Text>
<Text fontWeight="semibold">Semibold weight</Text>
<Text fontWeight="bold">Bold weight</Text>

// Truncate single line
<Text truncate>Lorem ipsum dolor sit amet...</Text>

// Line clamp (multi-line truncation)
<Text lineClamp="2">
  Lorem ipsum dolor sit amet, consectetur adipiscing elit.
  Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
</Text>

// Colors
<Text color="fg.muted">Muted text</Text>
<Text color="blue.500">Blue text</Text>
```

### Props
- `textStyle` - Text size preset (`xs` to `7xl`)
- `fontWeight` - Font weight (`light`, `normal`, `medium`, `semibold`, `bold`)
- `truncate` - Truncate to single line with ellipsis
- `lineClamp` - Truncate to N lines
- All style props apply

---

## Heading

Semantic heading component (h1-h6).

```tsx
import { Heading } from "@chakra-ui/react"

// Basic usage
<Heading>The quick brown fox</Heading>

// Sizes
<Heading size="sm">Small Heading</Heading>
<Heading size="md">Medium Heading</Heading>
<Heading size="lg">Large Heading</Heading>
<Heading size="xl">XL Heading</Heading>
<Heading size="2xl">2XL Heading</Heading>
<Heading size="3xl">3XL Heading</Heading>
<Heading size="4xl">4XL Heading</Heading>
<Heading size="5xl">5XL Heading</Heading>
<Heading size="6xl">6XL Heading</Heading>

// As different heading level
<Heading as="h1">Level 1</Heading>
<Heading as="h2">Level 2</Heading>
<Heading as="h3">Level 3</Heading>

// Font weights
<Heading fontWeight="normal">Normal</Heading>
<Heading fontWeight="medium">Medium</Heading>
<Heading fontWeight="semibold">Semibold</Heading>
<Heading fontWeight="bold">Bold</Heading>

// With Highlight
<Heading size="3xl" letterSpacing="tight">
  <Highlight query="with speed" styles={{ color: "teal.600" }}>
    Create accessible React apps with speed
  </Highlight>
</Heading>
```

### Props
- `size` - Heading size (`sm` to `6xl`)
- `as` - HTML element (`h1`, `h2`, `h3`, `h4`, `h5`, `h6`)
- All style props apply

---

## Highlight

Highlight specific text within a string.

```tsx
import { Highlight, Heading, Text } from "@chakra-ui/react"

// Basic highlight
<Highlight
  query="spotlight"
  styles={{ px: "0.5", bg: "orange.subtle", color: "orange.fg" }}
>
  With the Highlight component, you can spotlight words.
</Highlight>

// Multiple queries
<Highlight
  query={["spotlight", "emphasize", "accentuate"]}
  styles={{ px: "0.5", bg: "teal.muted" }}
>
  With the Highlight component, you can spotlight, emphasize and accentuate words.
</Highlight>

// Custom styles
<Highlight query="component" styles={{ fontWeight: "semibold" }}>
  With the Highlight component, you can spotlight words.
</Highlight>

// Case insensitive search
<Highlight ignoreCase query="spot" styles={{ fontWeight: "semibold" }}>
  Spotlight bulb
</Highlight>
```

### Props
- `query` - String or array of strings to highlight
- `styles` - Styles to apply to matched text
- `ignoreCase` - Case insensitive matching
- `matchAll` - Match all instances

---

## Em

Semantic emphasis element (renders as `<em>`).

```tsx
import { Em } from "@chakra-ui/react"

<Text>
  This is <Em>emphasized</Em> text.
</Text>
```

---

## Mark

Semantic mark element for highlighted text.

```tsx
import { Mark } from "@chakra-ui/react"

<Text>
  This is <Mark bg="yellow.100">highlighted</Mark> text.
</Text>

// Custom styled mark
<Mark
  css={{
    fontStyle: "italic",
    color: "red.500",
    position: "relative",
  }}
>
  Highlighted text
</Mark>
```

---

## Blockquote

Quote block with styling.

```tsx
import { Blockquote, Text } from "@chakra-ui/react"

<Blockquote>
  <Text>The best way to predict the future is to create it.</Text>
  <cite>— Peter Drucker</cite>
</Blockquote>

// With icon
<Blockquote icon={<LuQuote />}>
  <Text>Quote text here</Text>
</Blockquote>
```

### Props
- `icon` - Optional quote icon
- `cite` - Citation source

---

## Code

Inline code snippet.

```tsx
import { Code } from "@chakra-ui/react"

<Text>
  Use the <Code>useState</Code> hook for state management.
</Text>

// Colored code
<Code colorPalette="purple">npm install</Code>
<Code colorPalette="green">git commit</Code>
```

### Props
- `colorPalette` - Color theme for the code

---

## CodeBlock

Multi-line code block with syntax highlighting support.

```tsx
import { CodeBlock } from "@chakra-ui/react"

<CodeBlock code="const hello = 'world'" language="javascript" />

// With title
<CodeBlock
  code="npm install @chakra-ui/react"
  language="bash"
  title="Install Chakra UI"
/>

// Without copy button
<CodeBlock code="..." showCopyButton={false} />
```

### Props
- `code` - Code content
- `language` - Programming language for syntax highlighting
- `title` - Optional title
- `showCopyButton` - Show/hide copy button (default: true)

---

## Prose

Rich text content wrapper with sensible typography defaults.

```tsx
import { Prose } from "@chakra-ui/react"

<Prose>
  <h1>Heading</h1>
  <p>Paragraph with <strong>bold</strong> and <em>italic</em> text.</p>
  <ul>
    <li>List item 1</li>
    <li>List item 2</li>
  </ul>
  <pre><code>Code block</code></pre>
</Prose>

// Custom sizing
<Prose size="sm">...</Prose>
<Prose size="md">...</Prose>
<Prose size="lg">...</Prose>
```

### Props
- `size` - Prose size (`sm`, `md`, `lg`)

---

## Span

Inline text wrapper.

```tsx
import { Span } from "@chakra-ui/react"

<Text>
  This is <Span color="red.500">red</Span> text.
</Text>
```

---

## Strong

Semantic strong element for important text.

```tsx
import { Strong } from "@chakra-ui/react"

<Text>
  This is <Strong>important</Strong> text.
</Text>
```
