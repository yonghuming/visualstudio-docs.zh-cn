---
title: "File &lt;name&gt; cannot be registered as an COM component. | Microsoft Docs"
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
  - "vs.message.VB_E_IDACANTREGTYPELIB"
  - "vs.message.0x800A0017"
ms.assetid: afaa12f4-db6a-475c-a572-3910250f0005
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# File &lt;name&gt; cannot be registered as an COM component.
文件无法添加到项目的引用。  以下情况都会导致该错误：文件已损坏，文件不包含类型库，文件使用了不兼容的文件类型，或系统没有足够的资源完成操作。  
  
### 更正此错误  
  
1.  验证确保该文件包含有效类型库并重试。  
  
     \- 或 \-  
  
     重新安装已安装了该文件的产品。  
  
    > [!NOTE]
    >  安装该文件的产品可能不是 Visual Studio。  
  
## 请参阅  
 [Edit Custom Component Set Dialog Box](http://msdn.microsoft.com/zh-cn/dc995bd7-afbf-4389-ba1c-f377b677ded7)