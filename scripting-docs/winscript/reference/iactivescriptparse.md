---
title: "IActiveScriptParse |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptParse interface
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b0e3990ca43043909d99b309f58a344c1727450
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
如果 Windows 脚本引擎允许原始文本代码 scriptlet，若要添加到脚本中，或允许要在运行时计算的表达式文本，它实现`IActiveScriptParse`接口。 对于解释型脚本语言具有任何独立的创作环境，如 VBScript，此字段提供另外一种机制 (而不`IPersist*`) 脚本代码进入脚本引擎中，并将脚本片段附加到不同的对象事件。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|初始化脚本引擎。|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|将代码 scriptlet 添加到该脚本。|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|分析给定的代码 scriptlet，添加到命名空间声明和评估作为适当的代码。|  
  
## <a name="see-also"></a>另请参阅  
 [活动脚本接口](../../winscript/reference/active-script-interfaces.md)