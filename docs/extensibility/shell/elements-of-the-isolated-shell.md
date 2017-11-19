---
title: "元素的独立 Shell |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 32ca2aa4c3c37a4ff407ec06031ec8db16b54ea7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="elements-of-the-isolated-shell"></a>独立 Shell 中的元素
你可以修改注册表设置、 运行时设置和应用程序的独立的 shell 应用程序，其.vsct、.pkgdef、 and.pkgundef 文件的入口点。  
  
## <a name="registry-settings"></a>注册表设置  
 .Pkgdef 和.pkgundef 文件修改独立的 shell 应用程序的注册表设置。 当运行应用程序时，按以下顺序定义的注册表设置：  
  
 当运行应用程序时，按以下顺序定义的注册表设置：  
  
1.  创建应用程序的注册表项。  
  
2.  通过定义指定的项和条目情况下，注册表更新应用程序的.pkgdef 文件。  
  
3.  对于每个属于你的应用程序的包，该包的.pkgdef 文件更新注册表。 每个包由应用程序的.pkgdef 文件中 $RootKey$ \Packages\\{*vsPackageGuid*} 密钥包。  
  
4.  从 AppEnvConfig.pkgdef 和 BaseConfig.pkgdef 中的更新注册表*Visual Studio SDK 安装路径*\Common7\IDE\ShellExtensions\Platform 目录。 这些文件是 Visual Studio 的一部分，并且 Visual Studio Shell （独立的模式） 的可再发行组件包的一部分。  
  
5.  通过删除指定的项和条目从.pkgundef 文件的应用程序更新注册表。  
  
## <a name="run-time-settings"></a>运行时间设置  
 当用户启动独立的 shell 应用程序时，它将调用 Visual Studio shell 的开始入口点。 你的应用程序启动时，按以下方式定义应用程序设置：  
  
1.  Visual Studio shell 检查特定密钥的应用程序注册表。 如果对开始入口点调用中指定的键的设置，此值将重写注册表中的值。  
  
2.  如果既没有注册表，也没有入口点参数指定设置的值，然后使用设置的默认值。  
  
 当用户从命令行启动你的应用程序时，所有的命令行开关将传递给都按 Devenv 执行的相同方式处理它们的 Visual Studio shell。 有关 Devenv 开关的详细信息，请参阅[Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)和[Devenv 命令行开关，VSPackage 开发](../devenv-command-line-switches-for-vspackage-development.md)。 有关如何将包注册的命令行开关的详细信息，请参阅[添加命令行开关](../adding-command-line-switches.md)。  
  
## <a name="the-start-entry-point"></a>开始入口点  
 Appenvstub.dll 文件包含用于访问独立的 shell 的入口点。 当应用程序启动时，它将调用开始入口点的 Appenvstub.dll。  
  
 可以通过更改传递给开始入口点的最后一个参数的值来更改应用程序的行为。 有关详细信息，请参阅[独立 Shell 入口点参数 （c + +）](isolated-shell-entry-point-parameters-cpp.md)。  
  
## <a name="the-vsct-file"></a>。Vsct 文件  
 .Vsct 文件允许您指定的标准的 Visual Studio UI 元素将应用程序中可用。 有关详细信息，请参阅[。Vsct 文件](modifying-the-isolated-shell-by-using-the-dot-vsct-file.md)。  
  
## <a name="the-pkgundef-file"></a>。Pkgundef 文件  
 在已安装 Visual Studio 的计算机上安装应用，Visual Studio 的注册表项的副本创建应用程序。 默认情况下，应用程序使用计算机已安装的 Vspackage。 .Pkgundef 文件允许你排除注册表项以删除从应用程序的 Visual Studio shell 或扩展的特定元素。 有关详细信息，请参阅[。Pkgundef 文件](modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)。  
  
 .Pkgundef 文件允许你排除注册表项以删除从应用程序的 Visual Studio shell 或扩展的特定元素。 有关详细信息，请参阅[。Pkgundef 文件](modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)。  
  
 中列出的包 Guid，你可以排除的一套[包 Guid 的 Visual Studio 功能](package-guids-of-visual-studio-features.md)。  
  
## <a name="the-pkgdef-file"></a>。Pkgdef 文件  
 .Pkgdef 文件，可以定义应用程序时安装的应用程序设置的注册表项。 .Pkgdef 文件的说明和 Visual Studio 行解释器使用的注册表项的列表，请参阅[。Pkgdef 文件](modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)。  
  
## <a name="substitution-strings"></a>替换字符串  
 中列出的.pkgdef 和.pkgundef 文件中使用的替换字符串[中使用的替换字符串。Pkgdef 和。Pkgundef 文件](substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md)。  
  
## <a name="other-settings"></a>其他设置  
 如果你的独立的 shell 应用程序依赖于 Microsoft.VisualStudio.GraphModel.dll，你需要将以下绑定重定向添加到独立 Shell 应用程序的.config 文件：  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```