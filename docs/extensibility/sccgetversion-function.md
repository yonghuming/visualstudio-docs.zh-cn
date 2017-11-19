---
title: "SccGetVersion 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetVersion
helpviewer_keywords: SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4f64b1412d0750bba4d3985d33286915e22f1474
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sccgetversion-function"></a>SccGetVersion 函数
此函数获取受源代码管理插件的源控件插件 api 的版本号。  
  
## <a name="syntax"></a>语法  
  
```cpp  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>参数  
 无。  
  
## <a name="return-value"></a>返回值  
 A`LONG`数据类型，包含受支持的源控制插件 API 的版本号：  
  
|WORD|描述|  
|----------|-----------------|  
|HIWORD|主要版本|  
|LOWORD|次要版本|  
  
## <a name="remarks"></a>备注  
 例如，如果源代码管理插件支持版本 1.3 的源控制插件 API，此函数将返回 0x0103。  
  
## <a name="see-also"></a>另请参阅  
 [源代码管理插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)