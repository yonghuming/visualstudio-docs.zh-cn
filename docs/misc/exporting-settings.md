---
title: "导出设置 | Microsoft Docs"
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
  - "IDE, 使用托管包框架导出设置"
  - "托管包框架, 导出环境设置"
  - "用户设置 [Visual Studio SDK], 使用托管包框架导出"
  - "IDE 设置, 使用托管包框架导出"
ms.assetid: cb3ddb38-4e75-4f05-a83a-8396345bc36c
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# 导出设置
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 集成 \(IDE\)开发环境 \(ide\) 使用实现 <xref:Microsoft.VisualStudio.Shell.IProfileManager> 接口和类注册为支持给定查询 VSPackage 实现保存 VSPackage 状态的类。  
  
 由于 IDE 实例化实现 <xref:Microsoft.VisualStudio.Shell.IProfileManager> 接口支持设置的类，在独立类应实现 <xref:Microsoft.VisualStudio.Shell.IProfileManager> 。  
  
> [!NOTE]
>  不要实现该类的 <xref:Microsoft.VisualStudio.Shell.IProfileManager> 实现 <xref:Microsoft.VisualStudio.Shell.Package>。  
  
### 实现一组导出  
  
1.  声明实现 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 设置的类。  
  
     类声明为实现 <xref:Microsoft.VisualStudio.Shell.IProfileManager> 接口并为其提供 GUID。  
  
    > [!NOTE]
    >  实现 <xref:Microsoft.VisualStudio.Shell.IProfileManager> 的类还必须实现 <xref:System.ComponentModel.IComponent>。  这可能由派生类来完成从 <xref:System.ComponentModel.Component>。  
  
     例如：  
  
    ```  
    [Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
    internal class MyPackageProfileManager : Component, IProfileManager   
    ```  
  
2.  确保实现设置的类获取正确的状态信息。  此过程是特定于每个 VSPackage，也可以包含获取来自自动化的状态，查询注册表项或查询 VSPackage。  
  
     通常，在下面的示例中，请使用 <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> 方法的实现验证和临时 VSPackage 状态信息。  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> 方法由 IDE 还调用，或者初始化它所支持的 VSPackage 时。  
  
     在这种情况下， <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> 方法的实现执行这些操作:  
  
    -   获取对状态信息的访问在注册表中配置信息存储区的 VSPackage 当前配置。  
  
        ```vb#  
        Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
        Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
        Dim rootKey As RegistryKey = package.UserRegistryRoot  
        ```  
  
        ```c#  
        MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
        Package package = GetService(typeof(Package)) as Package;  
        RegistryKey rootKey = package.UserRegistryRoot;  
        ```  
  
    -   使用注册表设置，基于值在 VSPackage 返回，它将 `MakeCurrentSettingTheDefault` 方法更新使用当前 VSPackage 状态的注册表设置或为状态。  
  
        ```vb#  
        If mySvc.MyPackage.MakeCurrentSettingTheDefault() Then   
            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
        Else   
            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).LoadState(pbrsKey)   
        End If  
        ```  
  
        ```c#  
        if (mySvc.MyPackage.MakeCurrentSettingTheDefault()){  
          ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
        }else{  
          ((IComPropertyBrowser)mySvc.MyPackage.packageState).LoadState(pbrsKey);  
        }  
        ```  
  
         为简单起见，在此示例中，除非 `MakeCurrentSettingsTheDefault` 方法返回 `true`，当前状态始终被重置为存储在注册表中的默认值。  
  
3.  确保还实现设置的类保持该状态到磁盘。  
  
     必须由 <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> 方法的类实现总是执行状态信息实际写入设置磁盘文件的。  设置编写器操作的特定依赖于实现。  
  
     但是，类必须获取对状态信息的访问，而且必须使用所提供的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> 接口访问数据保存到设置的文件。  
  
     通常，在下面的示例中， <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> 方法的实现不验证状态信息。  该验证在 <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> 方法执行。  相反，实现只获取对状态信息并将访问它，在这种情况下，为字符串数据。  
  
    ```vb#  
    Dim mySvc As MyPackageService = TryCast(GetService(GetType(MyPackage)), MyPackageService)   
    If mySvc IsNot Nothing Then   
        ' Information is stored in a StateObject   
        Dim myState As StateObject = mySvc.MyPackage.packageState   
        writer.WriteSettingString("PbrsAlpha", (If(myState.SortState = SortState.Alphabetical, "1", "0")))   
        writer.WriteSettingString("PbrsShowDesc", (If(myState.HelpVisible, "1", "0")))   
    End If  
  
    ```  
  
    ```c#  
    MyPackageService mySvc = GetService(typeof(MyPackage)) as MyPackageService;  
    if (mySvc != null) {  
      // Information is stored in a StateObject  
      StateObject myState = mySvc.MyPackage.packageState;  
     writer.WriteSettingString(   
                                "PbrsAlpha",   
                                (myState.SortState == SortState.Alphabetical ? "1" : "0"));  
      writer.WriteSettingString(   
                                "PbrsShowDesc",   
                                (myState.HelpVisible ? "1" : "0"));  
    }  
    ```  
  
     实现详细信息如下所示:  
  
    -   除了数据外显式编写和透明到 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> 方法实现中，设置 API 还保存 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 版本信息。  因此，保存的设置可以向设置导入时生成它们 IDE 的版本进行比较。  
  
    -   `pszSettingName` 参数的值提供给 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> 接口的方法必须唯一标识在设置类别保存的每个数据元素。  
  
        > [!NOTE]
        >  名称必须是唯一的仅在实现类的范围内。  IDE 使用实现一组和 `pszSettingName` 的值标识每个已保存的设置类的 GUID。  如果多个具有相同 `pszSettingName` 值的一个 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> 方法调用，则原始值在设置文件复盖。  
  
    -   设置文件支持随机数据访问，因此，读取和写入操作顺序并不重要。  在下面的示例中，编写器操作的顺序。 <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> 方法的实现了读取操作的相反值在 <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> 方法的。  
  
    -   如果实现可以将数据添加到四个支持的格式之一，则不会对数以及类型的限制数据进行编写。  
  
        > [!NOTE]
        >  操作的工作划分在 <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> 和 <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> 方法之间的依赖于实现是某些任意的。  例如，实现会复盖使用 <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> 方法的一个空的实现以及由包含在 <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> 方法执行的任何注册表和状态查询。  
  
