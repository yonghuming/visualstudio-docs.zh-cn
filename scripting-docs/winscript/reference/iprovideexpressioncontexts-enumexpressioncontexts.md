---
title: "IProvideExpressionContexts::EnumExpressionContexts | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProvideExpressionContexts.EnumExpressionContexts
apilocation: jscript.dll
helpviewer_keywords: 
  - "IProvideExpressionContexts::EnumExpressionContexts"
ms.assetid: ec5f0065-00df-41e6-b480-4c04ba464872
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProvideExpressionContexts::EnumExpressionContexts
返回表达式上下文的枚举数此元素已知的。  
  
## 语法  
  
```  
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### 参数  
 `ppedec`  
 \[in\]表达式上下文的枚举数此元素已知的。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 进程内调试管理器使用此方法可查找所有全局表达式上下文与特定线程。  
  
> [!NOTE]
>  此方法调用从线程相关的内部。  将由标识当前线程并返回适当的枚举数的实现。  
  
## 请参阅  
 [IProvideExpressionContexts 接口](../../winscript/reference/iprovideexpressioncontexts-interface.md)