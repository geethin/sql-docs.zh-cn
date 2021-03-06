---
title: 连接到本机模式报表服务器 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.connectiondialog.F1
helpviewer_keywords:
- report servers [Reporting Services], configuring
ms.assetid: 8b9ea8d3-827c-4011-9e02-be2eac3bb364
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: fb8a192a2d33e2068be75f0acd19fb76166f0705
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48078427"
---
# <a name="connect-to-a-native-mode-report-server"></a>连接到本机模式的报表服务器
  使用此对话框连接到本地或远程[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]或更高版本[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]报表服务器实例。 不能使用此工具连接到早期版本的[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]报表服务器。 一次仅能连接到一个实例。  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 本机模式。  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]不使用配置管理器来配置和管理[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint 模式。 使用 SharePoint 管理中心和 PowerShell 脚本在 SharePoint 模式中配置报表服务器。 有关详细信息，请参阅[安装 Reporting Services SharePoint 模式适用于 SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
> [!TIP]  
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]配置管理器 (RSConfigTool.exe) 安装使用"highestavailable"权限级别。 这种行为是默认设置。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器要求与 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI API 进行通信。 一些 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI 通信要求更高级别的权限或管理权限。   
  
-   若要连接到本地报表服务器实例，请使用默认值并单击 **“连接”**。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器提供了本地服务器名称并可检测到默认实例。 在大多数情况下，您可以单击 **“连接”** 而不必更改值。 如果安装了多个实例，则必须选择要使用的实例。  
  
-   若要连接到远程报表服务器实例，请键入服务器名称，单击 **“查找”**，再选择该实例，然后单击 **“连接”**。  
  
 若要打开此对话框中，启动[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]配置管理器。 启动此工具后，该对话框会立即显示出来。 有关详细信息，请参阅 [Reporting Services Configuration Manager（本机模式）](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)。  
  
## <a name="options"></a>选项  
 **服务器名称**  
 在其上输入的计算机的网络名称[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]或更高版本[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]安装。 只键入计算机名称；不包括前缀或斜杠。  
  
 **查找**  
 查找 **“服务器名称”** 中指定的计算机。  
  
 **报表服务器实例**  
 如果安装了多个报表服务器实例，则选择哪个实例进行连接。 只有有效的实例可供选择。 如果运行旧版[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-并行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例，这些实例将不会显示在列表中。  
  
 **“连接”**  
 连接到指定的服务器和实例。  
  
## <a name="see-also"></a>请参阅  
 [Reporting Services Configuration Manager（本机模式）](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
