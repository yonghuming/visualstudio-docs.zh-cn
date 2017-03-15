---
title: "Resource transformation for file &#39;file&#39; failed. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.resx_generator_failed"
ms.assetid: 6b537d38-1da9-4f5f-9ae9-1f26e260c2ac
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Resource transformation for file &#39;file&#39; failed. &lt;reason&gt;
用于将 .resx 文件转换为二进制 .resources 文件的资源处理器失败。  将特定的原因（如果有的话）追加到字符串的末尾。  若发生此错误，则生成进程将会失败。  
  
 此错误极有可能由 .resx 文件错误引起。  例如，该文件可能已经在文本编辑器中打开和修改过。  
  
 如果收到 \<原因\> 为“已添加项。  字典中的关键字:‘NewControlName.\<Property Name\>’所添加的关键字:‘ControlName.\<Property Name\>’”，请按照下面的步骤再现并更正错误。  
  
### 再现此错误  
  
1.  创建新的 Windows 应用程序。  默认情况下，将创建 Form1。  
  
2.  在**“视图”**菜单上，单击**“属性”**。  
  
3.  在**“属性”**窗口中，将**“Localizable”**属性设置为 `True`。  
  
4.  在**“属性”**窗口中，单击**“Language”**，然后将值设置为“日语”。  
  
5.  将一个按钮从工具箱拖到窗体上。  
  
6.  将该按钮的名称从“Button1”更改为“BUTTON1”。  
  
7.  在**“生成”**菜单上，单击**“生成解决方案”**。  
  
### 更正此错误  
  
1.  在**“文件”**菜单上，指向**“打开”**，然后单击**“文件”**。  
  
2.  查找 Form1.resx 文件，然后单击**“确定”**。  将显示 Form1.resx。  
  
3.  查找原始的键值，然后将其手动从数据列表中删除。  例如，您具有一个名为“Button1”的按钮。  应将此按钮的名称修改为“BUTTON1”。  “Button1”和“BUTTON1”的键值都保存在 Form1.resx 中。  移除“Button1”的所有项，然后重新生成该项目。  
  
## 请参阅  
 [Resources in .Resx File Format](http://msdn.microsoft.com/zh-cn/0c476133-87e4-47e8-b0ef-4b88f4ef3dc5)   
 [File Types and File Extensions in Visual Basic and Visual C\#](http://msdn.microsoft.com/zh-cn/f793852c-da06-4d52-a826-65f635844772)