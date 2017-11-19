---
title: "如何： 更改域特定语言的 Namespace |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: "19"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: b7419766b4c195c3bcef2aa45e886004a89fb5ec
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>如何：更改域特定语言的命名空间
你可以更改域特定语言的命名空间。 必须进行的更改**DSL 资源管理器**、 Dsl 包项目的属性以及中的程序集信息。  
  
### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>若要更改的域特定语言的命名空间  
  
1.  在**DSL 资源管理器**，单击**Dsl**节点。  
  
2.  在**属性**窗口中，更改**Namespace**属性。  
  
3.  保存解决方案和转换模板。  
  
4.  上**项目**菜单上，单击**Dsl 属性**。  
  
     为你的项目的属性将出现。  
  
5.  单击“应用程序”  选项卡。  
  
6.  更改**默认命名空间**为新的命名空间名称的属性。  
  
7.  如果你还想要更改程序集的名称，更改**程序集名称属性。**  
  
8.  如果你更改了程序集名称，打开 DslPackage\Package.tt 并更新此行：  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. 如果你编写了任何自定义代码，请确保更改中的代码文件的命名空间和类的引用。  
  
10. 重置的 Visual Studio 实验实例。  
  
    1.  删除**\Users\\***{你的名称}***\AppData\Local\Microsoft\VisualStudio\\\*Exp**  
  
    2.  在 Windows**启动**菜单上，选择**所有程序**， **Microsoft Visual Studio 2010 SDK**，**工具**，**重置实验实例**。  
  
11. 上**生成**菜单上，选择**重新生成解决方案**。  
  
## <a name="see-also"></a>另请参阅  
 [域特定语言工具词汇表](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)