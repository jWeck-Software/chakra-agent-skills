# Data Display Components

## Table

Display data in tabular format.

```tsx
import { Table } from "@chakra-ui/react"

// Basic table
<Table.Root size="sm">
  <Table.Header>
    <Table.Row>
      <Table.ColumnHeader>Product</Table.ColumnHeader>
      <Table.ColumnHeader>Category</Table.ColumnHeader>
      <Table.ColumnHeader textAlign="end">Price</Table.ColumnHeader>
    </Table.Row>
  </Table.Header>
  <Table.Body>
    {items.map((item) => (
      <Table.Row key={item.id}>
        <Table.Cell>{item.name}</Table.Cell>
        <Table.Cell>{item.category}</Table.Cell>
        <Table.Cell textAlign="end">{item.price}</Table.Cell>
      </Table.Row>
    ))}
  </Table.Body>
</Table.Root>

// With footer
<Table.Root>
  <Table.Header>...</Table.Header>
  <Table.Body>...</Table.Body>
  <Table.Footer>
    <Table.Row>
      <Table.Cell>Total</Table.Cell>
      <Table.Cell></Table.Cell>
      <Table.Cell textAlign="end">$1,199.96</Table.Cell>
    </Table.Row>
  </Table.Footer>
</Table.Root>

// Sizes
<Table.Root size="sm">...</Table.Root>
<Table.Root size="md">...</Table.Root>
<Table.Root size="lg">...</Table.Root>

// Variants
<Table.Root variant="line">...</Table.Root>
<Table.Root variant="outline">...</Table.Root>

// Striped rows
<Table.Root striped>...</Table.Root>

// With caption
<Table.Root>
  <Table.Caption>Product Inventory</Table.Caption>
  <Table.Header>...</Table.Header>
  <Table.Body>...</Table.Body>
</Table.Root>
```

### Props
- `size` - `sm`, `md`, `lg`
- `variant` - `line`, `outline`
- `striped` - Add zebra-striping to rows

---

## Card

Container for grouping related content.

```tsx
import { Card, Button, Avatar, Heading } from "@chakra-ui/react"

// Basic card
<Card.Root width="320px">
  <Card.Body gap="2">
    <Avatar.Root size="lg" shape="rounded">
      <Avatar.Image src="https://picsum.photos/200/300" />
      <Avatar.Fallback name="Nue Camp" />
    </Avatar.Root>
    <Card.Title mt="2">Nue Camp</Card.Title>
    <Card.Description>
      This is the card body description.
    </Card.Description>
  </Card.Body>
  <Card.Footer justifyContent="flex-end">
    <Button variant="outline">View</Button>
    <Button>Join</Button>
  </Card.Footer>
</Card.Root>

// With header
<Card.Root>
  <Card.Header>
    <Card.Title>Sign up</Card.Title>
    <Card.Description>Fill in the form below</Card.Description>
  </Card.Header>
  <Card.Body>...</Card.Body>
  <Card.Footer>...</Card.Footer>
</Card.Root>

// Variants
<Card.Root variant="subtle">...</Card.Root>
<Card.Root variant="outline">...</Card.Root>
<Card.Root variant="elevated">...</Card.Root>

// Sizes
<Card.Root size="sm">...</Card.Root>
<Card.Root size="md">...</Card.Root>
<Card.Root size="lg">...</Card.Root>

// With form
<Card.Root maxW="sm">
  <Card.Header>
    <Card.Title>Sign up</Card.Title>
  </Card.Header>
  <Card.Body>
    <Stack gap="4" w="full">
      <Field.Root>
        <Field.Label>First Name</Field.Label>
        <Input />
      </Field.Root>
    </Stack>
  </Card.Body>
  <Card.Footer justifyContent="flex-end">
    <Button variant="outline">Cancel</Button>
    <Button variant="solid">Sign in</Button>
  </Card.Footer>
</Card.Root>
```

### Props
- `variant` - `subtle`, `outline`, `elevated`
- `size` - `sm`, `md`, `lg`

---

## Badge

Small label for status or categorization.

```tsx
import { Badge } from "@chakra-ui/react"

// Basic badges
<Badge>Default</Badge>
<Badge colorPalette="green">Success</Badge>
<Badge colorPalette="red">Removed</Badge>
<Badge colorPalette="purple">New</Badge>

// Variants
<Badge variant="outline">Outline</Badge>
<Badge variant="solid">Solid</Badge>
<Badge variant="subtle">Subtle</Badge>
<Badge variant="surface">Surface</Badge>

// Sizes
<Badge size="xs">Extra Small</Badge>
<Badge size="sm">Small</Badge>
<Badge size="md">Medium</Badge>
<Badge size="lg">Large</Badge>

// With icon
<Badge variant="solid" colorPalette="blue">
  <HiStar /> New
</Badge>

// Status indicator
<Badge colorPalette={status === 'success' ? 'green' : status === 'error' ? 'red' : 'yellow'}>
  {status}
</Badge>
```

