---
title: IDebugProperty3::CreateObjectID | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: 10
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
ms.openlocfilehash: a930579367d13d92953e3fe6c349b53e9308db70
ms.contentlocale: zh-cn
ms.lasthandoff: 08/28/2017

---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Creates a unique ID for this property to ensure that it is unique among all other properties.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```csharp  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 This method is called when the session debug manager wants to make sure that this property is uniquely identified among all other properties. The debug engine (DE) supports this method unless the properties it deals with are already uniquely identified. If the DE does not support this method, it returns `E_NOTIMPL`.  
  
 Any unique ID created with `CreateObjectID` is destroyed when the [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) method is called; this also signals the end of the need for uniquely identifying this property.  
  
> [!NOTE]
>  There is no method to retrieve this unique ID, so the DE can do whatever it wants for unique IDs when the `CreateObjectID` method is called.  
  
## <a name="see-also"></a>See Also  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)