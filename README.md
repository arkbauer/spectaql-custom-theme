### Setting up logo

If the logo is defined in `spectaql-config.yml` via `spectaql.logoFile` or `spectaql.logoUrl` setting, it's mandatory to add `spectaql.logoHeightPx` setting, otherwise your provided logo won't be shown.

### Custom Field Expansion Depth

You can also put field expansion depth values for seperate queries or mutations in `spectaql-config.yml` using `introspection.customFieldExpansionDepth.{Schema coordinates}` setting which will override `fieldExpansionDepth` setting for those queries and mutations. For example:

```yml
introspection:
    customFieldExpansionDepth:
        Query.categories: 4
        Mutation.returnOrderCreate: 4
```

### Mermaid charts (optional)

This custom spectaql theme supports mermaid charts processing in `x-introItems` and `x-outroItems`. In order for it to work you must specify `mermaid` javascript build file in the `spectaql-config.yml` with `spectaql.mermaidPath` setting.

### Custom Theme Colors

You can customize the appearance of your SpectaQL documentation by defining color variables in the `spectaql-config.yml` file. There's separate color configurations for **light** and **dark** themes using the following settings:

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
