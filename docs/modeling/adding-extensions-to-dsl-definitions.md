---
title: "将扩展添加到 DSL 定义 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: "6"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: f335db9f22392c4d0293a51111efff88c25c3145
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="adding-extensions-to-dsl-definitions"></a>向 DSL 定义中添加扩展
DSL 定义扩展，可创建的域特定语言 (DSL) 的扩展包。 DSL 的方式相同，DSL 扩展，它包含在 Visual Studio 集成扩展 (VSIX) 中，可以安装在用户的计算机上。 中的其他功能可以动态启用和禁用在运行时。 Dsl 不必专门为扩展，并且扩展可以被设计为更高版本或者由第三方而无需更改扩展的 DSL。  
  
 其他功能可以包括以下：  
  
-   模型和呈现元素的属性  
  
-   形状和连接器的修饰符  
  
-   类、 关系、 形状和连接器  
  
-   验证约束  
  
-   工具箱项和选项卡  
  
 扩展 DSL 的用户可以创建和保存模型包含实例的其他功能，和其他已安装相应的扩展的用户可以读取这些。 尚未安装该扩展的用户不能使用其他功能，但它们可以更新和保存模型而不会丢失的其他功能。  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>另请参阅  
 [相关的博客文章](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
