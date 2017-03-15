---
title: "如何调试 Windows API 函数？ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.api"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "API, 调试"
  - "调试 [C++], Windows API 函数"
  - "NT 符号和调试 Windows API 函数"
  - "Windows API 函数, 调试"
  - "Windows API, 调试 API 函数"
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何调试 Windows API 函数？
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果要调试加载了 NT 符号的 Windows API 函数，必须执行以下步骤。  
  
### 若要在加载了 NT 符号的 Windows API 函数中设置断点  
  
-   输入函数名以及函数所在 DLL 的名称。  在 32 位代码中，使用函数名的修饰形式。  例如，若要在 **MessageBeep** 上设置断点，必须输入以下内容。  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     若要获得修饰名，请参见[查看修饰名](http://msdn.microsoft.com/zh-cn/f79e2717-a4db-4d12-a689-69830cce2be0)。  
  
## 请参阅  
 [调试本机代码常见问题](../debugger/debugging-native-code-faqs.md)   
 [调试本机代码](../debugger/debugging-native-code.md)