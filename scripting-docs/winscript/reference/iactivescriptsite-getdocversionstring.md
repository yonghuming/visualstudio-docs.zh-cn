---
title: "IActiveScriptSite::GetDocVersionString |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSite.GetDocVersionString
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSite_GetDocVersionString
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4b009c9eb40b2935a5b1aeca0d551819462bafc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
检索唯一标识当前的文档版本的主机定义的字符串。 如果相关的文档已更改 （如记事本与正在编辑的 HTML 页的情况下） 的 Windows 脚本的作用域之外，脚本引擎可以将它保存以及其保持的状态，强制执行重新编译下次加载脚本。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pstrVersionString`  
 [out]主机定义的文档版本字符串的地址。  
  
## <a name="return-value"></a>返回值  
 返回`S_OK`如果成功，或`E_NOTIMPL`如果不支持此方法。  
  
## <a name="remarks"></a>备注  
 如果`E_NOTIMPL`返回，脚本引擎应假定该脚本是与文档同步。  
  
## <a name="see-also"></a>另请参阅  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)