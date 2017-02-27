---
title: "MSBuild 项目文件架构引用 | Microsoft Docs"
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
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
caps.latest.revision: 19
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
ms.openlocfilehash: b3b609dfcdc51852f5f163f48c55ba1a1fa57ddb

---
# <a name="msbuild-project-file-schema-reference"></a>MSBuild 项目文件架构引用
提供列有所有 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] XML 架构元素及其可用属性和子元素的表。  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 使用项目文件向生成引擎指示要生成的内容以及生成方法。 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 项目文件是 XML 文件，其遵循 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] XML 架构。 本部分介绍 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 的 XML 架构定义 (.xsd) 文件。  
  
## <a name="msbuild-xml-schema-elements"></a>MSBuild XML 架构元素  
 下表列出了所有 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] XML 架构元素及其子元素和属性。  
  
|元素|子元素|特性|  
|-------------|--------------------|----------------|  
|[Choose 元素 (MSBuild)](../msbuild/choose-element-msbuild.md)|Otherwise<br /><br /> When|--|  
|[Import 元素 (MSBuild)](../msbuild/import-element-msbuild.md)|--|条件<br /><br /> Project|  
|[ImportGroup 元素](../msbuild/importgroup-element.md)|导入|条件|  
|[Item 元素 (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|条件<br /><br /> 排除<br /><br /> 包括<br /><br /> 删除|  
|[ItemDefinitionGroup 元素 (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Item*|条件|  
|[ItemGroup 元素 (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Item*|条件|  
|[ItemMetadata 元素 (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Item*|条件|  
|[OnError 元素 (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|条件<br /><br /> ExecuteTargets|  
|[Otherwise 元素 (MSBuild)](../msbuild/otherwise-element-msbuild.md)|选择<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|  
|[Output 元素 (MSBuild)](../msbuild/output-element-msbuild.md)|--|条件<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> TaskParameter|  
|[Parameter 元素](../msbuild/parameter-element.md)|--|输出<br /><br /> ParameterType<br /><br /> 必需|  
|[ParameterGroup 元素](../msbuild/parametergroup-element.md)|*Parameter*|--|  
|[Project 元素 (MSBuild)](../msbuild/project-element-msbuild.md)|选择<br /><br /> 导入<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> 目标<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|  
|[ProjectExtensions 元素 (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|  
|[Property 元素 (MSBuild)](../msbuild/property-element-msbuild.md)|--|条件|  
|[PropertyGroup 元素 (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Property*|条件|  
|[Target 元素 (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Task*|AfterTargets<br /><br /> BeforeTargets<br /><br /> 条件<br /><br /> DependsOnTargets<br /><br /> 输入<br /><br /> KeepDuplicateOutputs<br /><br /> 名称<br /><br /> 输出<br /><br /> 返回|  
|[Task 元素 (MSBuild)](../msbuild/task-element-msbuild.md)|输出|条件<br /><br /> ContinueOnError<br /><br /> *Parameter*|  
|[TaskBody 元素 (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Data*|评估|  
|[UsingTask 元素 (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> TaskBody|AssemblyFile<br /><br /> AssemblyName<br /><br /> 条件<br /><br /> TaskFactory<br /><br /> TaskName|  
|[When 元素 (MSBuild)](../msbuild/when-element-msbuild.md)|选择<br /><br /> ItemGroup<br /><br /> PropertyGroup|条件|  
  
## <a name="see-also"></a>另请参阅  
 [任务参考](../msbuild/msbuild-task-reference.md)   
 [条件](../msbuild/msbuild-conditions.md)   
 [MSBuild 参考](../msbuild/msbuild-reference.md)  
 [MSBuild](../msbuild/msbuild.md)


<!--HONumber=Feb17_HO4-->


