---
title: "错误： 无法启动 DCOM 通信 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.unmarshal_server_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 2a7b27e6-2526-4f32-bc4d-eaee447f24ec
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c80f2455b53cba46f0f2f753c55ff1b7e9dad8d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="error-unable-to-initiate-dcom-communication"></a>错误：无法启动 DCOM 通信
当本地计算机尝试与远程计算机通信时，发生 DCOM 错误。 这是由于远程服务器上存在防火墙或远程计算机上的 Windows 身份验证已中断。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   如果远程计算机已启用 Windows 防火墙，请参阅[远程调试](../debugger/remote-debugging.md)有关如何针对本地调试配置防火墙的说明。  
  
-   若要还原 Windows 身份验证，请尝试重新启动本地计算机和远程计算机。 检查本地和远程计算机上的事件日志以找出 Kerberos 错误，并与域管理员联系以了解已知问题。  
  
## <a name="see-also"></a>另请参阅  
 [远程调试](../debugger/remote-debugging.md)