---
title: "IDebugPort2::GetPortRequest |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
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
ms.openlocfilehash: 58968a42b433ab87f556ff2dfbeb899fdcf3a681
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
获取以前使用以创建该端口 （如果可用） 的端口的说明。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetPortRequest(   
   IDebugPortRequest2** ppRequest  
);  
```  
  
```csharp  
int GetPortRequest(   
   out IDebugPortRequest2 ppRequest  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ppRequest`  
 [out]返回[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)表示用于创建该端口的请求的对象。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  返回`E_PORT_NO_REQUEST`如果端口不使用创建[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)端口请求。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [添加](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
