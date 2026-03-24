# Overlay Components

## Dialog

Modal dialog for user interactions.

```tsx
import { Dialog, Button, CloseButton, Portal } from "@chakra-ui/react"

// Basic dialog
<Dialog.Root>
  <Dialog.Trigger asChild>
    <Button variant="outline" size="sm">Open Dialog</Button>
  </Dialog.Trigger>
  <Portal>
    <Dialog.Backdrop />
    <Dialog.Positioner>
      <Dialog.Content>
        <Dialog.Header>
          <Dialog.Title>Dialog Title</Dialog.Title>
        </Dialog.Header>
        <Dialog.Body>
          <p>Dialog content goes here.</p>
        </Dialog.Body>
        <Dialog.Footer>
          <Dialog.ActionTrigger asChild>
            <Button variant="outline">Cancel</Button>
          </Dialog.ActionTrigger>
          <Button>Save</Button>
        </Dialog.Footer>
        <Dialog.CloseTrigger asChild>
          <CloseButton size="sm" />
        </Dialog.CloseTrigger>
      </Dialog.Content>
    </Dialog.Positioner>
  </Portal>
</Dialog.Root>

// Sizes
<Dialog.Root size="xs">...</Dialog.Root>
<Dialog.Root size="sm">...</Dialog.Root>
<Dialog.Root size="md">...</Dialog.Root>
<Dialog.Root size="lg">...</Dialog.Root>
<Dialog.Root size="cover">...</Dialog.Root>  // Full screen cover

// Controlled dialog
const [open, setOpen] = useState(false)
<Dialog.Root open={open} onOpenChange={(e) => setOpen(e.open)}>
  ...
</Dialog.Root>

// With placement
<Dialog.Root placement="center">...</Dialog.Root>
<Dialog.Root placement="top">...</Dialog.Root>

// Motion preset
<Dialog.Root motionPreset="slide-in-bottom">...</Dialog.Root>
<Dialog.Root motionPreset="scale">...</Dialog.Root>

// Lazy mount
<Dialog.Root lazyMount onOpenChange={(e) => setOpen(e.open)}>
  ...
</Dialog.Root>

// Alert dialog (modal that requires user interaction)
<Dialog.Root role="alertdialog">
  ...
</Dialog.Root>
```

### Props
- `size` - `xs`, `sm`, `md`, `lg`, `cover`
- `placement` - `center`, `top`
- `motionPreset` - `slide-in-bottom`, `scale`
- `open` - Controlled open state
- `onOpenChange` - Callback when open state changes
- `lazyMount` - Defer mounting until opened
- `role` - `dialog` or `alertdialog`

---

## Drawer

Side panel that slides in from the edge.

```tsx
import { Drawer, Button, CloseButton, Portal } from "@chakra-ui/react"

// Basic drawer
<Drawer.Root>
  <Drawer.Trigger asChild>
    <Button variant="outline" size="sm">Open Drawer</Button>
  </Drawer.Trigger>
  <Portal>
    <Drawer.Backdrop />
    <Drawer.Positioner>
      <Drawer.Content>
        <Drawer.Header>
          <Drawer.Title>Drawer Title</Drawer.Title>
        </Drawer.Header>
        <Drawer.Body>
          <p>Drawer content goes here.</p>
        </Drawer.Body>
        <Drawer.Footer>
          <Drawer.CloseTrigger asChild>
            <Button variant="outline">Cancel</Button>
          </Drawer.CloseTrigger>
          <Button>Save</Button>
        </Drawer.Footer>
        <Drawer.CloseTrigger asChild>
          <CloseButton size="sm" />
        </Drawer.CloseTrigger>
      </Drawer.Content>
    </Drawer.Positioner>
  </Portal>
</Drawer.Root>

// Placement
<Drawer.Root placement="start">...</Drawer.Root>  // Left
<Drawer.Root placement="end">...</Drawer.Root>    // Right
<Drawer.Root placement="top">...</Drawer.Root>
<Drawer.Root placement="bottom">...</Drawer.Root>

// Sizes
<Drawer.Root size="xs">...</Drawer.Root>
<Drawer.Root size="sm">...</Drawer.Root>
<Drawer.Root size="md">...</Drawer.Root>
<Drawer.Root size="lg">...</Drawer.Root>
<Drawer.Root size="full">...</Drawer.Root>

// Controlled
const [open, setOpen] = useState(false)
<Drawer.Root open={open} onOpenChange={(e) => setOpen(e.open)}>
  ...
</Drawer.Root>
```

### Props
- `placement` - `start`, `end`, `top`, `bottom`
- `size` - `xs`, `sm`, `md`, `lg`, `full`
- `open` - Controlled open state
- `onOpenChange` - Callback when open state changes

