---
title: "错误： 在本地计算机上防火墙 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.firewall.localmachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: ab60dda9-7934-4891-aa2f-001380d2ed83
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0eb7158fe2274fbe8707a147fe63a0937689d23
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="error-firewall-on-local-machine"></a>错误：本地计算机上的防火墙
本地计算机（您从中运行 Visual Studio 的计算机）上的 Internet 连接防火墙未设置为允许进行远程调试。 为了使用默认传输进行托管或本机远程调试，必须为 DCOM 通信打开 TCP 135 端口。 必须打开文件和打印机共享，且必须将 devenv.exe 添加到例外列表。 可能还需要打开某些 IPSEC 端口。  
  
 有关详细信息，请参阅[远程调试](../debugger/remote-debugging.md)。