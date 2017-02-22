---
title: "筛选节点 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
caps.latest.revision: 12
caps.handback.revision: 12
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# 筛选节点
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在着色器设计器中，筛选器节点转换输入—例如，一种颜色或纹理示例—到一个比方颜色值。  这些比方颜色值通常用于非逼真呈现或在其他可视化效果中作为组件。  
  
## 筛选器节点的引用  
  
|节点|详细信息|属性|  
|--------|----------|--------|  
|**模糊**|使用Gauss 函数模糊纹理中的像素。<br /><br /> 可以使用这来减少在纹理中的的颜色详细信息或噪声。<br /><br /> **输入：**<br /><br /> `UV`: `float2`<br /> 要测试的纹理的坐标。<br /><br /> **输出：**<br /><br /> `Output`: `float4`<br /> 模糊的颜色值。|**纹理**<br /> 与在模糊检测过程中使用的采样器关联的纹理寄存器。|  
|**去饱和**|减少指定颜色值中的颜色量。<br /><br /> 当颜色被移除后，该颜色值将近似于其灰度等效值。<br /><br /> **输入：**<br /><br /> `RGB`: `float3`<br /> 要去饱和的颜色。<br /><br /> `Percent`: `float`<br /> 移除颜色百分比表示为范围 \[0, 1\] 中规范化的值。<br /><br /> **输出：**<br /><br /> `Output`: `float3`<br /> 第一个固定的颜色。|**“亮度”**<br /> 为红色、绿色和蓝色分量指定的权重。|  
|**边缘检测**|使用 Canny 边检测器检测纹理中的边。  边缘像素是输出为白色；非边缘像素是输出为黑色。<br /><br /> 可使用此方法确定纹理中的边，以便能用其他效果处理边像素。<br /><br /> **输入：**<br /><br /> `UV`: `float2`<br /> 要测试的纹理的坐标。<br /><br /> **输出：**<br /><br /> `Output`: `float4`<br /> 如果纹素在边缘上，则为白色；否则为黑色。|**纹理**<br /> 与在边检测过程中使用的采样器关联的纹理寄存器。|  
|**锐化**|锐化纹理。<br /><br /> 可以使用下面突出显示了纹理的内容的详细信息。<br /><br /> **输入：**<br /><br /> `UV`: `float2`<br /> 要测试的纹理的坐标。<br /><br /> **输出：**<br /><br /> `Output`: `float4`<br /> 模糊的颜色值。|**纹理**<br /> 与在锐化检测过程中使用的采样器关联的纹理寄存器。|