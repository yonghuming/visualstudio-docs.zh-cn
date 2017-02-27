---
title: "格式化，XML，文本编辑器，“选项”对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# 格式化，XML，文本编辑器，“选项”对话框
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用此对话框可以指定“XML 编辑器”的格式化设置。可以从“工具”菜单访问“选项”对话框。  
  
> [!NOTE]
>  如果从“选项”对话框中依次选择“文本编辑器”文件夹、**XML** 文件夹，然后选择“格式化”选项，可以获得下列设置。  
  
## 属性  
 **保留手动属性格式化**  
 属性不会重新格式化。这是默认设置。  
  
> [!NOTE]
>  如果属性在多行上，编辑器将对每行属性进行缩进，以便与父元素的缩进匹配。  
  
 **使每个属性在自己的行上对齐**  
 使第二个以及后续的属性纵向对齐，以便与第一个属性的缩进匹配。以下 XML 文本是如何对齐属性的示例。  
  
```  
<item id = "123-A"  
      name = "hammer"  
      price = "9.95">  
</item>  
```  
  
## 自动重新格式化  
 **在从剪贴板粘贴时**  
 重新格式化从剪贴板粘贴的 XML 文本。  
  
 **完成结束标记时**  
 在完成结束标记时重新格式化元素。  
  
## 混合内容  
 **默认情况下保留混合内容**  
 确定编辑器是否重新格式化混合内容。默认情况下，编辑器尝试重新格式化混合内容，除非在 `xml:space="preserve"` 范围内找到该内容。  
  
 如果元素中包含文本和标记的混合，将认为内容是混合内容。以下是包含混合内容的元素示例。  
  
```  
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
</dir>  
```  
  
## 请参阅  
 [XML 文档属性，“属性”窗口](../xml-tools/xml-document-properties-properties-window.md)   
 [“XML 编辑器”的组件](../xml-tools/xml-editor-components.md)