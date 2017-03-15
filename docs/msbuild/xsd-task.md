---
title: "XSD 任务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.xsd"
  - "VC.Project.VCXMLDataGeneratorTool.Namespace"
  - "VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "XSD 任务 (MSBuild (Visual C++))"
  - "MSBuild （Visual c + +），XSD 任务"
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# <a name="xsd-task"></a>XSD 任务
包装从源生成架构或类文件的 XML 架构定义工具 (Xsd.exe)。  
  
## <a name="parameters"></a>参数  
 下表介绍了 **XSD** 任务的参数。  
  
-   **AdditionalOptions**  
  
     可选 **String** 参数。  
  
     在命令行上指定的选项列表。 例如，“*/option1 /option2 /option#*”。 使用此参数可指定未由任何其他 **XSD** 任务参数表示的选项。  
  
-   **GenerateFromSchema**  
  
     可选 **String** 参数。  
  
     指定从指定架构生成的类型。  
  
     指定以下一个值，其中每个值对应于一个 XSD 选项。  
  
    -   **classes** - **/classes**  
  
    -   **dataset** - **/dataset**  
  
-   **语言**  
  
     可选 **String** 参数。  
  
     指定要用于生成的代码的编程语言。  
  
     从 **CS**（默认情况下为 C#）、**VB** (Visual Basic) 或 **JS** (JScript) 中进行选择。 也可指定实现 `System.CodeDom.Compiler.CodeDomProvider Class` 的类的完全限定名。  
  
-   **Namespace**  
  
     可选 **String** 参数。  
  
     为生成的类型指定运行时命名空间。  
  
-   **Sources**  
  
     必选 `ITaskItem[]` 参数。  
  
     定义可以被任务使用和发出的 MSBuild 源文件项的数组。  
  
-   **SuppressStartupBanner**  
  
     可选 **Boolean** 参数。  
  
     如果为 `true`，则在任务开始时阻止显示版权和版本号消息。  
  
-   **TrackerLogDirectory**  
  
     可选 **String** 参数。  
  
     指定跟踪器日志目录。  
  
## <a name="see-also"></a>另请参阅  
 [任务参考](../msbuild/msbuild-task-reference.md)


<!--HONumber=Feb17_HO4-->


