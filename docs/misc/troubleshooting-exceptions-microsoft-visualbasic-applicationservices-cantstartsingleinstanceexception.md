---
title: "关于异常的疑难解答：Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CantStartSingleInstanceException 异常"
  - "Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException 异常"
ms.assetid: 3639f15d-9547-43da-8145-60da34782991
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException
当单实例应用程序的第二个实例未能连接到原始实例时，所引发的异常。  
  
## 备注  
 可能导致该问题的原因包括：  
  
-   原始实例停止了响应。  
  
-   应用程序没有创建内核对象的权限。  
  
     内核对象的基名称是通过串联程序集的 GUID、主版本号和次版本号得到的。 例如，基名称可以是 3639f15d\-9547\-43da\-8145\-60da347829915.1。  
  
## 请参阅  
 <xref:Microsoft.VisualBasic.ApplicationServices.CantStartSingleInstanceException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)