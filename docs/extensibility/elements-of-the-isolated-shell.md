---
title: "独立 Shell 中的元素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio shell，隔离模式"
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# 独立 Shell 中的元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以修改注册表设置、 运行时设置和应用程序的独立的 shell 应用程序中，其.vsct、.pkgdef、 and.pkgundef 文件的入口点。  
  
## 注册表设置  
 .Pkgdef 和.pkgundef 文件修改独立的 shell 应用程序的注册表设置。 当运行该应用程序时，按以下顺序定义了注册表设置︰  
  
 当运行该应用程序时，按以下顺序定义了注册表设置︰  
  
1.  创建应用程序的注册表项。  
  
2.  通过定义指定的键和条目从应用程序的.pkgdef 文件更新注册表。  
  
3.  对于您的应用程序的一部分的每个包，注册表更新，将从该程序包的.pkgdef 文件。 由 $RootKey$ \\Packages\\ 应用程序的.pkgdef 文件中定义的每个包 {*vsPackageGuid*} 密钥包。  
  
4.  从 AppEnvConfig.pkgdef 和 BaseConfig.pkgdef 中的更新注册表 *Visual Studio SDK 安装路径*\\Common7\\IDE\\ShellExtensions\\Platform 目录。 这些文件是 Visual Studio 的一部分也是 Visual Studio Shell （独立的模式） 可再发行组件包的一部分。  
  
5.  通过删除指定的项和条目从.pkgundef 文件的应用程序更新注册表。  
  
## 运行时设置  
 当用户启动独立的 shell 应用程序时，它将调用 Visual Studio shell 的开始入口点。 当您的应用程序启动时，按以下方式定义应用程序设置︰  
  
1.  Visual Studio shell 检查应用程序注册表中有特定的密钥。 如果对启动入口点的调用中指定的某个项设置，则该值将覆盖注册表中的值。  
  
2.  如果既没有注册表，也没有入口点参数指定的值的设置，然后使用该设置的默认值。  
  
 当用户从命令行开始您的应用程序时，所有命令行参数将传递到 Visual Studio shell，都按 Devenv 执行的相同方式处理它们。 有关 Devenv 命令行开关的详细信息，请参阅 [Devenv 命令行开关](../ide/reference/devenv-command-line-switches.md) 和 [有关 VSPackage 开发 Devenv 命令行开关](../extensibility/devenv-command-line-switches-for-vspackage-development.md)。 有关如何将包注册为命令行开关的详细信息，请参阅 [添加命令行开关](../extensibility/adding-command-line-switches.md)。  
  
## 启动入口点  
 Appenvstub.dll 文件包含用于访问独立的 shell 的入口点。 当应用程序启动时，它将调用开始入口点的 Appenvstub.dll。  
  
 可以通过更改传递给启动入口点的最后一个参数的值来更改该应用程序的行为。 有关详细信息，请参阅[独立的 Shell 入口点参数 \(c \+ \+\)](../extensibility/isolated-shell-entry-point-parameters-cpp.md)。  
  
## 。Vsct 文件  
 .Vsct 文件允许您指定哪些标准 Visual Studio UI 元素是应用程序中提供。 有关更多信息，请参见[.Vsct 文件](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md)。  
  
## 。Pkgundef 文件  
 已安装 Visual Studio 的计算机上安装应用程序后，Visual Studio 注册表项的一个副本由应用程序。 默认情况下，应用程序使用计算机已安装的 Vspackage。 .Pkgundef 文件允许你排除注册表项，以便从应用程序中删除的 Visual Studio shell 或扩展的特定元素。 有关详细信息，请参阅[.Pkgundef 文件](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)。  
  
 .Pkgundef 文件允许你排除注册表项，以便从应用程序中删除的 Visual Studio shell 或扩展的特定元素。 有关详细信息，请参阅[.Pkgundef 文件](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)。  
  
 中列出的包 Guid，您可以排除集 [Visual Studio 功能的包 Guid](../extensibility/package-guids-of-visual-studio-features.md)。  
  
## 。Pkgdef 文件  
 .Pkgdef 文件，可以定义为应用程序时安装应用程序设置的注册表项。 .Pkgdef 文件的说明和 Visual Studio shell 使用的注册表项的列表，请参阅 [.Pkgdef 文件](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)。  
  
## 替换字符串  
 .Pkgdef 和.pkgundef 文件中使用的替换字符串中列出了 [替换字符串中使用。Pkgdef 和。Pkgundef 文件](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md)。  
  
## 其他设置  
 如果独立的 shell 应用程序依赖于 Microsoft.VisualStudio.GraphModel.dll，则需要将以下绑定重定向添加到独立 Shell 应用程序的.config 文件︰  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```