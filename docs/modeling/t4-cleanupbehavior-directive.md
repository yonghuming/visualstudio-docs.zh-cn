---
title: "T4 CleanUpBehavior 指令 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e5a211f-a3bf-4229-bff0-7d2e45b71c64
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: f60151ba4563c07cd9f6f6619982d8e6a8657ead
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="t4-cleanupbehavior-directive"></a>T4 CleanUpBehavior 指令
若要在处理文本模板之后删除 appDomain，请包括以下行：  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 文本模板是在独立于主机进程之外的 appDomain 中进行处理的。 在大多数情况下，在处理了一个文本模板之后，则将再次使用 appdomain 处理下一个模板。 但如果你指定 CleanupBehavior，则将删除 appDomain 并且将在新的 appDomain 中处理下一个模板。  
  
 这将减慢文本处理的速度，但可用于确保释放资源。  
  
 此指令将仅在 Visual Studio 主机中起作用。