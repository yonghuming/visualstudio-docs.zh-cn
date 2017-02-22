---
title: "如何：导出包含 Mipmap 的纹理 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
caps.latest.revision: 7
caps.handback.revision: 7
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# 如何：导出包含 Mipmap 的纹理
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

作为项目生成阶段的一部分，图像内容管线能从源图像生成 mipmap。  当您不需要手动指定每个 MIP 级别的图像内容时（您可以这样做以实现特定的效果），在生成时间生成 mipmap 可确保 mipmap 内容始终保持同步，并在运行时消除生成 mipmap 的性能成本。  
  
 本文档演示这些活动：  
  
-   配置源图像，以便由图像内容管线对其进行处理。  
  
-   配置图像内容管线以生成 mipmaps。  
  
## 正在导出 Mipmap  
 Mipmapping 为 3D 游戏或应用程序的带纹理的图面提供自动屏幕空间级别详细信息。  它将通过纹理的预计算取样缩小版本来加强游戏或应用程序的渲染性能，使整个纹理每次取样时不必进行缩小取样。  
  
#### 导出具有 mipmaps 的纹理  
  
1.  从基本的纹理启动。  加载现有的图像文件或根据 [如何：创建基本纹理](../Topic/How%20to:%20Create%20a%20Basic%20Texture.md) 所述创建一个图像文件。  若要支持 mipmap，请指定一个宽度和高度尺寸都是 2 的幂的纹理，例如 64x64、256x256 或 512x512。  
  
2.  配置您刚创建的纹理文件，以便仅由图像内容管线处理。  在“解决方案资源管理器”中，打开刚创建的纹理文件的快捷菜单，然后选择“属性”。  在“配置属性”，“常规”页上，将“项类型”属性设置为“图像内容管线”。  确保“内容”属性设置为“是”且“从生成中排除”设置为“否”，然后选择“应用”按钮。  显示“图像内容管线”配置属性页。  
  
3.  配置图像内容管线以生成 mipmap。  在“配置属性”，“图像内容管线”，“常规”页上，设置“生成 Mip”属性为“是 \(\/generatemips\)”。  
  
4.  选择**“确定”**按钮。  
  
 生成项目后，图像内容管线将源图像从工作格式转换为指定的输出格式，包括 MIP 级别，该结果复制到项目的输出目录。