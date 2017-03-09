---
title: "MergeLocalizationDirectives 任务 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
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
- localizing XAML [WPF MSBuild], moving comments and attributes to a separate file
- MergeLocalizationDirectives task [WPF MSBuild], parameters
- MergeLocalizationDirectives task [WPF MSBuild]
- moving localization comments and attributes to a separate file [WPF MSBuild]
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
caps.latest.revision: 5
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
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: 94cd8bfa5807e46025f416ad87fc9d82990ef966
ms.lasthandoff: 02/22/2017

---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives 任务
<xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> 任务可将本地化属性和一个或多个 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 二进制格式文件的注释合并到整个程序集的单一文件中。  
  
## <a name="task-parameters"></a>任务参数  
  
|参数|说明|  
|---------------|-----------------|  
|`GeneratedLocalizationFiles`|必需的 **ITaskItem[]** 参数。<br /><br /> 指定单个 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 二进制格式文件的本地化指令文件列表。|  
|`OutputFile`|必需的 **String** 输出参数。<br /><br /> 指定编译的本地化指令程序集的输出路径。|  
  
## <a name="remarks"></a>备注  
 可将本地化属性和注释添加到 [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 内容中。 借助 [!INCLUDE[TLA#tla_wpf](../msbuild/includes/tlasharptla_wpf_md.md)] 本地化支持，可以去除本地化属性和注释，并将其放在独立于生成的程序集的 .loc 文件中。 可以通过使用 **LocalizationPropertyStorage** 属性执行此操作。 若要深入了解本地化属性和注释，以及 **LocalizationPropertyStorage**请参阅 [Localization Attributes and Comments](http://msdn.microsoft.com/Library/ead2d9ac-b709-4ec1-a924-39927a29d02f)（本地化属性和注释）。  
  
## <a name="example"></a>示例  
 下面的示例将多个 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 二进制文件的本地化注释合并到单个 .loc 文件中。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MergeLocalizationDirectivesTask">  
    <MergeLocalizationDirectives   
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"  
      OutputFile="obj\debug\WPFMSBuildSample.loc" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>另请参阅  
 [WPF MSBuild 引用](../msbuild/wpf-msbuild-reference.md)   
 [任务参考](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild 参考](../msbuild/msbuild-reference.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)   
 [Building a WPF Application (WPF)](http://msdn.microsoft.com/Library/a58696fd-bdad-4b55-9759-136dfdf8b91c)（生成 WPF 应用程序 (WPF)）
