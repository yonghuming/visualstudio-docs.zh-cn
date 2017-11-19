---
title: "IntelliSenseHostFlags |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d8e00768e544dbd6bb37a4de70e0f730fe967a70
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
指定 IntelliSense 主机标志。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum IntellisenseHostFlags  
{  
    IHF_READONLYCONTEXT      = 0x00000001  
    IHF_NOSEPARATESUBJECT    = 0x00000002  
    IHF_SINGLELINESUBJECT    = 0x00000004  
    IHF_FORCECOMMITTOCONTEXT = 0x00000008  
    IHF_OVERTYPE             = 0x00000010  
};  
```  
  
#### <a name="parameters"></a>参数  
  
|成员|描述|  
|-------------|-----------------|  
|`IHF_READONLYCONTEXT`|上下文缓冲区是只读的。|  
|`IHF_NOSEPARATESUBJECT`|没有使用者的文本。 上下文缓冲区包含 IntelliSense 目标 (意味着`!IHF_READONLYCONTEXT`)。|  
|`IHF_SINGLELINESUBJECT`|不支持多行的使用者文本。|  
|`IHF_FORCECOMMITTOCONTEXT`|与 `CanCommitIntoReadOnlyBuffer` 相同。|  
|`IHF_OVERTYPE`|编辑 （使用者或上下文） 中时，应该在改写模式来完成。|  
  
## <a name="requirements"></a>要求  
 SingleFileeditor.idl  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.VisualStudio.TextManager.Interop>