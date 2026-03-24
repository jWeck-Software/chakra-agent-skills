# Navigation Components

## Tabs

Tabbed interface for switching between content panels.

```tsx
import { Tabs } from "@chakra-ui/react"

// Basic tabs
<Tabs.Root defaultValue="members">
  <Tabs.List>
    <Tabs.Trigger value="members">Members</Tabs.Trigger>
    <Tabs.Trigger value="projects">Projects</Tabs.Trigger>
    <Tabs.Trigger value="settings">Settings</Tabs.Trigger>
  </Tabs.List>
  <Tabs.Content value="members">Manage your team members</Tabs.Content>
  <Tabs.Content value="projects">Manage your projects</Tabs.Content>
  <Tabs.Content value="settings">Manage your settings</Tabs.Content>
</Tabs.Root>

// With icons
<Tabs.Root defaultValue="members">
  <Tabs.List>
    <Tabs.Trigger value="members">
      <LuUser /> Members
    </Tabs.Trigger>
    <Tabs.Trigger value="projects">
      <LuFolder /> Projects
    </Tabs.Trigger>
  </Tabs.List>
  <Tabs.Content value="members">...</Tabs.Content>
  <Tabs.Content value="projects">...</Tabs.Content>
</Tabs.Root>

// Variants
<Tabs.Root variant="line">...</Tabs.Root>
<Tabs.Root variant="subtle">...</Tabs.Root>
<Tabs.Root variant="enclosed">...</Tabs.Root>
<Tabs.Root variant="outline">...</Tabs.Root>
<Tabs.Root variant="plain">...</Tabs.Root>

// With indicator (animated underline)
<Tabs.Root defaultValue="members" variant="plain">
  <Tabs.List bg="bg.muted" rounded="l3" p="1">
    <Tabs.Trigger value="members">Members</Tabs.Trigger>
    <Tabs.Trigger value="projects">Projects</Tabs.Trigger>
    <Tabs.Indicator rounded="l2" />
  </Tabs.List>
  ...
</Tabs.Root>

// Sizes
<Tabs.Root size="sm">...</Tabs.Root>
<Tabs.Root size="md">...</Tabs.Root>
<Tabs.Root size="lg">...</Tabs.Root>

// Lazy mounted content
<Tabs.Root lazyMount unmountOnExit defaultValue="tab-1">
  ...
</Tabs.Root>

// Controlled tabs
const [value, setValue] = useState("members")
<Tabs.Root value={value} onValueChange={(e) => setValue(e.value)}>
  ...
</Tabs.Root>

// Custom indicator styling
<Tabs.Root
  defaultValue="members"
  variant="plain"
  css={{
    "--tabs-indicator-bg": "colors.gray.subtle",
    "--tabs-indicator-shadow": "shadows.xs",
    "--tabs-trigger-radius": "radii.full",
  }}
>
  ...
</Tabs.Root>
```

### Props
- `variant` - `line`, `subtle`, `enclosed`, `outline`, `plain`
- `size` - `sm`, `md`, `lg`
- `defaultValue` - Initial active tab
- `value` - Controlled active tab
- `onValueChange` - Tab change callback
- `lazyMount` - Lazy mount tab content
- `unmountOnExit` - Unmount inactive content

---

## Breadcrumb

Navigation path indicator.

```tsx
import { Breadcrumb } from "@chakra-ui/react"

// Basic breadcrumb
<Breadcrumb.Root>
  <Breadcrumb.List>
    <Breadcrumb.Item>
      <Breadcrumb.Link href="#">Docs</Breadcrumb.Link>
    </Breadcrumb.Item>
    <Breadcrumb.Separator />
    <Breadcrumb.Item>
      <Breadcrumb.Link href="#">Components</Breadcrumb.Link>
    </Breadcrumb.Item>
    <Breadcrumb.Separator />
    <Breadcrumb.Item>
      <Breadcrumb.CurrentLink>Props</Breadcrumb.CurrentLink>
    </Breadcrumb.Item>
  </Breadcrumb.List>
</Breadcrumb.Root>

// Custom separator
<Breadcrumb.Root>
  <Breadcrumb.List>
    <Breadcrumb.Item>
      <Breadcrumb.Link href="#">Home</Breadcrumb.Link>
    </Breadcrumb.Item>
    <Breadcrumb.Separator>
      <LiaSlashSolid />
    </Breadcrumb.Separator>
    <Breadcrumb.Item>
      <Breadcrumb.CurrentLink>Current</Breadcrumb.CurrentLink>
    </Breadcrumb.Item>
  </Breadcrumb.List>
</Breadcrumb.Root>

// With icons
<Breadcrumb.Root>
  <Breadcrumb.List>
    <Breadcrumb.Item>
      <Breadcrumb.Link href="#">
        <LuHome /> Home
      </Breadcrumb.Link>
    </Breadcrumb.Item>
    ...
  </Breadcrumb.List>
</Breadcrumb.Root>

// Sizes
<Breadcrumb.Root size="sm">...</Breadcrumb.Root>
<Breadcrumb.Root size="md">...</Breadcrumb.Root>
<Breadcrumb.Root size="lg">...</Breadcrumb.Root>

// Variants
<Breadcrumb.Root variant="plain">...</Breadcrumb.Root>
<Breadcrumb.Root variant="underline">...</Breadcrumb.Root>
```

### Props
- `size` - `sm`, `md`, `lg`
- `variant` - `plain`, `underline`
- `separator` - Default separator character

---

## Pagination

Page navigation for lists and tables.

