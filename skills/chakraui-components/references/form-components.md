# Form Components

## Input

Text input field component.

```tsx
import { Input, InputGroup, Field } from "@chakra-ui/react"

// Basic input
<Input placeholder="Enter your email" />

// Variants
<Input variant="subtle" placeholder="Subtle" />
<Input variant="outline" placeholder="Outline" />
<Input variant="flushed" placeholder="Flushed" />

// Sizes
<Input size="xs" placeholder="Extra small" />
<Input size="sm" placeholder="Small" />
<Input size="md" placeholder="Medium" />
<Input size="lg" placeholder="Large" />

// With field wrapper
<Field.Root required>
  <Field.Label>
    Email <Field.RequiredIndicator />
  </Field.Label>
  <Input placeholder="me@example.com" />
  <Field.HelperText>We'll never share your email.</Field.HelperText>
</Field.Root>

// With error
<Field.Root invalid>
  <Field.Label>Email</Field.Label>
  <Input placeholder="Enter your email" />
  <Field.ErrorText>This field is required</Field.ErrorText>
</Field.Root>

// With start icon
<InputGroup startElement={<LuUser />}>
  <Input placeholder="Username" />
</InputGroup>

// With end icon
<InputGroup endElement={<LuSearch />}>
  <Input placeholder="Search" />
</InputGroup>

// With prefix text
<InputGroup startElement="https://" startElementProps={{ color: "fg.muted" }}>
  <Input ps="7ch" placeholder="yoursite.com" />
</InputGroup>

// Password input
<InputGroup>
  <Input type="password" placeholder="Password" />
</InputGroup>

// Number input
<Input type="number" placeholder="0" />
```

### Props
- `variant` - `subtle`, `outline`, `flushed`
- `size` - `xs`, `sm`, `md`, `lg`
- `type` - Input type (text, password, email, number, etc.)
- `placeholder` - Placeholder text
- `disabled` - Disable input
- `invalid` - Mark as invalid

---

## Field

Form field wrapper with label, helper text, and error handling.

```tsx
import { Field, Input, Textarea, NativeSelect } from "@chakra-ui/react"

// Basic field
<Field.Root>
  <Field.Label>Email</Field.Label>
  <Input placeholder="me@example.com" />
</Field.Root>

// Required field
<Field.Root required>
  <Field.Label>
    Email <Field.RequiredIndicator />
  </Field.Label>
  <Input placeholder="me@example.com" />
</Field.Root>

// With helper text
<Field.Root>
  <Field.Label>Email</Field.Label>
  <Input placeholder="me@example.com" />
  <Field.HelperText>We'll never share your email.</Field.HelperText>
</Field.Root>

// With error
<Field.Root invalid>
  <Field.Label>Email</Field.Label>
  <Input placeholder="me@example.com" />
  <Field.ErrorText>This field is required</Field.ErrorText>
</Field.Root>

// With error icon
<Field.Root invalid>
  <Field.Label>Email</Field.Label>
  <Input placeholder="me@example.com" />
  <Field.ErrorText width="full">
    <Field.ErrorIcon />
    This is an error text
  </Field.ErrorText>
</Field.Root>

// Horizontal layout
<Field.Root orientation="horizontal">
  <Field.Label>Name</Field.Label>
  <Input placeholder="John Doe" flex="1" />
</Field.Root>

// Disabled
<Field.Root disabled>
  <Field.Label>Email</Field.Label>
  <Input placeholder="me@example.com" />
</Field.Root>

// With optional badge
<Field.Root>
  <Field.Label>
    Email
    <Field.RequiredIndicator
      fallback={<Badge size="xs" variant="surface">Optional</Badge>}
    />
  </Field.Label>
  <Input placeholder="me@example.com" />
</Field.Root>

// With textarea
<Field.Root>
  <Field.Label>Message</Field.Label>
  <Textarea placeholder="Your message..." />
</Field.Root>

// With native select
<Field.Root>
  <Field.Label>Option</Field.Label>
  <NativeSelect.Root>
    <NativeSelect.Field>
      <option value="1">Option 1</option>
      <option value="2">Option 2</option>
    </NativeSelect.Field>
    <NativeSelect.Indicator />
  </NativeSelect.Root>
</Field.Root>
```

### Field.Root Props
- `required` - Mark field as required
- `invalid` - Mark field as invalid
- `disabled` - Disable the field
- `orientation` - `vertical` or `horizontal`

---

## Button

Interactive button component.

