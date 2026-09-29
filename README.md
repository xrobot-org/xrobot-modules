# XRobot Official Module Index

`index.yaml` is the official XRobot Module catalog, served at
<https://xrobot.work/xrobot-modules/index.yaml>. Each entry is a Module Git
repository; a GitHub URL gives the package identity `owner/Repo`.

## Use

`xrobot init` writes this catalog into a BSP's `Modules/sources.yaml`:

```yaml
sources:
  - url: https://xrobot.work/xrobot-modules/index.yaml
    priority: 0
```

To add it to an existing BSP, run in the BSP root:

```bash
xrobot source add-source https://xrobot.work/xrobot-modules/index.yaml --priority 0
```

Query and use a Module:

```bash
xrobot source list --type module
xrobot source get xrobot-org/BlinkLED
xrobot module add xrobot-org/BlinkLED@dev
xrobot setup
```

## Adding a Module

Append the repository URL to `modules` in `index.yaml` by pull request. The
repository must follow the XRobot 1.0 Module layout: primary header `Repo.hpp`
declaring a plain class `Repo`, a `MODULE MANIFEST V2` block, and CI through the
shared workflow `xrobot-org/XRobot/.github/workflows/module-ci.yml`. See
<https://xrobot.work/docs/proj_man/proj-man-create-mod>.

Entries may also be mappings with `id`, `repo` and `status` (`community`,
`verified` or `official`; the latter two require `tested_ref` and `tested_libxr`).
Catalog format: <https://xrobot.work/docs/proj_man/proj-man-source-man>.
