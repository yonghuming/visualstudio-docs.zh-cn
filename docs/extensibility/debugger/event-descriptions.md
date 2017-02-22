---
title: "事件描述 | Microsoft Docs"
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
  - "调试 [调试 SDK] 事件"
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# 事件描述
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

事件的每种类型都有特定用途。  
  
## 事件和原因它们的使用。  
  
|Event|说明|  
|-----------|--------|  
|activate 文档事件|，在调试引擎 \(DE\)希望 IDE 给前景，打开或使文档中发生。|  
|断点区域或断点错误事件|发送，当断点绑定时，或者当断点不能绑定时和错误返回。|  
|断点未绑定操作|，当绑定断点从代码，请在发生。|  
|可以停止事件|发送到 IDE 确定用户是否希望停止对指定点在代码。|  
|断点事件|，在代码或数据断点被命中，请发生。|  
|文档文本事件|，更改，请发生文档中的文本。  这些事件未通过 `IDebugEventCallBack2::Event` 方法发送。|  
|引擎创建事件|发送，当引擎首先创建。|  
|入口点事件|发送，当正在调试的程序运行时其初始化代码和达到其第一个输入点。|  
|异常事件|发送，当正在运行的程序遇到异常。|  
|表达式计算完成事件|发送，在异步表达式计算完成。|  
|查找符号事件|发送，只要 DE 需要要求用户查找模块的符号。|  
|加载完成事件|发送，仅当原始程序负载完成时与第一个代码将运行程序。|  
|邮件事件|发送，当发送给用户。|  
|模块加载事件|发送，在一个新模块加载或卸载。|  
|输出字符串操作|发送，当程序编写调试输出。|  
|创建和销毁事件|发送消息创建或损坏进程，程序、属性、会话和线程，因此 Visual Studio IDE 会记录被调试的程序的状态。|  
|步骤完成事件|发送，当步骤完成的。|  
|线程名称更改事件|发送，当用户更改线程的名称。|  
|过程名称更改事件|发送，当用户更改程序的名称。|  
  
## 请参阅  
 [发送事件](../../extensibility/debugger/sending-events.md)