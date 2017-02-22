---
title: "IDiaEnumTables | Microsoft Docs"
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
  - "IDiaEnumTables 接口"
ms.assetid: 016190c5-09e4-48f2-bf60-9b02603a03e0
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumTables
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

枚举在数据源中包含的各个表。  
  
## 语法  
  
```  
IDiaEnumTables : IUnknown  
```  
  
## 方法按 Vtable 顺序  
 下表显示 `IDiaEnumTables`方法。  
  
|方法|说明|  
|--------|--------|  
|[IDiaEnumTables::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumtables-get-newenum.md)|检索此枚举器的 [IEnumVARIANT Interface](http://msdn.microsoft.com/zh-cn/139e3c93-faef-4003-9079-e0e94494db3e) 版本。|  
|[IDiaEnumTables::get\_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)|检索表的数目。|  
|[IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)|通过索引或名称检索表。|  
|[IDiaEnumTables::Next](../Topic/IDiaEnumTables::Next.md)|检索表指定数目的枚举序列的。|  
|[IDiaEnumTables::Skip](../../debugger/debug-interface-access/idiaenumtables-skip.md)|跳过表指定数目的枚举序列的。|  
|[IDiaEnumTables::Reset](../Topic/IDiaEnumTables::Reset.md)|重置枚举序列与开头。|  
|[IDiaEnumTables::Clone](../../debugger/debug-interface-access/idiaenumtables-clone.md)|创建包含枚举状态和枚举当前枚举数相同的枚举数。|  
  
## 备注  
  
## 调用方的说明  
 通过调用 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) 方法获取此接口。  
  
## 示例  
 此示例演示如何从会话的 `IDiaEnumTables` 接口。  有关更完整的示例列表，请参见 [IDiaTable](../../debugger/debug-interface-access/idiatable.md) 接口。  
  
```cpp#  
void ShowTableNames(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    // Do something with table  
}  
```  
  
## 要求  
 标题:Dia2.h  
  
 库:diaguids.lib  
  
 DLL:msdia80.dll  
  
## 请参阅  
 [接口（调试接口访问 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)