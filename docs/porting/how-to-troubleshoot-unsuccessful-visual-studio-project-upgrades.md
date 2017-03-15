---
title: "如何：升级 Visual Studio 项目失败疑难解答 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VisualStudio.SourceControl.CannotOpenFromSourceControlDSW"
  - "vs.UpgradeProjectSolution.8.0"
helpviewer_keywords: 
  - "升级应用程序, Visual Studio"
  - "升级项目 [Visual Studio]"
  - "项目 [Visual Studio], 升级"
  - "Visual Studio 转换向导"
  - "转换向导"
ms.assetid: 842fe448-c044-4343-8eae-d81711cf48ba
caps.latest.revision: 30
caps.handback.revision: 30
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# 如何：升级 Visual Studio 项目失败疑难解答
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

有时Visual Studio不能完全转换从 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的早期版本的项目。  如果以下部分的提示不满足您的特定问题，则可以查找有关TechNet的 [Wiki:开发门户网站](http://go.microsoft.com/fwlink/?LinkId=254808)更多信息。  
  
## 项目因未找到文件而不运行。  
 项目文件包含 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 使用运行项目硬编码的文件路径，当按F5时。  这些路径可能包括 devenv.exe 和其他必需文件的位置。  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的已升级的版本，这些文件的路径可能已经更改。  
  
#### 解决文件路径不正确的问题  
  
1.  在文本编辑器中打开项目文件。  
  
2.  检查可能不正确的文件路径，包含一个 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 版本号的尤其是那些。  
  
3.  修改不正确的文件路径，使它们指向新的目标。  
  
## 项目因引用无效而不生成。  
 在升级 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]时，您可能还升级 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本。  如果项目包含引用在较新 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本中中断，则将无法正确解析。  这尤其可能发生在那些包含版本号的引用中，例如 `Microsoft.VisualStudio.Shell.Interop.8.0`。  
  
 如果您的代码具有许多无效的引用，最简单的解决方法可能是使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 多目标功能面向 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]的早期版本。  
  
#### 若要解决不正确的引用  
  
1.  在文本编辑器中打开项目文件。  
  
2.  打开项目属性。  
  
3.  选择正确的 **\*\*\* 目标framework \*\*\*** 值。  或者，可以修改 `<TargetFrameworkVersion>` 元素的值直接在项目文件。  
  
 如果您在升级后的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本希望项目运行，则必须更新项目的引用，并更新所有 `Imports` 或缩放的 `Using` 语句引用。  如果您的项目在IDE中加载，使用 **\*\*\* 解决方案资源管理器 \*\*\*** 或 **\*\*\* 引用管理器 \*\*\*** 对话框，可以更新引用。  
  
## 请参阅  
 [\/Upgrade](../ide/reference/upgrade-devenv-exe.md)   
 [Converting to ASP.NET 4](../Topic/Converting%20to%20ASP.NET%204.md)