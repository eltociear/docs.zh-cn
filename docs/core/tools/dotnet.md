---
title: dotnet 命令
description: 了解 dotnet 命令（.NET Core CLI 的通用驱动程序）及其用法。
ms.date: 02/13/2020
ms.openlocfilehash: 8692d419afd528bf49e1dc7dc1a7a5fd698b363b
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134079"
---
# <a name="dotnet-command"></a>dotnet 命令

 本文适用于： ✔️ .NET Core 2.1 SDK 及更高版本

## <a name="name"></a>“属性”

`dotnet` - .NET Core CLI 的通用驱动程序。

## <a name="synopsis"></a>摘要

获取有关可用命令和环境的信息：

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

运行命令（需要 SDK 安装）：

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

运行应用程序：

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

`--roll-forward` 自 .NET Core 3.x 起可用。 使用 .NET Core 2.x 的 `--roll-forward-on-no-candidate-fx`。

## <a name="description"></a>描述

`dotnet` 命令有两个函数：

- 它提供了用于处理 .NET Core 项目的命令。

  例如，[`dotnet build`](dotnet-build.md) 生成项目。 每个命令定义自己的选项和参数。 所有命令都支持 `--help` 选项，用于打印有关如何使用命令的简短文档。

- 它运行 .NET Core 应用程序。

  指定应用程序 `.dll` 文件的路径以运行应用程序。 例如，`dotnet myapp.dll` 运行 `myapp` 应用程序。 要了解部署选项，请参阅 [.NET Core 应用程序部署](../deploying/index.md)。

## <a name="options"></a>选项

`dotnet` 本身有不同的选项，可用于运行命令和运行应用程序。

### <a name="options-for-dotnet-by-itself"></a>dotnet 本身的选项

以下是 `dotnet` 本身的选项。 例如 `dotnet --info`。 这些选项打印出有关环境的信息。

- **`--info`**

  打印出有关 .NET Core 安装和计算机环境（如当前操作系统）的详细信息，并提交 .NET Core 版本的 SHA。

- **`--version`**

  打印使用中的 .NET Core SDK 版本。

- **`--list-runtimes`**

  打印已安装的 .NET Core 运行时的列表。

- **`--list-sdks`**

  打印已安装的 .NET Core SDK 的列表。

- **`-h|--help`**

  打印可用命令列表。

### <a name="sdk-options-for-running-a-command"></a>用于运行命令的 SDK 选项

以下选项适用于使用命令的 `dotnet`。 例如 `dotnet build --help`。

- **`-d|--diagnostics`**

  启用诊断输出。

- **`-v|--verbosity <LEVEL>`**

  设置命令的详细级别。 允许使用的值为 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 并非在每个命令中均受支持。 请参阅特定的命令页，确定此选项是否可用。

- **`-h|--help`**

  打印出给定命令的文档，如 `dotnet build --help`。

- **`command options`**

  每个命令定义特定于该命令的选项。 有关可用选项的列表，请参阅特定命令页。

### <a name="runtime-options"></a>运行时选项

`dotnet` 运行应用程序时，可以使用以下选项。 例如 `dotnet myapp.dll --fx-version 3.1.1`。

- **`--additionalprobingpath <PATH>`**

  包含要进行探测的探测策略和程序集的路径。

- **`--additional-deps <PATH>`**

  附加 .deps.json 文件的路径  。 deps.json 文件包含依赖项、编译依赖项和用于解决程序集冲突的版本信息列表  。 有关详细信息，请参阅 GitHub 上的[运行时配置文件](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)。

- **`--fx-version <VERSION>`**

  用于运行应用程序的 .NET Core 运行时版本。

