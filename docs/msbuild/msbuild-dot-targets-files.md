---
title: "MSBuild .Targets 文件 | Microsoft Docs"
ms.custom: 
ms.date: 02/24/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
caps.latest.revision: 17
author: kempb
ms.author: kempb
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
ms.sourcegitcommit: 3fb5627d2cc92c36e9dcf34f4b94796b6620321f
ms.openlocfilehash: e212fafb9eaf7891ff75084d4d5dd8b492718049
ms.contentlocale: zh-cn
ms.lasthandoff: 06/15/2017

---
# <a name="msbuild-targets-files"></a>MSBuild .Targets 文件
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 包括多个 .targets 文件，文件内容包含常见方案的项、属性、目标和任务。 这些文件将自动导入到大多数 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 项目文件中，以便简化维护，增强可读性。  

 项目通常会导入一个或多个 .targets 文件以定义它们的生成过程。 例如由 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 创建的 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 项目将导入 Microsoft.CSharp.targets，它可导入 Microsoft.Common.targets。 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 项目本身会定义特定于该项目的项和属性，但 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 项目的标准生成规则是在导入的 .targets 文件中进行定义。  

 `$(MSBuildToolsPath)` 值指定这些公用 .targets 文件的路径。 如果 `ToolsVersion` 为 4.0，则文件位于以下位置：`WindowsInstallationPath\Microsoft.NET\Framework\v4.0.30319\`  

> [!NOTE]
>  若要了解如何创建自己的目标，请参阅[目标](../msbuild/msbuild-targets.md)。 若要了解如何使用 `Import` 元素将项目文件插入到另一个项目文件，请参阅 [Import 元素 (MSBuild)](../msbuild/import-element-msbuild.md) 和[如何：在多个项目文件中使用同一目标](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)。  

## <a name="common-targets-files"></a>公用 .Targets 文件  

|.Targets 文件|描述|  
|-------------------|-----------------|  
|Microsoft.Common.targets|定义 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 和 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 项目标准生成过程中的步骤。<br /><br /> 由 Microsoft.CSharp.targets 和 Microsoft.VisualBasic.targets 文件导入，其中包括以下语句：`<Import Project="Microsoft.Common.targets" />`|  
|Microsoft.CSharp.targets|定义 Visual C# 项目标准生成过程中的步骤。<br /><br /> 由 Visual C# 项目文件 (.csproj) 导入，其中包括以下语句：`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`|  
|Microsoft.VisualBasic.targets|定义 Visual Basic 项目标准生成过程中的步骤。<br /><br /> 由 Visual Basic 项目文件 (.vbproj) 导入，其中包括以下语句：`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`|

## <a name="directorybuildtargets"></a>Directory.Build.targets
Directory.Build.targets 是用户定义的对目录下的项目提供自定义选项的文件。 除非属性 **ImportDirectoryBuildTargets** 设为 **false**，否则该文件将从 Microsoft.Common.targets 自动导入。

## <a name="see-also"></a>另请参阅  
 [Import 元素 (MSBuild)](../msbuild/import-element-msbuild.md)   
 [MSBuild 参考](../msbuild/msbuild-reference.md)  
 [MSBuild](../msbuild/msbuild.md)

