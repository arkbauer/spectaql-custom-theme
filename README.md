# Development

Branch `main` is for development. Branch `theme` is SpectaQL custom theme to be installed in other projects.

When making changes in `main` branches `spectaql` folder you must sync them with `theme` branch by running this command in `theme` branch: 

```sh
git checkout main -- spectaql
```

# Usage

Add dependency to your `package.json`:

```json
{
    "dependencies": {
        "spectaql-custom-theme": "git+https://github.com/arkbauer/spectaql-custom-theme.git#theme"
    }
}
```

Run package install command in your terminal and it'll add the packages `theme` branch code to the `node_modules/spectaql-custom-theme` folder.

Update your `specataql-config.yml` file to point to installed custom theme:

```yml
themeDir: pathToNodeModules/spectaql-custom-theme/spectaql
```