4.  实现类的设置为提供支持。 VSPackage 中注册。  
  
     将构造通过使用某个类 <xref:System.Type> 到 VSPackage <xref:Microsoft.VisualStudio.Shell.Package> 实现的实现 <xref:Microsoft.VisualStudio.Shell.IProfileManager><xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 的实例。  
  
    ```vb#  
    <ProvideProfile(GetType(MyPackageProfileManager), "CoreUI", "MyPackage", 1004, 1004, False)> _   
    <Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")> _   
    Class MyPackage   
        Inherits Package   
    End Class  
    ```  
  
    ```c#  
    [ProvideProfile(typeof(MyPackageProfileManager), "CoreUI", "MyPackage", 1004, 1004, false)]  
    [Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")]  
    class MyPackage: Package   
    ```  
  
     在本例中，特性通知 IDE `MyPackageProfileManager` 类提供一次一组实现。 `MyPackage` 类。  自定义在注册表下落点是在 \\Software\\Microsoft\\VisualStudio HKLM \\*版本*\\UserSettings\\ CoreUI\_MyPackage 下，其中 *版本* 是 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的，例如，版本 10.0。  
  
     有关更多信息，请参见[用户设置的的支持](../extensibility/internals/support-for-user-settings.md)和 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>。  
  
## 示例  
 下面的示例在类中实现 <xref:Microsoft.VisualStudio.Shell.IProfileManager> 。  
  
```vb#  
Imports System   
Imports System.Runtime.InteropServices   
Imports Microsoft.VisualStudio.Shell   
Imports Microsoft.VisualStudio.Shell.Interop   
Imports Microsoft.Win32   
Imports myPackageNameSpace   
Namespace myProfileManagerNameSpace  
  
    <Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")> _   
    Friend Class MyPackageProfileManager   
        Inherits System.ComponentModel.Component   
        Implements IProfileManager   
        Friend Const m_supportVer As Integer = 8   
        Public Sub SaveSettingsToXml(ByVal writer As IVsSettingsWriter)   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(MyPackage)), MyPackageService)   
            If mySvc IsNot Nothing Then   
                ' Information is stored in a StateObject.   
                Dim myState As StateObject = mySvc.MyPackage.packageState   
                writer.WriteSettingString("PbrsAlpha", (If(myState.SortState = SortState.Alphabetical, "1", "0")))   
                writer.WriteSettingString("PbrsShowDesc", (If(myState.HelpVisible, "1", "0")))   
            End If   
        End Sub   
  
        Public Sub LoadSettingsFromXml(ByVal reader As IVsSettingsReader)   
  
            Dim pnMajor As Integer, pnMinor As Integer, pnBuild As Integer   
            ' First, check if data is obtained from the correct major version   
            reader.ReadVersion(pnMajor, pnMinor, pnBuild)   
            If pnMajor <> m_supportVer Then   
                reader.ReportError("Unsupported Version")   
            Else   
                Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
                If mySvc IsNot Nothing Then   
                    Dim value As String   
                    Dim myState As StateObject = mySvc.MyPackage.packageState   
                    reader.ReadSettingString("PbrsShowDesc", value)   
                    ' Not all values must be present.   
                    If value Is Nothing OrElse value = "" Then   
                        reader.ReportError("Unable to Help Visibility Setting")   
                    Else   
                        myState.HelpVisible = Not value.Equals("0")   
                    End If   
                    reader.ReadSettingString("PbrsAlpha", value)   
                    ' Not all values must be present.   
                    If value Is Nothing OrElse value = "" Then   
                        reader.ReportError("Unable to Retrieve Sort Value")   
                    Else   
                        If Not value.Equals("0") Then   
                            myState.SortState = SortState.Alphabetical   
                        Else   
                            myState.SortState = SortState.Categorized   
                        End If   
                    End If   
                End If   
            End If   
        End Sub   
  
        Public Sub SaveSettingsToStorage()   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
            Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
            Dim rootKey As RegistryKey = package.UserRegistryRoot   
  
            If mySvc.MyPackage.packageState IsNot Nothing Then   
                Using rootKey   
                    Using pbrsKey As RegistryKey = rootKey.CreateSubKey(Me.[GetType]().Name)   
                        Using pbrsKey   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
                        End Using   
                    End Using   
                End Using   
            End If   
        End Sub   
  
        Public Sub LoadSettingsFromStorage()   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
            Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
            Dim rootKey As RegistryKey = package.UserRegistryRoot   
            Using rootKey   
                Dim pbrsKey As RegistryKey = rootKey.OpenSubKey(Me.[GetType]().Name)   
                If pbrsKey IsNot Nothing Then   
                    Using pbrsKey   
                        If mySvc.MyPackage.MakeCurrentSettingTheDefault() Then   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
                        Else   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).LoadState(pbrsKey)   
                        End If   
                    End Using   
                End If   
            End Using   
        End Sub   
    End Class   
End Namespace   
  
Convert C# to VB.NET  
  
```  
  
