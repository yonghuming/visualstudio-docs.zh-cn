---
title: "“解决方案属性页”对话框 -&gt;“通用属性”-&gt;“调试源文件” | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.options.FindSource"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "“调试源文件”属性页"
  - "调试 [Visual Studio]，指定源和符号文件"
  - "源文件，在调试器中指定"
  - "调试器，源文件"
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# “解决方案属性页”对话框 -&gt;“通用属性”-&gt;“调试源文件”
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

该属性页指定调试解决方案时调试器查找源文件的位置。  
  
 若要访问**“调试源文件”**属性页，请在**“解决方案资源管理器”**中右键单击您的解决方案，并从快捷菜单中选择**“属性”**。  展开**“公共属性”**文件夹并单击**“调试源文件”**页。  
  
 **包含源代码的目录**  
 包含在调试解决方案时调试器搜索源文件的目录的列表。  还可搜索指定目录的子目录。  
  
 **不查找这些源文件**  
 输入不希望调试器读取的任何文件的名称。  如果调试器在以上指定的某个目录中找到这些文件之一，它将忽略该文件。  如果在调试时出现**“查找源”**对话框，而您单击**“取消”**，那么您搜索的文件将被添加到此列表中，以使调试器不再继续搜索该文件。  
  
## 请参阅  
 [调试器安全](../debugger/debugger-security.md)   
 [调试设置和准备](../debugger/debugger-settings-and-preparation.md)