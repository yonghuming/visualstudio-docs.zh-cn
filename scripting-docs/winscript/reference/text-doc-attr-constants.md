---
title: "TEXT_DOC_ATTR 常量 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: TEXT_DOC_ATTR
apilocation: scrobj.dll
helpviewer_keywords: TEXT_DOC_ATTR constants
ms.assetid: fd9c53a4-8f73-4c6a-abe5-6b831ecd5b1e
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 130895e0e70b1044fab5d5ab406f940b036c37f0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="textdocattr-constants"></a>TEXT_DOC_ATTR 常量
描述文档的特性。  
  
## <a name="syntax"></a>语法  
  
```  
typedef DWORD TEXT_DOC_ATTR;  
```  
  
## <a name="constants"></a>常量  
  
|常量|值|描述|  
|--------------|-----------|-----------------|  
|TEXT_DOC_ATTR_READONLY|0x00000001|文档是只读的。|  
|TEXT_DOC_ATTR_TYPE_PRIMARY|0x00000002|文档是此文档树的主文件。|  
|TEXT_DOC_ATTR_TYPE_WORKER|0x00000004|文档是辅助进程。|  
|TEXT_DOC_ATTR_TYPE_SCRIPT|0x00000008|文档是一个脚本文件。|  
  
## <a name="see-also"></a>另请参阅  
 [活动脚本调试器常量、枚举和结构](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)