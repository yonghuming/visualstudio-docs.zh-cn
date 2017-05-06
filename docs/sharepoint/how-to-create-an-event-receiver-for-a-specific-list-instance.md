---
title: "如何：为特定列表实例创建事件接收器"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "事件接收器 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 事件接收器"
ms.assetid: 4b4b3564-161a-4327-8963-50896c084ac2
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# 如何：为特定列表实例创建事件接收器
  列表实例事件接收器可响应列表定义的任何实例中发生的事件。  尽管事件接收器模板不支持以特定列表实例为目标，但您可以将作用于列表定义的事件接收器修改为响应特定列表实例中的事件。  
  
 若要将特定列表实例作为目标，请将事件接收器的 Elements.xml 中的 `ListTemplateId` 替换为 `ListUrl` 并添加列表实例的 URL。  
  
## 创建列表实例事件接收器  
 以下步骤演示了如何将列表项事件接收器修改为只响应某个自定义公告列表实例中发生的事件。  
  
#### 将事件接收器修改为响应特定列表实例  
  
1.  在浏览器中打开 SharePoint 站点。  
  
2.  在导航窗格中，**列表** 链接。  
  
3.  在 **所有网站内容** 页中，选择 **创建** 链接。  
  
4.  在**“创建”**对话框中，选择**“公告”**类型，将公告命名为“TestAnnouncements”，然后选择**“创建”**按钮。  
  
5.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，创建一个事件接收器项目。  
  
6.  在**“需要哪种类型的事件接收器?”**列表中，选择**“列表项事件”**。  
  
    > [!NOTE]  
    >  还可以选择作用于列表定义的任何其他类型的事件接收器，例如**“列表电子邮件事件”**或**“列表工作流事件”**。  
  
7.  在 **哪个项应为事件源** 列表中，选择 **公告**。  
  
8.  在 **处理以下事件** 列表中，选择 **正在添加项** 复选框，然后选择 **完成** 按钮。  
  
9. 在**“解决方案资源管理器”**中，打开“EventReceiver1”下的“Elements.xml”。  
  
     事件接收器当前使用以下行来引用公告列表定义  
  
    ```  
    <Receivers ListTemplateId="104">  
    ```  
  
     将此行更改为以下文本：  
  
    ```  
    <Receivers ListUrl="Lists/TestAnnouncements">  
    ```  
  
     这将指示事件接收器只响应在刚创建的新 **TestAnnouncements** 公告列表中发生的事件。  您可以将 `ListURL` 特性更改为引用 SharePoint 服务器上的任何列表实例。  
  
10. 打开事件接收器的代码文件，然后在 ItemAdding 方法中放置一个断点。  
  
11. 选择 F5 键生成并运行解决方案。  
  
12. 在 SharePoint 中，选择导航窗格中的**“TestAnnouncements”**链接。  
  
13. 选择**“添加新公告”**链接。  
  
14. 键入公告的标题，然后选择 **保存** 按钮。  
  
     请注意，当向自定义公告列表添加新项时，将会命中断点。  
  
15. 选择 F5 键恢复。  
  
16. 在导航窗格中，选择 **列表** 链接，然后选择 **公告** 链接。  
  
17. 添加新公告。  
  
     请注意，事件接收器不会针对新公告而触发，因为该接收器已配置为只响应自定义公告列表实例**“TestAnnouncements”**中发生的事件。  
  
## 请参阅  
 [如何：创建事件接收器](../sharepoint/how-to-create-an-event-receiver.md)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  