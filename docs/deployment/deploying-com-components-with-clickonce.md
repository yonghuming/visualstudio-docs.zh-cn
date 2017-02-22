---
title: "使用 ClickOnce 部署 COM 组件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 部署, COM 组件"
  - "COM 组件, 部署"
  - "组件, 部署"
  - "部署应用程序 [ClickOnce], COM 组件"
  - "免注册 COM 部署"
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 使用 ClickOnce 部署 COM 组件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

旧版本 COM 组件的部署一向是个困难的任务。  因为需要对组件进行全局注册，所以可能会在重叠的应用程序之间产生非预期的副作用。  .NET Framework 应用程序中通常不会出现这种情况，因为组件与应用程序是完全隔离的或者组件是并行兼容的。  使用 Visual Studio 可以在 Windows XP 或更高版本的操作系统上部署独立的 COM 组件。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 为部署 .NET 应用程序提供了一种简单且安全的机制。  但是，如果应用程序使用的是旧版本 COM 组件，则需要采取附加步骤进行部署。  本主题介绍如何部署独立的 COM 组件和引用本机组件（例如从 Visual Basic 6.0 或 Visual C\+\+）。  
  
 有关部署独立的 COM 组件的更多信息，请参见位于 [http:\/\/msdn2.microsoft.com\/zh\-cn\/magazine\/cc188708.aspx](http://msdn2.microsoft.com/zh-cn/magazine/cc188708.aspx) 上的“Simplify App Deployment with [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] and Registration\-Free COM”（使用 ClickOnce 和免注册 COM 简化应用程序部署）。  
  
## 免注册 COM  
 免注册 COM 是一种部署和激活独立的 COM 组件的新技术。  它的工作方式是将所有组件的类型库和注册信息（通常安装到系统注册表中）放入一个称为“清单”的 XML 文件中，该文件和应用程序存储在同一文件夹中。  
  
 隔离 COM 组件要求组件在开发人员的计算机上注册，但不必在最终用户的计算机上注册。  要隔离 COM 组件，只需将其引用的**“Isolated”**属性设置为**“True”**。  默认情况下，此属性设置为**“False”**，以指示应将其视为注册的 COM 引用。  如果此属性的值为**“True”**，则将使得在生成时生成此组件的清单。  它还会使得在安装过程中将相应文件复制到应用程序文件夹。  
  
 清单生成器遇到独立的 COM 引用时，将枚举组件类型库中的所有 `CoClass` 项，将每一项与其对应的注册数据匹配，并为类型库文件中的所有 COM 类生成清单定义。  
  
## 使用 ClickOnce 部署免注册 COM 组件  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署技术非常适合部署独立的 COM 组件，因为 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 和免注册 COM 均要求组件具有清单才能够进行部署。  
  
 组件作者通常应提供清单。  但如果未提供，Visual Studio 能够为 COM 组件自动生成清单。  清单生成在 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 发布过程中执行；有关更多信息，请参见[发布 ClickOnce 应用程序](../deployment/publishing-clickonce-applications.md)。  此功能使您可以利用在早期开发环境（如 Visual Basic 6.0）中创作的旧版本组件。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 有两种部署 COM 组件的方式：  
  
-   使用引导程序部署 COM 组件，这种方式可用于系统支持的所有平台。  
  
-   使用本机组件隔离（也称为“免注册 COM”）部署。  但是，这种方式仅用于 Windows XP 或更高版本的操作系统。  
  
### 隔离和部署简单 COM 组件的示例  
 为演示免注册 COM 组件部署，此示例将使用 Visual Basic 创建一个基于 Windows 的应用程序（该应用程序引用使用 Visual Basic 6.0 创建的独立的本机 COM 组件），并使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 对其进行部署。  
  
 首先需要创建本机 COM 组件：  
  
##### 创建本机 COM 组件  
  
1.  使用 Visual Basic 6.0，从**“文件”**菜单中单击**“新建”**，然后单击**“项目”**。  
  
2.  在**“新建项目”**对话框中，选择**“Visual Basic”**节点，然后选择**“ActiveX DLL”**项目。  在**“名称”**框中键入 `VB6Hello`。  
  
    > [!NOTE]
    >  免注册 COM 只支持 ActiveX DLL 和 ActiveX 控件项目类型；不支持 ActiveX EXE 和 ActiveX 文档项目类型。  
  
3.  在**“解决方案资源管理器”**中双击**“Class1.vb”**打开文本编辑器。  
  
4.  在 Class1.vb 中，在 `New` 方法的生成代码后添加下面的代码：  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5.  生成组件。  从**“生成”**菜单中单击**“生成解决方案”**。  
  
> [!NOTE]
>  免注册 COM 只支持 DLL 和 COM 控件项目类型。  不能对免注册 COM 使用 EXE。  
  
 现在创建一个基于 Windows 的应用程序，并向其添加对 COM 组件的引用。  
  
##### 创建一个使用 COM 组件的基于 Windows 的应用程序  
  
1.  使用 Visual Basic，从**“文件”**菜单中单击**“新建”**，然后单击**“项目”**。  
  
2.  在**“新建项目”**对话框中选择**“Visual Basic”**节点，然后选择**“Windows 应用程序”**。  在**“名称”**框中键入 `RegFreeComDemo`。  
  
3.  在**“解决方案资源管理器”**中，单击**“显示所有文件”**按钮显示项目引用。  
  
4.  右击**“引用”**节点，然后从上下文菜单中选择**“添加引用”**。  
  
5.  在**“添加引用”**对话框中，单击**“浏览”**选项卡，导航至 VB6Hello.dll，然后选择它。  
  
     **“VB6Hello”**引用出现在引用列表中。  
  
6.  指向**“工具箱”**，选择一个**“Button”**控件，将其拖动到**“Form1”**窗体中。  
  
7.  在**“属性”**窗口中，将该按钮的**“Text”**属性设置为“Hello”。  
  
8.  双击按钮添加处理程序代码，并在代码文件中添加代码，使处理程序如下所示：  
  
    ```  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
        Dim VbObj As New VB6Hello.Class1  
        VbObj.SayHello()  
    End Sub  
    ```  
  
9. 运行该应用程序。  从**“调试”**菜单中，单击**“开始调试”**。  
  
 接下来需要隔离控件。  应用程序使用的每个 COM 组件在项目中都表示为 COM 引用。  在**“解决方案资源管理器”**窗口的**“引用”**节点下可以看到这些引用。  （注意，可以使用**“项目”**菜单上的**“添加引用”**命令直接添加引用，或将 ActiveX 控件拖动到窗体上间接添加引用。）  
  
 以下步骤演示如何隔离 COM 组件和发布包含独立控件的更新后的应用程序：  
  
##### 隔离 COM 组件  
  
1.  在**“解决方案资源管理器”**的**“引用”**节点中选择**“VB6Hello”**引用。  
  
2.  在**“属性”**窗口中，将**“Isolated”**属性的值从**“False”**更改为**“True”**。  
  
3.  从**“生成”**菜单中单击**“生成解决方案”**。  
  
 现在，按 F5 时，应用程序将按预期工作，但它现在运行的是免注册 COM。  为证明这一点，可尝试注销 VB6Hello.dll 组件，并在 Visual Studio IDE 之外运行 RegFreeComDemo1.exe。  这次单击按钮时，应用程序仍然工作。  如果您临时重命名应用程序清单，再次单击按钮时将失败。  
  
> [!NOTE]
>  可以通过临时注销 COM 组件来模拟缺少该组件的情况。  打开命令提示符，键入 `cd /d %windir%\system32` 以进入系统文件夹，然后键入 `regsvr32 /u VB6Hello.dll` 注销该组件。  键入 `regsvr32 VB6Hello.dll` 可以再次注册该组件。  
  
 最后一步是使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 发布应用程序：  
  
##### 发布使用独立 COM 组件的应用程序更新  
  
1.  从**“生成”**菜单中，单击**“发布 RegFreeComDemo”**。  
  
     出现“发布向导”。  
  
2.  在“发布向导”中，指定可访问和检查所发布文件的本地计算机磁盘上的位置。  
  
3.  单击**“完成”**以发布应用程序。  
  
 如果您检查发布的文件，将发现其中包括 sysmon.ocx 文件。  控件与此应用程序完全隔离，这意味着如果最终用户计算机上的另一个应用程序使用该控件的不同版本，将不会影响此应用程序。  
  
## 引用本机程序集  
 Visual Studio 支持对本机 Visual Basic 6.0 或 C\+\+ 程序集的引用；此类引用称为本机引用。  可以通过验证引用的**“文件类型”**属性设置为**“本机”**还是**“ActiveX”**来区分它是否为本机引用。  
  
 若要添加本机引用，请使用**“添加引用”**命令，然后浏览至清单。  某些组件将清单放在 DLL 内部。  在这种情况下，您只需选择 DLL 本身即可，因为 Visual Studio 只要检测到组件包含嵌入的清单，就会将该组件作为本机引用添加。  Visual Studio 还将自动包括清单中列出的任何依赖文件或程序集（如果它们作为引用的组件位于同一文件夹中）。  
  
 COM 控件隔离使您可以轻松部署尚不具有清单的 COM 组件。  但是，如果组件提供了清单，则可以直接引用该清单。  实际上，只要可能，就应始终使用组件作者提供的清单而不是使用**“Isolated”**属性。  
  
## 免注册 COM 组件部署的限制  
 免注册 COM 相对于传统部署技术提供了明显的优势。  但应该指出，也有一些限制和警告。  最大的限制在于它只能在 Windows XP 或更高版本上工作。  实现免注册 COM 要求更改组件在核心操作系统中的加载方式。  遗憾的是，免注册 COM 没有下层支持。  
  
 不是每个组件都适合作为免注册 COM。  一个组件只要满足以下任何一个条件，就不适合作为 RegFree COM：  
  
-   该组件是一个进程外服务器。  不支持 EXE 服务器；只支持 DLL。  
  
-   该组件是操作系统的一部分，或者是系统组件，如 XML、Internet Explorer 或 Microsoft 数据访问组件 \(MDAC\)。  应遵循组件作者的再发行策略；请与供应商核实。  
  
-   该组件是应用程序的一部分，如 Microsoft Office。  例如，不应尝试隔离 Microsoft Excel 对象模型。  这是 Office 的一部分，只能在安装有完整的 Office 产品的计算机上使用。  
  
-   该组件用作外接程序或管理单元，例如 Office 外接程序或 Web 浏览器中的控件。  此类组件通常需要超出清单本身范围之外的宿主环境定义的某种注册方案。  
  
-   该组件管理系统的物理设备或虚拟设备，例如后台打印程序的设备驱动程序。  
  
-   该组件是可再发行的数据访问组件。  数据应用程序通常要求安装单独的可再发行的数据访问组件才能运行。  不应尝试隔离类似 Microsoft ADO 数据控件、Microsoft OLE DB 或 Microsoft 数据访问组件 \(MDAC\) 这样的组件。  如果您的应用程序使用 MDAC 或 SQL Server Express，应将它们作设置为系统必备组件；请参见 [如何：与 ClickOnce 应用程序一起安装系统必备组件](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)。  
  
 在某些情况下，组件开发人员可以为免注册 COM 重新设计该组件。  如果不允许，还可通过使用引导程序的标准注册方案生成和发布依赖它们的应用程序。  有关更多信息，请参见[创建引导程序包](../deployment/creating-bootstrapper-packages.md)。  
  
 每个应用程序只能隔离一次 COM 组件。  例如，不能从作为同一应用程序的组成部分的两个不同**“类库”**项目隔离同一 COM 组件。  这样做将导致生成警告，运行时应用程序将无法加载。  为避免此问题，Microsoft 建议您在单个类库中封装 COM 组件。  
  
 还有几种情况，即使应用程序的部署不需要注册，也需要在开发人员的计算机上注册 COM。  `Isolated` 属性要求在开发人员的计算机上注册 COM 组件以在生成时自动生成清单。  没有能在生成时调用自行注册的注册捕获功能。  另外，类型库中任何没有显式定义的类将不反映在清单中。  使用带有预先存在的清单的 COM 组件（如本机引用）时，可能不需要在开发时注册该组件。  但是，如果组件是 ActiveX 控件并且您希望在**“工具箱”**和 Windows 窗体设计器中包括它，则需要注册。  
  
## 请参阅  
 [ClickOnce 安全和部署](../deployment/clickonce-security-and-deployment.md)