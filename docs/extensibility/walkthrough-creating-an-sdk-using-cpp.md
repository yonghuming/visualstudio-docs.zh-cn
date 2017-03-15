---
title: "演练︰ 创建一个 SDK，使用 c + + |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 32
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
ms.sourcegitcommit: d4458cb2cf0f3f198b2931beec15f8eead446ba6
ms.openlocfilehash: 3baf914755f0cdd4e0aa0a6c1405126faeec0364
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-an-sdk-using-c"></a>演练︰ 创建使用 c + + 的 SDK
本演练演示如何创建一个本机 c + + 的数学库 SDK，包的 SDK 与 Visual Studio 扩展 (VSIX)，并使用它来创建应用程序。 本演练分为以下步骤︰  
  
-   [若要创建的本机和 Windows 运行时库](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [若要创建 NativeMathVSIX 扩展项目](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [若要创建的示例应用程序使用类库](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>先决条件  
 要按照本演练的步骤操作，必须安装 Visual Studio SDK。 有关详细信息，请参阅[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
##  <a name="a-namecreateclasslibrarya-to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>若要创建的本机和 Windows 运行时库  
  
1.  在菜单栏上，依次选择“文件” 、“新建” 、“项目” 。  
  
2.  在模板列表中，展开**Visual c + +**， **Windows 应用商店**，然后选择**DLL （Windows 应用商店应用）**模板。 在**名称**框中，指定`NativeMath`，然后选择**确定**按钮。  
  
3.  更新 NativeMath.h 以匹配下面的代码。  
  
     [!code-cpp[CreatingAnSDKUsingCpp #&1;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  更新 NativeMath.cpp 以匹配此代码︰  
  
     [!code-cpp[CreatingAnSDKUsingCpp #&2;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  在**解决方案资源管理器**，打开快捷菜单**解决方案 NativeMath**，然后选择**添加**，**新项目**。  
  
6.  在模板列表中，展开**Visual c + +**，然后选择**Windows 运行时组件**模板。 在**名称**框中，指定`NativeMathWRT`，然后选择**确定**按钮。  
  
7.  若要与此代码相匹配的更新 class1.h 中︰  
  
     [!code-cpp[CreatingAnSDKUsingCpp #&3;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  更新 class1.cpp 中，以匹配此代码︰  
  
     [!code-cpp[CreatingAnSDKUsingCpp #&4;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. 在菜单栏上，依次选择 **“生成”**、 **“生成解决方案”**。  
  
##  <a name="a-namecreatevsixa-to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a>若要创建 NativeMathVSIX 扩展项目  
  
1.  在**解决方案资源管理器**，打开快捷菜单**解决方案 NativeMath**，然后选择**添加**，**新项目**。  
  
2.  在模板列表中，展开**Visual C#**，**扩展性**，然后选择**VSIX 包**。 在**名称**框中，指定**NativeMathVSIX**，然后选择**确定**按钮。  
  
3.  VSIX 清单设计器中出现时，关闭它。  
  
4.  在**解决方案资源管理器**，打开快捷菜单**source.extension.vsixmanifest**，然后选择**查看代码**。  
  
5.  使用下面的 XML 替换现有的 XML。  
  
    [!code-xml[CreatingAnSDKUsingCpp #&6;](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

6.  在**解决方案资源管理器**，打开快捷菜单**NativeMathVSIX**项目，，然后选择**添加**，**新项**。  
  
7.  在列表中**Visual C# 项**，展开**数据**，然后选择**XML 文件**。 在**名称**框中，指定`SDKManifest.xml`，然后选择**确定**按钮。  
  
8.  使用此 XML 替换该文件的内容︰  
  
     [!code-xml[CreatingAnSDKUsingCpp #&5;](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
9. 在**解决方案资源管理器**，请在**NativeMathVSIX**项目中，创建此文件夹结构︰  
  
    ```  
  
    \DesignTime  
          \CommonConfiguration  
                \Neutral  
                      \Include  
          \Debug  
                \x86  
    \Redist  
          \Debug  
                \x86  
    \References  
          \CommonConfiguration  
                \Neutral  
    ```  
  
10. 在**解决方案资源管理器**，打开快捷菜单**解决方案 NativeMath**，然后选择**在文件资源管理器中打开文件夹**。  
  
11. 在**文件资源管理器**，复制 \NativeMath\NativeMath.h，然后在**解决方案资源管理器**，请在**NativeMathVSIX**项目中，将其粘贴在 \DesignTime\CommonConfiguration\Neutral\Include\ 文件夹中。  
  
     复制 \Debug\NativeMath\NativeMath.lib，并粘贴 \DesignTime\Debug\x86\ 文件夹中。  
  
     复制 \Debug\NativeMath\NativeMath.dll 并将其粘贴在 \Redist\Debug\x86\ 文件夹中。  
  
     复制 DebugNativeMathWRTNativeMathWRT.dll 并将其粘贴在 RedistDebugx86 文件夹中。  
  
     复制 DebugNativeMathWRTNativeMathWRT.winmd 并将其粘贴在 ReferencesCommonConfigurationNeutral 文件夹中。  
  
     复制 DebugNativeMathWRTNativeMathWRT.pri 并将其粘贴在 ReferencesCommonConfigurationNeutral 文件夹中。  
  
12. \DesignTime\Debug\x86\ 文件夹中创建名为 NativeMathSDK.props，一个文本文件，然后在其中粘贴以下内容︰  
  
    [!code-xml[CreatingAnSDKUsingCpp #&7;](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. 在菜单栏上依次选择**视图**，**其他窗口**，**属性窗口**(键盘︰ 按 F4 键)。  
  
14. 在**解决方案资源管理器**，选择**NativeMathWRT.winmd**文件。 在**属性**窗口中，更改**生成操作**属性设置为**内容**，然后将更改**包含在 VSIX**属性设置为**True**。  
  
     重复此过程为**SimpleMath.pri**文件。  
  
     重复此过程为**NativeMath.Lib**文件。  
  
     重复此过程为**NativeMathSDK.props**文件。  
  
15. 在**解决方案资源管理器**，选择**NativeMath.h**文件。 在**属性**窗口中，更改**包含在 VSIX**属性设置为**True**。  
  
     重复此过程为**NativeMath.dll**文件。  
  
     重复此过程为**NativeMathWRT.dll**文件。  
  
     重复此过程为**SDKManifest.xml**文件。  
  
16. 在菜单栏上，依次选择 **“生成”**、 **“生成解决方案”**。  
  
17. 在**解决方案资源管理器**，打开快捷菜单**NativeMathVSIX**项目，，然后选择**在文件资源管理器中打开文件夹**。  
  
18. 在**文件资源管理器**，导航到 \bin\Debug\ 文件夹中，然后重新运行 NativeMathVSIX.vsix 以开始安装。  
  
19. 选择**安装**按钮，等待安装完成，然后再重新启动 Visual Studio。  
  
##  <a name="a-namecreatesamplea-to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>若要创建的示例应用程序使用类库  
  
1.  在菜单栏上，依次选择“文件” 、“新建” 、“项目” 。  
  
2.  在模板列表中，展开**Visual c + +**， **Windows 应用商店**，然后选择**空白应用程序**。 在**名称**框中，指定**NativeMathSDKSample**，然后选择**确定**按钮。  
  
3.  在**解决方案资源管理器**，打开快捷菜单**NativeMathSDKSample**项目，，然后选择**添加**，**引用**。  
  
4.  在**通用属性**，**框架和引用**属性页上，在引用类型的列表中展开**Windows**，然后选择**扩展**。 在详细信息窗格中，选择**本机数学 SDK**扩展名，然后选择**添加新引用**按钮。  
  
5.  在**添加引用**对话框中，选择**本机数学 SDK**复选框，然后再选择**确定**按钮。  
  
6.  NativeMathSDKSample 显示项目属性。  
  
     添加引用时，已应用在 NativeMathSDK.props 中定义的属性。 您可以通过检查对此进行验证**VC + + 目录**项目的属性**配置属性**。  
  
7.  在**解决方案资源管理器**，打开 MainPage.xaml，，然后使用下面的 XAML 来替换其中的内容︰  
  
     [!code-xml[CreatingAnSDKUsingCppDemoApp #&1;](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
8.  更新 Mainpage.xaml.h 中以匹配此代码︰  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp #&2;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
9. 更新 mainpage.xaml.cpp 中，以匹配此代码︰  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp #&3;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
10. 选择 F5 键以运行该应用程序。  
  
11. 在应用中，输入任何两个数字，选择的操作，然后选择** = **按钮。  
  
     将显示正确的结果。  
  
 本演练演示了如何创建和使用扩展 SDK 来调入[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)]库和非[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)]库。  
  
## <a name="next-steps"></a>后续步骤  
  
## <a name="see-also"></a>另请参阅  
 [演练︰ 创建使用 C# 或 Visual Basic 的 SDK](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [创建一个软件开发工具包](../extensibility/creating-a-software-development-kit.md)