```tsx
import { Button, HStack } from "@chakra-ui/react"

// Basic button
<Button>Click me</Button>

// Variants
<Button variant="solid">Solid</Button>
<Button variant="subtle">Subtle</Button>
<Button variant="surface">Surface</Button>
<Button variant="outline">Outline</Button>
<Button variant="ghost">Ghost</Button>
<Button variant="plain">Plain</Button>

// Sizes
<Button size="xs">Extra Small</Button>
<Button size="sm">Small</Button>
<Button size="md">Medium</Button>
<Button size="lg">Large</Button>
<Button size="xl">Extra Large</Button>

// Colors
<Button colorPalette="gray">Gray</Button>
<Button colorPalette="red">Red</Button>
<Button colorPalette="green">Green</Button>
<Button colorPalette="blue">Blue</Button>
<Button colorPalette="teal">Teal</Button>
<Button colorPalette="pink">Pink</Button>
<Button colorPalette="purple">Purple</Button>
<Button colorPalette="cyan">Cyan</Button>
<Button colorPalette="orange">Orange</Button>
<Button colorPalette="yellow">Yellow</Button>

// With icon
<Button colorPalette="teal" variant="solid">
  <RiMailLine /> Email
</Button>

<Button colorPalette="teal" variant="outline">
  Call us <RiArrowRightLine />
</Button>

// Loading state
<Button loading>Click me</Button>
<Button loading loadingText="Saving...">Click me</Button>

// Disabled
<Button disabled>Disabled</Button>

// As link
<Button asChild>
  <a href="/dashboard">Dashboard</a>
</Button>
```

### Props
- `variant` - `solid`, `subtle`, `surface`, `outline`, `ghost`, `plain`
- `size` - `xs`, `sm`, `md`, `lg`, `xl`
- `colorPalette` - Color theme
- `loading` - Show loading spinner
- `loadingText` - Text to show while loading
- `disabled` - Disable button
- `asChild` - Render as child element

---

## Checkbox

Checkbox input component.

```tsx
import { Checkbox } from "@chakra-ui/react"

// Basic checkbox
<Checkbox.Root>
  <Checkbox.HiddenInput />
  <Checkbox.Control />
  <Checkbox.Label>Accept terms and conditions</Checkbox.Label>
</Checkbox.Root>

// With indicator icon
<Checkbox.Root>
  <Checkbox.HiddenInput />
  <Checkbox.Control>
    <Checkbox.Indicator />
  </Checkbox.Control>
  <Checkbox.Label>Checkbox</Checkbox.Label>
</Checkbox.Root>

// Variants
<Checkbox.Root variant="outline">
  <Checkbox.HiddenInput />
  <Checkbox.Control />
  <Checkbox.Label>Outline</Checkbox.Label>
</Checkbox.Root>

<Checkbox.Root variant="subtle">
  <Checkbox.HiddenInput />
  <Checkbox.Control />
  <Checkbox.Label>Subtle</Checkbox.Label>
</Checkbox.Root>

<Checkbox.Root variant="solid">
  <Checkbox.HiddenInput />
  <Checkbox.Control />
  <Checkbox.Label>Solid</Checkbox.Label>
</Checkbox.Root>

// Sizes
<Checkbox.Root size="sm">
  <Checkbox.HiddenInput />
  <Checkbox.Control />
  <Checkbox.Label>Small</Checkbox.Label>
</Checkbox.Root>

// Colors
<Checkbox.Root colorPalette="blue">
  <Checkbox.HiddenInput />
  <Checkbox.Control />
  <Checkbox.Label>Blue</Checkbox.Label>
</Checkbox.Root>

// States
<Checkbox.Root disabled>
  <Checkbox.HiddenInput />
  <Checkbox.Control />
  <Checkbox.Label>Disabled</Checkbox.Label>
</Checkbox.Root>

<Checkbox.Root invalid>
  <Checkbox.HiddenInput />
  <Checkbox.Control />
  <Checkbox.Label>Invalid</Checkbox.Label>
</Checkbox.Root>

// Checked by default
<Checkbox.Root defaultChecked>
  <Checkbox.HiddenInput />
  <Checkbox.Control />
  <Checkbox.Label>Checked</Checkbox.Label>
</Checkbox.Root>
```

### Props
- `variant` - `outline`, `subtle`, `solid`
- `size` - `sm`, `md`, `lg`
- `colorPalette` - Color theme
- `defaultChecked` - Initial checked state
- `checked` - Controlled checked state
- `disabled` - Disable checkbox
- `invalid` - Mark as invalid
- `onCheckedChange` - Change callback

