---
title: "IDebugProperty3::CreateObjectID | Microsoft Docs"
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
  - "IDebugProperty3::CreateObjectID"
helpviewer_keywords: 
  - "IDebugProperty3::CreateObjectID"
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty3::CreateObjectID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

创建此特性唯一 ID 以确保它在其他属性中是唯一的。  
  
## 语法  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```c#  
int CreateObjectID();  
```  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 此方法，则当会议调试管理器若要确保时，此属性在其他属性中唯一标识。  调试 \(DE\)引擎它处理的此方法，除非属性中唯一标识。  如果 DE 不支持此方法，它返回 `E_NOTIMPL`。  
  
 在 `CreateObjectID` 创建的所有唯一 ID，当 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) 调用方法时，销毁;此还需要信号的结尾为唯一标识此属性的。  
  
> [!NOTE]
>  不检索此唯一 ID 的方法，因此， DE 可以执行将为唯一 ID 需要，在 `CreateObjectID` 调用方法时。  
  
## 请参阅  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)