---

## Popover

Floating content attached to a trigger element.

```tsx
import { Popover, Button, Portal } from "@chakra-ui/react"

// Basic popover
<Popover.Root>
  <Popover.Trigger asChild>
    <Button size="sm" variant="outline">Click me</Button>
  </Popover.Trigger>
  <Portal>
    <Popover.Positioner>
      <Popover.Content>
        <Popover.Arrow />
        <Popover.Body>
          <Popover.Title fontWeight="medium">Title</Popover.Title>
          <Text my="4">Popover content here.</Text>
        </Popover.Body>
      </Popover.Content>
    </Popover.Positioner>
  </Portal>
</Popover.Root>

// With close button
<Popover.Root>
  <Popover.Trigger asChild>
    <Button>Open</Button>
  </Popover.Trigger>
  <Portal>
    <Popover.Positioner>
      <Popover.Content>
        <Popover.CloseTrigger />
        <Popover.Body>
          <Popover.Title>Title</Popover.Title>
          Content
        </Popover.Body>
      </Popover.Content>
    </Popover.Positioner>
  </Portal>
</Popover.Root>

// Sizes
<Popover.Root size="xs">...</Popover.Root>
<Popover.Root size="sm">...</Popover.Root>
<Popover.Root size="md">...</Popover.Root>
<Popover.Root size="lg">...</Popover.Root>

// Placement
<Popover.Root positioning={{ placement: "top" }}>...</Popover.Root>
<Popover.Root positioning={{ placement: "bottom" }}>...</Popover.Root>
<Popover.Root positioning={{ placement: "left" }}>...</Popover.Root>
<Popover.Root positioning={{ placement: "right" }}>...</Popover.Root>

// Controlled
const [open, setOpen] = useState(false)
<Popover.Root open={open} onOpenChange={(e) => setOpen(e.open)}>
  ...
</Popover.Root>

// Lazy mount
<Popover.Root lazyMount>...</Popover.Root>

// Hover trigger
<Popover.Root openOnHover>...</Popover.Root>

// Close on click outside
<Popover.Root closeOnInteractOutside={false}>...</Popover.Root>
```

### Props
- `size` - `xs`, `sm`, `md`, `lg`
- `open` - Controlled open state
- `onOpenChange` - Callback when open state changes
- `positioning.placement` - Position of popover
- `openOnHover` - Open on hover instead of click
- `closeOnInteractOutside` - Close when clicking outside
- `lazyMount` - Defer mounting until opened

---

## Tooltip

Display information on hover.

```tsx
import { Tooltip, Button } from "@chakra-ui/react"

// Basic tooltip (using snippet component)
<Tooltip content="This is the tooltip content">
  <Button variant="outline" size="sm">Hover me</Button>
</Tooltip>

// With arrow
<Tooltip showArrow content="Tooltip with arrow">
  <Button>Hover me</Button>
</Tooltip>

// Placement
<Tooltip content="Tooltip" positioning={{ placement: "top" }}>
  <Button>Top</Button>
</Tooltip>

<Tooltip content="Tooltip" positioning={{ placement: "right-end" }}>
  <Button>Right End</Button>
</Tooltip>

// Offset
<Tooltip
  content="Tooltip"
  positioning={{ offset: { mainAxis: 4, crossAxis: 4 } }}
>
  <Button>Offset</Button>
</Tooltip>

// Delay
<Tooltip content="Tooltip" openDelay={500} closeDelay={100}>
  <Button>Delayed</Button>
</Tooltip>

// Custom background
<Tooltip
  showArrow
  content="Custom color"
  contentProps={{ css: { "--tooltip-bg": "tomato" } }}
>
  <Button>Custom BG</Button>
</Tooltip>

// Controlled
const [open, setOpen] = useState(false)
<Tooltip
  content="Tooltip Content"
  open={open}
  onOpenChange={(e) => setOpen(e.open)}
>
  <Button>{open ? "Hide" : "Show"} tooltip</Button>
</Tooltip>
```

### Props
- `content` - Tooltip text/content
- `showArrow` - Show arrow pointing to trigger
- `openDelay` - Delay before showing (ms)
- `closeDelay` - Delay before hiding (ms)
- `positioning.placement` - Position of tooltip
- `positioning.offset` - Offset from trigger
- `open` - Controlled open state
- `onOpenChange` - Callback when open state changes

---

## Toast

Temporary notification messages.