---

## Radio

Radio button component for single selection.

```tsx
import { RadioGroup } from "@chakra-ui/react"

// Basic radio group
<RadioGroup.Root defaultValue="option1">
  <HStack gap="6">
    <RadioGroup.Item value="option1">
      <RadioGroup.ItemHiddenInput />
      <RadioGroup.ItemControl />
      <RadioGroup.ItemLabel>Option 1</RadioGroup.ItemLabel>
    </RadioGroup.Item>
    <RadioGroup.Item value="option2">
      <RadioGroup.ItemHiddenInput />
      <RadioGroup.ItemControl />
      <RadioGroup.ItemLabel>Option 2</RadioGroup.ItemLabel>
    </RadioGroup.Item>
  </HStack>
</RadioGroup.Root>

// Vertical stack
<RadioGroup.Root>
  <VStack align="start">
    <RadioGroup.Item value="1">
      <RadioGroup.ItemHiddenInput />
      <RadioGroup.ItemControl />
      <RadioGroup.ItemLabel>Option 1</RadioGroup.ItemLabel>
    </RadioGroup.Item>
    <RadioGroup.Item value="2">
      <RadioGroup.ItemHiddenInput />
      <RadioGroup.ItemControl />
      <RadioGroup.ItemLabel>Option 2</RadioGroup.ItemLabel>
    </RadioGroup.Item>
  </VStack>
</RadioGroup.Root>

// Sizes
<RadioGroup.Root size="sm">...</RadioGroup.Root>
<RadioGroup.Root size="md">...</RadioGroup.Root>
<RadioGroup.Root size="lg">...</RadioGroup.Root>

// Colors
<RadioGroup.Root colorPalette="blue">...</RadioGroup.Root>
```

### Props
- `size` - `sm`, `md`, `lg`
- `colorPalette` - Color theme
- `defaultValue` - Initial value
- `value` - Controlled value
- `onValueChange` - Change callback

---

## Switch

Toggle switch component.

```tsx
import { Switch } from "@chakra-ui/react"

// Basic switch
<Switch.Root>
  <Switch.HiddenInput />
  <Switch.Control />
  <Switch.Label>Enable notifications</Switch.Label>
</Switch.Root>

// With track label
<Switch.Root>
  <Switch.HiddenInput />
  <Switch.Control>
    <Switch.Thumb />
  </Switch.Control>
  <Switch.Label>Toggle</Switch.Label>
</Switch.Root>

// Sizes
<Switch.Root size="sm">
  <Switch.HiddenInput />
  <Switch.Control />
</Switch.Root>

// Colors
<Switch.Root colorPalette="blue">
  <Switch.HiddenInput />
  <Switch.Control />
</Switch.Root>

// Checked by default
<Switch.Root defaultChecked>
  <Switch.HiddenInput />
  <Switch.Control />
</Switch.Root>

// Disabled
<Switch.Root disabled>
  <Switch.HiddenInput />
  <Switch.Control />
</Switch.Root>
```

### Props
- `size` - `sm`, `md`, `lg`
- `colorPalette` - Color theme
- `defaultChecked` - Initial checked state
- `checked` - Controlled checked state
- `disabled` - Disable switch
- `onCheckedChange` - Change callback

---

## Select

Custom select dropdown component.

```tsx
import { Select } from "@chakra-ui/react"

// Basic select
<Select.Root>
  <Select.Trigger>
    <Select.ValueText placeholder="Select option" />
  </Select.Trigger>
  <Select.Content>
    <Select.Item item="1">
      <Select.ItemText>Option 1</Select.ItemText>
    </Select.Item>
    <Select.Item item="2">
      <Select.ItemText>Option 2</Select.ItemText>
    </Select.Item>
  </Select.Content>
</Select.Root>

// With groups
<Select.Root>
  <Select.Trigger>
    <Select.ValueText placeholder="Select city" />
  </Select.Trigger>
  <Select.Content>
    <Select.ItemGroup>
      <Select.ItemGroupLabel>Germany</Select.ItemGroupLabel>
      <Select.Item item="berlin">Berlin</Select.Item>
      <Select.Item item="munich">Munich</Select.Item>
    </Select.ItemGroup>
    <Select.ItemGroup>
      <Select.ItemGroupLabel>USA</Select.ItemGroupLabel>
      <Select.Item item="new-york">New York</Select.Item>
    </Select.ItemGroup>
  </Select.Content>
</Select.Root>

// Multiple selection
<Select.Root multiple>
  ...
</Select.Root>
```

