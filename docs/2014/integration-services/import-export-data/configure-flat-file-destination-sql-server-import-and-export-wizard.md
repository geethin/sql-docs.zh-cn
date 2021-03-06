---
title: 配置平面文件目标（SQL Server 导入和导出向导）| Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.configureflatfiledest.f1
ms.assetid: 318e8da0-37d3-46cd-943a-fc5d66aad93a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 931c04a8a038612edcdaa48f40231c5fb6faed00
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48071487"
---
# <a name="configure-flat-file-destination-sql-server-import-and-export-wizard"></a>配置平面文件目标（SQL Server 导入和导出向导）
  使用**配置平面文件目标**页为目标平面文件中，指定格式选项，并继续操作之前预览结果。  
  
 若要了解有关此向导的详细信息，请参阅[SQL Server 导入和导出向导](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。 若要了解有关用于启动向导，以及若要成功运行该向导所需的权限选项，请参阅[运行 SQL Server 导入和导出向导](start-the-sql-server-import-and-export-wizard.md)。  
  
 SQL Server 导入和导出向导的作用是将数据从源复制到目标。 该向导还可以为您创建目标数据库和目标表。 但是，如果必须复制多个数据库或表，或者必须复制其他类型的数据库对象，则应改用复制数据库向导。 有关详细信息，请参阅 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。  
  
## <a name="options"></a>选项  
 **源平面文件**  
 目标文件的名称。  
  
 **行分隔符**  
 从行分隔符的列表中进行选择。  
  
|ReplTest1|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|行由回车符和换行符的组合分隔。|  
|**{CR}**|行由回车符分隔。|  
|**{LF}**|行由换行符分隔。|  
|**分号 {;}**|行由分号分隔。|  
|**冒号 {:}**|行由冒号分隔。|  
|**逗号 {,}**|行由逗号分隔。|  
|**制表符 {t}**|行由制表符分隔。|  
|**竖线 {&#124;}。**|行由竖线分隔。|  
  
 **列分隔符**  
 从列分隔符的列表中进行选择。  
  
|ReplTest1|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|列由回车符和换行符的组合分隔。|  
|**{CR}**|列由回车符分隔。|  
|**{LF}**|列由换行符分隔。|  
|**分号 {;}**|列由分号分隔。|  
|**冒号 {:}**|列由冒号分隔。|  
|**逗号 {,}**|列由逗号分隔。|  
|**制表符 {t}**|列由制表符分隔。|  
|**竖线 {&#124;}。**|列由竖线分隔。|  
  
 **预览**  
 在中查看**预览数据**对话框结果的所选的格式设置选项中为目标平面文件。  
  
 **编辑转换**  
 删除行、 追加行，并使用目标文件中配置的列**列映射**对话框。  
  
  
