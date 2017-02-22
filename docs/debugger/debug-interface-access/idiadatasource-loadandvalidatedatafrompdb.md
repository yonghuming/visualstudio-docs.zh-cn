---
title: "IDiaDataSource::loadAndValidateDataFromPdb | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaDataSource::loadAndValidateDataFromPdb 方法"
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource::loadAndValidateDataFromPdb
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

打开并验证程序数据库 \(.pdb\) 文件与所提供的签名信息，并准备 .pdb 文件作为调试数据源。  
  
## 语法  
  
```cpp#  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### 参数  
 `pdbPath`  
 \[in\] .pdb 文件的路径。  
  
 `pcsig70`  
 \[in\] 验证的 GUID 签名 .pdb 文件签名。  在 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 的仅 .pdb 文件和后具有 GUID 签名。  
  
 `sig`  
 \[in\] 验证的 32 位签名 .pdb 文件签名。  
  
 `age`  
 \[in\] 验证的年龄值。  年龄不一定对应于任何已知的值时，它使用定位 .pdb 文件是否不同步的与相应的 .exe 文件。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  下表显示可能返回此方法的值。  
  
|值|说明|  
|-------|--------|  
|E\_PDB\_NOT\_FOUND|未能打开文件或文件的格式无效。|  
|E\_PDB\_FORMAT|尝试访问具有过时的格式的文件。|  
|E\_PDB\_INVALID\_SIG|签名不匹配。|  
|E\_PDB\_INVALID\_AGE|年龄不匹配。|  
|E\_INVALIDARG|参数无效。|  
|E\_UNEXPECTED|数据源已准备。|  
  
## 备注  
 .pdb 文件包含签名和年龄值。  这些值在匹配 .pdb 文件的 .exe 或 .dll 文件复制。  在准备数据源之前，此方法验证名为 .pdb 文件签名和年龄与所提供的值。  
  
 若要填充 .pdb 文件，而不验证，请使用 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) 方法。  
  
 对数据加载若要访问进程 \(通过回调机制\)，使用 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 方法。  
  
 直接从内存若要填充 .pdb 文件，请使用 [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md) 方法。  
  
## 示例  
  
```cpp#  
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
  
## 请参阅  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md)