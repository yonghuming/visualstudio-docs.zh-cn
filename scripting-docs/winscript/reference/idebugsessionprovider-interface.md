---
title: "IDebugSessionProvider 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugSessionProvider interface
ms.assetid: 1b898423-7af9-44f5-8dda-987005309c99
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e61b1e5e794c68e34250f958cdda0f50b68334c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsessionprovider-interface"></a>IDebugSessionProvider 接口
提供由调试器 IDE 以启用主机和语言的主界面启动调试。 它将建立一个正在运行的应用程序的调试会话。 此接口由机调试管理器实现。  
  
 除了从继承的方法`IUnknown`、`IDebugSessionProvider`接口公开以下方法。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|启动与指定的应用程序的调试会话。|