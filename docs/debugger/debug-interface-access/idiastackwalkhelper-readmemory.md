---
title: "IDiaStackWalkHelper::readMemory |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cccec7df8428db0a1e7c1fe2274475c2b723d760
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
从内存中的可执行文件的映像进行读取数据的块。  
  
## <a name="syntax"></a>语法  
  
```C++  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### <a name="parameters"></a>参数  
 `type`  
 [in]取值范围为[MemoryTypeEnum 枚举](../../debugger/debug-interface-access/memorytypeenum.md)枚举指定内存，无法读取的类型。  
  
 va  
 [in]从此处开始读取映像中的虚拟地址。  
  
 `cbData`  
 [in]以字节为单位的数据缓冲区的大小。  
  
 `pcbData`  
 [out]返回实际读取的字节数。 如果`pbData`是`NULL`，则表明这是总的可用数据的字节数。  
  
 `pbData`  
 [在中，out]读取的内存使用填充缓冲区。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="see-also"></a>另请参阅  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [MemoryTypeEnum 枚举](../../debugger/debug-interface-access/memorytypeenum.md)