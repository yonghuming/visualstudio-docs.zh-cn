---
title: "IDebugBinder3::GetExceptionObjectAndType | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3::GetExceptionObjectAndType"
helpviewer_keywords: 
  - "IDebugBinder3::GetExceptionObjectAndType 方法"
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder3::GetExceptionObjectAndType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法检索异常与对象，因此，如果有的话\)。  
  
## 语法  
  
```cpp  
HRESULT GetExceptionObjectAndType(  
   IDebugObject** ppException,  
   IDebugField**  ppField  
);  
```  
  
```c#  
int GetExceptionObjectAndType(  
   out IDebugObject ppException,  
   out IDebugField  ppField  
);  
```  
  
#### 参数  
 `ppException`  
 \[out\] 返回表示异常的对象。  
  
 `ppField`  
 \[out\] 返回表示可能会导致异常的特定字段的对象 \(这可能是一个空值\)。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
> [!NOTE]
>  若要验证是否有异常，请检查 `ppException`返回的值:如果它是一个空值，则异常没有与此对象。  
  
## 请参阅  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)