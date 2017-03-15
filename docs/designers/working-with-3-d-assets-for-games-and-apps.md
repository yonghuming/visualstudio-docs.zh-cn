---
title: "为游戏和应用程序使用三维资产 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.graphics"
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
caps.latest.revision: 24
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 24
---
# 为游戏和应用程序使用三维资产
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

文档描述可用于创建或修改三维模型、纹理和基于 DirectX 的游戏和应用程序的着色器的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 工具。  
  
## 在 Visual Studio 的 DirectX 应用程序开发  
 DirectX app 通常与音频和三维可视化资产一起合并编程逻辑、DirectX API 和高级着色语言 \(HLSL\) 程序，表示丰富、交互式多媒体经验。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 包含可以用于处理图形和纹理、3\-D 模型和着色器的工具而无需离开 IDE 使用另一个工具。  Visual Studio 工具尤其适合创建“占位符”资产，在执行生产就绪资产之前您可以用于测试代码或生成原型，和当您调试应用程序时用于检查和修改生产就绪的资产。  
  
 这是有关在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中您可以利用的资源种类的更多信息。  
  
### 图像和纹理  
 图像和纹理在游戏和应用程序中提供了颜色和视觉详细信息。  在三维图形中，纹理具有多种格式、类型和几何图形支持不同的用法。  例如，法线贴图为各像素提供表面法线，以获得更精细的三维模型光照，立方体贴图在所有方向提供纹理，供环境映射、反射和球形纹理映射用。  纹理提供的 mip 映射可以支持高效呈现不同级别的详细信息，并且可支持不同颜色的通道和颜色顺序。  纹理可以占用较少的图形内存的各种压缩格式存储，也可以帮助 GPU 更有效地访问纹理。  
  
 可以使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 图像编辑器处理许多常见类型和格式的图像及纹理。  
  
### 3\-D 模型  
 三维模型在游戏和应用程序中创建空间和形状。  模型至少会编码三维空间中的点位置（这称为*顶点*）以及为数据编写索引，以定义表示模型形状的线条或三角形。  其他数据可与这些顶点（例如，颜色信息、法向量或特定于应用程序的属性）相关联。  每个模型还可以定义对象属性，例如，着色器用于计算对象的图面的外观，或者纹理应用于它。  
  
 可以使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 模型编辑器处理几种常用格式的三维模型。  
  
### 着色器  
 着色器是在处理单元 \(GPU\) 的图像运行的小，特定于域的程序。  着色器确定三维模型如何转换为屏幕上的形状，以及如何着色在这些形状的每个像素。  通过创建着色器并将其应用于在您的游戏或应用程序的对象，可以给予对象唯一外观。  
  
 使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 着色器设计器（基于关系图的着色器设计工具）可以创建自定义可视化效果，而无需进行 HLSL 编程。  
  
> [!NOTE]
>  有关如何以编程的 DirectX 启动的更多信息，请参见 [DirectX](http://go.microsoft.com/fwlink/p/?LinkId=224633)。  有关如何调试基于 DirectX 的应用程序的更多信息，请参见 [图形诊断（调试 DirectX 图形）](../debugger/visual-studio-graphics-diagnostics.md)。  
  
## DirectX 版本兼容性  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 使用 DirectX 来呈现二维和三维资产。  您可以选择 DirectX 11 呈现程序或 Windows 高级化平台 \(WARP\) 软件呈现器。  DirectX 11呈现器提供高性能和在 DirectX 11 和 DirectX 10 GPUs 上的硬件加速呈现。  WARP 呈现器有助于确保您的资产广泛使用计算机—这包含没有现代图形硬件的计算机和已集成图形硬件的计算机。  有关经线的更多信息，请参见 [窗口高级光栅化平台 \(WARP\) 指南](http://go.microsoft.com/fwlink/p/?LinkId=224634)。  
  
## 相关主题  
  
|标题|说明|  
|--------|--------|  
|[使用纹理和图像](../designers/working-with-textures-and-images.md)|描述如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 以图象和纹理运行。|  
|[使用三维模型](../designers/working-with-3-d-models.md)|描述如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 以三维模型运行。|  
|[使用着色器](../designers/working-with-shaders.md)|描述如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 着色器设计器创建和修改自定义着色器效果。|  
|[在游戏或应用程序中使用三维资产](../designers/using-3-d-assets-in-your-game-or-app.md)|描述如何使用资产，通过使用图像编辑器、模型、编辑或着色器设计器，可以在该游戏或应用程序创建。|