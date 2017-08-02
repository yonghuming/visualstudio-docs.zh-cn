---
title: "针对 Visual Studio 的 R 工具中的工作区 | Microsoft Docs"
ms.custom: 
ms.date: 4/27/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d610279c-d6c3-4084-939a-bf042f64d4dd
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 8ac025a9da5c07cbc9efff416d07c93b91aa2c14
ms.contentlocale: zh-cn
ms.lasthandoff: 05/12/2017

---


## <a name="controlling-where-r-code-runs-with-workspaces"></a>控制 R 代码在工作区中的运行位置

在针对 Visual Studio 的 R 工具 (RTVS) 中的工作区可以配置 R 会话运行的位置，既可以在本地计算机运行，也可以在远程计算机运。 其目的是让你在工作时获得不相上下的用户体验，同时能够利用潜在的、更强大的基于云的计算机。

要打开“工作区”窗口，请使用“R 工具”>“Windows”>“工作区”命令，或按 Ctrl+9。

![针对 Visual Studio (VS2017) 的 R 工具中的工作区](~/rtvs/media/workspaces-window.png)

在此窗口中，绿色选中标记表示 RTVS 绑定的活动工作区。 选择蓝色箭头来设置活动工作区。 通过每个工作区右侧的设置（齿轮）图表可更改工作区的名称、位置和命令行参数。 使用红色 X 将删除手动添加的工作区。

在本主题中：