### Props
- `variant` - `solid`, `subtle`, `outline`, `surface`, `plain`
- `size` - `xs`, `sm`, `md`, `lg`
- `colorPalette` - Color theme

---

## Tag

Labels for categories or keywords.

```tsx
import { Tag } from "@chakra-ui/react"

// Basic tag
<Tag.Root>
  <Tag.Label>Chakra UI</Tag.Label>
  <Tag.CloseTrigger />
</Tag.Root>

// Variants
<Tag.Root variant="subtle">
  <Tag.Label>Subtle</Tag.Label>
</Tag.Root>

<Tag.Root variant="outline">
  <Tag.Label>Outline</Tag.Label>
</Tag.Root>

<Tag.Root variant="solid">
  <Tag.Label>Solid</Tag.Label>
</Tag.Root>

// Sizes
<Tag.Root size="sm">
  <Tag.Label>Small</Tag.Label>
</Tag.Root>

<Tag.Root size="md">
  <Tag.Label>Medium</Tag.Label>
</Tag.Root>

<Tag.Root size="lg">
  <Tag.Label>Large</Tag.Label>
</Tag.Root>

// Colors
<Tag.Root colorPalette="blue">
  <Tag.Label>Blue</Tag.Label>
</Tag.Root>

// With icon
<Tag.Root>
  <Tag.StartIcon><LuPlus /></Tag.StartIcon>
  <Tag.Label>With Icon</Tag.Label>
</Tag.Root>

// Closable
<Tag.Root>
  <Tag.Label>Removable</Tag.Label>
  <Tag.CloseTrigger />
</Tag.Root>
```

### Props
- `variant` - `subtle`, `outline`, `solid`, `surface`
- `size` - `sm`, `md`, `lg`
- `colorPalette` - Color theme

---

## Avatar

User avatar with image and fallback.

```tsx
import { Avatar } from "@chakra-ui/react"

// Basic avatar
<Avatar.Root>
  <Avatar.Image src="https://example.com/avatar.jpg" />
  <Avatar.Fallback name="John Doe" />
</Avatar.Root>

// With name fallback (generates initials)
<Avatar.Root>
  <Avatar.Fallback name="John Doe" />
</Avatar.Root>

// Sizes
<Avatar.Root size="2xs">...</Avatar.Root>
<Avatar.Root size="xs">...</Avatar.Root>
<Avatar.Root size="sm">...</Avatar.Root>
<Avatar.Root size="md">...</Avatar.Root>
<Avatar.Root size="lg">...</Avatar.Root>
<Avatar.Root size="xl">...</Avatar.Root>
<Avatar.Root size="2xl">...</Avatar.Root>

// Shapes
<Avatar.Root shape="full">...</Avatar.Root>  // Circular
<Avatar.Root shape="rounded">...</Avatar.Root>  // Rounded corners

// Avatar group
<Avatar.Group>
  <Avatar.Root>
    <Avatar.Image src="user1.jpg" />
    <Avatar.Fallback name="User 1" />
  </Avatar.Root>
  <Avatar.Root>
    <Avatar.Image src="user2.jpg" />
    <Avatar.Fallback name="User 2" />
  </Avatar.Root>
  <Avatar.Root>
    <Avatar.Fallback>+3</Avatar.Fallback>
  </Avatar.Root>
</Avatar.Group>
```

### Props
- `size` - `2xs`, `xs`, `sm`, `md`, `lg`, `xl`, `2xl`
- `shape` - `full` (circular), `rounded`
- `name` - Name for fallback initials

---

## Stat

Display statistics or metrics.

```tsx
import { Stat } from "@chakra-ui/react"

// Basic stat
<Stat.Root>
  <Stat.Label>Unique visitors</Stat.Label>
  <Stat.ValueText>192.1k</Stat.ValueText>
</Stat.Root>

// With helper text
<Stat.Root>
  <Stat.Label>Converted</Stat.Label>
  <Stat.ValueText>84%</Stat.ValueText>
  <Stat.HelpText>+12% from last month</Stat.HelpText>
</Stat.Root>

// With trend indicator
<Stat.Root>
  <Stat.Label>Revenue</Stat.Label>
  <Stat.ValueText>$45,000</Stat.ValueText>
  <Stat.HelpText>
    <Stat.UpIndicator />
    +23%
  </Stat.HelpText>
</Stat.Root>

<Stat.Root>
  <Stat.Label>Expenses</Stat.Label>
  <Stat.ValueText>$12,000</Stat.ValueText>
  <Stat.HelpText>
    <Stat.DownIndicator />
    -5%
  </Stat.HelpText>
</Stat.Root>

// Sizes
<Stat.Root size="sm">...</Stat.Root>
<Stat.Root size="md">...</Stat.Root>
<Stat.Root size="lg">...</Stat.Root>
```

### Props
- `size` - `sm`, `md`, `lg`

---

## Status

Status indicator dot with label.

