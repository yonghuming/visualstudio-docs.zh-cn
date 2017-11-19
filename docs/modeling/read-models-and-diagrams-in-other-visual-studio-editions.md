---
title: "读取模型和其他 Visual Studio 版本中的关系图 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: models, versions of Visual Studio
ms.assetid: 46eee279-a9e4-4742-a024-5bd2cf032b86
caps.latest.revision: "20"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.openlocfilehash: 704c69efa4e0495a1a4aa7545fa6ba100488afe9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>在其他 Visual Studio 版本中读取模型和关系图
如果你在一个不支持创建模型的 Visual Studio 中打开模型，该模型将以只读模式打开。 在此模式下，你可以更改的关系图的布局，但不能更改该模型。  
  
 若要查看支持模型创建的 Visual Studio 的版本，请参阅[体系结构和建模工具的版本支持](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
## <a name="obtaining-access-to-a-model-and-diagrams"></a>获取对某一模型和关系图的访问权限  
 若要读取的依赖项关系图，必须首先使用 Visual Studio 打开建模项目中，，然后打开关系图中的。  
  
 出于此原因，如果你想要阅读依赖项关系图中，你还必须在其中创建的建模项目的访问权限。 可以通过从 [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)] 来获得访问权限，也可以通过获取项目文件的副本来获得访问权限。  
  
> [!NOTE]
>  这不适用于从代码生成的代码图和 .NET 类图。 这些关系图可以独立建模项目中查看。  
  
 若要读取的依赖项关系图，你需要的文件的最小集，是，如下所示：  
  
-   两个关系图文件为你想要阅读，例如，该关系图**MyDiagram.classdiagram 和 MyDiagram.classdiagram.layout**。  
  
    > [!NOTE]
    >  依赖项关系图中，你还应具有名为的文件*MyDiagram***。 layerdiagram.suppressions**。  
  
-   建模项目文件 (**MyModel.modelproj**)  
  
-   根模型文件 (**ModelDefinition\MyModel.uml**)  
  
-   引用关系图中的任何包的包文件 (**ModelDefinition\MyPackage.uml**)  
  
## <a name="changes-that-you-can-make-in-read-only-mode"></a>在只读模式下可执行的更改  
 如果你在一个不支持创建模型的 Visual Studio 中打开模型及其关系图，则你无法更改模型。 也就是说，你无法更改显示在关系图或模型资源管理器上的元素和关系。 但是，你可以对关系图的布局进行某些更改：  
  
-   重新排列关系图上的形状和连接符。  
  
-   展开和折叠形状  
  
 你可以保存这些更改。 如果你想要使所做的更改对其他用户可见，则必须至少发送更新**.layout**文件。  
  
##  <a name="RelatedTopics"></a>相关的主题  
  
|标题|描述|  
|-----------|-----------------|  
|[依赖项关系图：参考](../modeling/layer-diagrams-reference.md)|层关系图显示现有或建议的体系结构的结构。 写入代码后，可以自动依照层关系图对代码进行验证。|  
  
## <a name="see-also"></a>另请参阅  
 [为应用程序创建模型](../modeling/create-models-for-your-app.md)