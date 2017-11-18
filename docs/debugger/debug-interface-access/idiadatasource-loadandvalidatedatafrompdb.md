---
title: "Idiadatasource:: Loadandvalidatedatafrompdb |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb140470e45f49806087941127638f56ce5d7150
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
打开和验证程序数据库 (.pdb) 文件匹配的签名信息提供，并准备作为调试数据源的.pdb 文件。  
  
## <a name="syntax"></a>语法  
  
```C++  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pdbPath`  
 [in].Pdb 文件的路径。  
  
 `pcsig70`  
 [in]要对照的.pdb 文件签名验证的 GUID 签名。 仅.pdb 文件中[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]和更高版本具有 GUID 签名。  
  
 `sig`  
 [in]要对照的.pdb 文件签名验证的 32 位签名。  
  
 `age`  
 [in]若要验证的期限值。 保留时间不一定对应于任何已知的时间值，它用于确定.pdb 文件是否与相应的.exe 文件不同步。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。 下表显示可能的此方法的返回值。  
  
|值|描述|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|无法打开该文件，或该文件具有无效的格式。|  
|E_PDB_FORMAT|尝试访问具有过时的格式的文件。|  
|E_PDB_INVALID_SIG|签名不匹配。|  
|E_PDB_INVALID_AGE|保留时间不匹配。|  
|E_INVALIDARG|参数无效。|  
|E_UNEXPECTED|已准备好的数据源。|  
  
## <a name="remarks"></a>备注  
 .Pdb 文件包含签名和保留时间值。 在.exe 或.dll 文件相匹配的.pdb 文件中复制这些值。 准备之前数据源，此方法验证该命名的.pdb 文件的签名和年龄匹配提供的值。  
  
 若要加载的.pdb 文件而不进行验证，使用[idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)方法。  
  
 若要访问数据加载过程 （通过回调机制），使用[idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法。  
  
 若要直接从内存中加载的.pdb 文件，使用[idiadatasource:: Loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)方法。  
  
## <a name="example"></a>示例  
  
```C++  
IDiaDataSource* pSource;  // Previously created data source.  
DEFINE_GUID(expectedGUIDSignature,0x1234,0x5678,0x01,0x02,0x03,0x04,0x05,0x06,0x07,0x08);  
DWORD expectedFileSignature = 0x12345678;  
DWORD expectedAge           = 128;  
  
HRESULT hr;  
hr = pSource->loadAndValidateDataFromPdb( L"yprog.pdb",  
                                          &expectedGUIDSignature,  
                                          expectedFileSignature,  
                                          expectedAge);  
if (FAILED(hr))  
{  
    // Report an error  
}  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)