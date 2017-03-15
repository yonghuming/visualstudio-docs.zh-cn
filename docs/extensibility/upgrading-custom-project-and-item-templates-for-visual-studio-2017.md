---
title: "对 Visual Studio&quot;15&quot;升级自定义项目和项模板 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: af2000e6c3649b625c54ed9dc2706d64642016ad
ms.lasthandoff: 02/22/2017

---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-2017"></a>升级自定义项目和项模板的 Visual Studio 2017
从 Visual Studio 2017 开始，Visual Studio 正在改变它发现通过.vsix 或.msi 已安装的项目和项模板的方式。 如果您拥有使用自定义项目或项模板的扩展，您需要更新您的扩展。 本主题说明您必须执行的操作。  
  
 此更改将影响 Visual Studio 2017。 它不影响 Visual Studio 的早期版本。  
  
 如果您想要作为 VSIX 扩展的一部分创建的项目或项模板，请参阅[创建自定义项目和项模板](../extensibility/creating-custom-project-and-item-templates.md)。  
  
## <a name="template-scanning"></a>扫描的模板  
 以前， **devenv /setup**或**devenv /installvstemplates**扫描以查找项目和项模板的本地磁盘。 从预览版 4 开始，扫描将执行仅为用户级别位置 (**%USERPROFILE%\Documents\\<Visual studio=""></Visual>\>\My Exported Templates\\**) 用于通过生成模板**文件 / 导出模板**命令。  
  
 对于其他 （非用户） 的位置，您必须包含指定的位置和模板的其他特征的 manifest(.vstman) 文件。 用于模板的.vstemplate 文件一起生成.vstman 文件。 如果您安装使用.vsix 扩展，可以通过重新编译 Visual Studio 2017 中的扩展来实现此目的。 但是，如果您使用一个.msi，则需要手动进行更改。 您需要做才能实现这些更改的列表，请参阅**对扩展安装与升级。MSI**本主题中更高版本。  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>如何更新 VSIX 扩展与项目或项模板  
 此过程说明如何通过 Visual Studio 2017
1.  在 Visual Studio 2017 中打开解决方案。 您将需要升级的代码。 单击“确定”。  
  
2.  在升级完成后，您可能需要更改安装目标的版本。 在 VSIX 项目中，打开 source.extension.vsixmanifest 文件并选择**安装目标**选项卡。 如果**版本范围**字段是**[14.0]**，请单击**编辑**并将其更改为包含 Visual Studio 2017。 例如，您可以将其设置为**[14.0,15.0]**安装扩展，Visual Studio 2015 或 Visual Studio 2017，或指向**[15.0]**以将其安装到只需使用 Visual Studio 2017。  
  
3.  重新编译代码。  
  
4.  关闭 Visual Studio。  
  
5.  安装 VSIX。  
  
6.  可以通过执行以下测试的更新︰  
  
    1.  文件扫描更改激活由以下注册表项︰  
  
         **reg 添加 hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**  
  
    2.  添加键后，运行**devenv /installvstemplates**。  
  
    3.  重新打开 Visual Studio。 应该在预期位置中找到您的模板。  
  
    > [!NOTE]
    >  在注册表项存在时，Visual Studio 扩展性项目模板不可用。 您必须删除该注册表项 (并重新运行**devenv /installvstemplates**) 来使用它们。  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>部署项目和项模板的其他建议  
  
-   避免使用压缩的模板文件。 压缩文件需要被解压缩以便检索的资源和内容的模板，因此它们将 costlier 使用。 相反，应将项目和项模板部署为单独的文件，以加快模板初始化自己目录下。 VSIX 扩展 SDK 生成任务会自动将任何压缩的模板解压缩在创建 VSIX 文件时。  
  
-   避免以避免不必要的资源程序集加载模板在发现期间使用的模板名称、 说明、 图标或预览软件包/资源 ID 条目。 相反，本地化的清单可用于创建每个区域设置，从而使用本地化的名称或属性的模板条目。  
  
-   如果包含作为文件项模板，生成清单可能不会得到您预期的结果。 在这种情况下，您需要将手动生成清单添加到 VSIX 项目。  
  
## <a name="file-changes-in-project-and-item-templates"></a>在项目和项模板中的文件更改  
 我们将展示 Visual Studio 2015 版本模板文件的 Visual Studio"15"版本之间的差异点，以便可以正确地创建新文件。  
  
 下面是由 Visual Studio 2015 创建的默认项目.vstemplate 文件︰  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">  
  <TemplateData>  
    <Name>ProjectTemplate1</Name>  
    <Description>ProjectTemplate1</Description>  
    <Icon>ProjectTemplate1.ico</Icon>  
    <ProjectType>CSharp</ProjectType>  
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
    <SortOrder>1000</SortOrder>  
    <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>  
    <CreateNewFolder>true</CreateNewFolder>  
    <DefaultName>ProjectTemplate1</DefaultName>  
    <ProvideDefaultName>true</ProvideDefaultName>  
  </TemplateData>  
  <TemplateContent>  
    <Project File="ProjectTemplate.csproj" ReplaceParameters="true">  
      <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>  
      <ProjectItem ReplaceParameters="true" OpenInEditor="true">Class1.cs</ProjectItem>  
    </Project>  
  </TemplateContent>  
