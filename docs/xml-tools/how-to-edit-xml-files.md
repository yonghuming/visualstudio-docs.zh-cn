---
title: "如何：编辑 XML 文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# 如何：编辑 XML 文件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

“XML 编辑器”是 XML 文件的新编辑器。该编辑器可以用于独立的 XML 文件，也可以用于与 Visual Studio 项目关联的文件。XML 编辑器与以下文件扩展名关联：.config、.dtd、.xml、.xsd、.xdr、.xsl、.xslt 和 .vssettings。“XML 编辑器”还与任何其他没有注册特定编辑器并且包含 XML 或 DTD 内容的文件类型关联。  
  
> [!NOTE]
>  XHTML 文档由“HTML 编辑器”处理。  
  
### 编辑 XML 文件  
  
1.  双击要编辑的文件。  
  
### 向项目中添加新的 XML 文件  
  
1.  在“项目”菜单中选择“添加新项”。  
  
2.  在“模板”窗格中选择“XML 文件”。  
  
3.  在“名称”字段中输入文件名，然后按“添加”。  
  
     该 XML 文件将添加到项目中并在“XML 编辑器”中打开。该文件包含默认的 XML 声明 `<?xml version="1.0" encoding="utf-8" ?>`。  
  
### 向项目中添加现有的 XML 文件  
  
1.  从“项目”菜单中，选择“添加现有项”。  
  
     此时出现“添加现有项”对话框。  
  
2.  选择 XML 文件，然后按“添加”。  
  
### 新建 XML 或 XSLT 文件  
  
1.  在“文件”菜单中选择“新建”。  
  
     此时出现“新建文件”对话框。  
  
2.  要新建 XML 文件，选择“XML 文件”；要新建 XSLT 样式表，选择“XSLT 文件”。  
  
3.  单击“打开”。  
  
### 为 XML 文件创建项目  
  
1.  在“文件”菜单中选择“新建”，再选择“项目”。  
  
     此时出现“新建项目”对话框。  
  
2.  选择所需的代码语言，再选择“空白项目”，然后单击“确定”。  
  
3.  将 XML 文件添加到项目中。  
  
     “XML 编辑器”找到您添加到此项目中的架构，并在此项目打开时，使用这些架构在您编辑的任何 XML、架构或 XSLT 文件中进行验证和 IntelliSense。  
  
## 请参阅  
 [XML 编辑器](../xml-tools/xml-editor.md)   
 [XML 文档属性，“属性”窗口](../xml-tools/xml-document-properties-properties-window.md)   
 [如何：从 XML 文档创建 XML 架构](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)