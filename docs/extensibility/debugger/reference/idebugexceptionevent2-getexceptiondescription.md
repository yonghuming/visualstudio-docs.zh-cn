---
title: "IDebugExceptionEvent2::GetExceptionDescription | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExceptionEvent2::GetExceptionDescription"
helpviewer_keywords: 
  - "IDebugExceptionEvent2::GetExceptionDescription"
ms.assetid: d07d458f-5729-47e4-9b77-1bd59c61a75a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugExceptionEvent2::GetExceptionDescription
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取异常的可显示的标题。  
  
## 语法  
  
```cpp#  
HRESULT GetExceptionDescription(   
   BSTR* pbstrDescription  
);  
```  
  
```c#  
int GetExceptionDescription(   
   out string pbstrDescription  
);  
```  
  
#### 参数  
 `pbstrDescription`  
 \[out\] 返回一个异常的可显示的说明。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 ，发生异常时，此方法返回的字符串通常是异常的名称并显示在 **输出** 窗口。  
  
## 请参阅  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)