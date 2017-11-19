---
title: "IDebugArrayField::GetRank |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayField::GetRank
helpviewer_keywords: IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2467c8d4ed85a685de80511d68a20e24c047306e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
获取级别或数组的维数。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```csharp  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pdwRank`  
 [out]返回的排名。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回，则为 S_OK;否则，返回错误代码。  
  
## <a name="remarks"></a>备注  
 数组的秩对应于维度数。 在 c + + 和 C# 中，多维数组实际上是数组的数组，并因此可以视为只是一维数组 (和`GetRank`方法始终返回 1)。 在[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]另一方面，多维数组的处理方式不同，这样的数组的秩反映维度数 (和`GetRank`方法始终返回的维数)。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)