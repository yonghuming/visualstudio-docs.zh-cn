---
title: "SccUninitialize 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccUninitialize
helpviewer_keywords: SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 434987489feccd5f576e04d69afbb4b39e1dc754
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sccuninitialize-function"></a>SccUninitialize 函数
此函数将清除任何分配或打开连接到的以前调用创建[SccInitialize](../extensibility/sccinitialize-function.md)以准备关闭源代码管理插件。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>参数  
 pvContext  
 [in]在中创建指向源控件插件上下文结构的指针[SccInitialize](../extensibility/sccinitialize-function.md)。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|清理已成功完成。|  
  
## <a name="remarks"></a>备注  
 源代码管理插件负责准备关闭并释放插件为上下文结构已分配的内存。 每个插件的给定实例一次调用函数。 调用[SccInitialize](../extensibility/sccinitialize-function.md)之前此调用。 没有项目仍可以在调用时打开`SccUninitialize`。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)