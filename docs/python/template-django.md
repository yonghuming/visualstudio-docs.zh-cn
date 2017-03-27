---
title: "针对 Visual Studio 的 Python 工具中的 Django Web 项目模板 | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c479be58-13eb-4d77-9a27-c97ddc290963
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
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
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 7f65641fbf15edfe16931badc19602a0fc773bff
ms.lasthandoff: 03/07/2017

---

# <a name="django-web-project-template"></a>Django Web 项目模板

[Django](https://www.djangoproject.com/) 是高级 Python 框架，用于快速、安全及可扩展的 Web 开发。 针对 Visual Studio 的 Python 工具 (PTVS) 提供项目模板以设置基于 Django 的 Web 应用程序的结构。 若要在 Visual Studio 中使用模板，请选择“文件”>“新建”>“项目”，搜索“Django”，然后选择“Django Web 项目”模板。 生成的项目将包含 Boilerplate 代码，以及默认的 SQLite 数据库。 “空白 Django Web 项目”模板类似，但不包括数据库。

PTVS 为 Django 项目提供完整的 IntelliSense：

- 传递给模板的上下文变量：

    ![IntelliSense 的上下文变量](media/template-django-intellisense.png)

- 针对内置和用户定义的标记和筛选器：

    ![IntelliSense 的标记和筛选器](media/template-django-intellisense-filter.png)

- 嵌入式 CSS 和 JavaScript 的语法着色：

    ![CSS IntelliSense](media/template-django-intellisense-css.png)

    ![JavaScript IntelliSense](media/template-django-intellisense-js.png)


PTVS 还为 Django 项目提供完整的[调试支持](debugging.md)： 

![断点](media/template-django-debugging.png)

## <a name="django-management-console"></a>Django 管理控制台

Django 管理控制台可通过“项目”菜单上的各种命令或在解决方案资源管理器中右键单击项目来进行访问。

- **打开 Django Shell...**：将打开应用程序上下文中的 shell，这使你能够操作模型

    ![控制台](media/template-django-console-shell.png)

- **Django 同步数据库**：在交互式窗口中执行 `manage.py syncdb`：

    ![控制台](media/template-django-console-sync-db.png)

- **收集静态文件**：执行 `manage.py collectstatic --noinput` 以将所有静态文件复制到由 `settings.py` 中的 `STATIC_ROOT` 指定的路径中。 请注意，当[发布到 Microsoft Azure](template-web.md#publishing-to-azure-app-service) 时，将自动收集静态文件，作为发布操作的一部分。

    ![控制台](media/template-django-console-collect-static.png)

- **验证**：执行 `manage.py validate`，它将报告由 `settings.py` 中 `INSTALLED_APPS` 指定的已安装模型中的任何验证错误：

    ![控制台](media/template-django-console-validate.png)
