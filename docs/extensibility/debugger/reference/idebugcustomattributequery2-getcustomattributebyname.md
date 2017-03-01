---
title: "IDebugCustomAttributeQuery2::GetCustomAttributeByName |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: bc1b59d4f13029a765f11dfd4fe3dbe12778d00c
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
获取给定名称的自定义特性的自定义特性字节数。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT GetCustomAttributeByName(   
   LPCOLESTR pszCustomAttributeName,  
   BYTE*     ppBlob,  
   DWORD*    pdwLen  
);  
```  
  
```c#  
int GetCustomAttributeByName(  
   [In] string        pszCustomAttributeName,   
   [In, Out] byte[]   ppBlob,   
   [In, Out] ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pszCustomAttributeName`  
 [in]包含要查找的自定义特性的名称的字符串。  
  
 `ppBlob`  
 [in、 out]使用自定义特性字节填充的数组。  
  
 `pdwLen`  
 [in、 out]指定要在中返回的字节的最大数`ppBlob`数组中移除并返回实际写入到该数组的字节数。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回 S_OK，或如果自定义特性不存在，则返回 S_FALSE。 否则，返回错误代码。  
  
## <a name="remarks"></a>备注  
 设置`ppBlob`参数为 null 值，以返回数量的属性的可用字节。 分配一个数组，然后将为该数组中的传递`ppBlob`参数。  
  
 属性字节表示的原始数据的自定义属性。  
  
 如果`ppBlob`和`pdwLen`参数被设置为 null 值，可以使用此方法以确定是否只是存在自定义属性。 更容易，但是，也可以调用[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)方法。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
