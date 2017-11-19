---
title: "IDebugProgramNode2::GetEngineInfo |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramNode2::GetEngineInfo
helpviewer_keywords: IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5519da3e6db7422f3b8aacca3a41a45fdff06923
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
获取的名称和运行程序的调试引擎 (DE) 的标识符。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetEngineInfo (   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```csharp  
int GetEngineInfo(  
   out string pbstrEngine,   
   out Guid pguidEngine  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pbstrEngine`  
 [out]返回运行程序 DE 的名称 (c + + 专用： 这可以是 null 指针，该值指示调用方不涉及引擎的名称)。  
  
 `pguidEngine`  
 [out]返回运行程序 DE 的全局唯一标识符 (c + + 专用： 这可以是 null 指针，该值指示调用方不感兴趣的引擎的 GUID)。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)