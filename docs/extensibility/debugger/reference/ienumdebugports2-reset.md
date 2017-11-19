---
title: "IEnumDebugPorts2::Reset |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugPorts2::Reset
helpviewer_keywords: IEnumDebugPorts2::Reset
ms.assetid: 67da406c-eadb-421e-ae12-e26e9866f262
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b4a9e3915c6b26b0cc6844a8dcd5aee2bb66f5e8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugports2reset"></a>IEnumDebugPorts2::Reset
将枚举重置为第一个元素。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 调用此方法，对下一个调用后[下一步](../../../extensibility/debugger/reference/ienumdebugports2-next.md)方法返回的枚举的第一个元素。  
  
## <a name="see-also"></a>另请参阅  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)