```c#  
namespace myProfileManagerNameSpace  {  
  
  using System;  
  using System.Runtime.InteropServices;  
  using Microsoft.VisualStudio.Shell;  
  using Microsoft.VisualStudio.Shell.Interop;  
  using Microsoft.Win32;  
  using myPackageNameSpace;  
  
  [Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
  internal class MyPackageProfileManager : System.ComponentModel.Component , IProfileManager {  
    internal const int m_supportVer = 8;  
    public void SaveSettingsToXml(IVsSettingsWriter writer) {  
      MyPackageService mySvc = GetService(typeof(MyPackage)) as MyPackageService;  
      if (mySvc != null) {  
        // Information is stored in a StateObject.  
        StateObject myState = mySvc.MyPackage.packageState;  
        writer.WriteSettingString(   
                                  "PbrsAlpha",   
                                  (myState.SortState == SortState.Alphabetical ? "1" : "0"));  
        writer.WriteSettingString(   
                                  "PbrsShowDesc",   
                                  (myState.HelpVisible ? "1" : "0"));  
      }  
    }  
  
    public void LoadSettingsFromXml(IVsSettingsReader reader)  
    {  
  
      int pnMajor, pnMinor, pnBuild;  
      // First, check if data is obtained from the correct major version   
      reader.ReadVersion(pnMajor, pnMinor, pnBuild);  
      if (pnMajor != m_supportVer){  
        reader.ReportError("Unsupported Version");  
      }else{  
        MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
        if (mySvc != null){  
          string value;  
          StateObject myState = mySvc.MyPackage.packageState;  
          reader.ReadSettingString("PbrsShowDesc", out value);  
          // Not all values must be present.  
          if (value == null || value == ""){  
              reader.ReportError("Unable to Help Visibility Setting");  
          }else{  
            myState.HelpVisible = !value.Equals("0");  
          }  
          reader.ReadSettingString("PbrsAlpha", out value);  
          // Not all values must be present.  
          if (value == null || value == ""){  
              reader.ReportError("Unable to Retrieve Sort Value");  
          }else{  
            if (!value.Equals("0")){  
              myState.SortState = SortState.Alphabetical;  
            }else{  
              myState.SortState = SortState.Categorized;  
            }  
          }  
        }  
      }  
    }  
  
    public void SaveSettingsToStorage() {  
      MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
      Package package = GetService(typeof(Package)) as Package;  
      RegistryKey rootKey = package.UserRegistryRoot;  
  
      if (mySvc.MyPackage.packageState != null) {  
        using (rootKey) {  
          using(RegistryKey pbrsKey = rootKey.CreateSubKey(this.GetType().Name)) {  
            using (pbrsKey) {  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
            }  
          }  
        }  
      }  
    }  
  
    public void LoadSettingsFromStorage() {  
      MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
      Package package = GetService(typeof(Package)) as Package;  
      RegistryKey rootKey = package.UserRegistryRoot;  
      using (rootKey) {  
        RegistryKey pbrsKey = rootKey.OpenSubKey(this.GetType().Name);  
        if (pbrsKey != null) {  
          using (pbrsKey) {  
            if (mySvc.MyPackage.MakeCurrentSettingTheDefault()){  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
            }else{  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).LoadState(pbrsKey);  
            }  
          }  
        }  
      }  
    }  
  }  
}  
```  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.IProfileManager>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>   
 [导入设置](/visual-cpp/misc/importing-settings)   
 [用户设置的的支持](../extensibility/internals/support-for-user-settings.md)