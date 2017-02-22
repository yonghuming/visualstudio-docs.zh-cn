---
title: "创建可重用的按钮的组 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "在 Vspackage 中创建的按钮组"
  - "Vspackage，创建可重用按钮组"
  - "按钮，创建可重用的组"
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
caps.latest.revision: 44
caps.handback.revision: 44
ms.author: "gregvanl"
manager: "ghogen"
---
# 创建可重用的按钮的组
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

命令组是始终一起出现在菜单或工具栏上的命令的集合。 可以将其分配给不同的父菜单.vsct 文件的 CommandPlacements 部分中重新使用任何命令组。  
  
 命令组通常包含按钮，但它们也可以包含其他菜单或组合框。  
  
### 若要创建可重用的一组按钮  
  
1.  创建一个名为的 VSIX 项目 `ReusableButtons`。 有关详细信息，请参阅[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  当项目打开后时，添加一个名为的自定义命令项模板 **ReusableCommand**。 在 **解决方案资源管理器**, ，用鼠标右键单击项目节点并选择 **添加 \/ 新项**。 在 **添加新项** 对话框中，转到 **Visual C\# \/ 可扩展性** ，然后选择 **自定义命令**。 在 **名称** 在窗口的底部字段中，命令文件名称更改为 **ReusableCommand.cs**。  
  
3.  在.vsct 文件中，转到符号部分，并找到包含组和项目的命令的 GuidSymbol 元素。 其名称应为 guidReusableCommandPackageCmdSet。  
  
4.  添加您将添加到组中，如以下示例所示的每个按钮 IDSymbol。  
  
    ```xml  
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}"> <IDSymbol name="MyMenuGroup" value="0x1020" /> <IDSymbol name="ReusableCommandId" value="0x0100" /> <IDSymbol name="SecondReusableCommandId" value="0x0200" /> </GuidSymbol>  
    ```  
  
     默认情况下，该命令项目模板将创建一个名为组 **MyGroup** 和一个按钮，已提供，以及为每个 IDSymbol 条目的名称。  
  
5.  在组部分中，创建一个具有与符号部分中提供的那些相同的 GUID 和 ID 属性的组元素。 您还可以使用现有的组，或使用提供的命令模板，如以下示例所示的条目。 此组将出现在 **工具** 菜单  
  
    ```xml  
    <Groups> <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600"> <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/> </Group> </Groups>  
    ```  
  
### 若要创建一组以供重复使用的按钮  
  
1.  您可将命令或菜单组中使用的命令或菜单上，定义中的父组或通过使用 CommandPlacements 节组中放置命令或菜单。  
  
     按钮部分中定义具有您作为其父级的组的按钮或使用提供的包模板按钮，如下面的示例中所示。  
  
    ```xml  
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button"> <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" /> <Icon guid="guidImages" id="bmpPic1" /> <Strings> <ButtonText>Invoke ReusableCommand</ButtonText> </Strings> </Button>  
    ```  
  
2.  如果一个按钮必须出现在多个组，创建一个条目为其在 CommandPlacements 部分中，必须放在命令部分之后。 设置 CommandPlacement 元素来匹配这些您想要放置，按钮的 GUID 和 ID 属性，然后设置 GUID 和其父元素的 ID 与目标组中，如下面的示例中所示。  
  
    ```xml  
    <CommandPlacements> <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105"> <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" /> </CommandPlacement> </CommandPlacements>  
    ```  
  
    > [!NOTE]
    >  优先级字段的值确定该命令中的新的命令组的位置。 在元素中的项定义设置会覆盖的 CommandPlacement 设置优先级别。 在具有较高的优先级值的命令之前，会显示具有较低的优先级值的命令。 允许使用重复的优先级值，但不能保证具有相同的优先级值的命令的相对位置，因为顺序 **devenv \/setup** 命令创建最后一个接口的注册表位置可能会不一致。  
  
### 在菜单上放置一组可重用按钮  
  
1.  创建将项记入 `CommandPlacements` 部分。 设置的 GUID 和 ID `CommandPlacement` 元素与您的组，并将设置父 GUID 和 ID 为这些目标位置。  
  
     CommandPlacements 部分应放置命令节的后面:  
  
    ```xml  
    <CommandTable> ... <Commands>... </Commands> <CommandPlacements>... </CommandPlacements> ... </CommandTable>  
    ```  
  
     命令组可以包含多个菜单上。 父菜单可以是应用程序创建，由提供的其中一个 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(按所述 ShellCmdDef.vsct 或 SharedCmdDef.vsct\)，或在另一个 VSPackage 中定义的其中一个。 父级关系图层的数目不受限制，只要父菜单最终连接到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 或向 VSPackage 所显示的快捷菜单。  
  
     下面的示例将组放 **解决方案资源管理器** 工具栏上，其他按钮的右侧。  
  
    ```xml  
    <CommandPlacements> <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00"> <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/> </CommandPlacement> </CommandPlacements>  
    ```  
  
    ```xml  
    <CommandPlacements> <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup" priority="0x605"> <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" /> </CommandPlacement> </CommandPlacements>  
  
    ```