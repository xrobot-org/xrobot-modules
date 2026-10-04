# xrobot-modules

XRobot 官方模块源 / Official XRobot Module Source

`index.yaml` 是 XRobot 的官方模块源，地址为 <https://xrobot.work/xrobot-modules/index.yaml>。每个条目是一个模块的 Git 仓库，GitHub 地址给出包标识 `owner/Repo`。

`index.yaml` is the official XRobot Module Source, served at <https://xrobot.work/xrobot-modules/index.yaml>. Each entry is a Module Git repository; a GitHub URL gives the package identity `owner/Repo`.

## 使用 / Use

`xrobot init` 把本源写入 BSP 的 `Modules/sources.yaml`：

`xrobot init` writes this Source into a BSP's `Modules/sources.yaml`:

```yaml
sources:
  - url: https://xrobot.work/xrobot-modules/index.yaml
    priority: 0
```

已有的 BSP 在根目录运行以下命令加入本源：

An existing BSP adds it with the following command, run in the BSP root:

```bash
xrobot source add-source https://xrobot.work/xrobot-modules/index.yaml --priority 0
```

查询并使用模块：

Querying and using a Module:

```bash
xrobot source list --type module
xrobot source get xrobot-org/BlinkLED
xrobot module add xrobot-org/BlinkLED@dev
xrobot setup
```

## 添加模块 / Adding a Module

通过 PR 把仓库地址加入 `index.yaml` 的 `modules`。仓库需符合 XRobot 1.0 模块结构：主头文件 `Repo.hpp` 声明普通类 `Repo`，含 `MODULE MANIFEST V2`，CI 调用共享工作流 `xrobot-org/XRobot/.github/workflows/module-ci.yml`。见 <https://xrobot.work/docs/proj_man/proj-man-create-mod>。

条目也可以写成映射，字段为 `id`、`repo` 和 `status`（`community`、`verified` 或 `official`，后两者需要 `tested_ref` 和 `tested_libxr`）。源的格式见 <https://xrobot.work/docs/proj_man/proj-man-source-man>。

A Module is added by a pull request that appends its repository URL to `modules` in `index.yaml`. The repository follows the XRobot 1.0 Module layout: the primary header `Repo.hpp` declares a plain class `Repo` and contains a `MODULE MANIFEST V2` block, and CI calls the shared workflow `xrobot-org/XRobot/.github/workflows/module-ci.yml`. See <https://xrobot.work/docs/proj_man/proj-man-create-mod>.

Entries may also be mappings with `id`, `repo` and `status` (`community`, `verified` or `official`; the latter two require `tested_ref` and `tested_libxr`). Source format: <https://xrobot.work/docs/proj_man/proj-man-source-man>.
