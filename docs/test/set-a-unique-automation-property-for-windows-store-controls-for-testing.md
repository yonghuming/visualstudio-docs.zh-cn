---
title: "为 Windows 应用商店控件设置唯一的自动化属性以进行测试 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9bdd74ff-2534-4fc7-a5c3-a77bf7843037
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "mlearned"
manager: "douge"
---
# 为 Windows 应用商店控件设置唯一的自动化属性以进行测试
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果要对基于 XAML 的 Windows 应用商店应用运行编码的 UI 测试，必须拥有能够识别每个控件的唯一的自动化属性。  
  
 可基于应用程序中的 XAML 控件的类型分配一个唯一的自动化属性。  此处说明了如何在以下情况下分配此唯一的自动化属性：  
  
-   [控件的静态 XAML 定义](#UniquePropertyWindowsStoreControlsStaticXAML)  
  
-   [使用 Visual Studio 或 Blend For Visual Studio 分配唯一的自动化属性](#UniquePropertyWindowsStoreControlsExpressionBlend)  
  
-   [使用 DataTemplate](#UniquePropertyWindowsStoreControlsDataTemplate)  
  
-   [使用控件模板](#UniquePropertyWindowsStoreControlsControlTemplate)  
  
-   [动态控件](#UniquePropertyWindowsStoreControlsDynamicControls)  
  
## 使用方法分配唯一的自动化属性  
  
###  <a name="UniquePropertyWindowsStoreControlsStaticXAML"></a> 静态 XAML 定义  
 若要为 XAML 文件中定义的控件指定一个唯一的自动化属性，您可隐式或显式设置 AutomationProperties.AutomationId 或 AutomationProperties.Name，如以下示例所示。  通过设置上述任一值，可为控件分配一个唯一的自动化属性，当您创建编码的 UI 测试或操作录制时，可使用该属性标识控件。  
  
 **隐式设置属性**  
  
 在控件的 XAML 中，使用 Name 属性将 AutomationProperties.AutomationId 设置为 ButtonX。  
  
```xaml  
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />  
  
```  
  
 在控件的 XAML 中，使用 Content 属性将 AutomationProperties.Name 设置为 ButtonY。  
  
```xaml  
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />  
  
```  
  
 **显式设置属性**  
  
 在控件的 XAML 中，将 AutomationProperties.AutomationId 显式设置为 ButtonX。  
  
```xaml  
<Button AutomationProperties.AutomationId=“ButtonX” Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />  
  
```  
  
 在控件的 XAML 中，将 AutomationProperties.Name 显式设置为 ButtonY。  
  
```  
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />  
```  
  
###  <a name="UniquePropertyWindowsStoreControlsExpressionBlend"></a> 使用 Visual Studio 或 Blend For Visual Studio 分配唯一的自动化属性  
 您可使用 Visual Studio or Blend for Visual Studio 为交互元素（例如，按钮、列表框、组合框和文本框）分配唯一名称。  这将为控件的 AutomationProperties.Name 分配一个唯一值。  
  
 在 **Visual Studio:**  的 **工具** 菜单上，指向 **“选项”**，依次选择 **“文本编辑器”** 和 **“XAML”** 最后选择 **“杂项”**.  
  
 选择**交互元素创建时自动命名** 然后单击 **确定**.  
  
 ![XAML“杂项”选项](../test/media/cuit_windowsstoreapp_b.png "CUIT\_WindowsStoreApp\_B")  
  
 对以下方法的 **Blend for Visual Studio:**  使用一个执行该 Blend For Visual Studio。  
  
> [!NOTE]
>  您只能将此方法用于通过使用 XAML 静态创建的控件。  
  
 **为现有控件提供一个唯一名称**  
  
 在 **工具** 菜单中，选择 **命名交互元素**，如下所示：  
  
 ![从“工具”菜单中选择“命名交互元素”](../test/media/cuit_windowsstoreproperty_blend_1.png "CUIT\_WindowsStoreProperty\_Blend\_1")  
  
 **自动为创建的控件提供一个唯一名称**  
  
 在**“工具”**菜单上，指向**“选项”**，然后单击**“项目”**。  选择**交互元素创建时自动命名** 然后单击 **确定**.  
  
 ![将项目设置为命名交互元素](../test/media/cuit_windowsstoreproeprty_blend_2.png "CUIT\_WindowsStoreProeprty\_Blend\_2")  
  
###  <a name="UniquePropertyWindowsStoreControlsDataTemplate"></a> 使用数据模板  
 可以使用 ItemTemplate 定义一个简单模板，以使用以下 XAML 将列表框中的值绑定到变量。  
  
```xaml  
  
<ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">  
   <ListBox.ItemTemplate>  
      <DataTemplate>  
         <StackPanel Orientation="Horizontal">  
            <TextBlock Text="{Binding EmployeeName}" />  
            <TextBlock Text="{Binding EmployeeID}" />  
         </StackPanel>  
      </DataTemplate>  
   </ListBox.ItemTemplate>  
</ListBox>  
```  
  
 还可以将模板与 ItemContainerStyle 一起使用，以使用以下 XAML 将值绑定到变量。  
  
```xaml  
  
      <ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">  
            <ListBox.ItemContainerStyle>  
                <Style TargetType="ListBoxItem">  
                    <Setter Property="Template">  
                        <Setter.Value>  
                            <ControlTemplate TargetType="ListBoxItem">  
                                <Grid>  
                                    <Button Content="{Binding EmployeeName}" AutomationProperties.AutomationId="{Binding EmployeeID}"/>  
                                </Grid>  
                            </ControlTemplate>  
                        </Setter.Value>  
                    </Setter>  
                </Style>  
            </ListBox.ItemContainerStyle>           
        </ListBox>  
  
```  
  
 对于这两个示例，您必须重写 ItemSource 的 ToString\(\) 方法，如使用以下代码的情况所示。  此代码可确保设置 AutomationProperties.Name 值且该值是唯一的，因为您无法使用绑定为每个数据绑定列表项设置一个唯一的自动化属性。  在此示例中，为 Automation Properties.Name 设置一个唯一值即可。  
  
> [!NOTE]
>  通过使用此方法，还可通过绑定将列表项的内部内容设置为 Employee 类中的字符串。  如示例中所示，为每个列表项内的按钮控件分配一个唯一的自动化 ID（即 Employee ID）。  
  
```  
  
Employee[] employees = new Employee[]   
{  
   new Employee("john", "4384"),  
   new Employee("margaret", "7556"),  
   new Employee("richard", "8688"),  
   new Employee("george", "1293")  
};  
  
listBox1.ItemsSource = employees;  
  
public override string ToString()  
{  
    return EmployeeName + EmployeeID; // Unique Identification to be set as the AutomationProperties.Name  
}  
  
```  
  
###  <a name="UniquePropertyWindowsStoreControlsControlTemplate"></a> 使用控件模板  
 通过使用控件模板，可使得在代码中定义某个特定类型的每个实例时，这些实例都获得一个唯一的自动化属性。  您必须创建模板，以便 AutomationProperty 在控件实例中绑定到一个唯一的 ID。  以下 XAML 演示了使用控件模板创建此绑定的一种方法。  
  
```xaml  
  
<Style x:Key="MyButton" TargetType="Button">  
<Setter Property="Template">  
   <Setter.Value>  
<ControlTemplate TargetType="Button">  
   <Grid>  
      <CheckBox HorizontalAlignment="Left" AutomationProperties.AutomationId="{TemplateBinding Content}"></CheckBox>  
      <Button Width="90" HorizontalAlignment="Right" Content="{TemplateBinding Content}" AutomationProperties.AutomationId="{TemplateBinding Content}"></Button>  
   </Grid>  
</ControlTemplate>  
   </Setter.Value>  
</Setter>  
</Style>  
  
```  
  
 在使用此控件模板定义按钮的两个实例时，自动化 ID 在模板中将设置为控件的唯一内容字符串，如以下 XAML 所示。  
  
```xaml  
  
<Button Content=”Button1” Style="{StaticResource MyButton}" Width="140"/>  
<Button Content=”Button2” Style="{StaticResource MyButton}" Width="140"/>  
```  
  
###  <a name="UniquePropertyWindowsStoreControlsDynamicControls"></a> 动态控件  
 如果您具有的控件是从您的代码中动态创建的，而不是静态创建的或通过 XAML 文件中的模板创建的，则您必须设置控件的 Content 属性或 Name 属性。  这将确保每个动态控件都具有一个唯一的自动化属性。  例如，如果您的复选框必须在选择列表项时显示，则可设置这些属性，如此处所示：  
  
```c#  
  
private void CreateCheckBox(string txt, StackPanel panel)  
   {  
      CheckBox cb = new CheckBox();  
      cb.Content = txt; // Sets the AutomationProperties.Name  
      cb.Height = 50;  
      cb.Width = 100;  
      cb.Name = "DynamicCheckBoxAid"+ txt; // Sets the AutomationProperties.AutomationId  
      panel.Children.Add(cb);  
    }  
  
```  
  
## 请参阅  
 [使用编码的 UI 测试来测试 Windows Store 8.1 应用](../test/test-windows-store-8-1-apps-with-coded-ui-tests.md)