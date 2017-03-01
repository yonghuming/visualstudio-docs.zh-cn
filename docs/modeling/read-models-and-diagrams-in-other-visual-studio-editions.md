---
title: "读取模型和其他 Visual Studio 版本中的关系图 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- models, versions of Visual Studio
ms.assetid: 46eee279-a9e4-4742-a024-5bd2cf032b86
caps.latest.revision: 20
author: alexhomer1
ms.author: ahomer
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
translationtype: Machine Translation
ms.sourcegitcommit: 8f84f22444a5df5b9f4f4af44cd8ee9136403467
ms.openlocfilehash: 9ffc4c39dee2da1d6daa051f478eac18d9670151
ms.lasthandoff: 02/22/2017

---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>在其他 Visual Studio 版本中读取模型和关系图
如果你在一个不支持创建模型的 Visual Studio 中打开模型，该模型将以只读模式打开。 在此模式下，你可以更改的关系图的布局，但不能更改该模型。  
  
 若要查看哪些版本的 Visual Studio 支持创建模型，请参阅[体系结构和建模工具的版本支持](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
## <a name="obtaining-access-to-a-model-and-diagrams"></a>获取对某一模型和关系图的访问权限  
 若要读取依赖项关系图时，必须首先使用 Visual Studio 打开建模项目，然后打开在其中的关系图。  
  
 出于此原因，如果你想要读取一个依赖项关系图中，您还必须在其中创建建模项目的访问权限。 可以通过从 [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)] 来获得访问权限，也可以通过获取项目文件的副本来获得访问权限。  
  
> [!NOTE]
>  这不适用于从代码生成的代码图和 .NET 类图。 这些关系图可以独立建模项目中查看。  
  
 若要读取的依赖项关系图，所需的文件的最小集如下所述︰  
  
-   两个关系图的关系图，你想要读取，例如，文件**MyDiagram.classdiagram 和 MyDiagram.classdiagram.layout**。  
  
    > [!NOTE]
    >  有关依赖项关系图，你还应安装名为的文件*MyDiagram***。 layerdiagram.suppressions**。  
  
-   建模项目文件 (**MyModel.modelproj**)  
  
-   根模型文件 (**ModelDefinition\MyModel.uml**)  
  
-   在关系图中引用的任何包的包文件 (**ModelDefinition\MyPackage.uml**)  
  
## <a name="changes-that-you-can-make-in-read-only-mode"></a>在只读模式下可执行的更改  
 如果你在一个不支持创建模型的 Visual Studio 中打开模型及其关系图，则你无法更改模型。 也就是说，你无法更改显示在关系图或模型资源管理器上的元素和关系。 但是，你可以对关系图的布局进行某些更改：  
  
-   重新排列关系图上的形状和连接符。  
  
-   展开和折叠形状  
  
 你可以保存这些更改。 如果您想要使所做的更改对其他用户可见，则必须至少发送已更新**.layout**文件。  
  
##  <a name="a-namerelatedtopicsa-related-topics"></a><a name="RelatedTopics"></a>相关的主题  
  
|标题|说明|  
|-----------|-----------------|  
|[依赖项关系图︰ 参考](../modeling/layer-diagrams-reference.md)|层关系图显示现有或建议的体系结构的结构。 写入代码后，可以自动依照层关系图对代码进行验证。|  
  
## <a name="see-also"></a>另请参阅  
 [为应用程序创建模型](../modeling/create-models-for-your-app.md)
