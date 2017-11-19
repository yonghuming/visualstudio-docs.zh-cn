---
title: "IDebugErrorEvent2::GetErrorMessage |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords: IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0b8a4e4c2ca938d8c600d3fd9ef0e615aa847fd9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
返回允许构造的用户可读错误消息的信息。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetErrorMessage(  
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrErrorFormat,  
   HRESULT*     hrErrorReason,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```csharp  
int GetErrorMessage(  
   out enum_MESSAGETYPE   pMessageType,  
   out string             pbstrErrorFormat,  
   out int                phrErrorReason,  
   out uint               pdwType,  
   out string             pbstrHelpFileName,  
   out uint               pdwHelpId  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pMessageType`  
 [out]返回一个值从[MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)描述消息的类型的枚举。  
  
 `pbstrErrorFormat`  
 [out]向用户最后一条消息的格式 （有关详细信息，请参阅"备注"）。  
  
 `hrErrorReason`  
 [out]有关错误代码的消息。  
  
 `pdwType`  
 [out]错误严重级别 (使用为 MB_XXX 常量`MessageBox`; 例如，`MB_EXCLAMATION`或`MB_WARNING`)。  
  
 `pbstrHelpFileName`  
 [out]（设置为 null 的值，如果没有帮助文件） 中的帮助文件路径。  
  
 `pdwHelpId`  
 [out]若要显示 （设置为 0，如果没有任何帮助主题） 的帮助主题的 ID。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 错误消息的格式应沿行`"What I was doing.  %1"`。 `"%1"`应该然后用来替换由调用方派生自的错误代码的错误消息 (在返回的这`hrErrorReason`)。 `pMessageType`参数指示调用方应如何显示最终的错误消息。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)