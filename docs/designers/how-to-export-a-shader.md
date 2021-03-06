---
title: "如何：导出着色器 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ea578a020b4e60c3a2ff11af5d78570d636d822f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-export-a-shader"></a>如何：导出着色器
本文档演示如何使用着色器设计器导出有向图着色器语言 (DGSL) 着色器，使你能在应用中使用它。  
  
 本文档演示了此活动：  
  
-   导出着色器  
  
## <a name="exporting-a-shader"></a>导出着色器  
 在使用着色器设计器创建着色器之后且在应用中使它之前，必须以图形 API 理解的格式将其导出。 可以用不同的方式导出着色器以满足不同的需求。  
  
#### <a name="to-export-a-shader"></a>导出着色器  
  
1.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中，打开“视觉着色器图 (.dgsl)”文件。  
  
     如果没有要打开的“视觉着色器图 (.dgsl)”文件，请按照[如何：创建基本颜色着色器](../designers/how-to-create-a-basic-color-shader.md)中所述的步骤进行创建。  
  
2.  在“着色器设计器”工具栏上，依次选择“高级”、“导出”和“导出为”。 将显示“导出着色器”对话框。  
  
3.  在“另存为类型”下拉列表中，选择要导出的格式。  
  
     以下是可以选择的格式：  
  
     **HLSL 像素着色器 (\*.hlsl)**  
     将着色器以高级着色器语言 (HLSL) 源代码导出。 使用此选项可随后对着色器进行修改，即使在应用中部署它后也可修改。 尽管这可以使根据最终用户问题对代码进行调试和修补更加容易，但也使用户能更容易地以你不希望的方式修改你的着色器（例如，在竞争性游戏中获得不公平的优势）。 它还会增加着色器的加载时间。  
  
     **编译的像素着色器 (\*.cso)**  
     将着色器以 HLS 字节码导出。 使用此选项可随后对着色器进行修改，即使在应用中部署它后也可修改。 它可以使根据最终用户问题对代码进行调试和修补更加容易，但由于着色器是预编译的，因此当应用加载该着色器时，它不会产生额外的运行时开销。 技术娴熟的用户仍然可以以你不希望的方式修改着色器，但编译着色器会大大增强其难度。  
  
     **C++ 标头 (\*.h)**  
     将着色器导出为 C 样式标头，其定义包含 HLSL 字节码的字节数组。 此选项可能会使根据最终用户问题对代码进行调试和修补更加耗时，因为必须重新编译应用才能测试修补程序。 然而，因为此选项让用户难以（存在可能性）在着色器部署到应用后对其进行修改，因此也让用户难以以你不希望的方式修改着色器。  
  
4.  在“文件名”组合框中，为导出的着色器指定名称，然后选择“保存”按钮。  
  
## <a name="see-also"></a>另请参阅  
 [如何：创建基本颜色着色器](../designers/how-to-create-a-basic-color-shader.md)   
 [着色器设计器](../designers/shader-designer.md)