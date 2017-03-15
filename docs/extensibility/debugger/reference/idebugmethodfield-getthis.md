---
title: "IDebugMethodField::GetThis | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::GetThis"
helpviewer_keywords: 
  - "IDebugMethodField::GetThis 方法"
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugMethodField::GetThis
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取包含方法的对象的 `this` \(在 [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]的`Me` \) 指针。  
  
## 语法  
  
```cpp#  
HRESULT GetThis(   
   IDebugClassField** ppClass  
);  
```  
  
```c#  
int GetThis(  
   out IDebugClassField ppClass  
);  
```  
  
#### 参数  
 `ppClass`  
 \[out\] 返回表示 “this”指针的 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 对象。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 备注  
 在面向对象的语言，通常具有提示的指针类的当前实例。  这称为 " 在 C\#\/C\+\+ 的 `this` 和为 [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]的 `Me` 。  
  
## 请参阅  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)