---
title: "IDebugApplicationNode100::QueryIsChildNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100::QueryIsChildNode"
ms.assetid: 4f36f435-0f34-4f9e-bba3-e75285fd7bbb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplicationNode100::QueryIsChildNode
确定指定的文档是否属于某一个此节点的子节点。  
  
> [!IMPORTANT]
>  [IDebugApplicationNode100 接口](../../winscript/reference/idebugapplicationnode100-interface.md) 由PDM v10.0实现和更大。  找到在activdbg100.h。  
  
## 语法  
  
```cpp  
HRESULT QueryIsChildNode(  
        [in] IDebugDocument* pSearchKey  
        );  
```  
  
#### 参数  
 `pSearchKey`  
 检索关键字。  
  
## 请参阅  
 [IDebugApplicationNode100 接口](../../winscript/reference/idebugapplicationnode100-interface.md)