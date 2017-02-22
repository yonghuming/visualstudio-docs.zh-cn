---
title: "如何：导出包含自左乘的 Alpha 的纹理 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
caps.latest.revision: 4
caps.handback.revision: 4
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# 如何：导出包含自左乘的 Alpha 的纹理
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

图像内容管线能从源图像生成左乘的 alpha 纹理。  这些比不包含自左乘的 alpha 纹理更易于使用且更可靠。  
  
 本文档演示这些活动：  
  
-   配置源图像，以便由图像内容管线对其进行处理。  
  
-   配置图像内容管线以生成预乘的 alpha。  
  
## 预乘的 Alpha  
 预乘的 Alpha 相对于常规非预乘的 Alpha 来说具有若干优点，因为它通过透明度（允许通过的底色的量）来分离颜色的基值（它添加到场景中的颜色），更好的体现了现实世界与物理材质的光线交互。  使用自左乘的 alpha 的一些优点为：  
  
-   与预乘的 alpha 混合的是结合的操作，无论纹理混合的顺序如何，混合多个半透明纹理的结果都是相同的。  
  
-   因为混合预乘的 alpha 具有结合性，所以简化了半透明对象的多通渲染。  
  
-   通过使用预乘的 alpha，可以同时实现纯附加混合（通过将 alpha 设置为零）和线性内插混合。  例如，在粒子系统中，附加混合火粒子可能会成为通过使用线性插值法混合成的半透明烟粒子。  如果不预乘 alpha，您将必须单独从烟粒子中抽取火粒子，并修改抽取调用间的呈现状态。  
  
-   使用自左乘的 alpha 的纹理比不使用的纹理拥有更高的压缩质量，并且它们不显示变色的边缘（或“晕轮效应”），此效应会在混合不使用自左乘的 alpha 的纹理时出现。  
  
#### 创建使用自左乘 Alpha 的纹理  
  
1.  从基本的纹理启动。  加载现有的图像文件或根据 [如何：创建基本纹理](../Topic/How%20to:%20Create%20a%20Basic%20Texture.md) 所述创建一个图像文件。  
  
2.  配置纹理文件，以便由图像内容管线处理。  在“解决方案资源管理器”中，打开纹理文件的快捷菜单，然后选择“属性”。  在“配置属性”，“常规”页上，将“项类型”属性设置为“图像内容管线”。  确保“内容”属性设置为“是”且“从生成中排除”设置为“否”，然后选择“应用”按钮。  显示“图像内容管线”配置属性页。  
  
3.  配置图像内容管线以生成预乘的 alpha。  在“配置属性”，“图像内容管线”，“常规”页上，将“转换至预乘 Alpha 格式”属性设置为“是 \(\/generatepremultipliedalpha\)”。  
  
4.  选择**“确定”**按钮。  
  
 生成项目后，图像内容管线将源图像从工作格式转换为指定的输出格式，其中包括将图像转换为自左乘的 alpha 格式，该结果复制到项目的输出目录。