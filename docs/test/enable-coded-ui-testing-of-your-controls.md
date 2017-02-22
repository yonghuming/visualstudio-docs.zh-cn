---
title: "启用控件的编码的 UI 测试 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ef1188f-89dc-413d-801d-0efdaf9b0427
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "mlearned"
manager: "douge"
---
# 启用控件的编码的 UI 测试
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果实现用于编码的 UI 测试支持结构，您的控件可以更方便地测试。  可以逐级增大增量支持级别增量支持。  您可以通过支持录制、播放和属性验证开始。  在能够生成允许编码的 UI 测试生成器识别该控件的自定义特性，并提供自定义选件类访问从生成的代码的那些属性。  您还可以帮助编码的 UI 测试生成器获取事件，记录接近事件目的环境的方法。  
  
 **本主题内容：**  
  
1.  [通过实现辅助功能来支持录制和播放以及属性验证](../test/enable-coded-ui-testing-of-your-controls.md#recordandplayback)  
  
2.  [通过实现属性提供程序来支持自定义属性验证](../test/enable-coded-ui-testing-of-your-controls.md#customproprties)  
  
3.  [通过实现类以访问自定义属性来支持代码生成](../test/enable-coded-ui-testing-of-your-controls.md#codegeneration)  
  
4.  [通过实现操作筛选器来支持目的感知操作](../test/enable-coded-ui-testing-of-your-controls.md#intentawareactions)  
  
 ![CUIT&#95;Full](../test/media/cuit_full.png "CUIT\_Full")  
  
##  <a name="recordandplayback"></a> 通过实现辅助功能来支持录制和播放以及属性验证  
 编码的 UI 测试生成器获取有关控件记录时遇到的信息和并生成以回放该会话。  如果控件不支持辅助功能，则编码的 UI 测试生成器将使用屏幕坐标获得事件 \(如鼠标单击\) 。  测试时播放，生成的代码将在同一屏幕坐标发出鼠标单击命令。  如果控件在屏幕上的一个不同位置出现，测试时播放，生成的代码不能对控件执行该事件。  如果测试在不同的屏幕配置，在不同的环境，或者，在更改 UI 的布局之后播放，可能导致失败，。  
  
 ![CUIT&#95;RecordNoSupport](../test/media/cuit_recordnosupport.png "CUIT\_RecordNoSupport")  
  
 如果实现辅助功能，不过，当录制测试并生成代码时，编码的 UI 测试生成器将使用并获取有关控件的信息。  然后，当您运行测试，即使在用户界面的其他位置，生成的代码在您的控件之前将重播这些事件。  使用您的控件的基本属性，测试作者还可以创建维护。  
  
 ![CUIT&#95;Record](../test/media/cuit_record.png "CUIT\_Record")  
  
### 支持录制和播放、属性验证以及 Windows 窗体控件的导航  
 如以下过程所述，为控件实现辅助功能并且详细介绍了 <xref:System.Windows.Forms.AccessibleObject>。  
  
 ![CUIT&#95;Accessible](../test/media/cuit_accessible.png "CUIT\_Accessible")  
  
1.  实现从 <xref:System.Windows.Forms.Control.ControlAccessibleObject>派生的选件类，并重写 <xref:System.Windows.Forms.Control.AccessibilityObject%2A> 属性返回您的选件类对象。  
  
    ```c#  
    public partial class ChartControl : UserControl  
    {  
        // Overridden to return the custom AccessibleObject for the control.  
        protected override AccessibleObject CreateAccessibilityInstance()  
        {  
            return new ChartControlAccessibleObject(this);  
        }  
  
        // Inner class ChartControlAccessibleObject represents accessible information  
        // associated with the ChartControl and is used when recording tests.  
        public class ChartControlAccessibleObject : ControlAccessibleObject  
        {  
            ChartControl myControl;  
            public ChartControlAccessibleObject(ChartControl ctrl)  
                : base(ctrl)  
            {  
                myControl = ctrl;  
            }  
        }  
    }  
    ```  
  
2.  重写可访问对象的 <xref:System.Windows.Forms.AccessibleObject.Role%2A>、<xref:System.Windows.Forms.AccessibleObject.State%2A>、<xref:System.Windows.Forms.AccessibleObject.GetChild%2A> 和 <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> 属性和方法。  
  
3.  实现子控件的另一个辅助对象并重写子控件的 <xref:System.Windows.Forms.Control.AccessibilityObject%2A> 属性返回该辅助对象。  
  
4.  重写 <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>、<xref:System.Windows.Forms.AccessibleObject.Name%2A>、<xref:System.Windows.Forms.AccessibleObject.Parent%2A>、<xref:System.Windows.Forms.AccessibleObject.Role%2A>、<xref:System.Windows.Forms.AccessibleObject.State%2A>、<xref:System.Windows.Forms.AccessibleObject.Navigate%2A>和 <xref:System.Windows.Forms.AccessibleObject.Select%2A> 属性和方法子控件的可访问性对象的。  
  
> [!NOTE]
>  本主题从 <xref:System.Windows.Forms.AccessibleObject> 的可访问性示例过程开始，然后开始生成其余程序。  如果要创建辅助示例的一个有效的版本，请创建一个控制台应用程序，用示例代码替换 Program.cs 的代码。  您需要添加对辅助功能、System.Drawing 和 System.Windows.Forms 的引用。  您应更改辅助功能的 **嵌入互操作类型** 来消除错误生成警告。  可以从控件个应用程序到 windows 应用程序，更改项目的输出类型，以便当您运行应用程序时，控件台不显示窗口。  
  
##  <a name="customproprties"></a> 通过实现属性提供程序来支持自定义属性验证  
 一旦实现了一个基本用于记录支持，并且播放和属性验证，可以通过实现 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> 插件的测试,实现您的可用编码的 UI 控件的自定义属性。  例如，下面的过程创建允许编码的 UI 测试访问图表控件的 CurveLegend 子控件的状态属性的一个属性提供程序。  
  
 ![CUIT&#95;CustomProps](../test/media/cuit_customprops.png "CUIT\_CustomProps")  
  
### 支持自定义属性验证  
 ![CUIT&#95;Props](../test/media/cuit_props.png "CUIT\_Props")  
  
1.  通过在声明字符串的丰富的属性值，重写曲线声明可访问对象的 <xref:System.Windows.Forms.AccessibleObject.Description%2A> 属性，分离主要声明 \(以及，如果您实现多个属性\) 分号 \(;\)。  
  
    ```c#  
    public class CurveLegendAccessibleObject : AccessibleObject  
    {  
        // add the state property value to the description  
        public override string Description  
        {  
            get  
            {  
                // Add “;” and the state value to the end  
                // of the curve legend’s description  
                return "CurveLegend; " + State.ToString();  
            }  
        }  
    }  
    ```  
  
2.  创建 UI 通过创建选件类库项目来测试您的控件的扩展程序包并添加对辅助功能、Microsoft.VisualStudio.TestTools.UITesting、Microsoft.VisualStudio.TestTools.UITest.Common 和 Microsoft.VisualStudio.TestTools.Extension 的引用。  更改辅助功能的 **嵌入互操作类型** 为错误。  
  
3.  添加从 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>派生的属性提供程序选件类。  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using Accessibility;  
    using Microsoft.VisualStudio.TestTools.UITesting;  
    using Microsoft.VisualStudio.TestTools.UITest.Extension;  
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;  
    using Microsoft.VisualStudio.TestTools.UITest.Common;  
  
    namespace ChartControlExtensionPackage  
    {  
        public class ChartControlPropertyProvider : UITestPropertyProvider  
        {  
        }  
    }  
    ```  
  
4.  通过将属性名和属性说明符实现属性提供程序在 <xref:System.Collections.Generic.Dictionary%602>。  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
5.  重写 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName> 指示您的程序集对于您的控件及其子控件提供控件的特定支持。  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
6.  重写 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>剩余的抽象方法。  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
7.  添加从 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>派生的扩展程序包选件类。  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
8.  定义程序集的 `UITestExtensionPackage` 属性。  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
9. 在扩展程序包选件类，重写返回属性提供程序选件类的 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName>，当属性提供程序请求。  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
10. 替代 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>剩余的抽象方法和属性。  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
11. 生成的二进制文件并将其复制到 **%ProgramFiles%\\Common\\Microsoft Shared\\VSTT\\10.0\\UITestExtensionPackages**。  
  
> [!NOTE]
>  此扩展程序包将应用于类型“text”的所有控件。  如果测试同一类型的多个控件，则需要在记录测试时，单独测试扩展程序包，并管理已部署的。  
  
##  <a name="codegeneration"></a> 通过实现类以访问自定义属性来支持代码生成  
 当编码的 UI 测试时生成器生成参加会议记录的代码，它使用 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> 选件类访问您的控件。  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
 如果实现一个属性提供程序提供对控件的自定义特性，您可以添加用于访问这些属性的专用选件类，以便简化生成的代码。  
  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
### 添加专用类以访问您的控件  
 ![CUIT&#95;CodeGen](../test/media/cuit_codegen.png "CUIT\_CodeGen")  
  
1.  实现从 <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> 派生的选件类并添加控件的类型到构造函数的搜索属性集合。  
  
<CodeContentPlaceHolder>12</CodeContentPlaceHolder>  
2.  实现控件自定义属性作为选件类的属性。  
  
<CodeContentPlaceHolder>13</CodeContentPlaceHolder>  
3.  重写您的属性提供程序的 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> 方法返回新的选件类的类型曲线声明子控件的。  
  
<CodeContentPlaceHolder>14</CodeContentPlaceHolder>  
4.  重写您的属性提供程序的 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> 方法返回新的选件类的 PropertyNames 方法的类型。  
  
<CodeContentPlaceHolder>15</CodeContentPlaceHolder>  
##  <a name="intentawareactions"></a> 通过实现操作筛选器来支持目的感知操作  
 当 Visual Studio 录制测试时，它会获取鼠标和键盘事件。  但是，在某些情况下，该事件的目的在一系列的鼠标和键盘事件后可能会丢失。  例如，如果控件支持自动完成，当测试在不同的环境中进行，同一组中的鼠标和键盘事件可能产生不同的值。  添加操作筛选器插件，可以用单个操作替换一系列键盘和鼠标事件。  这样，您就可以用单个操作替换鼠标和键盘事件来得出同样的值。  从一个环境到另一个的自动差异测试，实现保护代码的 UI。  
  
### 支持目的感知操作  
 ![CUIT&#95;Actions](../test/media/cuit_actions.png "CUIT\_Actions")  
  
1.  实现从派生 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>，重写属性 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A>、<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>、<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>、<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>、<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> 和 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A>的操作筛选器选件类。  
  
<CodeContentPlaceHolder>16</CodeContentPlaceHolder>  
2.  重写 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ProcessRule%2A>。  此处示例用一个双击事件替换一个单击事件。  
  
<CodeContentPlaceHolder>17</CodeContentPlaceHolder>  
3.  对您的扩展程序包 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> 方法添加操作筛选器。  
  
<CodeContentPlaceHolder>18</CodeContentPlaceHolder>  
4.  生成的二进制文件并将其复制到 %ProgramFiles%\\Common\\Microsoft Shared\\VSTT\\10.0\\UITestExtensionPackages。  
  
> [!NOTE]
>  操作筛选器不依赖于辅助功能实现或属性提供程序。  
  
## 调试您的属性提供程序或操作筛选器  
 您的属性提供程序和操作筛选器在隔开你的应用程序的情况下，加载并且由代码UI测试生成器运行，并最终实现。  
  
#### 调试属性提供程序或操作筛选器  
  
1.  生成您的扩展程序包复制的调试版本 .dll 和 .pdb files %ProgramFiles%\\common files\\microsoft shared\\VSTT\\10.0\\UITestExtensionPackages。  
  
2.  不在调试器中运行您的应用程序。  
  
3.  运行编码的 UI 测试生成器。  
  
     `codedUITestBuilder.exe  /standalone`  
  
4.  将调试器附加到编码的UI测试生成器进程。  
  
5.  在代码中设置断点。  
  
6.  在编码的 UI 测试生成器，创建断言执行您的属性提供程序和记录事件实现自己的操作筛选器。  
  
## 外部资源  
  
### 指南  
 [Testing for Continuous Delivery with Visual Studio 2012 – Chapter 2: Unit Testing: Testing the Inside](http://go.microsoft.com/fwlink/?LinkID=255188)（使用 Visual Studio 2012 对连续交付进行测试 — 第 2 章：单元测试：测试内部）  
  
## 请参阅  
 <xref:System.Windows.Forms.AccessibleObject>   
 [使用 UI 自动化来测试代码](../test/use-ui-automation-to-test-your-code.md)