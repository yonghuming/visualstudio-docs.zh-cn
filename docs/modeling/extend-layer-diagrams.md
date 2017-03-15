---
title: "扩展依赖项关系图 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
ms.assetid: 83fca301-b008-485a-87eb-218050e71451
caps.latest.revision: 39
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: ad673b1bc7d3089c37717dd7e1f1fce4e86d8100
ms.lasthandoff: 02/22/2017

---
# <a name="extend-dependency-diagrams"></a>扩展依赖项关系图
您可以编写代码以创建和更新依赖项关系图，并验证您针对 Visual Studio 中的依赖项关系图的程序代码的结构。 可以添加显示在关系图的快捷（上下文）菜单上的命令、自定义拖放笔势并从文本模板访问层模型的命令。 可以将这些扩展打包到 Visual Studio 集成扩展 (VSIX) 中，并将其分发给其他 Visual Studio 用户。  
  
 依赖项关系图的详细信息，请参阅︰  
  
-   [依赖项关系图︰ 参考](../modeling/layer-diagrams-reference.md)  
  
-   [依赖项关系图︰ 准则](../modeling/layer-diagrams-guidelines.md)  
  
-   [在代码中创建依赖项关系图](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [使用依赖项关系图验证代码](../modeling/validate-code-with-layer-diagrams.md)  
  
##  <a name="a-nameprereqsa-requirements"></a><a name="prereqs"></a>要求  
 必须在想要开发层扩展的计算机上安装了以下内容：  
  
-   Visual Studio  
  
-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md)  
  
-   Visual Studio 的建模 SDK  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
 在想要运行层扩展的计算机上必须安装合适版本的 Visual Studio。 有关详细信息，请参阅[部署层模型扩展](../modeling/deploy-a-layer-model-extension.md)。  
  
 若要查看哪些版本的 Visual Studio 支持依赖项关系图，请参阅[体系结构和建模工具的版本支持](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
## <a name="in-this-section"></a>本节内容  
 [将命令和笔势添加到依赖项关系图](../modeling/add-commands-and-gestures-to-layer-diagrams.md)  
  
 [向依赖项关系图添加自定义体系结构验证](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)  
  
 [将自定义属性添加到依赖项关系图](../modeling/add-custom-properties-to-layer-diagrams.md)  
  
 [在程序代码中导航和更新层模型](../modeling/navigate-and-update-layer-models-in-program-code.md)  
  
 [部署层模型扩展](../modeling/deploy-a-layer-model-extension.md)  
  
 [有关依赖项关系图的扩展提供疑难解答](../modeling/troubleshoot-extensions-for-layer-diagrams.md)  
  
## <a name="see-also"></a>另请参阅  
 [定义和安装建模扩展](../modeling/define-and-install-a-modeling-extension.md)   
 [依赖项关系图︰ 参考](../modeling/layer-diagrams-reference.md)   
 [依赖项关系图︰ 准则](../modeling/layer-diagrams-guidelines.md)   
 [在代码中创建依赖项关系图](../modeling/create-layer-diagrams-from-your-code.md)   
 [使用依赖项关系图验证代码](../modeling/validate-code-with-layer-diagrams.md)   

