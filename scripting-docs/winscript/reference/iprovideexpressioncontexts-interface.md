---
title: "IProvideExpressionContexts 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IProvideExpressionContexts 接口"
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProvideExpressionContexts 接口
提供一种枚举特定元素的已知表达式上下文。  脚本引擎通常实现此接口。  
  
 进程内调试管理器使用此接口查找所有全局表达式上下文与特定线程。  
  
> [!NOTE]
>  此接口调用从线程相关的内部。  将由标识当前线程并返回适当的枚举数的实现。  
  
## 方法  
 除了从 `IUnknown` 继承的方法之外，`IProvideExpressionContexts` 接口还公开下面的方法。  
  
|方法|说明|  
|--------|--------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|返回表达式上下文的枚举数此元素已知的。|