- **`--runtimeconfig`**

  runtimeconfig.template.json 文件的路径  。 runtimeconfig.template.json 文件是包含运行时设置的配置文件  。 有关详细信息，请参阅 [.NET Core 运行时配置设置](../run-time-config/index.md#runtimeconfigjson)。

- `--roll-forward-on-no-candidate-fx <N>` 在 .NET Core 2.x SDK 中可用   。

  所需的共享框架不可用时，请定义行为。 `N` 可以是：

  - `0` - 禁用次要版本前滚。
  - `1` - 前滚次要版本，但不前滚主版本。 这是默认行为。
  - `2` - 前滚次要和主版本。

   有关详细信息，请参阅[前滚](../whats-new/dotnet-core-2-1.md#roll-forward)。

- `--roll-forward <SETTING>` 自 .NET Core SDK 3.0 起可用   。

  控制将前滚操作应用于应用的方式。 `SETTING` 可以为下列值之一。 如果未指定，则 `Minor` 为默认类型。

  - `LatestPatch` - 前滚到最高补丁版本。 这会禁用次要版本前滚。
  - `Minor` - 如果缺少所请求的次要版本，则前滚到最低的较高次要版本。 如果存在所请求的次要版本，则使用 LatestPatch 策略。
  - `Major` - 如果缺少所请求的主要版本，则前滚到最低的较高主要版本和最低的次要版本。 如果存在所请求的主要版本，则使用 Minor 策略。
  - `LatestMinor` - 即使存在所请求的次要版本，仍前滚到最高次要版本。 适用于组件托管方案。
  - `LatestMajor` - 即使存在所请求的主要版本，仍前滚到最高主要版本和最高次要版本。 适用于组件托管方案。
  - `Disable` - 不前滚。 仅绑定到指定的版本。 建议不要将此策略用于一般用途，因为它会禁用前滚到最新补丁的功能。 该值仅建议用于测试。

除 `Disable` 外，所有设置都将使用可用的最高补丁版本。

前滚行为还可以在项目文件属性、运行时配置文件属性和环境变量中进行配置。 有关详细信息，请参阅[主版本运行时前滚](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward)。

## <a name="dotnet-commands"></a>dotnet 命令

### <a name="general"></a>常规

| 命令                                       | 函数                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | 生成 .NET Core 应用程序。                                     |
| [dotnet build-server](dotnet-build-server.md) | 与通过生成启动的服务器进行交互。                          |
| [dotnet clean](dotnet-clean.md)               | 清除生成输出。                                                |
| [dotnet help](dotnet-help.md)                 | 显示命令更详细的在线文档。           |
| [dotnet migrate](dotnet-migrate.md)           | 将有效的预览版 2 项目迁移到 .NET Core SDK 1.0 项目。  |
| [dotnet msbuild](dotnet-msbuild.md)           | 提供对 MSBuild 命令行的访问权限。                        |
| [dotnet new](dotnet-new.md)                   | 为给定的模板初始化 C# 或 F# 项目。                |
| [dotnet pack](dotnet-pack.md)                 | 创建代码的 NuGet 包。                               |
| [dotnet publish](dotnet-publish.md)           | 发布 .NET 依赖于框架或独立应用程序。 |
| [dotnet restore](dotnet-restore.md)           | 还原给定应用程序的依赖项。                  |
| [dotnet run](dotnet-run.md)                   | 从源运行应用程序。                                   |
| [dotnet sln](dotnet-sln.md)                   | 用于添加、删除和列出解决方案文件中项目的选项。       |
| [dotnet store](dotnet-store.md)               | 将程序集存储到运行时包存储区。                     |
| [dotnet test](dotnet-test.md)                 | 使用测试运行程序运行测试。                                     |

### <a name="project-references"></a>项目引用

命令 | 函数
--- | ---
[dotnet add reference](dotnet-add-reference.md) | 添加项目引用。
[dotnet list reference](dotnet-list-reference.md) | 列出项目引用。
[dotnet remove reference](dotnet-remove-reference.md) | 删除项目引用。

### <a name="nuget-packages"></a>NuGet 包

命令 | 函数
--- | ---
[dotnet add package](dotnet-add-package.md) | 添加 NuGet 包。
[dotnet remove package](dotnet-remove-package.md) | 删除 NuGet 包。

### <a name="nuget-commands"></a>NuGet 命令

命令 | 函数
--- | ---
[dotnet nuget delete](dotnet-nuget-delete.md) | 从服务器删除或取消列出包。
[dotnet nuget push](dotnet-nuget-push.md) | 将包推送到服务器，并将其发布。
[dotnet nuget locals](dotnet-nuget-locals.md) | 清除或列出本地 NuGet 资源，例如 http 请求缓存、临时缓存或计算机范围的全局包文件夹。
[dotnet nuget add source](dotnet-nuget-add-source.md) | 添加 NuGet 源。
[dotnet nuget disable source](dotnet-nuget-disable-source.md) | 禁用 NuGet 源。
[dotnet nuget enable source](dotnet-nuget-enable-source.md) | 启用 NuGet 源。
[dotnet nuget list source](dotnet-nuget-list-source.md) | 列出所有已配置的 NuGet 源。
[dotnet nuget remove source](dotnet-nuget-remove-source.md) | 删除 NuGet 源。
[dotnet nuget update source](dotnet-nuget-update-source.md) | 更新 NuGet 源。

### <a name="global-tool-path-and-local-tools-commands"></a>全局、工具路径和本地工具命令

工具是控制台应用程序，它们从 NuGet 包中安装并从命令提示符处进行调用。 你可自行编写工具，也可安装由第三方编写的工具。 工具也称为全局工具、工具路径工具和本地工具。 有关详细信息，请参阅 [.NET Core 工具概述](global-tools.md)。 全局和工具路径工具从 .NET Core SDK 2.1 开始可用。 本地工具从 .NET Core SDK 3.0 开始可用。

命令 | 函数
--- | ---
[dotnet tool install](dotnet-tool-install.md) | 在计算机上安装工具。
[dotnet tool list](dotnet-tool-list.md) | 列出计算机上当前安装的所有全局、工具路径或本地工具。
[dotnet tool uninstall](dotnet-tool-uninstall.md) | 从计算机中卸载工具。
[dotnet tool update](dotnet-tool-update.md) | 更新计算机上安装的工具。

### <a name="additional-tools"></a>其他工具

自 .NET Core SDK 2.1.300 开始，许多使用 `DotnetCliToolReference` 的仅在每个项目的基础上可用的工具现作为 .NET Core SDK 的一部分提供。 下表中列出了这些工具：

| 工具                                              | 函数                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev-certs                                         | 创建和管理开发证书。                |
| [ef](/ef/core/miscellaneous/cli/dotnet)           | Entity Framework Core 命令行工具。                    |
| sql-cache                                         | SQL Server 缓存命令行工具。                         |
| [user-secrets](/aspnet/core/security/app-secrets) | 管理开发用户机密。                            |
| [watch](/aspnet/core/tutorials/dotnet-watch)      | 启动文件观察程序，以在更改文件时运行命令。 |

有关每个工具的详细信息，请键入 `dotnet <tool-name> --help`。

## <a name="examples"></a>示例

创建新的 .NET Core 控制台应用程序：

```dotnetcli
dotnet new console
```

生成给定目录中的项目及其依赖项：

```dotnetcli
dotnet build
```

运行应用程序：

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a>环境变量

- `DOTNET_ROOT`，`DOTNET_ROOT(x86)`

  指定 .NET Core 运行时的位置（如果运行时未安装在默认位置）。 Windows 上的默认位置为 `C:\Program Files\dotnet`。 Linux 和 macOS 上的默认位置为 `/usr/share/dotnet`。 此环境变量仅在通过生成的可执行文件 (apphosts) 运行应用时使用。 在 64 位 OS 上运行 32 位可执行文件时，改用 `DOTNET_ROOT(x86)`。

- `DOTNET_PACKAGES`

  全局包文件夹。 如果未设置，则默认为 Unix 上的 `~/.nuget/packages` 或 Windows 上的 `%userprofile%\.nuget\packages`。

- `DOTNET_SERVICING`

  指定加载运行时期间共享主机要使用的服务索引的位置。

- `DOTNET_NOLOGO`

  指定是否在首次运行时显示 .NET Core 欢迎消息和遥测消息。 设置为 `true` 可将这些消息静音（接受 `true`、`1` 或 `yes` 值），或者，设置为 `false` 可允许显示消息（接受 `false`、`0` 或 `no` 值）。 如果未设置，则默认值为 `false`，表示在首次运行时将显示消息。 请注意，此标志对遥测不起作用（请参阅 `DOTNET_CLI_TELEMETRY_OPTOUT` 中关于如何选择不发送遥测数据的信息）。

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  指定是否收集并向 Microsoft 发送 .NET Core 工具使用情况的相关数据。 设置为 `true` 以选择退出遥测功能（接受的值为 `true`、`1` 或 `yes`）。 否则，设置为 `false` 以选择加入遥测功能（接受的值为 `false`、`0` 或 `no`）。 如果未设置，则默认为 `false` 且遥测功能为活动状态。

- `DOTNET_MULTILEVEL_LOOKUP`

  指定是否从全局位置解析 .NET Core 运行时、共享框架或 SDK。 如果未设置，则默认为 1（逻辑 `true`）。 设置为 0（逻辑 `false`），不从全局位置解析，并且具有独立的 .NET Core 安装。 有关多级别查找的详细信息，请参阅 [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md)（多级别 SharedFX 查找）。

- `DOTNET_ROLL_FORWARD` 自 .NET Core 3.x SDK 起可用  。

  确定前滚行为。 有关详细信息，请参阅本文章前面介绍的 `--roll-forward` 选项。

- `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` 在 .NET Core 2.x SDK 中可用  。

  如果设置为 `0`，则禁用次要版本前滚。 有关详细信息，请参阅[前滚](../whats-new/dotnet-core-2-1.md#roll-forward)。

- `DOTNET_CLI_UI_LANGUAGE`

  使用区域设置值（如 `en-us`）设置 CLI UI 的语言。 支持的值与 Visual Studio 中的值相同。 有关详细信息，请参阅 [Visual Studio 安装文档](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019)中有关更改安装程序语言一节。 .NET 资源管理器规则适用，因此你无需选取精确匹配项 &mdash; 你还可以在 `CultureInfo` 树中选取后代。 例如，如果将其设置为 `fr-CA`，CLI 将查找并使用 `fr` 翻译。 如果你将其设置为不受支持的语言，CLI 会退回到英语。

- `DOTNET_DISABLE_GUI_ERRORS`

  对于启用了 GUI 的已生成可执行文件 - 禁用对话框弹出窗口，此窗口通常显示某些类错误。 在这些情况下，它仅写入到 `stderr` 并退出。
  
- `DOTNET_ADDITIONAL_DEPS`

  等效于 CLI 选项 `--additional-deps`。

- `DOTNET_RUNTIME_ID`

  替代检测到的 RID。

- `DOTNET_SHARED_STORE`

  程序集解析在某些情况下将回退到的“共享存储”的位置。

- `DOTNET_STARTUP_HOOKS`

  要从中加载和执行启动挂钩的程序集列表。

- `COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`

  控制来自托管组件（例如 `dotnet.exe`、`hostfxr` 和 `hostpolicy`）的诊断跟踪。

## <a name="see-also"></a>请参阅

- [运行时配置文件](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [.NET Core 运行时配置设置](../run-time-config/index.md)
