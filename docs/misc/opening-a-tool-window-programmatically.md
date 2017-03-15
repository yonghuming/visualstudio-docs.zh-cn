---
title: "以编程方式打开工具窗口 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "工具窗口，以编程方式创建"
ms.assetid: 0017441e-7aa3-4a61-9939-57af11d90d97
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# 以编程方式打开工具窗口
通常，通过单击菜单上的命令或按等效的键盘快捷方式可打开工具窗口。 但是，可能必须像命令处理程序一样，以编程方式打开工具窗口。  
  
 若要在提供它的托管 VSPackage 中打开工具窗口，请使用 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>。 若要在另一个 VSPackage 中打开工具窗口，请使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.FindToolWindow%2A>。 在任一种情况下，都按照需要创建工具窗口。  
  
 下面的代码摘自 C\# Reference.ToolWindow 示例。  
  
### 以编程方式打开工具窗口  
  
1.  创建工具窗口窗格、框架和实现它们的 VSPackage。 有关详细信息，请参阅[添加一个工具窗口](../extensibility/adding-a-tool-window.md)。  
  
2.  将 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> 添加到提供它的 VSPackage 中。  
  
    ```c#  
    [ProvideToolWindow(typeof(PersistedWindowPane), Style = VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideMenuResource(1000, 1)] [MsVsShell.DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\8.0Exp")] [PackageRegistration(UseManagedResourcesOnly = true)] [Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")] // your package will have a different GUID public class PackageToolWindow : Package {  
    ```  
  
     这将工具窗口 PersistedWindowPane 注册为打开时停靠在**解决方案资源管理器**中。 有关更多信息，请参见[注册一个工具窗口](../extensibility/registering-a-tool-window.md)。  
  
3.  使用 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 查找工具窗口窗格，如果不存在则创建该窗格。  
  
    ```vb#  
    ' Get the 1 (index 0) and only instance of our tool window. ' If it does not already exist it will get created. Dim pane As MsVsShell.ToolWindowPane = Me.FindToolWindow(GetType(PersistedWindowPane), 0, True) If pane Is Nothing Then End If  
  
    ```  
  
    ```c#  
    // Get the 1 (index 0) and only instance of our tool window. // If it does not already exist it will get created. MsVsShell.ToolWindowPane pane =     this.FindToolWindow(typeof(PersistedWindowPane), 0, true); if (pane == null) {  
    ```  
  
4.  从工具窗口窗格中获取工具窗口框架。  
  
    ```vb#  
    Dim frame As IVsWindowFrame = TryCast(pane.Frame, IVsWindowFrame) If frame Is Nothing Then End If  
  
    ```  
  
    ```c#  
    IVsWindowFrame frame = pane.Frame as IVsWindowFrame; if (frame == null) {  
    ```  
  
5.  显示工具窗口。  
  
    ```vb#  
    ' Bring the tool window to the front and give it focus ErrorHandler.ThrowOnFailure(frame.Show())  
  
    ```  
  
    ```c#  
    // Bring the tool window to the front and give it focus ErrorHandler.ThrowOnFailure(frame.Show());  
    ```