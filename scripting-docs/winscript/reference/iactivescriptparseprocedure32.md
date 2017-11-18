---
title: "IActiveScriptParseProcedure32 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 387a856b-f5dc-4371-8620-bd574e046c2c
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 8cd253db8cb63adad093b84c4bf47df07bd66d69
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
如果 Windows 脚本引擎允许过程添加到脚本中的源代码文本，它实现`IActiveScriptParseProcedure32`接口。 对于解释型脚本语言具有任何独立的创作环境，如 VBScript，此字段提供另外一种机制 (而不`IActiveScriptParse32`或`IPersist`*) 以将脚本过程添加到命名空间。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|||  
|-|-|  
|方法|描述|  
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|分析给定的代码过程并添加到命名空间的过程。|  
  
## <a name="see-also"></a>另请参阅  
 [活动脚本接口](../../winscript/reference/active-script-interfaces.md)