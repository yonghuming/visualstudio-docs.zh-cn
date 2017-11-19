---
title: "错误： 混合模式调试支持对 x64 进程是仅当使用 Microsoft.NET Framework 4 或更高版本 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e4b0216c-7006-4832-883f-08e982ba8d3f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 80487995064f01c61e21e067e92b9fb5eb0c53f4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>错误：仅当使用 Microsoft .NET Framework 4 或更高版本时才支持对 x64 进程执行混合模式调试
若要调试 64 位进程中的混合本机代码和托管代码，您必须安装了 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4 版。 低于 4 的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本不支持对 64 位进程进行混合模式调试。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   执行以下步骤之一：  
  
    -   将 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 升级到 4 版。  
  
    -   生成 32 位版本的应用程序以进行调试。  
  
## <a name="see-also"></a>另请参阅  
 [远程调试](../debugger/remote-debugging.md)