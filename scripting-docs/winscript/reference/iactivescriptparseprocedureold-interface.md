---
title: "IActiveScriptParseProcedureOld 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptParseProcedureOld
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptParseProcedureOld interface
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99cff9cd4d04c5d25489b6cc4c9b9af93792dc2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedureold-interface"></a>IActiveScriptParseProcedureOld 接口
允许添加到脚本中的过程的源代码文本。 对于解释型脚本语言没有独立的创作环境，如 VBScript，这提供了一种替代机制 (而不`IActiveScriptParse`或`IPersist*`) 若要将脚本过程添加到命名空间。  
  
> [!NOTE]
>  此接口已弃用鉴于`IActiveScriptParseProcedure`接口。  
  
## <a name="methods"></a>方法  
 除了从继承的方法`IUnknown`、`IActiveScriptParseProcedureOld`接口公开以下方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|分析给定的代码过程并添加到命名空间的过程。|  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)