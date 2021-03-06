---
title: sp_dropmergepartition (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergepartition_TSQL
- sp_dropmergepartition
helpviewer_keywords:
- sp_dropmergepartition
ms.assetid: 1be511c1-79ff-4947-9379-78d83b7b8945
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dfaebe93d4d714fabcfc582d531366a4e075b9c4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47685555"
---
# <a name="spdropmergepartition-transact-sql"></a>sp_dropmergepartition (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  从发布中删除参数化行筛选器的分区。 在发布服务器上对发布数据库执行此存储的过程。 此存储过程还删除分区的相应快照作业和快照文件。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_dropmergepartition [ @publication = ] 'publication'  
        , [ @suser_sname = ] 'suser_sname'  
        , [ @host_name = ] 'host_name'  
```  
  
## <a name="arguments"></a>参数  
 [ **@publication**] = **'***发布*****  
 发布的名称。 *发布*是**sysname**，无默认值。  
  
 [ **@suser_sname**=] **'***suser_sname*****  
 是的值[SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md)订阅服务器上的函数用于定义分区。 *suser_sname*是**sysname**，无默认值。  
  
 [ **@host_name** =] **'***host_name*****  
 是的值[HOST_NAME](../../t-sql/functions/host-name-transact-sql.md)订阅服务器上的函数用于定义分区。 *host_name*是**sysname**，无默认值。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功） 或**1** （失败）  
  
## <a name="remarks"></a>备注  
 **sp_dropmergepartition**合并复制中使用。  
  
## <a name="permissions"></a>Permissions  
 只有的成员**sysadmin**固定的服务器角色或**db_owner**固定的数据库角色可以执行**sp_dropmergepartition**。  
  
## <a name="see-also"></a>请参阅  
 [通过参数化筛选器为合并发布管理分区](../../relational-databases/replication/publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)  
  
  
