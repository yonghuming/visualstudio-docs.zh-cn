---
title: "关于异常的疑难解答：System.MissingMethodException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "MissingMethodException 类"
ms.assetid: 1ca4c351-ca26-4a6d-a5a1-c484ac193e2e
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.MissingMethodException
尝试动态访问不存在的方法时，将引发 <xref:System.MissingMethodException> 异常。  
  
## 相关提示  
 **如果类库中的某个方法已被移除或重命名，请重新编译引用该方法的所有程序集。**  
 此异常通常在尝试动态访问未通过其强名称引用的程序集中已删除或重命名的方法时引发。  
  
## 备注  
 正在调用非托管函数时，如果 CLR 无法找到该模块或函数，将引发此异常。  
  
## 请参阅  
 <xref:System.MissingMethodException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [互操作性疑难解答](/dotnet/visual-basic/programming-guide/com-interop/troubleshooting-interoperability)