---
title: "如何：选择要使用的 XML 架构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# 如何：选择要使用的 XML 架构
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

XML 编辑器提供的架构缓存位于 %InstallDir%\\Xml\\Schemas 目录中。架构缓存中包括用于智能感知和 XML 文档验证的常见 XML 架构。  
  
 **“架构”**文档属性用于选择一个或多个要使用的 XML 架构定义语言 \(XSD\) 架构。使用该属性可以从架构缓存中选择架构，也可以指定不在缓存中的架构。  
  
 指定的架构与所有其他 XML 文档属性一起保存在隐藏解决方案用户选项文件 \(.suo\) 中。因此，下次打开该解决方案时，不必重新输入这些值。  
  
> [!NOTE]
>  编辑器可以使用内联架构或 `xsd:schemaLocation` 属性引用的架构来进行验证。有关更多信息，请参见 [XML 文档验证](../xml-tools/xml-document-validation.md)。  
  
### 从架构缓存中选择 XML 架构  
  
1.  在“XML 编辑器”中打开文件。  
  
2.  在文档属性窗口中单击“架构”字段上的按钮。  
  
     即会显示**“XML 架构”**对话框。该对话框列出架构缓存中所有扩展名为 .xsd 的架构（包括在 catalog.xml 文件中引用的架构），还列出任何当前解决方案中的架构、在 Visual Studio 中打开的架构、在 `xsd:schemaLocation` 属性中引用的架构以及在**“架构”**属性中引用的架构。  
  
3.  通过执行下列操作之一选择用于验证的架构：  
  
    -   选择一个**“XML 架构”**对话框中列出的架构，单击**“使用”**列，然后选择**“使用此架构”**。  
  
     \- 或 \-  
  
    -   选择多个**“XML 架构”**对话框中列出的架构，右键单击并选择**“使用此架构”**。  
  
4.  单击“确定”。  
  
     所选架构的列表复制回“架构”文档属性。  
  
### 将 XML 架构添加到架构缓存中  
  
1.  在文档属性窗口中单击**“架构”**字段上的按钮。  
  
2.  单击“添加”。  
  
     这会打开**“打开 XSD 架构”**对话框。  
  
3.  浏览并选择要添加到架构缓存的架构。  
  
4.  单击**“打开”**。  
  
     架构添加到架构缓存，并且**“使用”**列值设置为**“使用此架构”**。  
  
### 从架构缓存中删除 XML 架构  
  
1.  在文档属性窗口中单击**“架构”**字段上的按钮。  
  
2.  选择要移除的架构，然后单击**“移除”**。  
  
     此架构即会从内存中的架构缓存中移除，但不会从文件系统中移除。  
  
    > [!NOTE]
    >  如果您还有通过 `schemaLocation` 属性引用的架构，或者有匹配的 `targetNamespace`，则在这种情况下，由于自动关联，不能使用**“移除”**。此时，建议在**“使用”**列中将此架构标记为**“不使用所选架构”**。  
  
## 请参阅  
 [架构缓存](../xml-tools/schema-cache.md)   
 [XML 架构对话框](../xml-tools/xml-schemas-dialog-box.md)   
 [XML 编辑器](../xml-tools/xml-editor.md)