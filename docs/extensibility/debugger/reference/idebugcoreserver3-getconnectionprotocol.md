---
title: "IDebugCoreServer3::GetConnectionProtocol |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCoreServer3::GetConnectionProtocol
helpviewer_keywords:
- IDebugCoreServer3::GetConnectionProtocol
ms.assetid: 368ced5b-c5d9-4090-a5b4-26ff400d1a55
caps.latest.revision: 8
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
ms.openlocfilehash: 8901f9fff01ecdfe21e3731df8b2d155fe250ac2
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# IDebugCoreServer3::GetConnectionProtocol
返回一个值，该值使用服务器和调试包之间进行通信的协议。  
  
## 语法  
  
```cpp  
HRESULT GetConnectionProtocol(  
   CONNECTION_PROTOCOL* pProtocol  
);  
```  
  
```csharp  
int GetConnectionProtocol(  
   CONNECTION_PROTOCOL[] pProtocol  
);  
```  
  
#### 参数  
 `pProtocol`  
 [out]返回从值之一[CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md)枚举。  
  
## 返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## 另请参阅  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md)
