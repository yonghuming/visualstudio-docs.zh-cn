---
title: "SCRIPTLANGUAGEVERSION 枚举 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4cee2966b326ca7b4c258ffdb85b6fa71d90992
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="scriptlanguageversion-enumeration"></a>SCRIPTLANGUAGEVERSION 枚举
指定脚本版本的可能。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>枚举值  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|默认版本。 整数值为 0。|  
|SCRIPTLANGUAGEVERSION_5_7|Windows Scripting 版本 5.7。 整数值为 1。|  
|SCRIPTLANGUAGEVERSION_5_8|Windows Scripting 版本 5.8。 整数值为 2。|  
|SCRIPTLANGUAGEVERSION_MAX|最高的版本。 整数值为 255。|  
  
## <a name="see-also"></a>另请参阅  
 [活动脚本常量、枚举和错误代码](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)