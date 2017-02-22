---
title: "IDebugMethodField::EnumLocals | Microsoft Docs"
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
  - "IDebugMethodField::EnumLocals"
helpviewer_keywords: 
  - "IDebugMethodField::EnumLocals 方法"
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMethodField::EnumLocals
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

创建方法的选定的局部变量的枚举数。  
  
## 语法  
  
```cpp#  
HRESULT EnumLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```c#  
int EnumLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### 参数  
 `pAddress`  
 \[in\] 表示选择上下文或范围访问本地的调试地址的 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 对象。  
  
 `ppLocals`  
 \[out\] 返回表示本地的列表 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 对象;否则，; 如果没有本地用户，则返回 null 值。  
  
## 返回值  
 如果成功，则返回 S\_OK 或返回 S\_FALSE，如果没有本地。  否则，返回错误代码。  
  
## 备注  
 在包含给定的块中定义的变量只调试地址枚举。  如果所有本地包括任何编译器生成的本地是必需的，请调用 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) 方法。  
  
 方案可包含多个范围上下文或阻止。  例如，下面的阴影的方法包含三个范围，两个内部块和方法体。  
  
```c#  
public void func(int index)  
{  
    // Method body scope  
    int a = 0;  
    if (index == 1)  
    {  
        // Inner scope 1  
        int temp1 = a;  
    }  
    else  
    {  
        // Inner scope 2  
        int temp2 = a;  
    }  
}  
```  
  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) 对象表示 `func` 方法。  例如调用与 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 的 `EnumLocals` 方法设置为 `Inner Scope 1` 地址返回包含 `temp1` 变量的枚举，。  
  
## 请参阅  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)