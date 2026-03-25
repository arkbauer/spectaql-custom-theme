# Development

Branch `main` is for development. Branch `theme` is SpectaQL custom theme to be installed in other projects.

When making changes in `main` branches `spectaql` folder you must sync them with `theme` branch by running this command in `theme` branch: 

```sh
git checkout origin/main -- spectaql
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
themeDir: <path-to-node-modules>/spectaql-custom-theme/spectaql
```

### You can view all of the custom features [here](https://github.com/arkbauer/spectaql-custom-theme/blob/theme/README.md). 

> **NOTE**: If you provide logo, then there is a breaking change for [setting up logo](https://github.com/arkbauer/spectaql-custom-theme/blob/theme/README.md#setting-up-logo) that you must adhear to.