---
title: "Idiadatasource:: Loaddatafrompdb |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4b9192484e2ac9c957bc53a2e5a5a5965fd7a46a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
将打开并准备作为调试数据源的程序数据库 (.pdb) 文件。  
  
## <a name="syntax"></a>语法  
  
```C++  
HRESULT loadDataFromPdb (  
   LPCOLESTR pdbPath  
);  
```  
  
#### <a name="parameters"></a>参数  
 pdbPath  
 [in].Pdb 文件的路径。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。 下表显示可能的此方法的返回值。  
  
|值|描述|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|无法打开该文件，或确定该文件具有无效的格式。|  
|E_PDB_FORMAT|尝试访问具有过时的格式的文件。|  
|E_INVALIDARG|参数无效。|  
|E_UNEXPECTED|数据源尚未准备好。|  
  
## <a name="remarks"></a>备注  
 此方法直接从.pdb 文件加载调试数据。  
  
 若要验证.pdb 文件是否符合特定条件，使用[idiadatasource:: Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)方法。  
  
 若要访问数据加载过程 （通过回调机制），使用[idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法。  
  
 若要直接从内存中加载的.pdb 文件，使用[idiadatasource:: Loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)方法。  
  
## <a name="example"></a>示例  
  
```C++  
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );  
if (FAILED(hr))  
{  
    // report error  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Idiadatasource:: Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)