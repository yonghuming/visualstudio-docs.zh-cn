---
title: "IDebugClassField::GetEnclosingClass |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugClassField::GetEnclosingClass
helpviewer_keywords: IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fbec5ac48280cf10bc89e73faca0779384bf3549
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
获取包含此类的类。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```csharp  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ppClassField`  
 [out]返回[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)对象表示封闭类。 如果没有任何封闭类，则返回 null 值。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回，则为 S_OK;否则，返回错误代码。  
  
## <a name="remarks"></a>备注  
 如果此类表示[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)对象是一个嵌套的类，则`ppClassField`参数返回`IDebugClassField`对象表示封闭类。 例如，给定此类定义：  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 调用`GetEnclosingClass`方法`IDebugClassField`对象，表示`NestedClass`类返回`IDebugClassField`表示类对象`RootClass`。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)