# This is custom theme for SpectaQL with additional features

## SpectaQL config options

These settings apply only to the `spectaql-config.yml` file. The default configuration continues to function as usual and the options listed below simply introduce additional features.

### Setting up logo

If the logo is defined via `spectaql.logoFile` or `spectaql.logoUrl` setting, it's mandatory to add `spectaql.logoHeightPx` setting, otherwise your provided logo won't be shown.

### Custom Field Expansion Depth

You can also put field expansion depth values for seperate queries or mutations using `introspection.customFieldExpansionDepth.{Schema coordinates}` setting which will override `fieldExpansionDepth` setting for those queries and mutations. For example:

```yml
introspection:
    customFieldExpansionDepth:
        Query.categories: 4
        Mutation.returnOrderCreate: 4
```

### Mermaid charts (optional)

This custom spectaql theme supports mermaid charts processing in `x-introItems` and `x-outroItems`. In order for it to work you must specify `mermaid` javascript build file with `spectaql.mermaidPath` setting.

### Sort alphabetically

By default `Operations`, `Types` and `Directives` are sorted alphabetically, but if you want to sort it by how it is written in your GraphQL schema, you must set `spectaql.sortAlphabetically` setting value as false. 

### Custom Theme Colors

You can customize the appearance of your SpectaQL documentation by defining color variables. There's separate color configurations for **light** and **dark** themes using the following settings:

- `spectaql.themeVariables.lightTheme`
- `spectaql.themeVariables.darkTheme`

Both themes support the same set of color variables.

#### Available Color Variables

```
--spectaql-background
--spectaql-background-subtle
--spectaql-text-color
--spectaql-text-color-subtle
--spectaql-link-color
--spectaql-link-color-hover
--spectaql-border-color
--spectaql-border-color-subtle
--spectaql-code-background
--spectaql-code-background-subtle
--spectaql-code-text-color
--spectaql-sidebar-background
--spectaql-examples-background
--spectaql-scrollbar-thumb
--spectaql-table-stripe
--spectaql-nav-group-title
--spectaql-group-name-bg
--spectaql-group-name-bg-hover
--spectaql-group-name-color
--spectaql-code-copy-bg
--spectaql-code-copy-bg-hover
--spectaql-code-copy-color
--spectaql-code-copy-color-hover
--spectaql-code-copy-success
--admonition-warning-bg
--admonition-warning-border
--admonition-warning-title-color
--admonition-warning-title-bg
--admonition-info-bg
--admonition-info-border
--admonition-info-title-color
--admonition-info-title-bg
--admonition-danger-bg
--admonition-danger-border
--admonition-danger-title-color
--admonition-danger-title-bg
--text-highlight-bg
--text-highlight-color
--hljs-background
--hljs-color
--hljs-comment
--hljs-keyword
--hljs-name
--hljs-literal
--hljs-string
--hljs-attr
--hljs-number
--hljs-title
--hljs-built-in
--hljs-code
```

#### Example Configuration

```yml
spectaql:
  themeVariables:
    lightTheme:
      --spectaql-background: "#ffffff"
      --spectaql-text-color: "#1a1a1a"

    darkTheme:
      --spectaql-background: "#000000"
      --spectaql-text-color: "#921028"
```

### x-outroItems

`x-outroItems` appends additional documentation sections **after** the auto-generated API reference content.

It mirrors the structure of SpectaQL's built-in `x-introItems`, but renders its content at the **end** of the documentation rather than the beginning.

#### Configuration

Use `info.x-outroItems` to define additional sections. Each entry represents a titled section and can optionally include nested items that link to individual Markdown files.

```yaml
x-outroItems:
  - title: section title
    items:
      - title: title
        file: ./pathToFile
```

## x-introItems and x-outroItems additional processing features

These features are available when writing Markdown files used in `x-introItems` or `x-outroItems` sections. They extend standard Markdown syntax with additional formatting and interactive components.

### Admonition blocks

Admonition blocks let you highlight important information in your documentation using simple, readable markup that renders as styled callout blocks.

#### Syntax

To use an admonition block in a Markdown file, wrap your content between `$$TYPE` and `$$`:

```
$$WARNING
title: Be Careful
This action cannot be undone.
$$
```

#### Supported Types

| Type      | Description                                      |
|-----------|--------------------------------------------------|
| `WARNING` | Cautions the reader about potential issues       |
| `INFO`    | Provides helpful supplementary information       |
| `DANGER`  | Highlights critical or destructive actions       |

#### Title

The `title:` field is optional. If omitted, the title defaults to the admonition type (e.g. `WARNING`, `INFO`, `DANGER`).

```
$$INFO
No title defined here — will default to "INFO".
$$
```

#### Notes

- The pattern matching is **case-insensitive**, so `$$warning`, `$$Warning`, and `$$WARNING` are all valid.
- Admonition blocks can span multiple lines.

### Text highlighting

Text highlighting lets you visually emphasize inline content in your documentation by wrapping text in a simple syntax that renders as a highlighted mark.

#### Syntax

Wrap any text between double equals signs to highlight it:

```
This is ==highlighted text== in a sentence.
```

### Tabbed content

Tabbed content lets you present multiple variants of content — such as code examples in different languages or platform-specific instructions — under a single switchable tab component.

#### Syntax

Wrap your tabbed content between `$$generic` and `$$`, and define each tab using `=== "Tab Title"`:

```
$$generic
=== "JavaScript"
    console.log("Hello World")

=== "Python"
    print("Hello World")
$$
```

> Each tab's content must be **indented with 4 spaces**. This indentation is stripped automatically during processing.

#### Notes

- Tab titles must be **quoted** (e.g. `=== "My Tab"`)

### Mermaid charts

Mermaid charts let you embed diagrams and flowcharts directly in your documentation using simple text-based syntax that renders as visual graphics.

#### Syntax

Wrap your Mermaid diagram in a `mermaid` code block:

````
```mermaid
flowchart TD
    A["room_stays()"] --> B["createRoomAccessKey()"]
    B --> C["addRoomAccessKey()"]
    C --> D["removeRoomAccessKey()"]
    D --> E["deleteRoomAccessKey()"]
```
````

> For mermaid charts to work, you **MUST** do processing file setup instructions, see [Mermaid charts](#mermaid-charts-optional) under **SpectaQL config options**.

# Examples

### SpectaQL config file example

You can see a working minimal file named `spectaql-config.example.yml` with all custom settings in use.

### Dynamic Example Processing Module example

You can see a working example of a dynamic example processing module named `dynamicExamplesProcessingModule.example.js`. It demonstrates how to return realistic example values for GraphQL fields based on field name, type name, or parent type.