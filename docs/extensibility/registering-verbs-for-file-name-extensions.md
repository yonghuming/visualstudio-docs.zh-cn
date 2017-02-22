---
title: "注册文件扩展名的谓词 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "谓词注册"
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# 注册文件扩展名的谓词
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

与应用程序的文件扩展名关联通常具有首选的操作，当用户双击文件时发生。 此优先操作链接到的谓词，例如打开时，与操作相对应。  
  
 您可以注册在 HKEY\_CLASSES\_ROOT\\ 使用 Shell 注册表位于与扩展的编程标识符 \(ProgID\) 关联的谓词*progid*\\shell。 有关详细信息，请参阅 [文件类型](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx)。  
  
## 注册标准谓词  
 操作系统能够识别以下标准谓词︰  
  
-   打开  
  
-   Edit  
  
-   播放  
  
-   打印  
  
-   预览  
  
 只要有可能，注册标准谓词。 最常见的选择是动词 Open。 使用编辑谓词，只有在打开的文件和编辑该文件之间有明显差异。 例如，打开一个.htm 文件将其显示在浏览器中，而编辑一个.htm 文件启动 HTML 编辑器。 标准谓词被本地化与操作系统区域设置。  
  
> [!NOTE]
>  在注册标准谓词时, 未设置打开项的默认值。 默认值包含在菜单上的显示字符串。 操作系统提供标准谓词该的字符串。  
  
 项目文件应注册为在启动的新实例 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 当用户在打开该文件。 下面的示例演示的标准谓词注册 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 项目。  
  
```  
[HKEY_CLASSES_ROOT\.csproj]  
@="VisualStudio.csproj.8.0"  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList]  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]  
"VisualStudio.csproj.8.0"=""  
  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]  
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]  
@="C# Project file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]  
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""  
```  
  
 若要打开的文件中的现有实例 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ，注册 DDEEXEC 密钥。 下面的示例演示的标准谓词注册 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .cs 文件。  
  
```  
[HKEY_CLASSES_ROOT\.cs]  
@="VisualStudio.cs.8.0"  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithList]  
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]  
"VisualStudio.cs.8.0"=""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]  
@="C# Source file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]  
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]  
@="Open(\"%1\")"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]  
@="VisualStudio.8.0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]  
@="system"  
```  
  
## 设置默认的谓词  
 将使用默认动词是当用户双击 Windows 资源管理器中的文件执行的操作。 将使用默认动词是指定为默认值为 HKEY\_CLASSES\_ROOT\\ 动词*progid*\\Shell 键。 如果未不指定任何值，将使用默认动词是 HKEY\_CLASSES\_ROOT\\ 中指定的第一个动词*progid*\\Shell 键列表。  
  
> [!NOTE]
>  如果您想将更改默认的谓词中的并行部署的扩展插件，请考虑对安装和删除的影响。 在安装过程中会覆盖原始的默认值。  
  
## 请参阅  
 [Creating a File Association](_win32_file_associations)   
 [管理\-并行文件关联](../extensibility/managing-side-by-side-file-associations.md)