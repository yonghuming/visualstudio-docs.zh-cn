---
title: "IDebugPortRequest2::GetPortName |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortRequest2::GetPortName
helpviewer_keywords: IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab94c9bcb0ec686b9b2d8aba7378bbd55ca71c72
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
获取端口的名称。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```csharp  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pbstrPortName`  
 [out]返回的端口的名称。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)接口通常从传递调试包 （客户端） 到端口供应商 （服务器） 以获取连接到的端口。 调试包和端口提供程序均为感知的端口可能的选择。 如果一个简单的字符串可以描述端口，则`IDebugPortRequest2::GetPortName`方法有足够的信息来建立连接。 否则，其他接口可以由客户端，可以通过使用 server 获取`IDebugPortRequest2::QueryInterface`。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)