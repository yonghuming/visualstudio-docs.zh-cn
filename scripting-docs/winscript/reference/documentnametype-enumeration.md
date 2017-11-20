---
title: "DOCUMENTNAMETYPE 枚举 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DOCUMENTNAMETYPE
apilocation: scrobj.dll
helpviewer_keywords: DOCUMENTNAMETYPE enumeration
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0bd21dddd209f21ae64ea2775bbaa0da226f077
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="documentnametype-enumeration"></a>DOCUMENTNAMETYPE 枚举
描述为文档获取哪种类型。  
  
## <a name="syntax"></a>语法  
  
```  
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,} DOCUMENTNAMETYPE;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|DOCUMENTNAMETYPE_APPNODE|获取它在应用程序树中显示的名称。|  
|DOCUMENTNAMETYPE_TITLE|获取它显示在查看器标题栏上的名称。|  
|DOCUMENTNAMETYPE_FILE_TAIL|获取不含路径的文件名称。|  
|DOCUMENTNAMETYPE_URL|获取文档的 URL。|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|获取枚举为标识追加的标题。|  
  
## <a name="see-also"></a>另请参阅  
 [活动脚本调试器常量、枚举和结构](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)