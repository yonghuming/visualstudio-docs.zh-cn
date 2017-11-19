---
title: "消息枚举器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 000b853c1f25d8b68ccdda87e6c0496aeeaaca0e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="message-enumerator"></a>消息枚举器
以下标志用于`TEXTOUTPROC`函数，这是一个 IDE 提供时，它调用的回调函数[SccOpenProject](../extensibility/sccopenproject-function.md) (请参阅[LPTEXTOUTPROC](../extensibility/lptextoutproc.md)有关回调的详细信息函数）。  
  
 如果 IDE 需要取消该过程，它可能会收到一条取消消息。 在这种情况下，源代码管理插件使用`SCC_MSG_STARTCANCEL`提出 IDE 以显示**取消**按钮。 此后，可能会发送普通消息的任何集。 如果任何这些返回`SCC_MSG_RTN_CANCEL`，则该插件会退出该操作并返回。 插件还轮询`SCC_MSG_DOCANCEL`定期以确定用户已取消该操作。 完成的所有操作，或如果用户已取消，插件将发送时`SCC_MSG_STOPCANCEL`。 `SCC_MSG_INFO`，SCC_MSG_WARNING，和 SCC_MSG_ERROR 类型用于消息滚动列表中显示的消息。 `SCC_MSG_STATUS`是一种特殊类型，该值指示，文本应显示在状态栏或临时的显示区域中。 它不会保留永久列表中。  
  
## <a name="syntax"></a>语法  
  
```  
enum {   
   SCC_MSG_RTN_CANCEL = -1,   
   SCC_MSG_RTN_OK = 0,   
   SCC_MSG_INFO = 1   
   SCC_MSG_WARNING,   
   SCC_MSG_ERROR,   
   SCC_MSG_STATUS,   
   SCC_MSG_DOCANCEL,   
   SCC_MSG_STARTCANCEL,   
   SCC_MSG_STOPCANCEL   
};  
```  
  
## <a name="members"></a>成员  
 SCC_MSG_RTN_CANCEL  
 返回从回调，以指示取消。  
  
 SCC_MSG_RTN_OK  
 返回从回调以继续。  
  
 SCC_MSG_INFO  
 为信息性消息。  
  
 SCC_MSG_WARNING  
 消息是一个警告。  
  
 SCC_MSG_ERROR  
 消息是一个错误。  
  
 SCC_MSG_STATUS  
 消息的目的是为了所的状态栏。  
  
 SCC_MSG_DOCANCEL  
 没有文本;IDE 返回`SCC_MSG_RTN_OK`或`SCC_MSG_RTN_CANCEL`。  
  
 SCC_MSG_STARTCANCEL  
 启动取消循环。  
  
 SCC_MSG_STOPCANCEL  
 停止取消循环。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)