- [保存和重置工作区](#saving-and-resetting-a-workspace)
- [本地工作区](#local-workspaces)
- [远程工作区](#remote-workspaces)
- [在工作区间进行切换](#switching-between-workspaces)
- [本地和远程计算机上的目录](#directories-on-local-and-remote-computers)
- [将项目文件复制到远程工作区](#copying-project-files-to-remote-workspaces)
- [从远程工作区复制文件](#copying-files-from-a-remote-workspace)

## <a name="saving-and-resetting-a-workspace"></a>保存和重置工作区

默认情况下，在关闭和重新打开项目时，RTVS 将不会保存工作区状态。 但是，可以通过[工作区选项](options.md#workspace)更改此行为。

“R 工具”>“会话”>“重置”命令和交互窗口中的重置工具栏按钮也可以随时重置工作区状态。 对于远程工作区，重置将删除首次连接到远程服务器时所创建的用户配置文件，从而有效地删除那里积累的所有文件。

## <a name="local-workspaces"></a>本地工作区

本地工作区列表显示所有安装在计算机上的 R 解释器。 

Visual Studio 启动时，RTVS 通过搜索 `HKEY_LOCAL_MACHINE\Software\R-Core\` 注册表项尝试自动检测已安装的所有 R 版本。 由于仅在启动时执行此检查，因此安装新 R 解释器时无需重启 Visual Studio。

RTVS 可能无法检测以非标准方式（例如，仅仅将文件复制到文件夹，而不是运行安装程序）安装的 R 解释器。 在这种情况下，请按下列步骤手动创建新的本地 R 工作区：

1. 在“工作区”窗口，选择“添加”按钮。
1. 输入新工作区的名称。
1. 输入 R 根文件夹的路径，在此文件夹中具有包含解释器的 `bin` 文件夹，以及在被 RTVS 启动时传递给解释器的可选命令行参数。
1. 完成操作后，选择“保存”。

![添加一个新工作区](~/rtvs/media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>远程工作区

通过远程工作区可连接到远程计算机上的 R 会话。 （请参阅[设置远程工作区](workspaces-remote-setup.md)，了解如何配置计算机以实现此目的。）

RTVS 不会自动检测远程工作区，因此必须使用“工作区”窗口中的“添加”按钮来手动添加工作区（如上一节中所述）。 在这种情况下，请输入远程计算机的 URI 而非本地路径。

> [!Important]
> 远程工作区必须由使用 HTTPS 协议的 URI 标识，以保证与远程计算机之间通信的隐私和完整性。 RTVS 无法连接到不支持 HTTPS 的远程计算机。

> [!Note]
> 远程工作区在预览中有效。 我们正在为未来版本努力优化解决文件同步问题，欢迎提供有关如何优化用户体验的想法和反馈。


## <a name="switching-between-workspaces"></a>在工作区间进行切换

RTVS 一次只能绑定一个单独的工作区，“工作区”窗口中该工作区旁边的绿色选中标记指示了绑定情况。 默认情况下，RTVS 将绑定到上个会话所打开的最新本地工作区。

要更改活动工作区，请选择所需工作区旁的蓝色箭头。 执行此操作后，系统会提示保存会话，终止当前工作区，然后切换到新的工作区。

> [!Tip]
> 要禁用保存提示，请选择“R 工具”>“选项”命令，然后将“在切换工作区前显示确认对话框”选项设置为 `No`。 请参阅[工作区选项](options.md#workspace)。

如果尝试切换到已卸载的本地工作区或不可用的远程工作区，则有可能遇到 RTVS 项目未绑定到任何工作区的情况。 结果，当你在交互窗口输入代码，或尝试运行其他代码时，将出现如下所示的错误。 要更正此问题，只仅需在“工作区”窗口中切换到其他工作区。 如果都不可用，则需安装 R 解释器。 还可以在 Visual Studio 运行期间，尝试重启已安装解释器的 Visual Studio。

![工作区未绑定到 RTVS 时出错](~/rtvs/media/workspaces-disconnected-interactive-window.png)

### <a name="switching-to-a-remote-workspace"></a>切换到远程工作区

首次连接远程工作区时，RTVS 将提示输入凭据，并为后面的会话缓存这些凭据（使用安全 Windows 凭据保险箱）。 然后就可以通过 HTTPS（必需）与远程服务器安全通信。

根据服务器的配置，在连接时有可能遇到证书警告“远程 R 服务提供的安全证书阻止我们证明你确实正连接到计算机（名称）。”

![连接到远程工作区时的自签名证书警告](~/rtvs/media/workspaces-remote-self-signed-certificate-warning.png)

该证书是你正尝试连接的计算机向 RTVS 提供的文档，其中包含标识该计算机 URI 的字段。 当 RTVS 检测到证书中 URI 和连接计算机所用 URI 不匹配时，系统将发出警告，指示服务器的安全性可能已遭破坏。

但是如果已使用*自签名证书*在远程计算机上启用 HTTPS，而不是使用来自受信任提供程序，也会出现此警告。 有关详细信息，请参阅[设置远程工作区](workspaces-remote-setup.md)。

## <a name="directories-on-local-and-remote-computers"></a>本地和远程计算机上的目录

默认情况下，当在本地工作区启动新 R 解释器时，当前的工作目录是 `%userprofile%\Documents`。 可以随时通过“R 工具”>“工作目录”命令进行更改，也可通过在 Visual Studio 解决方案资源管理器中右键单击项目，然后选择像“在此设置工作目录”之类的命令进行更改。

在远程计算机上，当首次连接到该服务器时，RTVS 将自动基于凭据创建用户配置文件，因此工作目录是位于该配置文件下的 `Documents` 文件夹。 所有使用相同凭据的后续远程会话都将用到它。 

因此，对于本地和远程工作区而言，运行代码的确切位置可以有所不同。 在代码中，请避免对数据文件之类使用绝对路径，因为代码可能无法跨平台移植。 请改为使用相对路径。

另请注意，对于远程工作区，工作目录中的所有文件在相同用户配置文件的会话中仍保持在原来位置。 如前文所述，在使用远程工作区时，可通过“R 工具”>“会话”>“重置”命令（或交互窗口中的重置按钮）将它们删除。 这将再次从服务器删除重新连接时重新创建的用户配置文件。

## <a name="copying-project-files-to-remote-workspaces"></a>将项目文件复制到远程工作区

在 Visual Studio 中处理 R 项目时，即使正使用远程工作区，本地计算机也将拥有最新项目文件。 即，在 Visual Studio 中打开项目时（这通常意味着打开一个包含该项目的解决方案），RTVS 将假定项目内容完全驻留在本地计算机上。 实际上，远程工作区仅是项目文件的临时主机，以及任何来自代码的输出。 这意味着，例如要在交互窗口中使用 `source` 加载文件，则该文件必须已经在所提供路径的远程计算机上，或者，必须在远程 R 解释器的当前工作目录（使用 `setwd()` 函数设置）。

将文件复制到远程服务器，如下所示：

- 为了通过交互窗口远程处理文件，必须首先在解决方案资源管理器中右键单击该文件（或项目）进行手动复制，然后选择“寻源所选文件”。 对于单独的文件，在服务器上将其复制到工作目录；在复制项目时，RTVS 将为项目创建文件夹。

- 还可以在解决方案资源管理器中选择文件进行复制，然后选择“寻源所选文”。 这些文件将在交互窗口中加载和运行。 如果会话连接到远程计算机，则首先在那里复制文件。

- 当 RTVS 绑定到远程工作区，如果按 F5，选择“调试”>“启动调试”或通过其他方式开始运行代码，RTVS 会默认自动将项目文件复制到远程工作区（有关如何控制此过程，请参阅下方内容）。

- 服务器上任何现有的文件都将被覆盖。

> [!Note]
> 由于 RTVS 无法可靠地截获所有 R 函数调用，因此从交互窗口调用诸如 `source()` 或 `runApp()`（适用于 Shiny 应用程序）函数时，将不会向远程工作区复制文件。

[项目属性](projects.md#project-properties)决定 RTVS 是否在项目运行时复制文件、以及究竟复制哪些文件。 要打开此页，请选择“项目”>“(名称)属性...”菜单命令，或在解决方案资源管理器中右键单击项目，选择“属性...”。

![包含文件传输设置的项目属性运行选项卡](~/rtvs/media/workspaces-remote-file-transfer-filter-settings.png)

在此处，“运行时传输文件”决定 RTVS 是否自动复制项目文件。 然后，“要传输的文件”值将准确筛选出传输的文件。 默认情况下，仅复制 `.R`、`.Rmd`、`.sql`、`.md` 和 `.cpp` 文件。 这样可避免在每次运行时不慎将大型数据文件复制到服务器。 

## <a name="copying-files-from-a-remote-workspace"></a>从远程工作区复制文件

如果 R 脚本在服务器中生成了文件，可使用 `rtvs::fetch_file` 函数将它们复制回客户端。 此函数至少会接受你希望复制到计算机的文件的远程路径，可以选择性接受你希望文件复制到的计算机路径。 如果不指定路径，则将文件复制到 `%userprofile%\Downloads` 文件夹。

