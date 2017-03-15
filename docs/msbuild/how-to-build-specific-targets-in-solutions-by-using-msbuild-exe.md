---
title: "如何：使用 MSBuild.exe 生成解决方案中的特定目标 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: 10
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
translationtype: Human Translation
ms.sourcegitcommit: 3ba7680d46345f2b49019659c715cfb418933d39
ms.openlocfilehash: 22c46117f929447dc9a85b940bdaac911b35a7d8

---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>如何：使用 MSBuild.exe 生成解决方案中的特定目标
你可以使用 MSBuild 在解决方案中生成特定项目的特定目标。  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>在解决方案中生成特定项目的特定目标  
  
1.  在命令行中，键入 `MSBuild.exe <SolutionName>.sln`，其中 `<SolutionName>` 对应于包含要执行的目标的解决方案的文件名。  
  
2.  指定 *ProjectName* 格式的 **/t** 开关后的目标：*TargetName*。  
  
## <a name="example"></a>示例  
 以下示例执行 `NotInSlnFolder` 项目的 `Rebuild` 目标，然后执行位于 `NewFolder` 解决方案文件夹的 `InSolutionFolder` 项目的 `Clean` 目标。  
  
```  
msbuild SlnFolders.sln /t:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>另请参阅  
 [命令行参考](../msbuild/msbuild-command-line-reference.md)   
 [MSBuild 参考](../msbuild/msbuild-reference.md)   
 [ MSBuild](../msbuild/msbuild.md)  
 [MSBuild 概念](../msbuild/msbuild-concepts.md)


<!--HONumber=Feb17_HO4-->


