---
title: "IDebugProgram2::Terminate |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::Terminate
helpviewer_keywords: IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 16f9e718eaebbb1ab82ea96c08661622ef7e1cd1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
终止程序。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 如果可能，将终止并从进程; 中卸载程序否则，请调试引擎 (DE) 将执行任何必要的清除。  
  
 此方法或[终止](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)由 IDE、 通常以响应停止所有调试用户调用方法。 此方法的实现应，理想情况下，终止进程内的程序。 如果这是不可能，DE 应阻止程序运行此过程中更多 （和执行任何必要的清理操作）。 如果`IDebugProcess2::Terminate`由 IDE 调用了方法，将一段时间后终止的整个过程`IDebugProgram2::Terminate`调用方法。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [终止](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)