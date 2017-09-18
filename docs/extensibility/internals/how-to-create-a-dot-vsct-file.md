---
title: "如何: 创建。Vsct 文件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT 文件创建"
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何: 创建。Vsct 文件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

有多种方法可以创建一个基于 XML 的 Visual Studio 命令表配置 \(.vsct\) 文件。  
  
-   您可以创建新的 VSPackage 中 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 包模板。  
  
-   基于 XML 的命令表配置编译器 Vsct.exe，可用于从现有.ctc 文件中生成文件。  
  
-   Vsct.exe 可用于从现有的.cto 文件生成.vsct 文件。  
  
-   您可以手动创建一个新的.vsct 文件。  
  
 本主题说明如何手动创建一个新的.vsct 文件。  
  
### 若要手动创建新的.vsct 文件  
  
1.  启动 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
2.  在 **文件** 菜单上，指向 **新建**, ，然后单击 **文件**。  
  
3.  在 **模板** 窗格中，单击 **XML 文件** ，然后单击 **打开**。  
  
4.  在 **视图** 菜单上，单击 **属性窗口** 要显示的 XML 文件的属性。  
  
5.  在 **属性** 窗口中，单击浏览 \(...\) 架构属性的按钮。  
  
6.  在 XSD 架构的列表中，选择 vsct.xsd 架构。 如果不是在列表中，请单击 **添加** ，然后找到本地驱动器上的文件。 单击 **确定** 完消息后。  
  
7.  在 XML 文件中，键入 `<CommandTable` 然后按 tab 键。 通过键入来结束该标记 `>`。  
  
     这将创建一个基本.vsct 文件。  
  
8.  填写你想要添加的 XML 文件的元素，根据 [VSCT 架构](../../extensibility/vsct-xml-schema-reference.md)。 有关详细信息，请参阅[创作。Vsct 文件](../../extensibility/internals/authoring-dot-vsct-files.md)。  
  
## 编译代码  
 只需将.vsct 文件添加到项目不会导致编译它。 必须在生成过程中将其合并。  
  
### 若要将.vsct 文件添加到项目编译  
  
1.  在编辑器中打开你的项目文件。 如果加载该项目，您必须首先卸载它。  
  
2.  添加 [ItemGroup 元素](../../msbuild/itemgroup-element-msbuild.md) 包含一个 VSCTCompile 元素，如下面的示例中所示。  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     ResourceName 元素应始终设置为 `Menus.ctmenu`。  
  
3.  如果您的项目包含.resx 文件，请添加 EmbeddedResource 元素，其中包含一个 MergeWithCTO 元素，如下面的示例中所示。  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     此标记应该包含嵌入的资源的 ItemGroup 元素内。  
  
4.  打开包文件，通常名为 *p o j*Package.cs 或 *p o j*Package.vb，在编辑器中的。  
  
5.  向包类中，添加 ProvideMenuResource 属性，如下面的示例中所示。  
  
    ```c#  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     第一个参数值必须匹配在项目文件中定义的资源名称特性的值。  
  
## 请参阅  
 [创作。Vsct 文件](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio 命令表 \(。Vsct\) 文件](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [如何：从现有的 .Ctc 文件创建 .Vsct 文件](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [如何：从现有 .Cto 文件创建 .Vsct 文件](../Topic/How%20to:%20Create%20a%20.Vsct%20File%20from%20an%20Existing%20.Cto%20File.md)   
 [VSCT XML 架构参考](../../extensibility/vsct-xml-schema-reference.md)