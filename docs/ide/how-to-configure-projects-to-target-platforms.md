---
title: "如何：配置项目以面向目标平台 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: c730f161ed0a38c94362d63544af1c5f3794d985
ms.contentlocale: zh-cn
ms.lasthandoff: 05/13/2017

---
# <a name="how-to-configure-projects-to-target-platforms"></a>如何：配置项目以面向目标平台
可使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 将应用程序设置为面向不同平台（包括 64 位平台）。 若要深入了解 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中对 64 位平台的支持，请参阅 [64 位应用程序](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)。  
  
## <a name="targeting-platforms-with-the-configuration-manager"></a>使用配置管理器设定目标平台  
 “配置管理器”提供了一种快速添加面向项目的新平台的方法。 如果选择 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 附带的平台之一，则将修改项目属性，以便生成适用于所选平台的项目。  
  
#### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>将项目配置为面向 64 位平台  
  
1.  在菜单栏上，依次选择 **“生成”**、 **“配置管理器”**。  
  
2.  在“活动解决方案平台”列表中，选择一个 64 位平台作为解决方案目标，然后选择“关闭”按钮。  
  
    1.  如果所需平台未出现在“活动解决方案平台”列表中，请选择“新建”。  
  
         将显示“新建解决方案平台”对话框。  
  
    2.  在“键入或选择新平台”列表中，选择“x64”。  
  
        > [!NOTE]
        >  如果对配置进行了重命名，则可能需要修改“项目设计器”中的设置，以面向正确的平台。  
  
    3.  如果要复制当前平台配置的设置，请选择它，然后选择“确定”按钮。  
  
 面向 64 位平台的所有项目的属性均已更新，并将为 64 位平台优化项目的下一个生成。  
  
## <a name="targeting-platforms-in-the-project-designer"></a>在项目设计器中设定平台目标  
 项目设计器还提供使项目面向不同平台的方法。 如果在“新建解决方案平台”对话框的列表中选择的平台之一不适合自己的解决方案，则可以创建自定义配置名称并修改“项目设计器”中的配置以面向正确的平台。  
  
 此任务的执行根据所用编程语言而有所不同。 有关详细信息，请参阅以下链接：  
  
-   对于 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 项目，请参阅 [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform)。  
  
-   对于 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 项目，请参阅[“项目设计器”->“生成”页 (C#)](../ide/reference/build-page-project-designer-csharp.md)。  
  
-   对于 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] 项目，请参阅 [/clr（公共语言运行时编译）](/cpp/build/reference/clr-common-language-runtime-compilation)。  
  
## <a name="see-also"></a>另请参阅  
 [了解生成平台](../ide/understanding-build-platforms.md)   
 [-platform（C# 编译器选项）](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)   
 [64 位应用程序](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Visual Studio IDE 64 位支持](../ide/visual-studio-ide-64-bit-support.md)
