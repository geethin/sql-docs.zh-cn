---
title: 停止对系统版本控制临时表的系统版本控制 | Microsoft Docs
ms.custom: ''
ms.date: 10/11/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: dddd707e-bfb1-44ff-937b-a84c5e5d1a94
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 37fe6d7b3dfe92e2cdf53e7a7b26ab363a567510
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/27/2018
ms.locfileid: "52409155"
---
# <a name="stopping-system-versioning-on-a-system-versioned-temporal-table"></a>停止对系统版本的临时表的系统版本控制
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  你可能希望暂时或永久停止对临时表的版本控制。   
可以通过将 **SYSTEM_VERSIONING** 子句设置为 **OFF**实现此操作。  
  
## <a name="setting-systemversioning--off"></a>将 SYSTEM_VERSIONING 设置为 OFF  
 如果希望对时态表执行特定的维护操作或者不再需要版本控制的表，请停止系统版本控制。 完成此操作后，将获得两个独立的表：  
  
-   具有时间段定义的当前表  
  
-   作为常规表的历史记录表  
  
### <a name="important-remarks"></a>重要提示  
  
-   设置  **SYSTEM_VERSIONING = OFF** 或删除 **SYSTEM_TIME** 时间段时不会出现数据丢失的情况。  
  
-   设置 **SYSTEM_VERSIONING = OFF** 且不删除 **SYSTEM_TIME** 时间段时，系统将继续更新每个插入和更新操作的时间段列。 在当前表中执行的删除操作是永久性的。  
  
-   删除 **SYSTEM_TIME** 时间段以完全删除该时间段列。  
  
-   设置 **SYSTEM_VERSIONING = OFF**时，具有足够权限的所有用户都能够修改历史记录表的架构和内容，甚至还可以永久删除该历史记录表。  
  
### <a name="permanently-remove-systemversioning"></a>永久删除 SYSTEM_VERSIONING  
 此示例永久删除了 SYSTEM_VERSIONING 并完全删除了时间段列。 删除时间段列是可选的操作。  
  
```  
ALTER TABLE dbo.Department SET (SYSTEM_VERSIONING = OFF);   
/*Optionally, DROP PERIOD if you want to revert temporal table to a non-temporal*/   
ALTER TABLE dbo.Department   
DROP PERIOD FOR SYSTEM_TIME;  
  
```  
  
### <a name="temporarily-remove-systemversioning"></a>暂时删除 SYSTEM_VERSIONING  
 以下是需要将系统版本控制设置为 **OFF**的操作列表：  
  
-   从历史记录中删除不必要的数据（**DELETE** 或 **TRUNCATE**）  
  
-   从没有版本控制的当前表中删除数据（**DELETE**、 **TRUNCATE**）  
  
-   从当前表对 **SWITCH OUT** 进行分区  
  
-   将 **SWITCH IN** 分区到历史记录表  
  
 此示例暂时停止了 SYSTEM_VERSIONING 以便可以执行特定的维护操作。 如果作为表维护的先决条件暂时停止了版本控制，那么强烈建议在事务内执行此操作以保持数据一致性。  
  
```  
BEGIN TRAN   
ALTER TABLE dbo.Department SET (SYSTEM_VERSIONING = OFF);   
TRUNCATE TABLE [History].[DepartmentHistory]   
WITH (PARTITIONS (1,2))   
ALTER TABLE dbo.Department SET    
(   
SYSTEM_VERSIONING = ON (HISTORY_TABLE = History.DepartmentHistory)   
);   
COMMIT ;  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [临时表](../../relational-databases/tables/temporal-tables.md)   
 [系统版本控制临时表入门](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)   
 [管理版本由系统控制的临时表中历史数据的保留期](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [系统版本控制的临时表与内存优化表](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [创建由系统控制版本的临时表](../../relational-databases/tables/creating-a-system-versioned-temporal-table.md)   
 [在系统版本控制的临时表中修改数据](../../relational-databases/tables/modifying-data-in-a-system-versioned-temporal-table.md)   
 [在系统版本控制临时表中查询数据](../../relational-databases/tables/querying-data-in-a-system-versioned-temporal-table.md)   
 [更改系统版本控制的临时表架构](../../relational-databases/tables/changing-the-schema-of-a-system-versioned-temporal-table.md)  
  
  
