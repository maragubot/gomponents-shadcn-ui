# Design

gomponents-shadcn-ui is a Go port of the [shadcn/ui](https://ui.shadcn.com/) component library, built with [gomponents](https://www.gomponents.com/).

## Distribution Model

Following shadcn's philosophy, components are designed to be **copied into your project** rather than imported as a dependency. This gives full ownership and customization freedom.

The primary distribution is documentation-driven: find the component you need, copy the Go code into your project. A CLI tool may be added later as a convenience layer.

## Component Structure

Each component lives in its own self-contained `.go` file with minimal cross-dependencies. When you want a Button, you copy `button.go` - nothing else.

### Variants

Components use a props struct for variants:

```go
type ButtonProps struct {
    Variant string // "default", "destructive", "outline", "secondary", "ghost", "link"
    Size    string // "default", "sm", "lg", "icon"
}

func Button(props ButtonProps, children ...g.Node) g.Node {
    // ...
}
```

### Class Handling

For class merging, we use simple concatenation with gomponents' built-in tools. Smart Tailwind class conflict resolution may be added later if needed.

## Styling

Styling follows shadcn's approach:

1. **CSS variables** define the design tokens (`--primary`, `--background`, `--radius`, etc.)
2. **Tailwind v4 classes** reference those variables

Users must set up the CSS variables in their project. We provide the standard shadcn CSS as reference.

## Repository & Workflow

- **Main repo**: `github.com/maragu/gomponents-shadcn-ui` - issues and merged code
- **Bot fork**: `github.com/maragubot/gomponents-shadcn-ui` - branches and PRs from here

## Tracking

One GitHub issue per component on the main repo. Minimal format: title like "Implement Button component" with a link to the shadcn docs.

## Scope

The goal is to port the entire shadcn/ui component library.
