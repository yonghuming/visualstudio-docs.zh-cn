---
title: "如何：设置 VSPackage 的外观方案（C# 和 Visual Basic） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "“关于”对话框"
  - "VSPackage, 初始屏幕"
  - "VSPackage, 外观方案"
ms.assetid: 705a41c3-63d6-4c1e-9f82-771be9191579
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# 如何：设置 VSPackage 的外观方案（C# 和 Visual Basic）
若要显示 **有关** 对话框和初始屏幕， Vspackage 必须实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> 接口。  这提供下列信息。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   名称  
  
-   ID，例如序列化的或版本号  
  
-   信息  
  
-   徽标图标  
  
 下面的代码是从 [VSSDK 示例](../misc/vssdk-samples.md)。  
  
### 实现接口 IVsInstalledProduct  
  
1.  添加 <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> 属性设置为实现 VSPackage 的类。  此类必须从 <xref:Microsoft.VisualStudio.Shell.Package> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>派生。  
  
     [!code-cs[VSSDKPackageSplashHelpAboutLoadKey#1](../misc/codesnippet/CSharp/how-to-brand-a-vspackage-csharp-and-visual-basic_1.cs)]
     [!code-vb[VSSDKPackageSplashHelpAboutLoadKey#1](../misc/codesnippet/VisualBasic/how-to-brand-a-vspackage-csharp-and-visual-basic_1.vb)]  
  
     第一个参数， <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute.UseInterface%2A>， <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> 特性通知 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> 获取产品信息，而不是 InstalledProducts 注册表项。  其余的参数选择字符串资源显示产品名称、详细信息和 ID，分别。  但是，在中，因为第一个参数是 `true`，其余的参数是 `null`。  
  
2.  右击 <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>，指向 **实现接口**，然后单击 **实现接口**。  
  
3.  使用下面的代码中，实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> 。  
  
     [!code-cs[VSSDKPackageSplashHelpAboutLoadKey#2](../misc/codesnippet/CSharp/how-to-brand-a-vspackage-csharp-and-visual-basic_2.cs)]
     [!code-vb[VSSDKPackageSplashHelpAboutLoadKey#2](../misc/codesnippet/VisualBasic/how-to-brand-a-vspackage-csharp-and-visual-basic_2.vb)]  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 调用这些方法来获得署名的 VSPackage 信息。  GetResourceString 方法可用于本地化此信息。  
  
    > [!NOTE]
    >  代码注释简洁起见被删除。  可以找到它们在 [VSSDK 示例](../misc/vssdk-samples.md)。  
  
### 维护产品信息字符串  
  
1.  双击 .resx 资源文件与 VSPackage。  
  
     资源编辑器中打开。  
  
2.  查找或添加产品名称、信息和 ID.  
  
     下面的资源字符串来自 [VSSDK 示例](../misc/vssdk-samples.md)。  
  
     @101  
     包初始屏幕和帮助涉及正式名称 \(c\# 中\)。  
  
     @102  
     此包演示如何显示文本和图像在初始屏幕和帮助。  
  
     @104  
     8.0  
  
3.  选择和编辑此信息，您希望。  
  
### 维护产品图标和位图  
  
1.  添加位图和图标添加到项目用作项目资源。  
  
     有关更多信息，请参见 [NOT IN BUILD: Adding and Editing Resources \(Visual C\#\)](http://msdn.microsoft.com/zh-cn/95f15d03-bed0-410c-8d1f-dece5199ba1e)。  
  
2.  关闭资源编辑器并重新打开在 XML 或文本编辑器的 .resx 文件。  
  
    > [!NOTE]
    >  除了字符串之外，资源编辑器不支持分配资源 ID 到项目中。  
  
3.  查找或添加图标和位图资源。 .resx 文件。  下面的资源是从 [VSSDK 示例](../misc/vssdk-samples.md)。  
  
    ```  
    <data name="300" type="System.Resources.ResXFileRef, System.Windows.Forms">  
        <value>GenericPackage.bmp;System.Drawing.Bitmap, System.Drawing,  
            Version=2.0.0.0, Culture=neutral,         PublicKeyToken=b03f5f7f11d50a3a</value>  
    </data>  
    <data name="400" type="System.Resources.ResXFileRef, System.Windows.Forms">  
        <value>GenericPackage.ico;System.Drawing.Icon, System.Drawing,  
            Version=2.0.0.0, Culture=neutral,         PublicKeyToken=b03f5f7f11d50a3a</value>  
    </data>  
    ```  
  
### 测试对话框和初始屏幕  
  
-   若要测试 VSPackage，请参见 [如何：测试帮助主题和初始屏幕](../misc/how-to-test-the-help-about-and-splash-screens.md)。  
  
## 请参阅  
 [Vspackage 外观方案](/visual-cpp/misc/vspackage-branding)