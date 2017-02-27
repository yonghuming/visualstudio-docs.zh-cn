---
title: "IDebugProcess2::GetAttachedSessionName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::GetAttachedSessionName"
helpviewer_keywords: 
  - "IDebugProcess2::GetAttachedSessionName"
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProcess2::GetAttachedSessionName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取调试此进程内会话的名称。  IDE 会显示此信息对特定计算机调试特定进程的用户。  
  
> [!NOTE]
>  此方法已弃用，因此，其实现应始终返回 `E_NOTIMPL`。  
  
## 语法  
  
```  
HRESULT GetAttachedSessionName(  
   BSTR* pbstrSessionName  
);  
```  
  
#### 参数  
 `pbstrSessionName`  
  
## 返回值  
 此方法应始终返回 `E_NOTIMPL`。  
  
## 请参阅  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)