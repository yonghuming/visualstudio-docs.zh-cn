---
title: "IDiaEnumSegments | Microsoft Docs"
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
  - "IDiaEnumSegments 接口"
ms.assetid: 0c9edd5e-b9ce-43e1-a791-cd4c5d16d923
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaEnumSegments
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

枚举数据源包含的各段。  
  
## 语法  
  
```  
IDiaEnumSegments : IUnknown  
```  
  
## 方法按 Vtable 顺序  
 下表显示 `IDiaEnumSegments`方法。  
  
|方法|说明|  
|--------|--------|  
|[IDiaEnumSegments::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumsegments-get-newenum.md)|检索此枚举器的 [IEnumVARIANT Interface](http://msdn.microsoft.com/zh-cn/139e3c93-faef-4003-9079-e0e94494db3e) 版本。|  
|[IDiaEnumSegments::get\_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)|检索段的数目。|  
|[IDiaEnumSegments::Item](../Topic/IDiaEnumSegments::Item.md)|通过索引检索段。|  
|[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)|检索段指定数目的枚举序列的。|  
|[IDiaEnumSegments::Skip](../../debugger/debug-interface-access/idiaenumsegments-skip.md)|跳过段指定数目的枚举序列的。|  
|[IDiaEnumSegments::Reset](../../debugger/debug-interface-access/idiaenumsegments-reset.md)|重置枚举序列与开头。|  
|[IDiaEnumSegments::Clone](../Topic/IDiaEnumSegments::Clone.md)|创建包含枚举状态和枚举当前枚举数相同的枚举数。|  
  
## 备注  
  
## 调用方的说明  
 通过调用 [IDiaTable](../../debugger/debug-interface-access/idiatable.md) 对象的 `QueryInterface` 方法获取此接口。  请参见下面的示例有关详细信息。  
  
## 示例  
 此示例演示如何从表的 `IDiaEnumSections` 接口。  有关更完整的示例段，请参见 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) 接口。  
  
```cpp#  
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pSegments;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                __uuidof( IDiaEnumSegments ),  
                                (void**)&pSegments )  
                  )  
       )  
    {  
        // Do something with this enumeration  
    }  
}  
```  
  
## 要求  
 标题:Dia2.h  
  
 库:diaguids.lib  
  
 DLL:msdia80.dll  
  
## 请参阅  
 [接口（调试接口访问 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)