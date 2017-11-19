---
title: "IActiveScriptParse32::InitNew |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 31de8258ae13855741c6dd5ca9e4ff2c589e97bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
初始化脚本引擎。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>返回值  
 返回`S_OK`如果成功，或`E_FAIL`如果初始化期间出错。  
  
## <a name="remarks"></a>备注  
 可以使用的脚本引擎之前，必须调用以下方法之一： `IPersist*::Load`， `IPersist*::InitNew`，或`IActiveScriptParse32::InitNew`。 此方法的语义相等`IPersistStreamInit::InitNew`、 中，此方法可以指示脚本引擎来初始化自身。 请注意它不是最有效地请同时调用`IPersist*::InitNew`或`IActiveScriptParse32::InitNew`和`IPersist*::Load`，也不是有效调用`IPersist*::InitNew`， `IActiveScriptParse32::InitNew`，或`IPersist*::Load`不止一次。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)