---

## NativeSelect

Native HTML select element.

```tsx
import { NativeSelect } from "@chakra-ui/react"

<NativeSelect.Root>
  <NativeSelect.Field>
    <option value="1">Option 1</option>
    <option value="2">Option 2</option>
    <option value="3">Option 3</option>
  </NativeSelect.Field>
  <NativeSelect.Indicator />
</NativeSelect.Root>

// Sizes
<NativeSelect.Root size="sm">...</NativeSelect.Root>
<NativeSelect.Root size="md">...</NativeSelect.Root>
<NativeSelect.Root size="lg">...</NativeSelect.Root>
```

---

## Slider

Range slider component.

```tsx
import { Slider } from "@chakra-ui/react"

// Basic slider
<Slider.Root defaultValue={[50]}>
  <Slider.Control>
    <Slider.Track>
      <Slider.Range />
    </Slider.Track>
    <Slider.Thumb index={0}>
      <Slider.HiddenInput />
    </Slider.Thumb>
  </Slider.Control>
</Slider.Root>

// With marks
<Slider.Root defaultValue={[50]}>
  <Slider.Control>
    <Slider.Track>
      <Slider.Range />
    </Slider.Track>
    <Slider.Thumb index={0}>
      <Slider.HiddenInput />
    </Slider.Thumb>
  </Slider.Control>
  <Slider.Marks marks={[0, 25, 50, 75, 100]} />
</Slider.Root>

// Range slider
<Slider.Root defaultValue={[25, 75]}>
  <Slider.Control>
    <Slider.Track>
      <Slider.Range />
    </Slider.Track>
    <Slider.Thumb index={0}>
      <Slider.HiddenInput />
    </Slider.Thumb>
    <Slider.Thumb index={1}>
      <Slider.HiddenInput />
    </Slider.Thumb>
  </Slider.Control>
</Slider.Root>

// Min and max
<Slider.Root defaultValue={[0]} min={0} max={100} step={5}>
  ...
</Slider.Root>
```

---

## Textarea

Multi-line text input.

```tsx
import { Textarea } from "@chakra-ui/react"

// Basic textarea
<Textarea placeholder="Comment..." />

// Variants
<Textarea variant="outline" placeholder="Outline" />
<Textarea variant="subtle" placeholder="Subtle" />
<Textarea variant="flushed" placeholder="Flushed" />

// Sizes
<Textarea size="xs" placeholder="Extra small" />
<Textarea size="sm" placeholder="Small" />
<Textarea size="md" placeholder="Medium" />
<Textarea size="lg" placeholder="Large" />
<Textarea size="xl" placeholder="Extra large" />

// With field wrapper
<Field.Root>
  <Field.Label>Message</Field.Label>
  <Textarea placeholder="Your message..." />
  <Field.HelperText>Max 500 characters</Field.HelperText>
</Field.Root>

// Auto resize
<Textarea autoresize placeholder="Auto resizing" />

// Min/max rows
<Textarea minH="100px" maxH="200px" placeholder="Constrained height" />
```

---

## Rating

Star rating component.

```tsx
import { RatingGroup } from "@chakra-ui/react"

// Basic rating
<RatingGroup.Root defaultValue={3}>
  <RatingGroup.HiddenInput />
  <RatingGroup.Control>
    <RatingGroup.Context>
      {({ items }) =>
        items.map((item) => (
          <RatingGroup.Item key={item} index={item}>
            <RatingGroup.ItemIndicator />
          </RatingGroup.Item>
        ))
      }
    </RatingGroup.Context>
  </RatingGroup.Control>
</RatingGroup.Root>

// Read only
<RatingGroup.Root readOnly defaultValue={4}>
  ...
</RatingGroup.Root>

// Sizes
<RatingGroup.Root size="sm">...</RatingGroup.Root>
<RatingGroup.Root size="md">...</RatingGroup.Root>
<RatingGroup.Root size="lg">...</RatingGroup.Root>
```

---

## Editable

Inline editable text.

```tsx
import { Editable } from "@chakra-ui/react"

// Basic editable
<Editable.Root defaultValue="Hello world">
  <Editable.Preview />
  <Editable.Input />
</Editable.Root>

// With placeholder
<Editable.Root placeholder="Click to edit">
  <Editable.Preview />
  <Editable.Input />
</Editable.Root>

// With textarea
<Editable.Root>
  <Editable.Preview />
  <Editable.Textarea />
</Editable.Root>
```
