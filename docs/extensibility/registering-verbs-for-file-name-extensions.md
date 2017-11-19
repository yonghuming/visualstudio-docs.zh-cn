---
title: "注册文件扩展名谓词 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f430486c613e6281404110d4441d2a3d2100534
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="registering-verbs-for-file-name-extensions"></a>注册为文件扩展名的谓词
与应用程序的文件扩展名关联通常具有首选的操作，当用户双击文件时发生。 这首选的操作链接到的谓词，例如打开，对应于操作。  
  
 你可以注册在 hkey_classes_root。 使用位于的 Shell 密钥与扩展的编程标识符 (ProgID) 关联的谓词\\*progid*\shell。 有关详细信息，请参阅[文件类型](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx)。  
  
## <a name="registering-standard-verbs"></a>注册标准谓词  
 操作系统识别出以下标准谓词：  
  
-   打开  
  
-   Edit  
  
-   播放  
  
-   的  
  
-   预览  
  
 只要有可能，注册标准谓词。 最常见的选择是打开的谓词。 只有在打开的文件和编辑文件之间有明显差异，请使用编辑谓词。 例如，打开.htm 文件将其显示在浏览器中，而编辑.htm 文件启动 HTML 编辑器。 标准谓词已本地化的操作系统的区域设置。  
  
> [!NOTE]
>  注册标准谓词时, 未设置打开密钥的默认值。 默认值包含在菜单上的显示字符串。 操作系统提供标准谓词此字符串。  
  
 应注册项目文件以启动的新实例[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]当用户打开该文件。 下面的示例演示的标准谓词登记[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]项目。  
  
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
  
 若要打开的文件中的现有实例[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，注册 DDEEXEC 密钥。 下面的示例演示的标准谓词登记[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].cs 文件。  
  
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
  
## <a name="setting-the-default-verb"></a>设置默认的谓词  
 默认的谓词是当用户双击 Windows 资源管理器中的文件执行的操作。 默认的谓词是作为默认值为 hkey_classes_root。 指定的动词\\*progid*\Shell 密钥。 如果未不指定任何值，默认谓词是在注册表中指定的第一个动作\\*progid*\Shell 键列表。  
  
> [!NOTE]
>  如果你计划更改中的并行部署的扩展的默认谓词，请考虑对安装和删除的影响。 在安装过程会覆盖原始的默认值。  
  
## <a name="see-also"></a>另请参阅  
 [管理并行文件关联](../extensibility/managing-side-by-side-file-associations.md)