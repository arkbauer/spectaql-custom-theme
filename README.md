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