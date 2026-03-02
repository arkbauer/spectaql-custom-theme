### Setting up logo

If the logo is defined in `spectaql-config.yml` via `logoFile` or `logoUrl` setting, it's mandatory to add `logoHeightPx` setting, otherwise your provided logo won't be shown.

### Custom Field Expansion Depth

You can also put field expansion depth values for seperate queries or mutations in `spectaql-config.yml` using `introspection.customFieldExpansionDepth.{Schema coordinates}` setting which will override `fieldExpansionDepth` setting for those queries and mutations. For example:

```yml
introspection:
    customFieldExpansionDepth:
        Query.categories: 4
        Mutation.returnOrderCreate: 4
```