---
title: "确定项目的默认命名空间 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "自定义工具, 计算默认命名空间"
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# 确定项目的默认命名空间
为 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]，因此，如果 `CustomToolNamespace` 属性在输入文件设置，然后 `CustomToolNamespace` 的值将成为默认命名空间参数的值传递给 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> 方法。  否则， `wszDefaultNamespace` 参数传递给 `Generate` 的根命名空间始终是相同的。  有关命名空间的更多信息，请参见 [命名空间关键字](/dotnet/csharp/language-reference/keywords/namespace-keywords)。  
  
 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 使用文件夹基于命名空间。  即命名空间包括根命名空间，以及包含自定义工具的任何文件夹的名称。  每个文件夹名称转换为有效的标识符，因此，句点分隔任何名称。  例如，在中，如果输入文件是 FolderA \\FolderB\\FolderC\\MyInput.txt， and the root namespace is CL 9，则计算的默认命名空间为 **CL9.FolderA.FolderB.FolderC**。  
  
 ，在层次结构链包含一个 Web 引用 " 文件夹，此规则的例外情况发生。  例如，如果：  
  
-   FolderC 是 Web 引用 " 文件夹，命名空间是 **CL9.FolderC**。  
  
-   FolderB 是 Web 引用 " 文件夹，命名空间是 **CL9.FolderB.FolderC**。  
  
 即命名空间使用以下格式:  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## 请参阅  
 [实现单文件生成器](../extensibility/internals/implementing-single-file-generators.md)   
 [注册的单文件生成器](../extensibility/internals/registering-single-file-generators.md)   
 [公开到可视化设计器的类型](../extensibility/internals/exposing-types-to-visual-designers.md)