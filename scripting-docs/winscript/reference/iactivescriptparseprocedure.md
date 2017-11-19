---
title: "IActiveScriptParseProcedure |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptParseProcedure interface
ms.assetid: 741a35bb-5b92-489e-ba8a-a406b42125fc
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77aaa60942855a71f7d71037fbefb06462336a13
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedure"></a>IActiveScriptParseProcedure
如果 Windows 脚本引擎允许过程添加到脚本中的源代码文本，它实现`IActiveScriptParseProcedure`接口。 对于解释型脚本语言具有任何独立的创作环境，如 VBScript，此字段提供另外一种机制 (而不`IActiveScriptParse`或`IPersist`*) 以将脚本过程添加到命名空间。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|||  
|-|-|  
|方法|描述|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|分析给定的代码过程并添加到命名空间的过程。|  
  
## <a name="see-also"></a>另请参阅  
 [活动脚本接口](../../winscript/reference/active-script-interfaces.md)