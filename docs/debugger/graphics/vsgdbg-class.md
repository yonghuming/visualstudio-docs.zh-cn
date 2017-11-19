---
title: "VsgDbg 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0ee36596521f26ff4dd948e697640d0c82d796f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="vsgdbg-class"></a>VsgDbg 类
表示用于以编程方式控制图形诊断的应用内组件的接口。  
  
## <a name="syntax"></a>语法  
  
```C++  
class VsgDbg;  
```  
  
## <a name="members"></a>成员  
 `VsgDbg`类支持以下成员。  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[VsgDbg::VsgDbg（构造函数）](vsgdbg-vsgdbg-constructor.md)|构造的实例`VsgDbg`类并 （可选） 准备图形诊断以主动捕获并记录图形信息的应用内组件。|  
|[VsgDbg::~VsgDbg（析构函数）](vsgdbg-tilde-vsgdbg-destructor.md)|销毁实例`VsgDbg`类。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[AddMessage](addmessage.md)|将自定义消息添加到图形诊断 HUD （提醒显示）。|  
|[BeginCapture](begincapture.md)|开始将结尾的捕获时间间隔`EndCapture`。|  
|[CaptureCurrentFrame](capturecurrentframe.md)|将当前帧的剩余部分捕获到图形日志文件。|  
|[复制（编程捕获）](copy-programmatic-capture.md)|将活动图形日志 (.vsglog) 文件的内容复制到新文件。|  
|[EndCapture](endcapture.md)|结束以 `BeginCapture` 开始的捕获时间间隔。|  
|[Init](init.md)|准备图形诊断以主动捕获并记录图形信息的应用内组件。|  
|[ToggleHUD](togglehud.md)|切换在图形诊断 HUD 覆盖区上，打开或关闭。|  
|[UnInit](uninit.md)|完成图形日志文件，将其关闭，并且在应用主动记录图形信息时释放已使用的资源。|  
  
## <a name="remarks"></a>备注  
 `VsgDbg`类表示的接口，可用于以编程方式控制图形诊断功能。 你可以使用一些功能，即使你当前不捕获和记录图形信息;这包括`AddMessage`成员函数和`ToggleHUD`成员函数。 其他成员函数准备图形诊断工具启动或停止活动捕获图形信息的应用内组件，或必须在应用主动捕获并记录到图形日志文件的图形信息时调用。