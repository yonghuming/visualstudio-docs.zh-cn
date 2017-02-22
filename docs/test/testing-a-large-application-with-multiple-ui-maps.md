---
title: "使用多个 UI 映射测试大型应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编码的 UI 测试, 用于大型应用程序"
  - "编码的 UI 测试, 多个 UI 映射"
ms.assetid: 6e1ae9ec-e9b1-458a-bd96-0eb15e46f1d5
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "mlearned"
manager: "douge"
---
# 使用多个 UI 映射测试大型应用程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主题讨论在使用多个 UI 映射来测试大型应用程序时如何使用编码的 UI 测试。  
  
 **要求**  
  
-   Visual Studio Enterprise  
  
 在创建新的编码 UI 测试时，默认情况下，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 测试框架会在 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> 类中生成测试代码。  有关如何录制编码的 UI 测试的详细信息，请参阅[创建编码的 UI 测试](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)和[编码的 UI 测试剖析](../test/anatomy-of-a-coded-ui-test.md)。  
  
 为 UI 映射生成的代码针对与测试交互的每个对象都包含一个类。  对于每个生成的方法，都会专门为该方法生成方法参数的伴生类。  如果应用程序中存在大量对象、页以及窗体和控件，UI 映射可能会变得很大。  而且，如果多个人正在执行测试，则只有一个大型 UI 映射文件的应用程序会变得难以操作。  
  
 使用多个 UI 映射文件具有以下优点：  
  
-   每个映射可与应用程序的一个逻辑子集关联。  这样就更便于管理变更。  
  
-   每个测试人员都可以处理应用程序的一个部分并签入其代码，而不会干扰正在处理应用程序的其他部分的其他测试人员。  
  
-   可以增量方式调整对应用程序 UI 的内容添加，从而最大程度地减少对 UI 其他部分测试的影响。  
  
## 你是否需要多个 UI 映射？  
 可在以下情况下创建多个 UI 映射：  
  
-   一起执行逻辑操作的多个复杂的复合 UI 控件集，如网站中的注册页或购物车的购买页。  
  
-   可从应用程序的各个点进行访问的独立的一组控件，如具有多个操作页的向导。  如果向导的每页都特别复杂，则可为每页创建单独的 UI 映射。  
  
## 添加多个 UI 映射  
  
#### 向编码的 UI 测试项目中添加 UI 映射  
  
1.  若要在编码的 UI 测试项目中创建文件夹以存储所有 UI 映射，请在**“解决方案资源管理器”**中右击编码的 UI 测试项目文件、指向**“添加”**，再选择**“新建文件夹”**。  例如，可将其命名为 `UIMaps`。  
  
     新文件夹显示在编码的 UI 测试项目下面。  
  
2.  右击 `UIMaps` 文件夹、指向**“添加”**，然后选择**“新建项”**。  
  
     显示**“添加新项”**对话框。  
  
    > [!NOTE]
    >  若要添加新的编码 UI 测试映射，你必须在编码的 UI 测试项目中。  
  
3.  从列表中选择**“编码的 UI 测试映射”**。  
  
     在**“名称”**框中，输入新 UI 映射的名称。  使用该映射将表示的组件或页的名称，例如，`HomePageMap`。  
  
4.  选择**“添加”**。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 窗口将最小化，同时显示**“编码的 UI 测试生成器”**对话框。  
  
5.  为第一个方法录制操作，然后选择**“生成代码”**。  
  
6.  在为第一个组件或页录制所有操作和断言并将它们分组为方法后，关闭**“编码的 UI 测试生成器”**对话框。  
  
7.  继续创建 UI 映射。  为每个组件录制操作和断言并将它们分组为方法，然后生成代码。  
  
 在许多情况下，应用程序的顶级窗口对所有向导、窗体和页保持不变。  尽管每个 UI 映射都有一个用于顶级窗口的类，但所有映射可能都引用同一个顶级窗口，应用程序的所有组件都在该窗口中运行。  编码的 UI 测试会按层次结构从顶级窗口开始从上至下搜索控件，所以在复杂应用程序中，每个 UI 映射中的实际顶级窗口可能是重复的。  如果实际顶级窗口是重复的，则在该窗口发生改变时，将会进行多项修改。  当你在 UI 映射之间进行切换时，这可能会引起性能问题。  
  
 为了尽量减小这种影响，可以使用 `CopyFrom()` 方法来确保该 UI 映射中的新顶级窗口与主顶级窗口相同。  
  
## 示例  
 以下示例是某个实用工具类的一部分，该类可提供对每个组件及其子控件的访问权限，而这些子控件由在各种 UI 映射中生成的类表示。  
  
 对于本示例，名为 `Contoso` 的 Web 应用程序具有一个主页、一个产品页和一个购物车页。  上述每个页共享一个公共的顶级窗口，即浏览器窗口。  每页都有一个 UI 映射，而且实用工具类具有类似于下面的代码：  
  
```  
using ContosoProject.UIMaps;  
using ContosoProject.UIMaps.HomePageClasses;  
using ContosoProject.UIMaps.ProductPageClasses;  
using ContosoProject.UIMaps.ShoppingCartClasses;  
  
namespace ContosoProject  
{  
    public class TestRunUtility  
    {  
        // Private fields for the properties  
        private HomePage homePage = null;  
        private ProductPage productPage = null;  
        private ShoppingCart shoppingCart = null;  
  
        public TestRunUtility()  
        {  
            homePage = new HomePage();  
        }  
  
        // Properties that get each UI Map  
        public HomePage HomePage  
        {  
            get { return homePage; }  
            set { homePage = value; }  
        }  
  
        // Gets the ProductPage from the ProductPageMap.  
        public ProductPage ProductPageObject  
        {  
            get  
            {  
                if (productPage == null)  
                {  
                    // Instantiate a new page from the UI Map classes  
                    productPage = new ProductPage();  
  
                    // Since the Product Page and Home Page both use  
                    // the same browser page as the top level window,  
                    // get the top level window properties from the  
                    // Home Page.  
                    productPage.UIContosoFinalizeWindow.CopyFrom(  
                        HomePage.UIContosoWindowsIWindow);  
                }  
                return productPage;  
            }  
        }  
  
    // Continue to create properties for each page, getting the   
    // page object from the corresponding UI Map and copying the   
    // top level window properties from the Home Page.  
}  
```  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.BrowserWindow.CopyFrom%2A>   
 [使用 UI 自动化来测试代码](../test/use-ui-automation-to-test-your-code.md)   
 [创建编码的 UI 测试](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [编码的 UI 测试剖析](../test/anatomy-of-a-coded-ui-test.md)