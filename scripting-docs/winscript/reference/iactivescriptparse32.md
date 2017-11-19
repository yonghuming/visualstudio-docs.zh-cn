---
title: "IActiveScriptParse32 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 688a89515179912c1ed3ac815f0febf50ab4db0f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
如果 Windows 脚本引擎允许原始文本代码 scriptlet，若要添加到脚本中，或允许要在运行时计算的表达式文本，它实现`IActiveScriptParse32`接口。 对于解释型脚本语言具有任何独立的创作环境，如 VBScript，此字段提供另外一种机制 (而不`IPersist*`) 脚本代码进入脚本引擎中，并将脚本片段附加到不同的对象事件。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|将代码 scriptlet 添加到该脚本。|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|初始化脚本引擎。|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|分析给定的代码 scriptlet，添加到命名空间声明和评估作为适当的代码。|