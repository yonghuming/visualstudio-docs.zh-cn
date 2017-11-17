---
title: "在开发过程中验证你的系统 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: dependency diagrams
ms.assetid: c9dafb47-7b1d-4c72-9432-d43be3db1799
caps.latest.revision: "37"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.openlocfilehash: 56d67aff89c7f0cf58911cebfdaf5bfdb1464796
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="validate-your-system-during-development"></a>在开发过程中验证系统
Visual Studio 可帮助使你的软件与用户的要求和系统的体系结构保持一致。  
  
 若要查看支持各个功能的 Visual Studio 版本，请参阅 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
## <a name="key-tasks"></a>关键任务  
 使用以下任务来验证软件。  
  
|**任务**|**相关主题**|  
|---------------|---------------------------|  
|**请确保软件满足用户要求**：<br /><br /> 可以使用要求模型和体系结构模型来帮助组织系统及其组件的测试。 这种做法有助于确保你测试了对于用户和其他利益干系人而言非常重要的要求，并可帮助你在要求发生变化时快速更新测试。|-   [基于模型开发测试](../modeling/develop-tests-from-a-model.md)|  
|**请确保你的软件与系统的预期设计保持一致：**<br /><br /> 依赖项关系图描述了你的应用程序组件之间的预期依赖关系。 在开发期间，你可以验证代码中的实际依赖关系是否符合预期设计。|-   [在代码中创建依赖项关系图](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [使用依赖项关系图验证代码](../modeling/validate-code-with-layer-diagrams.md)|  
  
## <a name="external-resources"></a>外部资源  
  
|**类别**|**链接**|  
|------------------|---------------|  
|**视频**|![视频链接](../data-tools/media/playvideo.gif "PlayVideo") [第 9 频道： Doug 七： 代码了解和使用 Visual Studio 2010 的系统设计](http://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![视频链接](../data-tools/media/playvideo.gif "PlayVideo") [第 9 频道： 构建应用程序使用依赖项关系图](http://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![视频链接](../data-tools/media/playvideo.gif "PlayVideo") [MSDN 如何实现系列： 如何使用依赖项关系图验证代码](http://go.microsoft.com/fwlink/?LinkID=214405)|  
|**论坛**|-   [Visual Studio 可视化和建模工具](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio 可视化和建模 SDK（DSL 工具）](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**博客**|-   [Visual Studio ALM + Team Foundation Server 博客](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**技术文章和日志**|[MSDN 体系结构中心](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>另请参阅  
 [测试应用程序](https://www.visualstudio.com/en-gb/docs/test/overview)   
 [建立用户需求模型](../modeling/model-user-requirements.md)   
 [体系结构分析和建模](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
