---
title: "SCRIPTUICITEM 枚举 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fbf01f1b-5d7f-4d92-8d10-3da65e352d93
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6620553bce810abcf1a51ac8592061ef017dd9bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="scriptuicitem-enumeration"></a>SCRIPTUICITEM 枚举
表示 UI 项的类型。 在中使用[iactivescriptsiteuicontrol:: Getuibehavior 方法](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md)。  
  
## <a name="syntax"></a>语法  
  
```vb  
typedef enum tagSCRIPTUICITEM {     SCRIPTUICITEM_INPUTBOX = 1,     SCRIPTUICITEM_MSGBOX = 2,     } SCRIPTUICITEM;   
```  
  
## <a name="enumeration-values"></a>枚举值  
  
|||  
|-|-|  
|SCRIPTUICITEM_INPUTBOX|输入的控件。|  
|SCRIPTUICITEM_MSGBOX|一个消息框。|