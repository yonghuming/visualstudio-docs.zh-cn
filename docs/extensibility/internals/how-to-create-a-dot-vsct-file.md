---
title: "如何： 创建。Vsct 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f05461aa75a8088f758bd24ec5e73ccd407a8681
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-vsct-file"></a>如何： 创建。Vsct 文件  
  
有多种方法来创建一个基于 XML 的 Visual Studio 命令表配置 (.vsct) 文件。  
  
-   你可以创建新 VSPackage 中的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]包模板。  
  
-   基于 XML 的命令表的配置编译器 Vsct.exe，可用于从现有的.ctc 文件生成文件。  
  
-   Vsct.exe 可用于从现有.cto 文件生成一个.vsct 文件。  
  
-   你可以手动创建新的.vsct 文件。  
  
 本主题说明如何手动创建新的.vsct 文件。  
  
### <a name="to-manually-create-a-new-vsct-file"></a>若要手动创建新的.vsct 文件  
  
1.  启动 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
2.  上**文件**菜单上，指向**新建**，然后单击**文件**。  
  
3.  在**模板**窗格中，单击**XML 文件**，然后单击**打开**。  
  
4.  上**视图**菜单上，单击**属性窗口**以显示 XML 文件的属性。  
  
5.  在**属性**窗口中，单击架构属性上的浏览 （...） 按钮。  
  
6.  在 XSD 架构的列表中，选择 vsct.xsd 架构。 如果它不在列表中，单击**添加**，然后找到本地驱动器上的文件。 单击**确定**完成之后。  
  
7.  在 XML 文件中，键入`<CommandTable`然后按 tab 键。 通过键入结束标记`>`。  
  
     这将创建一个基本的.vsct 文件。  
  
8.  填写你想要添加的 XML 文件的元素，根据[VSCT 架构](../../extensibility/vsct-xml-schema-reference.md)。 有关详细信息，请参阅[创作。Vsct 文件](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>如何：从现有的 .Ctc 文件创建 .Vsct 文件  
  
可以从现有的命令表 .ctc 源文件创建一个基于 XML 的 .vsct 文件。 通过执行此操作，你可以充分利用新的基于 XML 的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]命令表 (VSCT) 编译器格式。  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>从 .ctc 文件创建 .vsct  文件  
  
1.  获取 Perl 语言的副本。  
  
2.  获得 Perl 脚本 ConvertCTCToVSCT.pl，通常位于一份 *\<Visual Studio SDK 安装路径 >*\VisualStudioIntegration\Tools\bin 文件夹。  
  
3.  获取要转换的 .ctc 源文件的副本。  
  
4.  将这些文件放在同一个目录中。  
  
5.  在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]命令提示窗口中，导航到的目录。  
  
6.  类型  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     其中，PkgCmd.ctc 是 .ctc 文件的名称，PkgCmd.vsct 是要创建的 .vsct 文件的名称。  
  
     这将创建一个新的 .vsct XML 命令表源文件。 可以像其他任何 .vsct 文件一样，使用 VSCT 编译器 Vsct.exe 来编译此文件。  
  
    > [!NOTE]
    >  可以通过重新格式化 XML 注释来提高 .vsct 文件的可读性。  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>如何：从现有 .Cto 文件创建 .Vsct 文件  
  
可从现有的二进制 .cto 文件创建一个基于 XML 的 .vsct 文件。 这样既可充分利用新的命令表编译器格式。 即使 .cto 文件是从 .ctc 文件编译而来，此过程仍然有效。 你可以编辑 .vsct 文件并将其编译到其他 .cto 文件。  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>从 .cto 文件创建 .Vsct 文件  
  
1.  获取 .cto 文件及其对应 .ctsym 文件的副本。  
  
2.  将文件与 vsct.exe 编译器放在同一目录中。  
  
3.  在 Visual Studio 命令提示符处，转到包含 .cto 和 .ctsym 文件的目录。  
  
4.  类型 **vsct.exe** *ctofilename***.cto** *vsctfilename***.vsct -S***symfilename***.ctsym**。  
  
     `ctofilename`是.cto 文件的名称`vsctfilename`是你想要创建的 vsct 文件的名称和`symfilename`是.ctsym 文件的名称。  
  
     此过程可创建新的 .vsct XML 命令表编译器文件。 可像任何其他 .vsct 文件一样，使用 vsct.exe（vsct 编译器）来编辑和编译此文件。  
  
## <a name="compiling-the-code"></a>编译代码  
 只需向项目中添加.vsct 文件不会导致编译它。 必须在生成过程中将其合并。  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>若要添加到项目编译的.vsct 文件  
  
1.  在编辑器中打开项目文件。 如果加载该项目，你必须先卸载它。  
  
2.  添加[ItemGroup 元素](../../msbuild/itemgroup-element-msbuild.md)包含一个 VSCTCompile 元素，如下面的示例中所示。  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     ResourceName 元素应始终设置为`Menus.ctmenu`。  
  
3.  如果你的项目包含.resx 文件，添加包含 MergeWithCTO 元素 EmbeddedResource 元素，如下面的示例中所示。  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     此标记应转包含嵌入的资源的 p 元素内。  
  
4.  打开包文件，通常名为*ProjectName*Package.cs 或*ProjectName*Package.vb，在编辑器中的。  
  
5.  在下面的示例所示，请将 ProvideMenuResource 属性添加到包类。  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     第一个参数值必须匹配在项目文件中定义的资源名称特性的值。  
  
## <a name="see-also"></a>另请参阅  
 [创作。Vsct 文件](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio 命令表 (。Vsct) 文件](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML 架构参考](../../extensibility/vsct-xml-schema-reference.md)