---
title: "sp_setdefaultdatatypemapping (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_setdefaultdatatypemapping
- sp_setdefaultdatatypemapping_TSQL
helpviewer_keywords: sp_setdefaultdatatypemapping
ms.assetid: 7394e8ca-4ce1-4e99-a784-205007c2c248
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 28b267b8e03fed032811aeaa98bbbf8b7c4b515c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="spsetdefaultdatatypemapping-transact-sql"></a>sp_setdefaultdatatypemapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  将标记之间的现有数据类型映射[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]和非-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据库管理系统 (DBMS) 作为默认值。 此存储过程在分发服务器上的任何数据库中执行。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_setdefaultdatatypemapping [ [ @mapping_id = ] mapping_id ]  
    [ , [ @source_dbms = ] 'source_dbms' ]  
    [ , [ @source_version = ] 'source_version' ]  
    [ , [ @source_type = ] 'source_type' ]   
    [ , [ @source_length_min = ] source_length_min ]  
    [ , [ @source_length_max = ] source_length_max ]  
    [ , [ @source_precision_min = ] source_precision_min ]  
    [ , [ @source_precision_max = ] source_precision_max ]  
    [ , [ @source_scale_min = ] source_scale_min ]  
    [ , [ @source_scale_max = ] source_scale_max ]  
    [ , [ @source_nullable = ] source_nullable ]  
    [ , [ @destination_dbms = ] 'destination_dbms' ]  
    [ , [ @destination_version = ] 'destination_version' ]  
    [ , [ @destination_type = ] 'destination_type' ]  
    [ , [ @destination_length = ] destination_length ]  
    [ , [ @destination_precision = ] destination_precision ]  
    [ , [ @destination_scale = ] destination_scale ]  
    [ , [ @destination_nullable = ] source_nullable ]  
```  
  
## <a name="arguments"></a>参数  
 [  **@mapping_id=** ] *mapping_id*  
 标识现有数据类型映射。  *mapping_id*是**int**，默认值为 NULL。 如果指定*mapping_id*，则剩余的参数不需要。  
  
 [  **@source_dbms** =] *source_dbms*  
 从中映射数据类型的 DBMS 的名称。 *source_dbms*是**sysname**，和可以是以下值之一。  
  
|值|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|源为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。|  
|**ORACLE**|源为 Oracle 数据库。|  
|NULL（默认值）||  
  
 如果必须指定此参数*mapping_id*为 NULL。  
  
 [  **@source_version=** ] *source_version*  
 源 DBMS 的版本号。 *source_version*是**varchar(10)**，默认值为 NULL。  
  
 [  **@source_type** =] *source_type*  
 源 DBMS 中的数据类型。 *source_type*是**sysname**。 如果必须指定此参数*mapping_id*为 NULL。  
  
 [  **@source_length_min=** ] *source_length_min*  
 源 DBMS 中的数据类型的最小长度。 *source_length_min*是**bigint**，默认值为 NULL。  
  
 [  **@source_length_max=** ] *source_length_max*  
 源 DBMS 中的数据类型的最大长度。 *source_length_max*是**bigint**，默认值为 NULL。  
  
 [  **@source_precision_min=** ] *source_precision_min*  
 源 DBMS 中的数据类型的最小精度。 *source_precision_min*是**bigint**，默认值为 NULL。  
  
 [  **@source_precision_max=** ] *source_precision_max*  
 源 DBMS 中的数据类型的最大精度。 *source_precision_max*是**bigint**，默认值为 NULL。  
  
 [  **@source_scale_min=** ] *source_scale_min*  
 源 DBMS 中的数据类型的最小小数位数。 *source_scale_min*是**int**，默认值为 NULL。  
  
 [  **@source_scale_max=** ] *source_scale_max*  
 源 DBMS 中的数据类型的最大小数位数。 *source_scale_max*是**int**，默认值为 NULL。  
  
 [  **@source_nullable=** ] *source_nullable*  
 源 DBMS 中的数据类型是否支持 NULL 值。 *source_nullable*是**位**，默认值为 NULL。 **1**意味着支持 NULL 值。  
  
 [  **@destination_dbms**  =] *destination_dbms*  
 目标 DBMS 的名称。 *destination_dbms*是**sysname**，和可以是以下值之一。  
  
|值|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|目标为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。|  
|**ORACLE**|目标为 Oracle 数据库。|  
|**DB2**|目标为 IBM DB2 数据库。|  
|**SYBASE**|目标为 Sybase 数据库。|  
|NULL（默认值）||  
  
 [  **@destination_version** =] *destination_version*  
 是目标 DBMS 的产品版本。 *destination_version*是**varchar(10)**，默认值为 NULL。  
  
 [  **@destination_type** =] *destination_type*  
 目标 DBMS 中列出的数据类型。 *destination_type*是**sysname**，默认值为 NULL。  
  
 [  **@destination_length=** ] *destination_length*  
 目标 DBMS 中的数据类型的长度。 *destination_length*是**bigint**，默认值为 NULL。  
  
 [  **@destination_precision=** ] *destination_precision*  
 是目标 DBMS 中的数据类型的精度。 *destination_precision*是**bigint**，默认值为 NULL。  
  
 [  **@destination_scale=** ] *destination_scale*  
 是目标 DBMS 中的数据类型的小数位数。 *destination_scale*是**int**，默认值为 NULL。  
  
 [  **@destination_nullable=** ] *destination_nullable*  
 目标 DBMS 中的数据类型是否支持 NULL 值。 *destination_nullable*是**位**，默认值为 NULL。 **1**意味着支持 NULL 值。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功） 或**1** （失败）  
  
## <a name="remarks"></a>注释  
 **sp_setdefaultdatatypemapping**中所有类型之间的复制使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]和非-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DBMS。  
  
 默认数据类型映射适用于所有包含指定 DBMS 的复制拓扑。  
  
## <a name="permissions"></a>Permissions  
 只有的成员**sysadmin**固定的服务器角色可以执行**sp_setdefaultdatatypemapping**。  
  
## <a name="see-also"></a>另请参阅  
 [指定 Oracle 发布服务器的数据类型映射](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [sp_getdefaultdatatypemapping &#40;Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)   
 [sp_helpdatatypemap &#40;Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md)  
  
  