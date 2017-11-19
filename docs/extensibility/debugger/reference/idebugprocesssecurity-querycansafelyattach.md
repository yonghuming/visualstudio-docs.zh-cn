---
title: "IDebugProcessSecurity::QueryCanSafelyAttach |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ad6b7ffde868bf6b9dc4f9ef3bab9d9094ab765
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
此方法允许端口供应商联系，以显示一条警告之前用户将附加到一个不安全的过程。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>返回值  
 返回值如下所示：  
  
-   `S_OK`： 附加到进程，则可以安全和没有警告对话框中所示。  
  
-   `S_FALSE`： 附加可能是一个安全问题，并显示一个对话框以及一条警告。  
  
-   `FAILURE`： 附加到进程将失败。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)