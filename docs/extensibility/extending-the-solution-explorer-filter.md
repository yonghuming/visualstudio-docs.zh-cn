---
title: "扩展的解决方案资源管理器中筛选器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "解决方案资源管理器扩展"
  - "扩展性 [Visual Studio]、 项目和解决方案"
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# 扩展的解决方案资源管理器中筛选器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以扩展 **解决方案资源管理器** 筛选功能，以显示或隐藏不同的文件。 例如，您可以创建显示只有 C\# 类工厂中的文件的筛选器 **解决方案资源管理器**, ，如本演练中所示。  
  
## 系统必备  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关更多信息，请参见[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
### 创建 Visual Studio 程序包项目  
  
1.  创建一个名为的 VSIX 项目 `FileFilter`。 添加一个名为的自定义命令项模板 **FileFilter**。 有关详细信息，请参阅[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  添加对引用 `System.ComponentModel.Composition` 和 `Microsoft.VisualStudio.Utilities`。  
  
3.  使显示在该菜单命令 **解决方案资源管理器** 工具栏。 打开 FileFilterPackage.vsct 文件。  
  
4.  更改 `<Button>` 块，以下列︰  
  
    ```xml  
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">  
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>FileNameFilter</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
### 更新清单文件  
  
1.  在 source.extension.vsixmanifest 文件中，添加为 MEF 组件的资产。  
  
2.  在 **资产** 选项卡上，选择 **新建** 按钮。  
  
3.  在 **类型** 字段中，选择 **Microsoft.VisualStudio.MefComponent**。  
  
4.  在 **源** 字段中，选择 **当前解决方案中的项目**。  
  
5.  在 **项目** 字段中，选择 **FileFilter**, ，然后选择 **确定** 按钮。  
  
### 添加筛选器代码  
  
1.  将某些 Guid 添加到 FileFilterPackageGuids.cs 文件︰  
  
    ```c#  
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file  
    public const int FileFilterId = 0x100;  
    ```  
  
2.  将类文件添加到名为 FileNameFilter.cs 的过滤项目。  
  
3.  使用下面的代码替换空命名空间和空类。  
  
     `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` 方法采用集合，其中包含的解决方案根目录 \(`rootItems`\)，并返回要在筛选器中包含的项集合。  
  
     `ShouldIncludeInFilter` 方法筛选器中的项 **解决方案资源管理器** 基于前提是您指定层次结构。  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using System.Text.RegularExpressions;  
    using System.Threading.Tasks;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio.Shell;  
  
    namespace FileFilter  
    {  
        // Implements ISolutionTreeFilterProvider. The SolutionTreeFilterProvider attribute declares it as a MEF component  
        [SolutionTreeFilterProvider(FileFilterPackageGuids.guidFileFilterPackageCmdSetString, (uint)(FileFilterPackageGuids.FileFilterId))]  
        public sealed class FileNameFilterProvider : HierarchyTreeFilterProvider  
        {  
            SVsServiceProvider svcProvider;  
            IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;  
  
            // Constructor required for MEF composition  
            [ImportingConstructor]  
            public FileNameFilterProvider(SVsServiceProvider serviceProvider, IVsHierarchyItemCollectionProvider hierarchyCollectionProvider)  
            {  
                this.svcProvider = serviceProvider;  
                this.hierarchyCollectionProvider = hierarchyCollectionProvider;  
            }  
  
            // Returns an instance of Create filter class.  
            protected override HierarchyTreeFilter CreateFilter()  
            {  
                return new FileNameFilter(this.svcProvider, this.hierarchyCollectionProvider, FileNamePattern);  
            }  
  
            // Regex pattern for CSharp factory classes  
            private const string FileNamePattern = @"\w*factory\w*(.cs$)";  
  
            // Implementation of file filtering  
            private sealed class FileNameFilter : HierarchyTreeFilter  
            {  
                private readonly Regex regexp;  
                private readonly IServiceProvider svcProvider;  
                private readonly IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;  
  
                public FileNameFilter(  
                    IServiceProvider serviceProvider,  
                    IVsHierarchyItemCollectionProvider hierarchyCollectionProvider,  
                    string fileNamePattern)  
                {  
                    this.svcProvider = serviceProvider;  
                    this.hierarchyCollectionProvider = hierarchyCollectionProvider;  
                    this.regexp = new Regex(fileNamePattern, RegexOptions.IgnoreCase);  
                }  
  
                // Gets the items to be included from this filter provider.   
                // rootItems is a collection that contains the root of your solution  
                // Returns a collection of items to be included as part of the filter  
                protected override async Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem> rootItems)  
                {  
                    IVsHierarchyItem root = HierarchyUtilities.FindCommonAncestor(rootItems);  
                    IReadOnlyObservableSet<IVsHierarchyItem> sourceItems;  
                    sourceItems = await hierarchyCollectionProvider.GetDescendantsAsync(  
                                        root.HierarchyIdentity.NestedHierarchy,  
                                        CancellationToken);  
  
                    IFilteredHierarchyItemSet includedItems = await hierarchyCollectionProvider.GetFilteredHierarchyItemsAsync(  
                        sourceItems,  
                        ShouldIncludeInFilter,  
                        CancellationToken);  
                    return includedItems;  
                }  
  
                // Returns true if filters hierarchy item name for given filter; otherwise, false</returns>  
                private bool ShouldIncludeInFilter(IVsHierarchyItem hierarchyItem)  
                {  
                    if (hierarchyItem == null)  
                    {  
                        return false;  
                    }  
                    return this.regexp.IsMatch(hierarchyItem.Text);  
                }  
            }  
        }  
    }  
  
    ```  
  
4.  在 FileFilter.cs，从 FileFilter 构造函数中删除命令放置和处理代码。 结果应如下所示︰  
  
    ```c#  
    private FileFilter(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException("package");  
        }  
  
        this.package = package;  
    }  
    ```  
  
     删除的 ShowMessageBox\(\) 方法。  
  
5.  在 FileFilterPackage，cs，替换为以下替换 initialize （） 方法中的代码︰  
  
    ```c#  
    protected override void Initialize()  
    {  
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
    }  
    ```  
  
### 测试您的代码  
  
1.  生成并运行该项目。 将显示 Visual Studio 的第二个实例。 这称为实验实例。  
  
2.  在 Visual Studio 的实验实例中，打开一个 C\# 项目。  
  
3.  查找添加到解决方案资源管理器工具栏的按钮。 它应该是左侧起的第四个按钮。  
  
4.  当单击按钮时，应出，筛选出所有文件，你应该看到"所有项目都已被都都过滤视图中。" 在解决方案资源管理器。