</VSTemplate>  
  
```  
  
 下面是源于重新生成 VSIX 项目.vstman 文件 （可以在 VSIX 项目的清单目录中找到它）︰  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Project">  
    <RelativePathOnDisk>CSharp\1033\ProjectTemplate1</RelativePathOnDisk>  
    <TemplateFileName>ProjectTemplate1.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>ProjectTemplate1</Name>  
        <Description>ProjectTemplate1</Description>  
        <Icon>ProjectTemplate1.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <SortOrder>1000</SortOrder>  
        <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>  
        <CreateNewFolder>true</CreateNewFolder>  
        <DefaultName>ProjectTemplate1</DefaultName>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 所提供的信息[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)元素保持不变。 ** \<VSTemplateContainer&1;>**元素指向关联的模板的.vstemplate 文件。  
  
 下面是由 Visual Studio 2015 创建的默认项.vstemplate 文件︰  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">  
  <TemplateData>  
    <Name>ItemTemplate1</Name>  
    <Description>ItemTemplate1</Description>  
    <Icon>ItemTemplate1.ico</Icon>  
    <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>  
    <ProjectType>CSharp</ProjectType>  
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    <DefaultName>Class.cs</DefaultName>  
  </TemplateData>  
  <TemplateContent>  
    <References>  
      <Reference>  
        <Assembly>System</Assembly>  
      </Reference>  
    </References>  
    <ProjectItem ReplaceParameters="true">Class.cs</ProjectItem>  
  </TemplateContent>  
</VSTemplate>  
  
```  
  
 下面是源于重新生成 VSIX 项目.vstman 文件 （可以在 VSIX 项目的清单目录中找到它）︰  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Item">  
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>  
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>ItemTemplate1</Name>  
        <Description>ItemTemplate1</Description>  
        <Icon>ItemTemplate1.ico</Icon>  
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <DefaultName>Class.cs</DefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 所提供的信息** \<TemplateData&1;>**元素保持不变。 ** \<VSTemplateContainer&1;>**元素指向关联的模板的.vstemplate 文件  
  
 有关.vstman 文件的不同元素的详细信息，请参阅[Visual Studio 模板清单架构参考](../extensibility/visual-studio-template-manifest-schema-reference.md)。  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>与安装的扩展的升级。MSI  
 某些基于 MSI 的扩展插件将模板部署到常用模板位置，如下所示︰  
  
-   **\<Visual Studio 安装目录&1;> \Common7\IDE\\<ProjectTemplates temtemplates="">**</ProjectTemplates>  
  
-   **\<Visual Studio 安装目录&1;> \Common7\IDE\Extensions\\<>\>\\<Project temtemplates="">**</Project>  
  
 如果您的扩展插件执行的基于 MSI 的部署，您需要手动生成模板清单，并确保包括扩展安装程序。 您应比较上面列出的.vstman 示例和[Visual Studio 模板清单架构参考](../extensibility/visual-studio-template-manifest-schema-reference.md)。 若要查看您需要包括  
  
 您应创建单独的项目和项模板的清单，它们应指向根模板目录指定更高版本。 您应创建每个扩展名和区域设置提供一个清单。  
  
## <a name="troubleshooting-template-installation"></a>模板安装疑难解答  
 如果您遇到问题部署项目或项模板，可以启用诊断日志记录。  
  
1.  运行以下命令以设置注册表项来启用日志记录︰  
  
     **reg 添加 HKCU\software\microsoft\visualstudio\15.0_Config\VSTemplate /v EnableTemplateDiscoveryLog /t REG_DWORD /d 1**  
  
2.  启动 Visual Studio 并启动新项目和新项对话框，以便初始化两个模板树。 模板日志现在将出现在**%LOCALAPPDATA%\Microsoft\VisualStudio\15.0\VsTemplateDiagnosticsList.csv**。 每个模板树初始化追加到此日志条目。  
  
 日志文件包含以下列︰  
  
-   **FullPathToTemplate**，它具有以下值︰  
  
    -   1 表示基于清单的部署  
  
    -   对于基于磁盘的部署的&0;  
  
-   **TemplateFileName**  
  
-   其他模板属性
