---
title: "SccGetEvents 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetEvents
helpviewer_keywords: SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5eed4b08398b2acd9a136ba0ccf67527a574f16f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sccgetevents-function"></a>SccGetEvents 函数
此函数可检索排队的状态事件。  
  
## <a name="syntax"></a>语法  
  
```cpp  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### <a name="parameters"></a>参数  
 pvContext  
 [in]源控件插件上下文结构。  
  
 lpFileName  
 [在中，out]源代码管理插件其中放入 （最多 _MAX_PATH 个字符） 返回的文件名的缓冲区。  
  
 lpStatus  
 [在中，out]将返回状态代码 (请参阅[文件状态代码](../extensibility/file-status-code-enumerator.md)有关可能的值)。  
  
 pnEventsRemaining  
 [在中，out]返回此调用后留在队列的条目数。 如果此数量很大，调用方可能会决定要调用[SccQueryInfo](../extensibility/sccqueryinfo-function.md)以获取所有相关信息一次。  
  
## <a name="return-value"></a>返回值  
 此函数的源代码控制插件实现应返回以下值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|获取事件成功。|  
|SCC_E_OPNOTSUPPORTED|不支持此函数。|  
|SCC_E_NONSPECIFICERROR|非特定的失败。|  
  
## <a name="remarks"></a>备注  
 在空闲处理，以查看是否已在源代码管理下的文件的任何状态更新过程中调用此函数。 源代码管理插件保持它知道的所有文件的状态，每当更改状态记录由该插件的状态和关联的文件存储在队列中。 当`SccGetEvents`调用时，顶部检索并返回队列的元素。 此函数被约束为返回唯一以前缓存的信息，并且必须具有非常快速周转时间 （即，没有读取的磁盘或状态请求的源控制系统）;否则，可能会启动 IDE 的性能下降。  
  
 如果报表没有状态更新，源代码管理插件会将空字符串存储在通过指向的缓冲区`lpFileName`。 否则，该插件将存储该文件的完整路径名称为该状态信息已更改并返回相应的状态代码 (中详述的值之一[文件状态代码](../extensibility/file-status-code-enumerator.md))。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)   
 [文件状态代码](../extensibility/file-status-code-enumerator.md)