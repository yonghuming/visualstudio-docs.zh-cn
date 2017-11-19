---
title: "查找 Visual Studio |Microsoft 文档"
ms.custom: 
ms.date: 08/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: ghogen
ms.openlocfilehash: c6dfe76ef1bfcfbcb0c39c33ea01668cc96f2596
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="locating-visual-studio"></a>查找 Visual Studio

从 Visual Studio 2017 年 1 开始，你可以安装相同版本或甚至版本的多个实例。 如果你想要在保留先前安装的同时预览主开发计算机上的新功能，这非常有用。 由于这些变化，没有单个环境变量或注册表值可用于查找的实例。 相反，你可以使用[COM 查询 API](https://msdn.microsoft.com/library/microsoft.visualstudio.setup.configuration.aspx)查找基于条件与你的扩展相关的实例。

这是与用于本机和托管代码的 NuGet 包的快速、 只读的 API。

| 代码 | Package |
| ---- | --- |
| Native | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Managed | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

你可以找到给定路径或当前进程的单个实例或枚举所有实例。 请参阅[我们的示例](https://github.com/Microsoft/vs-setup-samples)有关如何查找 Visual Studio 的完整示例。

## <a name="tools"></a>工具

若要查找 Visual Studio 和其他工具生成环境、 PowerShell 脚本、 安装程序、 和更多方案中，我们有许多开放源代码工具可以直接使用或与你自己的脚本一起重新分发。

| Project | 描述 |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | 单个文件本机可执行文件才能找到满足条件，例如发布或预发行版、 已安装哪种产品，日期和安装的工作负荷的实例。 此外支持查找 Visual Studio 2010 和更高版本，尽管较少的信息返回的有关 Visual Studio 2017 和更高版本。 请参阅[wiki](https://github.com/Microsoft/vswhere/wiki)有关示例。 |
| [VSSetup cmdlet](https://github.com/Microsoft/vssetup.powershell) | 支持的 PowerShell cmdlet 2.0 和更高版本，返回可用来查找实例基于相同的条件作为对象的丰富信息_vswhere_和以发现实例有关的更多属性。 请参阅[wiki](https://github.com/Microsoft/vssetup.powershell/wiki)有关示例。 |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | 自动定位_VSIXInstaller_并传递通过命令行安装_*.vsix_文件。 这可以在安装程序没有为查询 Api 直接支持。 请参阅[wiki](https://github.com/Microsoft/vsixbootstrapper/wiki)有关示例。 |

## <a name="see-also"></a>另请参阅

* [Visual Studio 自 2017 年 1 安装程序的变化](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup)
