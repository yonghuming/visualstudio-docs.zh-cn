---
title: "符号提供程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f845e18bbd4c06d5652571ec83270a80d31ec852
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="symbol-provider"></a>符号提供程序
表达式计算器实现必须访问才能计算变量与表达式由语言编译器生成的符号调试信息。 它通过使用的接口符号提供程序 (SP)，也称为符号处理程序来执行此操作。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供了 SPs 一些有关托管的代码，以及使用的程序数据库 (PDB) 符号文件格式的本机代码。 如果没有为强需要针对你的程序来使用的自定义格式存储的符号，则建议你使用由提供 SPs [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="implementation-notes"></a>实现说明  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]希望与使用公共语言运行时 (CLR) 接口 SPs 交流的调试引擎。 因此，将使用 Visual Studio 的调试引擎 SP 必须支持 CLR。 所有 CLR 调试接口的完整列表可以位于 debugref.doc，是一部分的[!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]。  
  
 如果你 SP 将仅使用你自定义调试引擎，你可以实现 SP，根据你的具体取决于你的调试引擎的需求。  
  
## <a name="see-also"></a>另请参阅  
 [调试器组件](../../extensibility/debugger/debugger-components.md)