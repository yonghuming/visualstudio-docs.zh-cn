---
title: "在 Windows 窗体中嵌入一个关系图 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa6cd040-7c88-4329-b9c3-2a80b312610f
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: c2f100e88f2c256cc0bc85bc90f92f6d101a862e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>在 Windows 窗体中嵌入图表
您可以在 Windows 控件，它显示在控件中嵌入 DSL 图[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]窗口。  
  
## <a name="embedding-a-diagram"></a>嵌入关系图  
  
#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>将 Windows 控件嵌入 DSL 图  
  
1.  添加新**用户控件**到 DslPackage 项目的文件。  
  
2.  将面板控件添加到用户控件。 此面板将包含 DSL 图。  
  
     添加需要其他控件。  
  
     设置控件的定位点属性。  
  
3.  在解决方案资源管理器，右键单击用户控件文件，然后单击**查看代码**。 将此构造函数和变量添加到代码中：  
  
    ```csharp  
  
    internal UserControl1(MyDSLDocView docView, Control content)  
      : this()  
    {  
      panel1.Controls.Add(content);  
      this.docView = docView;  
    }  
    private MyDSLDSLDocView docView;  
  
    ```  
  
4.  将新文件添加到 DslPackage 项目中，使用以下内容：  
  
    ```  
    using System.Windows.Forms;  
    namespace Company.MyDSL  
    {  
      partial class MyDSLDocView  
      {  
        private UserControl1 container;  
        public override IWin32Window Window  
        {  
          get  
          {  
            if (container == null)  
            {  
              // Put our own form inside the DSL window:  
              container = new UserControl1(this,  
                (Control)base.Window);  
            }  
            return container;  
    } } } }  
  
    ```  
  
5.  若要测试 DSL，按 F5 并打开示例模型文件。 关系图将显示在控件内。 工具箱和其他功能正常工作。  
  
#### <a name="updating-the-form-using-store-events"></a>更新使用应用商店事件窗体  
  
1.  在窗体设计器中，添加**ListBox**名为`listBox1`。 这将在模型中显示的元素的列表。 它将保留在模型使用 synchronism*存储事件*。 有关详细信息，请参阅[事件处理程序传播更改外部模型](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
2.  在自定义代码文件中，重写进一步 DocView 类的方法：  
  
    ```  
  
    partial class MyDSLDocView  
    {  
     /// <summary>  
     /// Register store event listeners.  
     /// This method is called when the model and diagram    
     /// have completed loading.   
     /// </summary>  
     protected override bool LoadView()  
      {  
        bool result = base.LoadView();  
        Store store = this.DocData.Store;  
        EventManagerDirectory emd = store.EventManagerDirectory;  
        DomainClassInfo componentClass = store.DomainDataDirectory.FindDomainClass(typeof(ExampleElement));  
        emd.ElementAdded.Add(componentClass, new EventHandler<ElementAddedEventArgs>(AddElement));  
        emd.ElementDeleted.Add(componentClass, new EventHandler<ElementDeletedEventArgs>(RemoveElement));  
  
        // Do the initial parts list:  
        container.SetUpFormFromModel();  
        return result;  
      }  
     /// <summary>  
     /// Listener method called on creation of each instance of   
     /// the ExampleElement class or its subclasses.  
     /// </summary>  
     private void AddElement(object sender, ElementAddedEventArgs e)  
     {  
       container.Add(e.ModelElement as ExampleElement);  
     }  
     /// <summary>  
     /// Listener method called after deletion of each instance of   
     /// the ExampleElement class or its subclasses.  
     /// </summary>  
     private void RemoveElement(object sender, ElementDeletedEventArgs e)  
     {  
       container.Remove(e.ModelElement as ExampleElement);  
     }  
  
    ```  
  
3.  在代码隐藏用户控件中，插入方法来侦听的添加和移除的元素：  
  
    ```  
  
          public partial class UserControl1 : UserControl { ...  
  
    private ExampleModel modelRoot;  
  
    internal void Add(ExampleElement e) { UpdatePartsList(); }  
    internal void Remove(ExampleElement e) { UpdatePartsList(); }  
  
    internal void SetUpFormFromModel()  
    {  
      modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;  
      UpdatePartsList();  
    }  
  
    private void UpdatePartsList()  
    {  
      StringBuilder builder = new StringBuilder();  
      listBox1.Items.Clear();  
      foreach (ExampleElement c in modelRoot.Elements)  
      {  
        listBox1.Items.Add(c.Name);  
      }  
    }  
  
    ```  
  
4.  若要测试 DSL，按 F5 并在实验实例中的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，打开示例模型文件。  
  
     请注意列表框中显示的元素的列表，在模型中，以及它是正确和撤消和重做任何添加或删除操作后。  
  
## <a name="see-also"></a>另请参阅  
 [导航和更新程序代码中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [编写代码以自定义域特定语言](../modeling/writing-code-to-customise-a-domain-specific-language.md)