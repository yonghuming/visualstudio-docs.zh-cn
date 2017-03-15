---
title: "IDiaDataSource::loadDataFromPdb | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaDataSource::loadDataFromPdb 方法"
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaDataSource::loadDataFromPdb
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

打开并准备程序数据库 \(.pdb\) 文件作为调试数据源。  
  
## 语法  
  
```cpp#  
HRESULT loadDataFromPdb (  
   LPCOLESTR pdbPath  
);  
```  
  
#### 参数  
 pdbPath  
 \[in\] .pdb 文件的路径。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  下表显示可能返回此方法的值。  
  
|值|说明|  
|-------|--------|  
|E\_PDB\_NOT\_FOUND|未能打开文件或确定文件的格式无效。|  
|E\_PDB\_FORMAT|尝试访问具有过时的格式的文件。|  
|E\_INVALIDARG|参数无效。|  
|E\_UNEXPECTED|数据源已准备。|  
  
## 备注  
 此方法直接从 .pdb 文件加载调试数据。  
  
 若要验证 .pdb 文件特定条件，请使用 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) 方法。  
  
 对数据加载若要访问进程 \(通过回调机制\)，使用 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 方法。  
  
 直接从内存若要填充 .pdb 文件，请使用 [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md) 方法。  
  
## 示例  
  
```cpp#  
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );  
if (FAILED(hr))  
{  
    // report error  
}  
```  
  
## 请参阅  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md)