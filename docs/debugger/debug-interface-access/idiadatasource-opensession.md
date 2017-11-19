---
title: "Idiadatasource:: Opensession |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72fa36bd077a08484c225e1349134929e541d074
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
将打开一个可用于查询符号会话。  
  
## <a name="syntax"></a>语法  
  
```C++  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### <a name="parameters"></a>参数  
 ppSession  
 [out]返回[IDiaSession](../../debugger/debug-interface-access/idiasession.md)表示打开的会话对象。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。 下表显示可能的此方法的返回值。  
  
|值|描述|  
|-----------|-----------------|  
|E_UNEXPECTED|[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)对象以前尚未初始化了一个来源为符号。|  
|E_INVALIDARG|无效`ppSession`参数。|  
|E_OUTOFMEMORY|内存不足，无法打开会话。|  
  
## <a name="remarks"></a>备注  
 此方法打开[IDiaSession](../../debugger/debug-interface-access/idiasession.md)为数据源的对象。  
  
 `IDiaSession`对象实现到数据源的查询。 会话管理每个集的调试符号的一个地址空间。 如果数据源符号所描述的.exe 或.dll 文件是多个地址中的处于活动状态范围 （例如，因为多个进程将其加载），则应使用为每个地址范围的一个会话。  
  
## <a name="example"></a>示例  
  
```C++  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [概述](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [查询 .Pdb 文件](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)