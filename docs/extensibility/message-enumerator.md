---
title: "消息枚举器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "消息枚举器"
  - "源代码管理插件，消息枚举"
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 消息枚举器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

以下标志用于 `TEXTOUTPROC` 函数，这是在它调用时，IDE 提供了一个回调函数 [SccOpenProject](../extensibility/sccopenproject-function.md) \(请参阅 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) 有关回调函数的详细信息\)。  
  
 如果系统询问 IDE 取消该过程，它可能会收到一条取消消息。 在这种情况下，源代码管理插件用 `SCC_MSG_STARTCANCEL` 询问 IDE 以显示 **取消** 按钮。 此后，仍可能发送任何一组普通消息。 如果任何这些返回 `SCC_MSG_RTN_CANCEL`, ，则该插件会退出该操作并返回。 该插件也会轮询 `SCC_MSG_DOCANCEL` 定期以确定该用户已取消该操作。 当所有操作完成都后，或如果用户已经取消了，该插件会发送 `SCC_MSG_STOPCANCEL`。`SCC_MSG_INFO`, ，SCC\_MSG\_WARNING，和 SCC\_MSG\_ERROR 类型用于显示在滚动列表中的消息的消息。`SCC_MSG_STATUS` 是一种特殊类型，该值指示文本应该出现在状态栏或临时显示区域。 它不会保持永久列表中。  
  
## 语法  
  
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
  
## 成员  
 SCC\_MSG\_RTN\_CANCEL  
 从回调，以指示取消返回。  
  
 SCC\_MSG\_RTN\_OK  
 返回从回调以继续。  
  
 SCC\_MSG\_INFO  
 消息仅供参考。  
  
 SCC\_MSG\_WARNING  
 消息是一个警告。  
  
 SCC\_MSG\_ERROR  
 消息是错误的。  
  
 SCC\_MSG\_STATUS  
 消息适用于状态栏。  
  
 SCC\_MSG\_DOCANCEL  
 没有文本;IDE 返回 `SCC_MSG_RTN_OK` 或 `SCC_MSG_RTN_CANCEL`。  
  
 SCC\_MSG\_STARTCANCEL  
 启动取消循环。  
  
 SCC\_MSG\_STOPCANCEL  
 停止取消循环。  
  
## 请参阅  
 [源代码管理插件](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)