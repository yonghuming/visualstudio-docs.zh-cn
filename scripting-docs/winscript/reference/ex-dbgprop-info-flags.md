---
title: "EX_DBGPROP_INFO_FLAGS |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: EX_DBGPROP_INFO_FLAGS
apilocation: scrobj.dll
helpviewer_keywords: EX_DBGPROP_INFO_FLAGS
ms.assetid: ee309dfe-9432-4dff-8756-7a8d677f9dcc
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0af0de81c0253b72fe432cb3cefe11c362bc2ec4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="exdbgpropinfoflags"></a>EX_DBGPROP_INFO_FLAGS
用于指定`ExtendedDebugPropertyInfo`字段。  
  
## <a name="syntax"></a>语法  
  
```  
enum {  
   EX_DBGPROP_INFO_ID  =0x0100,  
   EX_DBGPROP_INFO_NTYPE  =0x0200,  
   EX_DBGPROP_INFO_NVALUE  =0x0400,  
   EX_DBGPROP_INFO_LOCKBYTES  =0x0800,  
   EX_DBGPROP_INFO_DEBUGEXTPROP  =0x1000  
};  
```  
  
## <a name="members"></a>成员  
 EX_DBGPROP_INFO_ID  
 初始化属性的标识符。  
  
 EX_DBGPROP_INFO_NTYPE  
 初始化类型的属性。  
  
 EX_DBGPROP_INFO_NVALUE  
 初始化的属性的值。  
  
 EX_DBGPROP_INFO_LOCKBYTES  
 初始化`plb`字段。  
  
 EX_DBGPROP_INFO_DEBUGEXTPROP  
 初始化`pDebugExtProp`字段，其中包含`IDebugExtendedProperty`接口。  
  
## <a name="see-also"></a>另请参阅  
 [ExtendedDebugPropertyInfo 结构](../../winscript/reference/extendeddebugpropertyinfo-structure.md)   
 [IDebugExtendedProperty 接口](../../winscript/reference/idebugextendedproperty-interface.md)