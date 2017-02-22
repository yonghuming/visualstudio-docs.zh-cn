---
title: "如何：取消显示编译器警告 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：取消显示编译器警告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

通过指定一个或多个可以 declutter 生成日志编译器警告您不希望它包含。  例如，可以使用此方法检查自动生成的数组，但不是全部信息，在设置生成记录详细级别为正常，详细时，或者诊断。  有关详细的更多信息，请参见 [如何：查看、保存和配置生成日志文件](../ide/how-to-view-save-and-configure-build-log-files.md)。  
  
### 禁止显示 Visual C\# 或 F\# 的特定警告  
  
1.  在 **解决方案资源管理器**，选择要禁止显示警告的项目。  
  
2.  在菜单栏上，依次选择 **查看**，**属性页**。  
  
3.  选择 **生成** 页。  
  
4.  在 **禁止显示警告** 框中，指定要禁止显示警告的错误代码，由分号分隔，然后重新生成解决方案。  
  
### 禁止显示 Visual C\+\+ 的特定警告  
  
1.  在 **解决方案资源管理器**，选择要禁止显示警告的项目或源文件。  
  
2.  在菜单栏上，依次选择 **查看**，**属性页**。  
  
3.  选择 **配置属性** 类别中，选择 **C\/C\+\+** 类别，然后选择 **高级** 页。  
  
4.  执行以下步骤之一：  
  
    -   在 **禁用特定警告** 框中，指定要禁止显示警告的错误代码，由分号分隔。  
  
    -   在 **禁用特定警告** 框中，选择 **编辑** 显示多个选项卡。  
  
5.  选择 **确定** 按钮，然后重新生成解决方案。  
  
## 禁止显示 Visual Basic 的警告  
 可以通过编辑该项的 .vbproj 文件隐藏 Visual Basic 的特定编译器警告。  还可以使用 [编译页，项目设计器](../ide/reference/compile-page-project-designer-visual-basic.md) 按类别禁止显示警告。  有关更多信息，请参见[在 Visual Basic 中配置警告](../ide/configuring-warnings-in-visual-basic.md)。  
  
#### 禁止显示 Visual Basic 的特定警告  
  
1.  在 **解决方案资源管理器**，选择要禁止显示警告的项目。  
  
2.  在菜单栏上，选择 **项目**，**卸载项目**。  
  
3.  在 **解决方案资源管理器**，请打开项目的快捷菜单，然后选择 **编辑***ProjectName***.vbproj**。  
  
     项目文件将在代码编辑器中打开。  
  
4.  设置 `<NoWarn></NoWarn>` 元素将生成的生成配置。  
  
     下面的示例在"调试"生成配置的粗体文本显示 `<NoWarn></NoWarn>` 元素在 x86 平台：  
  
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
        <NoWarn> </NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
5.  添加一个或多个警告编号为 `<NoWarn>` 元素的值。  如果指定多个警告编号，请之间用逗号，如下面的示例所示。  
  
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
  
6.  保存到 .vbproj 文件的更改。  
  
7.  在菜单栏上，选择 **项目**，**重新加载项目**。  
  
8.  在菜单栏上，依次选择 **生成**，**重新生成解决方案**。  
  
     **输出** windows 不再表示警告，请指定了。  
  
 有关更多信息，请参见[\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)。  
  
## 请参阅  
 [演练：生成应用程序](../ide/walkthrough-building-an-application.md)   
 [如何：查看、保存和配置生成日志文件](../ide/how-to-view-save-and-configure-build-log-files.md)   
 [在 Visual Studio 中构建应用程序](../ide/compiling-and-building-in-visual-studio.md)