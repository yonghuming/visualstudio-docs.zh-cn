---
title: "IDiaDataSource::loadDataForExe | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "IDiaDataSource::loadDataForExe 方法"
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource::loadDataForExe
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

打开并准备调试数据与 .exe\/.dll 文件。  
  
## 语法  
  
```cpp#  
HRESULT loadDataForExe (  
   LPCOLESTR executable,  
   LPCOLESTR searchPath,  
   IUnknown* pCallback  
);  
```  
  
#### 参数  
 executable  
 \[in\] .exe 或 .dll 文件的路径。  
  
 searchPath  
 \[in\] 搜索的备用路径为调试数据。  
  
 pCallback  
 \[in\] 支持一调试回调接口，如 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)、 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)、 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)，和\/或 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) 接口的对象 `IUnknown` 接口。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  下表显示了一些此方法可能的错误代码。  
  
|值|说明|  
|-------|--------|  
|E\_PDB\_NOT\_FOUND|未能打开文件或文件的格式无效。|  
|E\_PDB\_FORMAT|尝试访问具有过时的格式的文件。|  
|E\_PDB\_INVALID\_SIG|签名不匹配。|  
|E\_PDB\_INVALID\_AGE|年龄不匹配。|  
|E\_INVALIDARG|参数无效。|  
|E\_UNEXPECTED|数据源已准备。|  
  
## 备注  
 .exe\/.dll 文件的调试标头名称关联的调试数据位置。  
  
 此方法读取调试标题并搜索和准备调试数据。  搜索的进度可以通过回调，可选择，报告和进行控制。  例如，那么，当 `IDiaDataSource::loadDataForExe` 方法查找并处理一调试目录时， [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) 调用。  
  
 文件时，在不能直接通过标准文件 I\/O 时，访问 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) 和 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) 接口允许客户端应用程序来读取可执行文件的数据提供替代方法。  
  
 若要填充 .pdb 文件，而不验证，请使用 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) 方法。  
  
 若要验证 .pdb 文件特定条件，请使用 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) 方法。  
  
 直接从内存若要填充 .pdb 文件，请使用 [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md) 方法。  
  
## 示例  
  
```cpp#  
class MyCallBack: public IDiaLoadCallback  
{  
...  
};  
MyCallBack callback;  
...  
HRESULT hr = pSource->loadDataForExe( L"myprog.exe", L".\debug", (IUnknown*)&callback);  
if (FAILED(hr))  
{  
    // Report error  
}  
```  
  
## 请参阅  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md)