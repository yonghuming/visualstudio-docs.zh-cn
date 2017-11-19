---
title: "Idiaenumdebugstreamdata:: Next |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumDebugStreamData::Next method
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ac3e4e59f96c1178a57dbcb7b936a69905fa265d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumdebugstreamdatanext"></a>IDiaEnumDebugStreamData::Next
检索指定枚举的序列中的记录数。  
  
## <a name="syntax"></a>语法  
  
```C++  
HRESULT Next (   
   ULONG  celt,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[],  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>参数  
 celt  
 [in]要检索的记录数。  
  
 cbData  
 [in]数据缓冲区，以字节为单位的大小。  
  
 pcbData  
 [out]返回返回的字节的数。 如果`data`为 NULL，则`pcbData`为所有请求的记录包含总的可用数据的字节数。  
  
 数据]  
 [out]是要调试流记录数据填充缓冲区。  
  
 pceltFetched  
 [在中，out]返回的记录数`data`。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`。 返回`S_FALSE`如果没有更多记录。 否则，返回错误代码。  
  
## <a name="see-also"></a>另请参阅  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)