```tsx
import { Toast, toaster } from "@chakra-ui/react"

// Create toaster component in app
<Toaster />

// Show toast
toaster.create({
  title: "Success!",
  description: "Your changes have been saved.",
  type: "success",
})

// Toast types
toaster.create({ title: "Success", type: "success" })
toaster.create({ title: "Error", type: "error" })
toaster.create({ title: "Warning", type: "warning" })
toaster.create({ title: "Info", type: "info" })

// With duration
toaster.create({
  title: "Quick message",
  duration: 3000, // 3 seconds
})

// Persistent toast (no auto-close)
toaster.create({
  title: "Important",
  duration: Infinity,
})

// With action
toaster.create({
  title: "File deleted",
  action: {
    label: "Undo",
    onClick: () => console.log("Undo"),
  },
})

// Promise-based toast
toaster.promise(saveData, {
  loading: { title: "Saving..." },
  success: { title: "Saved!" },
  error: { title: "Failed to save" },
})

// Dismiss specific toast
const id = toaster.create({ title: "Dismissable" })
toaster.dismiss(id)

// Dismiss all toasts
toaster.dismiss()
```

### Toaster Props
- `placement` - `top`, `bottom`, `top-start`, `top-end`, `bottom-start`, `bottom-end`

### Toast Options
- `title` - Toast title
- `description` - Toast description
- `type` - `success`, `error`, `warning`, `info`
- `duration` - Auto-close duration in ms (default: 5000)
- `action` - Action button configuration
- `closable` - Show close button

---

## Menu

Dropdown menu for actions and navigation.

```tsx
import { Menu, Button, Portal } from "@chakra-ui/react"

// Basic menu
<Menu.Root>
  <Menu.Trigger asChild>
    <Button variant="outline" size="sm">Open Menu</Button>
  </Menu.Trigger>
  <Portal>
    <Menu.Positioner>
      <Menu.Content>
        <Menu.Item value="edit">Edit</Menu.Item>
        <Menu.Item value="duplicate">Duplicate</Menu.Item>
        <Menu.Item value="delete">Delete</Menu.Item>
        <Menu.Separator />
        <Menu.Item value="share">Share</Menu.Item>
      </Menu.Content>
    </Menu.Positioner>
  </Portal>
</Menu.Root>

// With icons
<Menu.Root>
  <Menu.Trigger asChild>
    <Button>Actions</Button>
  </Menu.Trigger>
  <Portal>
    <Menu.Positioner>
      <Menu.Content>
        <Menu.Item value="edit">
          <LuEdit /> Edit
        </Menu.Item>
        <Menu.Item value="copy">
          <LuCopy /> Copy
        </Menu.Item>
        <Menu.Separator />
        <Menu.Item value="delete" color="red.500">
          <LuTrash /> Delete
        </Menu.Item>
      </Menu.Content>
    </Menu.Positioner>
  </Portal>
</Menu.Root>

// With groups
<Menu.Root>
  <Menu.Trigger asChild>
    <Button>Options</Button>
  </Menu.Trigger>
  <Portal>
    <Menu.Positioner>
      <Menu.Content>
        <Menu.ItemGroup>
          <Menu.ItemGroupLabel>Actions</Menu.ItemGroupLabel>
          <Menu.Item value="edit">Edit</Menu.Item>
          <Menu.Item value="copy">Copy</Menu.Item>
        </Menu.ItemGroup>
        <Menu.Separator />
        <Menu.ItemGroup>
          <Menu.ItemGroupLabel>View</Menu.ItemGroupLabel>
          <Menu.Item value="list">List</Menu.Item>
          <Menu.Item value="grid">Grid</Menu.Item>
        </Menu.ItemGroup>
      </Menu.Content>
    </Menu.Positioner>
  </Portal>
</Menu.Root>

// Checkbox/radio items
<Menu.Root>
  ...
  <Menu.Content>
    <Menu.CheckboxItem value="bold">Bold</Menu.CheckboxItem>
    <Menu.CheckboxItem value="italic">Italic</Menu.CheckboxItem>
    <Menu.RadioItemGroup>
      <Menu.RadioItem value="left">Left</Menu.RadioItem>
      <Menu.RadioItem value="center">Center</Menu.RadioItem>
    </Menu.RadioItemGroup>
  </Menu.Content>
</Menu.Root>

// Sizes
<Menu.Root size="sm">...</Menu.Root>
<Menu.Root size="md">...</Menu.Root>
<Menu.Root size="lg">...</Menu.Root>

// Controlled
const [value, setValue] = useState("")
<Menu.Root value={value} onValueChange={(e) => setValue(e.value)}>
  ...
</Menu.Root>
```

### Props
- `size` - `sm`, `md`, `lg`
- `value` - Selected value
- `onValueChange` - Selection callback
- `closeOnSelect` - Close menu after selection (default: true)
