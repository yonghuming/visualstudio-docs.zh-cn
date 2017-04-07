---
title: "提高代码质量"
ms.custom: na
ms.date: 02/17/2017
ms.reviewer: na
ms.suite: na
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: na
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- team-based development
ms.assetid: 73baa961-c21f-43fe-bb92-3f59ae9b5945
caps.latest.revision: 39
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 2fa87621ed76fb93a9e92d558be5519d783274c5
ms.lasthandoff: 03/07/2017

---
# <a name="improve-code-quality"></a>提高代码质量
什么是代码质量？ 创建优秀的代码涉及到正确性、可维护性甚至优美性。 不论你如何定义，Visual Studio 测试工具均可帮助你和你的团队达到并保持高标准的代码卓越性。  
  
 **要求**  
  
-   本部分中描述的某些工具和功能只在特定版本的 Visual Studio 中提供 - 并非 Visual Studio 的所有版本均提供。 我们将列出这些工具和功能文档中的特定版本要求。  
  
## <a name="in-this-section"></a>本节内容  
 下表列出了常规任务的说明，还提供了一些链接，这些链接指向有关如何成功完成这些任务的更多信息。  
  
|||  
|-|-|  
|[单元测试代码](../test/unit-test-your-code.md)|“测试资源管理器”可以在开发实践中轻松地集成单元测试。 可以使用 Microsoft 单元测试框架或若干第三方和开源框架之一。|  
|[使用 Visual Studio 进行实时单元测试](../test/live-unit-testing.md)|Live Unit Testing 会自动在后台运行单元测试，并在 Visual Studio 代码编辑器中以图形方式显示代码覆盖率和测试结果。|  
|[分析应用程序质量](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|静态代码分析工具可查找 C++ 和托管代码里的设计、使用、可维护性和样式问题。 其中的许多问题可能导致难以在标准测试环境中重现的 bug。|  
|[测量托管代码的复杂性和可维护性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|代码度量是一组软件度量值，使开发人员可以更好地了解他们正在开发的代码。 度量值包括函数和类的可维护性指数、函数的圈复杂度、类的继承深度和类耦合度的数值。|  
  
## <a name="related-scenarios"></a>相关方案  
 [利用 Visual Studio 和 Team Foundation Server 进行应用程序生命周期管理](assetId:///7ae9182f-4762-4bd3-b238-39ce987932e5)  
 如果不熟悉 Visual Studio Team Foundation，可以详细了解如何在团队开发环境中使用它来提高生产力并降低与应用程序开发相关的风险。  
  
 [体系结构分析和建模](../modeling/analyze-and-model-your-architecture.md)  
 可以使用 [!INCLUDE[vsPreExt](../test/includes/vspreext_md.md)] 管理设计软件期间的难题和复杂性。 可以使用 [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)]以直观的方式按照应用程序的现状和你希望的未来状况为应用程序建模。 可以创建和维护关系图，以帮助你在将应用程序的逻辑模型映射到物理模型的同时，将这些逻辑模型可视化；这使你可以更改、验证和分析处于“设计中”的软件。  
  
 [测试应用程序](https://www.visualstudio.com/docs/test/overview)  
 可以使用 [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)]和 [!INCLUDE[vsUltShort](../test/includes/vsultshort_md.md)]提高整个测试生存期的工作效率。 使用 [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)]或 [!INCLUDE[vsUltShort](../test/includes/vsultshort_md.md)]可规划你的测试工作量。 可以同时创建、管理、编辑和运行手动和自动测试。 还可以根据计划查看测试进度。  
  
 [使用 PreEmptive Protection 保护应用程序- Dotfuscator](../ide/dotfuscator/index.md)  
 你可以使用免费的 Dotfuscator 社区版帮助保护商业机密和其他知识产权 (IP)，减少盗版和伪造，并防止篡改和未经授权进行调试。  Dotfuscator 无需进行其他编程，甚至无需访问源代码，即可保护和强化已编译程序集。
  
 [生成应用程序](https://www.visualstudio.com/docs/build/overview)  
 可以使用 [!INCLUDE[esprbuild](../test/includes/esprbuild_md.md)] 创建和管理代码的自动生成。 使用 [!INCLUDE[esprbuild](../test/includes/esprbuild_md.md)] 可以创建放置服务器以部署生成的应用程序。 此外，还可分析生成趋势。  
  
 [使用 Visual Studio Online 或 Team Foundation Server 跟踪工作](https://www.visualstudio.com/docs/work/overview)  
 可以使用 [!INCLUDE[vstsTfsLong](../test/includes/vststfslong_md.md)] 规划并跟踪你的项目，不论你使用的是敏捷过程、正式过程还是这些过程的变化形式，都是如此。 通过规划项目、对照计划跟踪进度并作出必要的调整，可以降低风险、避免出现不好的意外事件以及控制项目的成本。