```tsx
import { Status } from "@chakra-ui/react"

// Basic status
<Status.Root>
  <Status.Indicator />
  <Status.Label>Online</Status.Label>
</Status.Root>

// Colors
<Status.Root colorPalette="green">
  <Status.Indicator />
  <Status.Label>Active</Status.Label>
</Status.Root>

<Status.Root colorPalette="red">
  <Status.Indicator />
  <Status.Label>Error</Status.Label>
</Status.Root>

<Status.Root colorPalette="yellow">
  <Status.Indicator />
  <Status.Label>Warning</Status.Label>
</Status.Root>

<Status.Root colorPalette="gray">
  <Status.Indicator />
  <Status.Label>Offline</Status.Label>
</Status.Root>

// Sizes
<Status.Root size="sm">...</Status.Root>
<Status.Root size="md">...</Status.Root>
<Status.Root size="lg">...</Status.Root>
```

### Props
- `colorPalette` - `green`, `red`, `yellow`, `gray`, `blue`
- `size` - `sm`, `md`, `lg`

---

## Progress

Progress bar indicator.

```tsx
import { Progress } from "@chakra-ui/react"

// Basic progress
<Progress.Root defaultValue={40}>
  <Progress.Track>
    <Progress.Range />
  </Progress.Track>
</Progress.Root>

// With label
<Progress.Root defaultValue={60}>
  <Progress.Label>Upload progress</Progress.Label>
  <Progress.Track>
    <Progress.Range />
  </Progress.Track>
  <Progress.ValueText>60%</Progress.ValueText>
</Progress.Root>

// Sizes
<Progress.Root size="xs">...</Progress.Root>
<Progress.Root size="sm">...</Progress.Root>
<Progress.Root size="md">...</Progress.Root>
<Progress.Root size="lg">...</Progress.Root>

// Colors
<Progress.Root colorPalette="green">...</Progress.Root>
<Progress.Root colorPalette="blue">...</Progress.Root>

// Indeterminate (loading)
<Progress.Root indeterminate>
  <Progress.Track>
    <Progress.Range />
  </Progress.Track>
</Progress.Root>

// With value text
<Progress.Root defaultValue={75}>
  <Progress.Track>
    <Progress.Range />
  </Progress.Track>
  <Progress.ValueText />
</Progress.Root>
```

### Props
- `size` - `xs`, `sm`, `md`, `lg`
- `colorPalette` - Color theme
- `defaultValue` - Initial value (0-100)
- `value` - Controlled value
- `indeterminate` - Show indeterminate state
- `min` - Minimum value (default: 0)
- `max` - Maximum value (default: 100)

---

## ProgressCircle

Circular progress indicator.

```tsx
import { ProgressCircle } from "@chakra-ui/react"

// Basic circle
<ProgressCircle.Root value={75}>
  <ProgressCircle.Circle>
    <ProgressCircle.Track />
    <ProgressCircle.Range />
  </ProgressCircle.Circle>
  <ProgressCircle.ValueText />
</ProgressCircle.Root>

// Without value text
<ProgressCircle.Root value={50}>
  <ProgressCircle.Circle>
    <ProgressCircle.Track />
    <ProgressCircle.Range />
  </ProgressCircle.Circle>
</ProgressCircle.Root>

// Sizes
<ProgressCircle.Root size="sm">...</ProgressCircle.Root>
<ProgressCircle.Root size="md">...</ProgressCircle.Root>
<ProgressCircle.Root size="lg">...</ProgressCircle.Root>

// Colors
<ProgressCircle.Root colorPalette="green">...</ProgressCircle.Root>
```

---

## List

Display list of items.

```tsx
import { List } from "@chakra-ui/react"

// Basic list
<List.Root>
  <List.Item>Item 1</List.Item>
  <List.Item>Item 2</List.Item>
  <List.Item>Item 3</List.Item>
</List.Root>

// With icon
<List.Root>
  <List.Item>
    <List.Indicator asChild>
      <LuCheckCircle />
    </List.Indicator>
    Feature 1
  </List.Item>
  <List.Item>
    <List.Indicator asChild>
      <LuCheckCircle />
    </List.Indicator>
    Feature 2
  </List.Item>
</List.Root>

// Unordered (bullets)
<List.Root variant="unordered">...</List.Root>

// Ordered (numbers)
<List.Root variant="ordered">...</List.Root>

// Sizes
<List.Root size="sm">...</List.Root>
<List.Root size="md">...</List.Root>
<List.Root size="lg">...</List.Root>
```

---

## DataList

Key-value pair display.

```tsx
import { DataList } from "@chakra-ui/react"

<DataList.Root>
  <DataList.Item>
    <DataList.ItemLabel>Name</DataList.ItemLabel>
    <DataList.ItemValue>John Doe</DataList.ItemValue>
  </DataList.Item>
  <DataList.Item>
    <DataList.ItemLabel>Email</DataList.ItemLabel>
    <DataList.ItemValue>john@example.com</DataList.ItemValue>
  </DataList.Item>
</DataList.Root>

// Orientation
<DataList.Root orientation="horizontal">
  ...
</DataList.Root>
```
