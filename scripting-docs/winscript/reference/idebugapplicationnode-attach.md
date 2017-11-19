---
title: "IDebugApplicationNode::Attach |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplicationNode.Attach
apilocation: pdm.dll
helpviewer_keywords: IDebugApplicationNode::Attach
ms.assetid: f4aad4ae-5bb0-4b5e-8f70-912a677f8f7a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 393186330979d464fe54bde339806a5d8335a859
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnodeattach"></a>IDebugApplicationNode::Attach
将此应用程序节点添加到指定的项目树。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT Attach(  
   IDebugApplicationNode*  pdanParent  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pdanParent`  
 [in]此应用程序节点都是要添加项目树。  
  
## <a name="return-value"></a>返回值  
 该方法返回 `HRESULT`。 可能的值包括（但并不限于）下表中的项。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>备注  
 此方法将此应用程序节点添加到项目树，使用`pdanParent`与父项。 如果`pdanParent`是`NULL`，此应用程序节点将作为顶级节点。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)   
 [IDebugApplicationNode 接口](../../winscript/reference/idebugapplicationnode-interface.md)