---
title: "LPTEXTOUTPROC |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 658193f526123d237ef9b90a05861492b9f007c9
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC
当用户执行从在集成的开发环境 (IDE) 的源代码管理操作时，源代码管理插件可能想要传达与操作相关的错误或状态消息。 该插件可以为此目的中显示其自己的消息框。 但是，对于多个无缝集成，插件可以将字符串传递到 IDE，然后将其显示在其本机的显示状态信息的方式。 此机制是`LPTEXTOUTPROC`函数指针。 IDE 实现此函数用于显示错误和状态 （在下面更详细地介绍）。  
  
 IDE 将传递到源代码管理插件对此函数的函数指针作为`lpTextOutProc`参数，在调用时[SccOpenProject](../extensibility/sccopenproject-function.md)。 在源代码管理操作，例如情况下，在调用中间期间[SccGet](../extensibility/sccget-function.md)涉及多个文件，该插件可以调用`LPTEXTOUTPROC`函数，并定期传递要显示的字符串。 IDE 可能会显示在状态栏上，在输出窗口中，或在单独的消息框中，根据这些字符串。 （可选），IDE 可能能够显示与特定消息**取消**按钮。 这使用户能够取消操作，并为 IDE 提供将此信息传递回该插件的功能。  
  
## <a name="signature"></a>签名  
 IDE 的输出函数具有以下签名：  
  
```cpp  
typedef LONG (*LPTEXTOUTPROC) (  
   LPSTR display_string,  
   LONG mesg_type  
);  
```  
  
## <a name="parameters"></a>参数  
 display_string  
 要显示的文本字符串。 此字符串不应以回车返回或换行符终止。  
  
 mesg_type  
 消息的类型。 下表列出了此参数支持的值。  
  
|值|描述|  
|-----------|-----------------|  
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|信息、 警告或错误，则认为消息。|  
|`SCC_MSG_STATUS`|消息显示状态，并且可以在状态栏中显示。|  
|`SCC_MSG_DOCANCEL`|不发送任何消息字符串。|  
|`SCC_MSG_STARTCANCEL`|开始显示**取消**按钮。|  
|`SCC_MSG_STOPCANCEL`|将不再显示**取消**按钮。|  
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|询问 IDE 是否后台操作已取消： IDE 返回`SCC_MSG_RTN_CANCEL`如果操作已取消; 否则，返回`SCC_MSG_RTN_OK`。 `display_string`参数被强制转换为[SccMsgDataIsCancelled](#LinkSccMsgDataIsCancelled)结构，它由源代码管理插件提供。|  
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|关于文件告知 IDE，才能检索从版本控制。 `display_string`参数被强制转换为[SccMsgDataOnBeforeGetFile](#LinkSccMsgDataOnBeforeGetFile)结构，它由源代码管理插件提供。|  
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|选项将告知 IDE 文件已从版本控制中检索它后。 `display_string`参数被强制转换为[SccMsgDataOnAfterGetFile](#LinkSccMsgDataOnAfterGetFile)结构，它由源代码管理插件提供。|  
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|告知 IDE 后台操作的当前状态。 `display_string`参数被强制转换为[SccMsgDataOnMessage](#LinkSccMsgDataOnMessage)结构，它由源代码管理插件提供。|  
  
## <a name="return-value"></a>返回值  
  
|值|描述|  
|-----------|-----------------|  
|SCC_MSG_RTN_OK|显示字符串，或操作已成功完成。|  
|SCC_MSG_RTN_CANCEL|用户想要取消该操作。|  
  
## <a name="example"></a>示例  
 假设 IDE 调用[SccGet](../extensibility/sccget-function.md)具有 20 个文件名。 源代码管理插件希望阻止取消中间文件 get 操作。 获取每个文件后，它调用`lpTextOutProc`，将其传递对每个文件的状态信息并发送`SCC_MSG_DOCANCEL`消息是否没有报告的状态。 如果在任何时候插件将收到一个返回值的`SCC_MSG_RTN_CANCEL`从 IDE，它取消获取操作立即，以便检索更多文件。  
  
## <a name="structures"></a>结构  
  
###  <a name="LinkSccMsgDataIsCancelled"></a>SccMsgDataIsCancelled  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
} SccMsgDataIsCancelled;  
```  
  
 此结构不会发送`SCC_MSG_BACKGROUND_IS_CANCELLED`消息。 它用于通信的后台操作已取消的 ID。  
  
###  <a name="LinkSccMsgDataOnBeforeGetFile"></a>SccMsgDataOnBeforeGetFile  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
} SccMsgDataOnBeforeGetFile;  
```  
  
 此结构不会发送`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`消息。 它用于通信要检索的文件的名称和正在检索的后台操作的 ID。  
  
###  <a name="LinkSccMsgDataOnAfterGetFile"></a>SccMsgDataOnAfterGetFile  
  
```cpp  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szFile;  
   SCCRTN sResult;  
} SccMsgDataOnAfterGetFile;  
```  
  
 此结构不会发送`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`消息。 它用于通信检索指定的文件，以及未检索的后台操作的 ID 的结果。 请参阅的返回值[SccGet](../extensibility/sccget-function.md)有关什么可以作为结果提供。  
  
###  <a name="LinkSccMsgDataOnMessage"></a>SccMsgDataOnMessage  
 [C++]  
  
```  
typedef struct {  
   DWORD dwBackgroundOperationID;  
   PCSTR szMessage;  
   BOOL bIsError;  
} SccMsgDataOnMessage;  
```  
  
 此结构不会发送`SCC_MSG_BACKGROUND_ON_MESSAGE`消息。 它用于通信的后台操作的当前状态。 状态表示为字符串由 IDE、 显示和`bIsError`指示消息的严重性 (`TRUE`为一条错误消息;`FALSE`警告或信息性消息)。 此外会提供发送状态的后台操作的 ID。  
  
## <a name="code-example"></a>代码示例  
 下面是调用简短示例`LPTEXTOUTPROC`发送`SCC_MSG_BACKGROUND_ON_MESSAGE`消息，显示如何强制结构转换调用。  
  
```cpp  
LONG SendStatusMessage(  
    LPTEXTOUTPROC pTextOutProc,  
    DWORD         dwBackgroundID,  
    LPCTSTR       pStatusMsg,  
    BOOL          bIsError)  
{  
    SccMsgDataOnMessage msgData = { 0 };  
    LONG                result  = 0;  
  
    msgData.dwBackgroundOperationID = dwBackgroundID;  
    msgData.szMessage               = pStatusMsg;  
    msgData.bIsError                = bIsError;  
  
    result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE);  
    return result;  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [由 IDE 实现的回调函数](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [源代码管理插件](../extensibility/source-control-plug-ins.md)