```tsx
import { Pagination, ButtonGroup, IconButton } from "@chakra-ui/react"

// Basic pagination
<Pagination.Root count={100} pageSize={10} defaultPage={1}>
  <ButtonGroup variant="ghost" size="sm">
    <Pagination.PrevTrigger asChild>
      <IconButton>
        <LuChevronLeft />
      </IconButton>
    </Pagination.PrevTrigger>

    <Pagination.Items
      render={(page) => (
        <IconButton variant={{ base: "ghost", _selected: "outline" }}>
          {page.value}
        </IconButton>
      )}
    />

    <Pagination.NextTrigger asChild>
      <IconButton>
        <LuChevronRight />
      </IconButton>
    </Pagination.NextTrigger>
  </ButtonGroup>
</Pagination.Root>

// With page text
<Pagination.Root count={100} pageSize={10} defaultPage={1}>
  <Pagination.PrevTrigger>Previous</Pagination.PrevTrigger>
  <Pagination.PageText />
  <Pagination.NextTrigger>Next</Pagination.NextTrigger>
</Pagination.Root>

// Sizes
<Pagination.Root size="xs">...</Pagination.Root>
<Pagination.Root size="sm">...</Pagination.Root>
<Pagination.Root size="md">...</Pagination.Root>
<Pagination.Root size="lg">...</Pagination.Root>

// Controlled
const [page, setPage] = useState(1)
<Pagination.Root
  count={100}
  pageSize={10}
  page={page}
  onPageChange={(e) => setPage(e.page)}
>
  ...
</Pagination.Root>

// With ellipsis
<Pagination.Root count={100} pageSize={10} defaultPage={1}>
  <Pagination.PrevTrigger />
  <Pagination.Items />
  <Pagination.Ellipsis />
  <Pagination.NextTrigger />
</Pagination.Root>
```

### Props
- `count` - Total number of items
- `pageSize` - Items per page
- `defaultPage` - Initial page
- `page` - Controlled current page
- `onPageChange` - Page change callback
- `siblingCount` - Number of sibling pages to show
- `size` - `xs`, `sm`, `md`, `lg`

---

## Steps

Step-by-step process indicator.

```tsx
import { Steps } from "@chakra-ui/react"

// Basic steps
<Steps.Root defaultValue={0}>
  <Steps.List>
    <Steps.Item index={0}>
      <Steps.Indicator>
        <Steps.Status
          complete={<LuCheck />}
          incomplete={<Steps.Number />}
          current={<Steps.Number />}
        />
      </Steps.Indicator>
      <Steps.Title>Step 1</Steps.Title>
    </Steps.Item>
    <Steps.Item index={1}>
      <Steps.Indicator>
        <Steps.Status
          complete={<LuCheck />}
          incomplete={<Steps.Number />}
          current={<Steps.Number />}
        />
      </Steps.Indicator>
      <Steps.Title>Step 2</Steps.Title>
    </Steps.Item>
    <Steps.Item index={2}>
      <Steps.Indicator>
        <Steps.Status
          complete={<LuCheck />}
          incomplete={<Steps.Number />}
          current={<Steps.Number />}
        />
      </Steps.Indicator>
      <Steps.Title>Step 3</Steps.Title>
    </Steps.Item>
  </Steps.List>

  <Steps.Content index={0}>Step 1 Content</Steps.Content>
  <Steps.Content index={1}>Step 2 Content</Steps.Content>
  <Steps.Content index={2}>Step 3 Content</Steps.Content>

  <Steps.Completed>All steps completed!</Steps.Completed>
</Steps.Root>

// Sizes
<Steps.Root size="sm">...</Steps.Root>
<Steps.Root size="md">...</Steps.Root>
<Steps.Root size="lg">...</Steps.Root>

// Controlled
const [step, setStep] = useState(0)
<Steps.Root step={step} onStepChange={(e) => setStep(e.step)}>
  ...
</Steps.Root>
```

### Props
- `defaultValue` - Initial step
- `step` - Controlled current step
- `onStepChange` - Step change callback
- `size` - `sm`, `md`, `lg`
- `count` - Total number of steps

---

## TreeView

Hierarchical tree navigation.

```tsx
import { TreeView } from "@chakra-ui/react"

// Basic tree
<TreeView.Root>
  <TreeView.Item value="src">
    <TreeView.Branch>
      <TreeView.Item value="components">
        <TreeView.Branch>
          <TreeView.Item value="Button.tsx" />
          <TreeView.Item value="Input.tsx" />
        </TreeView.Branch>
      </TreeView.Item>
      <TreeView.Item value="utils">
        <TreeView.Branch>
          <TreeView.Item value="helpers.ts" />
        </TreeView.Branch>
      </TreeView.Item>
    </TreeView.Branch>
  </TreeView.Item>
</TreeView.Root>

// With selection
<TreeView.Root selectionMode="single">
  ...
</TreeView.Root>

// With checkboxes
<TreeView.Root selectionMode="multiple">
  ...
</TreeView.Root>
```

---

## Link

Navigation link component.

```tsx
import { Link } from "@chakra-ui/react"

// Basic link
<Link href="/dashboard">Dashboard</Link>

// External link
<Link href="https://example.com" external>
  External Site
</Link>

// Variants
<Link variant="underline">Underlined</Link>
<Link variant="plain">Plain</Link>

// With icon
<Link>
  <LuExternalLink /> Open Link
</Link>

// As button
<Link asChild>
  <Button>Link Button</Button>
</Link>
```

### Props
- `href` - Link URL
- `external` - Open in new tab
- `variant` - `underline`, `plain`
- `asChild` - Compose with child element
