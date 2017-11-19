---
title: "IActiveScriptSiteWindow::EnableModeless |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSiteWindow.EnableModeless
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSiteWindow_EnableModeless
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7099fe7d13a1cb3231e67049104722af9373d7a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
导致该主机启用或禁用的主窗口，以及任何无模式对话框。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### <a name="parameters"></a>参数  
 `fEnable`  
 [in]如果标志， `TRUE`，启用的主窗口和无模式对话框或者，如果`FALSE`，禁用它们。  
  
## <a name="return-value"></a>返回值  
 返回`S_OK`如果成功，或`E_FAIL`如果发生错误。  
  
## <a name="remarks"></a>备注  
 此方法等同于`IOleInPlaceFrame::EnableModeless`方法。  
  
 可以嵌套调用此方法。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)