---
title: "如何：构建三维地形模型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
caps.latest.revision: 17
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 17
---
# 如何：构建三维地形模型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本文档演示如何使用“模型编辑”创建基本的三维地形模型。  
  
 本文档演示这些活动：  
  
-   向集合中添加对象  
  
-   选择文本和点  
  
-   转换选定  
  
-   使用 **细分面** 工具  
  
-   在设计图面上给对象搭建框架  
  
## 创建三维地形模型  
 您可以通过分解平面进行其他文本，然后操作其顶点创建感兴趣的地形函数来创建三维地形。  
  
 完成后，模型应如下所示：  
  
 ![显示地形模型的三维场景](../designers/media/digit-terrain-model.png "Digit\-Terrain\-Model")  
  
 在开始之前，请确保显示**“属性”**窗口和**“工具箱”**。  
  
#### 创建三维地形模型  
  
1.  创建三维模型来工作。  有关如何向项目中添加模型的信息，请参见[模型编辑器](../designers/model-editor.md) 中的“入门”部分。  
  
2.  将长度平面添加到场景。  在**“形状”**下的**“工具箱”**，选择**“平面”**并将其移动到设计图面。  
  
    > [!TIP]
    >  若要更易于使用平面对象，在设计图面上对其进行设计。  在**“选择”**模式下，选择该平面对象，然后在“模型编辑器”工具栏上，选择**“帧对象”**按钮。  
  
3.  输入面选择模式。  在模型编辑器工具栏上，选择 **选择面**。  
  
4.  细分平面。  在文本选择模式，一次选择进行激活其选择的，然后再次选择它选择其唯一的文本。  在模型编辑器工具栏上，选择 **细分面**。  这将添加到新的顶点平面拆分到四相等大小的部分。  
  
5.  创建更多的部分。  选定仍选择的新面孔，请再选择 **细分面** 两次。  这总共创建了 64 个面。  通过创建多个细分，可以提供该地形的更详细信息。  
  
6.  输入点选择模式。  在模型编辑器工具栏上，选择 **选择点**。  
  
7.  修改点以创建地形功能。  在点选择模式下，选择其中一个点，然后在“模型编辑器”工具栏上，选择 **“转换”**工具。  表示点的框显示在设计图面上。  使用绿色箭头移动框，从而修改该点的高度。  重复不同位置的此步骤，以创建值得关注的地形功能。  
  
    > [!TIP]
    >  您可以以统一的方式立即选择多个点修改它们。  
  
 地形模型已完成。  下面又是最终模型，并 Phong 卷影应用：  
  
 ![显示地形模型的三维场景](../designers/media/digit-terrain-model.png "Digit\-Terrain\-Model")  
  
 可以使用此地域模型来演示 [如何：创建基于几何图形的渐变着色器](../designers/how-to-create-a-geometry-based-gradient-shader.md) 中描述的渐变着色器的效果。  
  
## 请参阅  
 [模型编辑器](../designers/model-editor.md)