---
title: "文本模板的安全性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, security
ms.assetid: 567a2383-7d43-4acc-af4a-cd70b7a0151e
caps.latest.revision: "23"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 7c99f0a519ec62a2b9946baba072b0256a78697a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="security-of-text-templates"></a>文本模板的安全性
文本模板具有以下安全问题：  
  
-   文本模板是任意代码插入到易受攻击。  
  
-   如果主机用来查找指令处理器的机制不是安全的无法运行恶意的指令处理器。  
  
## <a name="arbitrary-code"></a>任意代码  
 当你需要编写一个模板时, 可以将之内的任何代码\<# # > 标记。 这允许从文本模板内部执行任意代码。  
  
 请确保从可信的源获取模板。 请确保你的应用程序无法执行并非来自受信任源的模板的最终用户，则发出警告。  
  
## <a name="malicious-directive-processor"></a>恶意的指令处理器  
 与转换主机和一个或多个指令处理器转换到输出文件的模板文本，文本模板引擎进行交互。 有关详细信息，请参阅[文本模板转换过程](../modeling/the-text-template-transformation-process.md)。  
  
 如果主机用来查找指令处理器的机制是不安全的它将运行运行恶意的指令处理器的风险。 恶意的指令处理器可以提供在中运行的代码`FullTrust`模式时运行该模板。 如果创建了自定义文本模板转换宿主，你必须使用一种安全机制，如注册表中，要找到指令处理器的引擎。