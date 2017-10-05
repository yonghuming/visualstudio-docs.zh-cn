---
title: "IDebugClassField::EnumBaseClasses |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 21e2de0ff49be7b1ef25d2b9d5be81ef0aafc6dd
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
创建此类的基类的一个枚举器。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT EnumBaseClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumBaseClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ppEnum`  
 [out]返回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)表示基的类的列表对象。 如果没有基类，则返回 null 值。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回，则为 S_OK，没有基类是否返回 S_SH_NO_BASE_CLASSES (和`ppEnum`参数设置为 null 值); 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 中的枚举器对象的基类中最远程基类的最直接的 （或派生程度最高的） 基类的顺序指定。 例如，给定的 c + + 类：  
  
```  
class Root { }  
class Level1 : Root { }  
class Level2 : Level1 { }  
class MyClass : Level2 { }  
```  
  
 在枚举将按顺序返回基类`Level2`， `Level1`， `Root`。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
