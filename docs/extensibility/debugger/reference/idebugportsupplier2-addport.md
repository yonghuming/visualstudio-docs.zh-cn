---
title: "IDebugPortSupplier2::AddPort |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
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
ms.openlocfilehash: 2845b7c3d10b62c268843f934cf3730019afd657
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
将添加一个端口。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT AddPort(   
   IDebugPortRequest2* pRequest,  
   IDebugPort2**       ppPort  
);  
```  
  
```csharp  
int AddPort(   
   IDebugPortRequest2 pRequest,  
   out IDebugPort2    ppPort  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pRequest`  
 [in][IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)对象，描述要添加的端口。  
  
 `ppPort`  
 [out]返回[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)表示的端口的对象。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 此方法实际创建请求的端口，以及将其添加到活动的端口的端口供应商的内部列表。 [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)方法可以首先调用，以避免可能需要很长时间延迟。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)
