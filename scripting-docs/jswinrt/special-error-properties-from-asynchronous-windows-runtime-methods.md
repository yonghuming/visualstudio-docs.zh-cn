---
title: "异步 Windows 运行时方法中的特殊错误属性 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45155584-06d8-4e7f-93a6-8564a93f643d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 120d8f699c8bedd0fe5762300203c5d5ec18e73e
ms.contentlocale: zh-cn
ms.lasthandoff: 08/11/2017

---
# <a name="special-error-properties-from-asynchronous-windows-runtime-methods"></a>异步 Windows 运行时方法中的特殊错误属性
可能难以在 JavaScript 中调试异步 Windows 运行时方法，因为可能会在调用堆栈的深层位置引发错误。 JavaScript `Error` 对象具有特定的额外属性，此类属性仅在应用以调试模式运行时，从异步 Windows 运行时方法引发错误时出现。  
  
## <a name="special-error-properties"></a>特殊错误属性  
 由调试模式下失败的 Windows 运行时异步操作生成的错误对象具有以下特殊属性：  
  
-   `asyncOpSource`（对象）获取有关执行出错的调用的原始位置的信息。 属性 `asyncOpSource.originatingCall`（字符串）显示源自异步操作的用户代码中的位置。  
  
-   asyncOpType（字符串）获取引发错误的异步操作类型的名称。  
  
 有关异步操作错误的详细信息，请参阅：  
  
-   [如何处理有关承诺的错误 ](https://msdn.microsoft.com/en-us/library/windows/apps/hh700337.aspx)  
  
-   [Windows 运行时错误疑难解答](http://msdn.microsoft.com/en-us/1ef7d7df-82ac-441d-8ad0-54ab1318de64)
