---
title: "如何：取消显示编译器警告 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 77230702bf8dc582e176e4dd0f17eab3385966c6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-suppress-compiler-warnings"></a>如何：取消显示编译器警告
可清理生成日志，方法是指定一种或多种不希望包含的编译器警告。 例如，将生成日志的详细级别设置为“一般”、“详细”或“诊断”时，可以使用此方法查看自动生成的部分信息，但不是所有信息。 有关详细级别的更多信息，请参阅[如何：查看、保存和配置生成日志文件](../ide/how-to-view-save-and-configure-build-log-files.md)。  
  
### <a name="to-suppress-specific-warnings-for-visual-c-or-f"></a>取消显示特定的 Visual C# 或 F# 警告 #
  
1.  在**解决方案资源管理器**中，选择想要取消显示警告的项目。  
  
2.  在菜单栏上，依次选择 **“查看”**、 **“属性页”**。  
  
3.  选择“生成”页。  
  
4.  在“取消显示警告”框中，指定想要取消显示的警告的错误代码，使用分号分隔，然后重新生成解决方案。  
  
### <a name="to-suppress-specific-warnings-for-visual-c"></a>要取消显示特定的 Visual C++ 警告  
  
1.  在**解决方案资源管理器**中，选择想要取消显示警告的项目或源文件。  
  
2.  在菜单栏上，依次选择 **“查看”**、 **“属性页”**。  
  
3.  依次选择“配置属性”类别、“C/C++”类别和“高级”页。  
  
4.  执行以下步骤之一：  
  
    -   在“禁用特定警告”框中，指定想要取消显示的警告的错误代码，并使用分号分隔。  
  
    -   在“禁用特定警告”框中，选择“编辑”以显示更多选项。  
  
5.  选择“确定”按钮，然后重新生成解决方案。  
  
## <a name="suppressing-warnings-for-visual-basic"></a>取消显示 Visual Basic 警告  
 可以通过编辑项目的 .vbproj 文件，隐藏 Visual Basic 的特定编译器警告。 你还可以使用[编译页，项目设计器](../ide/reference/compile-page-project-designer-visual-basic.md)来按类别取消显示警告。 有关详细信息，请参阅[在 Visual Basic 中配置警告](../ide/configuring-warnings-in-visual-basic.md)。  
  
#### <a name="to-suppress-specific-warnings-for-visual-basic"></a>要取消显示特定的 Visual Basic 警告  
  
1.  在**解决方案资源管理器**中，选择想要取消显示警告的项目。  
  
2.  在菜单栏上，依次选择“项目”、“卸载项目”。  
  
3.  在“解决方案资源管理器”中，打开项目的快捷菜单，然后选择“编辑*ProjectName*.vbproj”。  
  
     此项目文件在代码编辑器中打开。  
  
4.  找到生成所使用的生成配置中的 `<NoWarn></NoWarn>` 元素。  
  
     以下示例显示在 x86 平台上的调试生成配置中的使用粗体文本的 `<NoWarn></NoWarn>` 元素：  
  
    ```  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
        <PlatformTarget>x86</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <ErrorReport>prompt</ErrorReport>  
        <NoWarn></NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
5.  添加一个或多个警告编号作为 `<NoWarn>` 元素的值。 如果指定多个警告编号，请使用逗号分隔，如以下示例所示。  
  
    ```  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
        <PlatformTarget>x86</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <ErrorReport>prompt</ErrorReport>  
        <NoWarn>40059,42024</NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
6.  保存对 .vbproj 文件所做的更改。  
  
7.  在菜单栏上，依次选择“项目”、“重载项目”。  
  
8.  在菜单栏上，依次选择“生成”、“重新生成解决方案”。  
  
     “输出”窗口不再显示指定的警告。  
  
 有关详细信息，请参阅 [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)。  
  
## <a name="see-also"></a>另请参阅  
 [演练：生成应用程序](../ide/walkthrough-building-an-application.md)   
 [如何：查看、保存和配置生成日志文件](../ide/how-to-view-save-and-configure-build-log-files.md)   
 [编译和生成](../ide/compiling-and-building-in-visual-studio.md)
