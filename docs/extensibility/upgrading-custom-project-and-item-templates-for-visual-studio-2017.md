---
title: "升级自定义项目和项模板的 Visual Studio 2017 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
caps.latest.revision: "3"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 76437dff5aa59e4864216318e64a07245c15c68d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-2017"></a>升级自定义项目和项模板的 Visual Studio 2017
从 Visual Studio 2017 年 1 开始，Visual Studio 正在改变其发现由.vsix 或.msi 安装的项目和项模板的方式。 如果你拥有使用自定义项目或项模板的扩展，你需要更新你的扩展。 本主题介绍你必须执行的操作。  
  
 此更改影响仅 Visual Studio 自 2017 年 1。 它不影响 Visual Studio 的早期版本。  
  
 如果你想要创建项目或项模板作为 VSIX 扩展的一部分，请参阅[创建自定义项目和项模板](../extensibility/creating-custom-project-and-item-templates.md)。  
  
## <a name="template-scanning"></a>扫描的模板  
 以前， **devenv /setup**或**devenv /installvstemplates**扫描本地磁盘上，以查找项目和项模板。 从预览版 4 开始，扫描将执行仅为用户级别位置 (**%USERPROFILE%\Documents\\< Visual Studio 版本\>\My 导出模板\\**)，用来为模板生成的**文件 / 导出模板**命令。  
  
 对于其他 （非用户） 位置中，你必须包括指定的位置和模板的其他特征的 manifest(.vstman) 文件。 .Vstman 文件生成以及用于模板的.vstemplate 文件中。 如果你安装你使用.vsix 的扩展，可以通过重新编译 Visual Studio 自 2017 年中的扩展来实现此目的。 但如果使用一个.msi 时，你需要手动进行更改。 你需要如何手动进行这些更改的列表，请参阅**升级为与安装的扩展。MSI**本主题中更高版本。  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>如何使用项目或项模板更新 VSIX 扩展  
 本过程说明如何通过 Visual Studio 2017
1.  在 Visual Studio 2017 中打开解决方案。 你将需要升级的代码。 单击“确定”。  
  
2.  在升级完成后，你可能需要更改安装目标版本。 在 VSIX 项目中，打开 source.extension.vsixmanifest 文件并选择**安装目标**选项卡。如果**版本范围**字段是**[14.0]**，单击**编辑**和将其更改为包含 Visual Studio 2017。 例如，你可以将其设置为**[14.0,15.0]**安装扩展到 Visual Studio 2015 或 Visual Studio 2017，或**[15.0]**以将其安装到只是 Visual Studio 自 2017 年 1。  
  
3.  重新编译代码。  
  
4.  关闭 Visual Studio。  
  
5.  安装 VSIX。  
  
6.  你可以通过执行以下测试更新：  
  
    1.  扫描更改的文件被激活由以下注册表项：  
  
         **reg 添加 hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**  
  
    2.  添加键后，运行**devenv /installvstemplates**。  
  
    3.  重新打开 Visual Studio。 你应该在预期位置中找到你的模板。  
  
    > [!NOTE]
    >  注册表项存在时，Visual Studio 扩展性项目模板不可用。 你必须删除注册表项 (和重新运行**devenv /installvstemplates**) 以使用它们。  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>部署项目和项模板的其他建议  
  
-   避免使用压缩的模板文件。 压缩文件需要以检索资源和内容未压缩的模板，因此它们将是 costlier 使用。 相反，应将项目和项模板部署为可加速模板初始化自己目录下的单独文件。 对于 VSIX 扩展，SDK 生成任务会自动将任何压缩的模板解压缩时创建的 VSIX 文件。  
  
-   避免使用以在模板发现期间避免不必要的资源程序集加载的模板名称、 说明、 图标或预览的包/资源 ID 条目。 相反，本地化的清单可用于创建每个区域设置，从而使用本地化的名称或属性的模板项。  
  
-   如果你包含作为文件项模板，清单生成可能不会得到你预期的结果。 在这种情况下，你将需要将手动生成清单添加到 VSIX 项目。  
  
## <a name="file-changes-in-project-and-item-templates"></a>项目和项模板中的文件更改  
我们显示在 Visual Studio 2015 和 Visual Studio 2017 版本的模板文件之间的差异的点，以便可以正确创建新的文件。  
  
 下面是由 Visual Studio 2015 创建的默认项目.vstemplate 文件：  
  
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
  
 下面是造成的 VSIX 项目的重新生成.vstman 文件 （可以在 VSIX 项目的清单目录中找到它）：  
  
```xml  
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
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
  
 提供的信息[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)元素保持不变。 **\<VSTemplateContainer >**元素指向关联的模板的.vstemplate 文件。  
  
 下面是由 Visual Studio 2015 创建的默认项.vstemplate 文件：  
  
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
  
 下面是造成的 VSIX 项目的重新生成.vstman 文件 （可以在 VSIX 项目的清单目录中找到它）：  
  
```xml  
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
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
  
 提供的信息 **\<TemplateData >**元素保持不变。 **\<VSTemplateContainer >**元素指向关联的模板的.vstemplate 文件  
  
 有关.vstman 文件的不同元素的详细信息，请参阅[Visual Studio 模板清单架构参考](../extensibility/visual-studio-template-manifest-schema-reference.md)。  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>使用安装扩展的升级。MSI  
 某些基于 MSI 的扩展将模板部署到常用的模板位置，如下所示：  
  
-   **\<Visual Studio 安装目录 > \Common7\IDE\\< ProjectTemplates/ItemTemplates >**  
  
-   **\<Visual Studio 安装目录 > \Common7\IDE\Extensions\\< ExtensionName\>\\< 项目项模板 >**  
  
 如果你的扩展执行的基于 MSI 的部署，你需要手动生成模板清单，并确保它包含在扩展安装。 您应比较上面列出的.vstman 示例和[Visual Studio 模板清单架构参考](../extensibility/visual-studio-template-manifest-schema-reference.md)。 若要查看你需要包括  
  
 应创建单独的清单项目和项模板，且它们应指向根模板目录指定更高版本。 你应创建一个清单，每个扩展和区域设置。  
  
## <a name="troubleshooting-template-installation"></a>模板安装疑难解答  
 如果在部署项目或项模板的问题，你可以启用诊断日志记录。  
  
1.  在其中创建 pkgdef 文件 Common7\IDE\CommonExtensions 文件夹安装 (例如 C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef) 包含以下内容：  
  
     ```
     [$RootKey$\VsTemplate]
     "EnableTemplateDiscoveryLog"=dword:00000001
     ```

2. 通过在 Windows 搜索中搜索打开"开发人员命令提示"你的安装并运行`devenv /updateConfiguration`。

3.  启动 Visual Studio 并启动新项目和新项对话框，以便初始化两个模板树。 模板日志现在将出现在**%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** （instanceid 对应于你的 Visual Studio 实例的安装 ID）。 每个模板树初始化附加到此日志条目。  
  
 日志文件包含以下列：  
  
-   **FullPathToTemplate**，它具有以下值：  
  
    -   基于清单的部署的 1  
  
    -   基于磁盘的部署的 0  
  
-   **TemplateFileName**  
  
-   其他模板属性

注意： 若要禁用日志记录，请删除 pkgdef 文件或更改的值`EnableTemplateDiscoveryLog`到`dword:00000000`并运行`devenv /updateConfiguration`试。