---
title: "Visual Studio 安装命令行参数示例 | Microsoft Docs"
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 0f07824b29e7851e353d472838a897853e227d6c
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Visual Studio 2017 安装命令行参数示例
为了说明如何[使用命令行参数来安装 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)，本文介绍了多个示例，你可以根据自己的需求自定义这些示例。

在每个示例中，`vs_enterprise.exe`、`vs_professional.exe` 和 `vs_community.exe` 表示 Visual Studio 安装引导程序的相应版本，这是启动下载过程的小型（大约 1 MB）文件。 若要使用其他版本，请用相应的安装引导程序名称进行替换。

> [!NOTE]
> 所有命令都需要进行管理提升，如果没有通过提升的提示符启动进程，将显示用户帐户控制提示。

> [!NOTE]
>  可以在命令行末尾使用 `^` 字符，将多行连接到一个命令中。 也可以直接在一行中编写这些代码行。 在 PowerShell 中，等效字符为反引号 (`` ` ``)。 

* 安装 Visual Studio 的最小实例，不显示任何交互式提示，但显示进度：
```
vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
```

* 无提示安装包含法语语言包的 Visual Studio 桌面实例，仅在产品安装后才返回值。
```
vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
```

> [!NOTE]
>  `--wait` 参数旨在用于批处理文件。 在批处理文件中，只有在安装完成后，才会继续执行下一个命令。 `%ERRORLEVEL%` 环境变量包含命令的返回值，如[使用命令行参数安装 Visual Studio](use-command-line-parameters-to-install-visual-studio.md) 页面所述。

* 下载 Visual Studio 核心编辑器（最起码的 Visual Studio 配置）。 仅包括英语语言包：

```cmd
vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
```

* 下载 .NET 桌面和 .NET Web 工作负载，以及所有推荐组件和 GitHub 扩展。 仅包括英语语言包：
```
vs_community.exe --layout C:\VS2017 ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
```

* 启动交互式安装 Visual Studio 2017 Enterprise 版本中的所有工作负载和组件：
```
vs_enterprise.exe --all --includeRecommended --includeOptional
```

* 借助 Node.js 开发支持，在已安装 Visual Studio 2017 Community 版本的计算机上安装 Visual Studio 2017 Professional 的第二个命名实例：
```
vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
```

* 从默认安装的 Visual Studio 实例中删除分析工具组件：
```
vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
```

## <a name="see-also"></a>请参阅

 * [Visual Studio 管理员指南](visual-studio-administrator-guide.md)
 * [使用命令行参数安装 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [创建 Visual Studio 2017 的脱机安装](create-an-offline-installation-of-visual-studio.md)

