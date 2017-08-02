---
title: "为控件启用编码的 UI 测试 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ef1188f-89dc-413d-801d-0efdaf9b0427
caps.latest.revision: 22
ms.author: douge
manager: douge
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 59c18804574725c584b1b06df8f1ba8a5cf37824
ms.contentlocale: zh-cn
ms.lasthandoff: 05/13/2017

---
# <a name="enable-coded-ui-testing-of-your-controls"></a>启用控件的编码的 UI 测试
如果实现对编码的 UI 测试框架的支持，则可以更轻松地测试你的控件。 您能够以增量方式增加支持级别。 您可以先从支持录制、播放和属性验证开始。 在此基础上，可以允许编码的 UI 测试生成器识别控件的自定义属性，并提供自定义类以便从生成的代码访问这些属性。 你还可以帮助编码的 UI 测试生成器，使之以一种与所录制操作的目的更为接近的方法来捕获操作。  
  
 **本主题内容：**  
  
1.  [通过实现可访问性来支持录制和播放以及属性验证](../test/enable-coded-ui-testing-of-your-controls.md#recordandplayback)  
  
2.  [通过实现属性提供程序来支持自定义属性验证](../test/enable-coded-ui-testing-of-your-controls.md#customproprties)  
  
3.  [通过实现用于访问自定义属性的类来支持代码生成](../test/enable-coded-ui-testing-of-your-controls.md#codegeneration)  
  
4.  [通过实现操作筛选器来支持意向感知操作](../test/enable-coded-ui-testing-of-your-controls.md#intentawareactions)  
  
 ![CUIT&#95;Full](~/docs/test/media/cuit_full.png "CUIT_Full")  
  
##  <a name="recordandplayback"></a>通过实现可访问性来支持录制和播放以及属性验证  
 编码的 UI 测试生成器可捕获与它在录制期间所遇到的控件有关的信息，然后生成代码以重播该会话。 如果控件不支持辅助功能，则编码的 UI 测试生成器将使用屏幕坐标来捕获操作（例如，鼠标单击）。 播放测试时，生成的代码将在同一屏幕坐标释放这些鼠标单击操作。 在播放测试时，如果控件出现在屏幕上的其他位置，则生成的代码将无法对控件执行该操作。 如果在不同的屏幕配置下、在不同的环境中，或者在 UI 布局发生更改之后播放测试，则这可能会导致失败。  
  
 ![CUIT&#95;RecordNoSupport](../test/media/cuit_recordnosupport.png "CUIT_RecordNoSupport")  
  
 不过，如果实现辅助功能，则它在录制测试并生成代码时，将使用这一辅助功能来捕获有关控件的信息。 然后，当您运行测试时，生成的代码将针对您的控件重播这些事件，即使它位于用户界面中的其他位置。 测试作者还可以使用控件的基本属性创建断言。  
  
 ![CUIT&#95;Record](../test/media/cuit_record.png "CUIT_Record")  
  
### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>支持录制和播放、属性验证以及 Windows 窗体控件的导航  
 根据以下过程中的概述和 <xref:System.Windows.Forms.AccessibleObject> 中的详细介绍，为您的控件实现辅助功能。  
  
 ![CUIT&#95;Accessible](~/docs/test/media/cuit_accessible.png "CUIT_Accessible")  
  
1.  实现一个从 <xref:System.Windows.Forms.Control.ControlAccessibleObject> 派生的类，并重写 <xref:System.Windows.Forms.Control.AccessibilityObject%2A> 属性以便返回类的对象。  
  
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
  
2.  替代可访问对象的 <xref:System.Windows.Forms.AccessibleObject.Role%2A>、<xref:System.Windows.Forms.AccessibleObject.State%2A>、<xref:System.Windows.Forms.AccessibleObject.GetChild%2A> 和 <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> 属性及方法。  
  
3.  实现子控件的另一个辅助功能对象并替代子控件的 <xref:System.Windows.Forms.Control.AccessibilityObject%2A> 属性，以便返回该辅助功能对象。  
  
4.  替代子控件辅助功能对象的 <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>、<xref:System.Windows.Forms.AccessibleObject.Name%2A>、<xref:System.Windows.Forms.AccessibleObject.Parent%2A>、<xref:System.Windows.Forms.AccessibleObject.Role%2A>、<xref:System.Windows.Forms.AccessibleObject.State%2A>、<xref:System.Windows.Forms.AccessibleObject.Navigate%2A> 和 <xref:System.Windows.Forms.AccessibleObject.Select%2A> 属性及方法。  
  
> [!NOTE]
>  本主题在此过程中从 <xref:System.Windows.Forms.AccessibleObject> 辅助功能示例开始，然后在此基础上完成剩余过程。 如果要创建辅助功能示例的可行版本，请创建一个控制台应用程序，然后用示例代码替换 Program.cs 中的代码。 需要添加对辅助功能、System.Drawing 和 System.Windows.Forms 的引用。 若要消除生成警告，应将可访问性的“嵌入互操作类型”更改为“False”。 可以将项目的输出类型从“控制台应用程序”更改为“Windows 应用程序”，以便在运行应用时不显示控制台窗口。  
  
##  <a name="customproprties"></a>通过实现属性提供程序来支持自定义属性验证  
 在实现对录制、播放和属性验证的基本支持后，可以通过实现 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> 插件，使控件的自定义属性可供编码的 UI 测试使用。 例如，下面的过程将创建一个属性提供程序，该程序允许编码的 UI 测试访问图表控件的 CurveLegend 子控件的 State 属性。  
  
 ![CUIT&#95;CustomProps](~/docs/test/media/cuit_customprops.png "CUIT_CustomProps")  
  
### <a name="to-support-custom-property-validation"></a>支持自定义属性验证  
 ![CUIT&#95;Props](~/docs/test/media/cuit_props.png "CUIT_Props")  
  
1.  替代曲线图例可访问对象的 <xref:System.Windows.Forms.AccessibleObject.Description%2A> 属性，以便传递说明字符串中丰富的属性值，并通过分号 (;) 与主说明分隔开来（如果要实现多个属性，则每个属性之间也相互分隔）。  
  
    ```c#  
    public class CurveLegendAccessibleObject : AccessibleObject  
    {  
        // add the state property value to the description  
        public override string Description  
        {  
            get  
            {  
                // Add ";" and the state value to the end  
                // of the curve legend's description  
                return "CurveLegend; " + State.ToString();  
            }  
        }  
    }  
    ```  
  
2.  通过创建一个类库项目并添加对辅助功能、Microsoft.VisualStudio.TestTools.UITesting、Microsoft.VisualStudio.TestTools.UITest.Common 和 Microsoft.VisualStudio.TestTools.Extension 的引用，为你的控件创建一个 UI 测试扩展包。 将可访问性的“嵌入互操作类型”更改为“False”。  
  
3.  添加一个派生自 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> 的属性提供程序类。  
  
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
  
4.  通过将属性名称和属性描述符放在 <xref:System.Collections.Generic.Dictionary%602> 中，实施此属性提供程序。  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
5.  重写 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName>，指明您的程序集为控件及其子控件提供特定于控件的支持。  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
6.  重写 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName> 的剩余抽象方法。  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
7.  添加一个派生自 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> 的扩展包类。  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
8.  定义程序集的 `UITestExtensionPackage` 特性。  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
9. 在扩展包类中，重写 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName>，以便在请求属性提供程序时返回属性提供程序类。  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
10. 重写 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> 的剩余抽象方法和属性。  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
11. 生成二进制文件，然后将其复制到 **%ProgramFiles%\Common\Microsoft Shared\VSTT\10.0\UITestExtensionPackages**。  
  
> [!NOTE]
>  此扩展包将应用于类型为“Text”的所有控件。 如果测试同一类型的多个控件，则需要分别进行测试，并管理在录制测试时要部署哪些扩展包。  
  
##  <a name="codegeneration"></a>通过实现用于访问自定义属性的类来支持代码生成  
 当编码的 UI 测试时生成器生成会话录制的代码时，它将使用 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> 类来访问您的控件。  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
 如果已实现一个属性提供程序来访问控件的自定义属性，则可以添加一个用于访问这些属性的专用类，以便简化所生成的代码。  
  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
### <a name="to-add-a-specialized-class-to-access-your-control"></a>添加专用类以访问您的控件  
 ![CUIT&#95;CodeGen](~/docs/test/media/cuit_codegen.png "CUIT_CodeGen")  
  
1.  实现派生自 <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> 类，并将控件的类型添加到构造函数中的搜索属性集合。  
  
<CodeContentPlaceHolder>12</CodeContentPlaceHolder>  
2.  实现控件的自定义属性，作为类的属性。  
  
<CodeContentPlaceHolder>13</CodeContentPlaceHolder>  
3.  替代属性提供程序的 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> 方法，以便返回曲线图例子控件的新类的类型。  
  
<CodeContentPlaceHolder>14</CodeContentPlaceHolder>  
4.  替代属性提供程序的 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> 方法，以便返回新类的 PropertyNames 方法的类型。  
  
<CodeContentPlaceHolder>15</CodeContentPlaceHolder>  
##  <a name="intentawareactions"></a>通过实现操作筛选器来支持意向感知操作  
 当 Visual Studio 录制测试时，它会捕获鼠标和键盘事件。 但是，在某些情况下，在一系列鼠标和键盘事件中可能会丢失操作的目的。 例如，如果控件支持自动完成，则在其他环境中播放测试时，同一组鼠标和键盘事件可能会产生不同的值。 您可以添加一个操作筛选器插件，将一系列键盘和鼠标事件替换为单一操作。 这样一来，您就可以将结果为选择某一值的一系列鼠标和键盘事件替换为设置值的单一操作。 当从一个环境转到另一个环境时，这样可以保护编码的 UI 测试，使之不受自动完成差异的影响。  
  
### <a name="to-support-intent-aware-actions"></a>支持目的感知操作  
 ![CUIT&#95;Actions](~/docs/test/media/cuit_actions.png "CUIT_Actions")  
  
1.  实现派生自 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> 的操作筛选器类，并替代属性 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A>、<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>、<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>、<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>、<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> 和 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A>。  
  
<CodeContentPlaceHolder>16</CodeContentPlaceHolder>  
2.  重写 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ProcessRule%2A>。 这里的示例将一个双击操作替换成了单击操作。  
  
<CodeContentPlaceHolder>17</CodeContentPlaceHolder>  
3.  将操作筛选器添加到扩展包的 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> 方法。  
  
<CodeContentPlaceHolder>18</CodeContentPlaceHolder>  
4.  生成二进制文件，然后将其复制到 %ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages。  
  
> [!NOTE]
>  操作筛选器不依赖于辅助功能实现或属性提供程序。  
  
## <a name="debug-your-property-provider-or-action-filter"></a>调试您的属性提供程序或操作筛选器  
 您的属性提供程序和操作筛选器在一个扩展包中实现，此扩展包在一个与应用程序分离的进程中，由编码的 UI 测试生成器来加载和运行。  
  
#### <a name="to-debug-your-property-provider-or-action-filter"></a>调试属性提供程序或操作筛选器  
  
1.  生成扩展包的调试版本，然后将 .dll 和 .pdb 文件复制到 %ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages。  
  
2.  运行您的应用程序（不在调试器中）。  
  
3.  运行编码的 UI 测试生成器。  
  
     `codedUITestBuilder.exe  /standalone`  
  
4.  将调试器附加到 codedUITestBuilder 进程。  
  
5.  在代码中设置断点。  
  
6.  在编码的 UI 测试生成器中，创建断言以执行您的属性提供程序，并录制操作以运用您的操作筛选器。  
  
## <a name="external-resources"></a>外部资源  
  
### <a name="guidance"></a>指导  
 [使用 Visual Studio 2012 测试连续交付 - 第 2 章：单元测试：测试内部](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Windows.Forms.AccessibleObject>   
 [使用 UI 自动化来测试代码](../test/use-ui-automation-to-test-your-code.md)

