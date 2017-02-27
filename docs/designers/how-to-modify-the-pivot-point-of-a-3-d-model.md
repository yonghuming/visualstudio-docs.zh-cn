---
title: "如何：修改三维模型的透视点 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
caps.latest.revision: 14
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：修改三维模型的透视点
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本文档演示如何使用模型编辑器修改的 *支点* 三维模型。  支点是为旋转和缩放在定义对象的数学中心的空间中的点。  
  
 本文档演示此活动：  
  
-   修改某个对象的数据透视点  
  
## 修改三维模型的支点  
 可以通过修改其支点重新定义三维模型的原点。  
  
 确保**“属性”**窗口和**“工具箱”**都显示。  
  
#### 修改三维模型的数据透视点  
  
1.  从现有的三维模型开始，例如在 [如何：创建基本三维模型](../Topic/How%20to:%20Create%20a%20Basic%203-D%20Model.md) 中所描述的。  
  
2.  输入数据透视模式。  在**“模型编辑模式”**工具栏上，选择 **“数据透视模式”** 按钮激活数据透视模式。  框在**“透视模式”**按钮旁边出现表明“模式编辑器”现在处于透视模式。  在透视模式下，操作如变换影响对象的透视点而不是在全局空间中的对象的结构。  
  
3.  修改对象的数据透视点。  在**“选择”**模式下，选择该对象，然后在**“模型查看器”**工具栏上，选择**“转换”**工具。  表示透视点的框显示在设计图面上。  移动该框以修改对象的数据透视点。  
  
     滚动框，在所有三维可以移动支点。  若要沿一条轴转换顶点，请移动对应于该轴的箭头。  框和箭头变成一个黄色颜色指示受转换影响的轴。  
  
     还可以通过使用**“属性”**窗口中的**“数据透视转换”**属性指定透视点。  
  
    > [!TIP]
    >  通过旋转该对象，您可以查看新透视点的效果。  若要将其旋转，请使用**“旋转”**工具或修改**“旋转”**属性。  
  
 具有已修改透视点的模型:  
  
 ![具有已修改透视点的建筑模型](../designers/media/digit-modified-model.png "Digit\-Modified\-Model")  
  
## 请参阅  
 [如何：创建基本三维模型](../Topic/How%20to:%20Create%20a%20Basic%203-D%20Model.md)   
 [模型编辑器](../designers/model-editor.md)