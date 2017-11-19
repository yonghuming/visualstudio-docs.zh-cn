---
title: "扩展依赖项关系图 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
ms.assetid: 83fca301-b008-485a-87eb-218050e71451
caps.latest.revision: "39"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.openlocfilehash: 2b661d894a471a3734a54806a89381d06fd3bd2d
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="extend-dependency-diagrams"></a>扩展依赖项关系图
你可以编写代码以创建和更新依赖项关系图，并针对 Visual Studio 中的依赖项关系图程序代码的结构进行验证。 可以添加显示在关系图的快捷（上下文）菜单上的命令、自定义拖放笔势并从文本模板访问层模型的命令。 可以将这些扩展打包到 Visual Studio 集成扩展 (VSIX) 中，并将其分发给其他 Visual Studio 用户。  
  
 有关依赖项关系图的详细信息，请参阅：  
  
-   [依赖项关系图：参考](../modeling/layer-diagrams-reference.md)  
  
-   [依赖项关系图：指南](../modeling/layer-diagrams-guidelines.md)  
  
-   [从代码创建依赖项关系图](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [使用依赖项关系图验证代码](../modeling/validate-code-with-layer-diagrams.md)  
  
##  <a name="prereqs"></a> 要求  
 必须在想要开发层扩展的计算机上安装了以下内容：  
  
-   Visual Studio  
  
-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md)  
  
-   For Visual Studio 建模 SDK  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
 在想要运行层扩展的计算机上必须安装合适版本的 Visual Studio。 有关详细信息，请参阅[部署层模型扩展](../modeling/deploy-a-layer-model-extension.md)。  
  
 若要查看支持的 Visual Studio 的版本的依赖项关系图，请参阅[体系结构和建模工具的版本支持](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
## <a name="in-this-section"></a>本节内容  
 [向依赖项关系图添加命令和手势](../modeling/add-commands-and-gestures-to-layer-diagrams.md)  
  
 [向依赖项关系图添加自定义体系结构验证](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)  
  
 [向依赖项关系图添加自定义属性](../modeling/add-custom-properties-to-layer-diagrams.md)  
  
 [在程序代码中导航和更新层模型](../modeling/navigate-and-update-layer-models-in-program-code.md)  
  
 [部署层模型扩展](../modeling/deploy-a-layer-model-extension.md)  
  
 [依赖项关系图扩展疑难解答](../modeling/troubleshoot-extensions-for-layer-diagrams.md)  
  
## <a name="see-also"></a>另请参阅  
 [依赖项关系图： 参考](../modeling/layer-diagrams-reference.md)   
 [依赖项关系图： 准则](../modeling/layer-diagrams-guidelines.md)   
 [在代码中创建依赖项关系图](../modeling/create-layer-diagrams-from-your-code.md)   
 [使用依赖项关系图验证代码](../modeling/validate-code-with-layer-diagrams.md)   
