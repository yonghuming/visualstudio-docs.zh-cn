---
title: "演练： 创建自定义编辑器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 74408fd88a594503c2a585cd0edfa86f28ed596e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-custom-editor"></a>演练： 创建自定义编辑器
VSPackage 项目模板可以在 c + + 中创建一个简单的自定义编辑器。  VSPackage 项目模板不再支持 C# 或 Visual Basic 项目。 有关详细信息，请参阅[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## <a name="prerequisites"></a>先决条件  
 要按照本演练的步骤操作，必须安装 Visual Studio SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="the-visual-studio-package-project-template"></a>Visual Studio 包项目模板  
 可以在中找到 Visual Studio 包项目模板**新项目**c + + 扩展性文件夹中的对话框  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>若要创建 VSPackage 使用 Visual Studio 包模板  
  
1.  使用 Visual Studio 包模板创建项目。  
  
2.  选择**自定义编辑器**选项，然后单击**下一步**。 **编辑器选项**显示页。  
  
3.  键入您的编辑器中的名称**编辑器名称**框。 键入你想要与您的编辑器中关联的文件扩展名**文件扩展名**框。 你的编辑器是适用于具有此扩展名的文件。 文件扩展名为注册 Visual Studio 仅，不适用于 Windows。 键入与你的编辑器中创建的新文档的默认文件名称**默认文件名**框。  
  
4.  单击“完成”  以在指定的文件夹中创建 VSPackage。  
  
### <a name="to-test-your-custom-editor"></a>若要测试自定义编辑器  
  
1.  上**文件**菜单上，指向**新建**，然后单击**文件**。  
  
2.  在**已安装的模板**窗格**新文件**对话框中，选择文件模板中，则该文件类型你刚刚注册。  
  
3.  单击**打开**查看和编辑文档。  
  
     编辑器支持剪切和粘贴、 查找和替换和打开负载操作。  
  
## <a name="see-also"></a>另请参阅  
 [VSPackage](../extensibility/internals/vspackages.md)