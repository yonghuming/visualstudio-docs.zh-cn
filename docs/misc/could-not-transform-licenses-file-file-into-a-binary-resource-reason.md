---
title: "Could not transform licenses file &#39;file&#39; into a binary resource. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.licx_generator_failed"
ms.assetid: 875e948c-d7a3-4ffc-be0d-f341de5f6310
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not transform licenses file &#39;file&#39; into a binary resource. &lt;reason&gt;
出于某种原因，用于将 .licx 文件转换为二进制资源的许可证处理器失败。  
  
 此错误通常是由 .licx 文件错误引起的。  例如，该文件可能已经在文本编辑器中打开和修改过。  
  
 若发生此错误，则生成进程将会失败。  
  
### 更正此错误  
  
1.  在解决方案资源管理器中选择项目。  
  
2.  在**“项目”**菜单中单击**“显示所有文件”**。  
  
3.  在“解决方案资源管理器”中，展开 obj 文件夹，再展开**“Debug”**文件夹。  
  
4.  找到名为“myApplication.exe.licenses”的文件，其中 myApplication 为 Windows 窗体应用程序的名称。  
  
5.  删除此文件，并重新生成解决方案。  
  
## 请参阅  
 [如何：授予组件和控件许可权限](../Topic/How%20to:%20License%20Components%20and%20Controls.md)