---
title: sp_addmergealternatepublisher (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_addmergealternatepublisher_TSQL
- sp_addmergealternatepublisher
helpviewer_keywords:
- sp_addmergealternatepublisher
ms.assetid: de46e0b1-d946-4021-bff6-2d8e3187656d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a13601a907b5ae3f37e9ad6e0451859091361eb3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47674845"
---
# <a name="spaddmergealternatepublisher-transact-sql"></a>sp_addmergealternatepublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  为订阅服务器添加使用备用同步伙伴的功能。 发布属性必须指定订阅服务器可以与其他发布服务器同步。 此存储过程在订阅服务器的订阅数据库中执行。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_addmergealternatepublisher [ @publisher= ] 'publisher'  
          , [ @publisher_db= ] 'publisher_db'  
          , [ @publication= ] 'publication'  
          , [ @alternate_publisher= ] 'alternate_synchronization_partner'  
          , [ @alternate_publisher_db= ] 'alternate_publisher_db'  
          , [ @alternate_publication= ] 'alternate_synchronization_partner'  
     , [ @alternate_distributor= ] 'alternate_distributor'   
    [ , [ @friendly_name= ] 'friendly_name' ]   
    [ , [ @reserved= ] 'reserved' ]  
```  
  
## <a name="arguments"></a>参数  
 [ **@publisher=**] **'***publisher***'**  
 发布服务器的名称。 *发布服务器*是**sysname**，无默认值。  
  
 [ **@publisher_db=**] **'***publisher_db***'**  
 发布数据库的名称。 *publisher_db*是**sysname**，无默认值。  
  
 [ **@publication=**] **'***publication***'**  
 发布的名称。 *发布*是**sysname**，无默认值。  
  
 [ **@alternate_publisher=**] **'***alternate_synchronization_partner*****  
 是备用发布服务器的名称。 *alternate_synchronization_partner*是**sysname**，无默认值。  
  
 [ **@alternate_publisher_db=**] **'***alternate_publisher_db*****  
 备用发布服务器上的发布数据库的名称。 *alternate_publisher_db*是**sysname**，无默认值。  
  
 [ **@alternate_publication=**] **'***alternate_synchronization_partner*****  
 备用同步伙伴上的发布的名称。 *alternate_synchronization_partner*是**sysname**，无默认值。  
  
 [ **@alternate_distributor=**] **'***alternate_distributor*****  
 备用同步伙伴的分发服务器的名称。 *alternate_distributor*是**sysname**，无默认值。  
  
 [ **@friendly_name=**] **'***friendly_name*****  
 显示名称，通过该名称可以标识构成备用同步伙伴的发布服务器、发布和分发服务器之间的关联。 *friendly_name*是**nvarchar(255)**，默认值为 NULL。  
  
 [ **@reserved=**] **'***保留*****  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功） 或**1** （失败）  
  
## <a name="remarks"></a>备注  
 **sp_addmergealternatepublisher**合并复制中使用。  
  
## <a name="permissions"></a>Permissions  
 只有的成员**sysadmin**固定的服务器角色或**db_owner**固定的数据库角色可以执行**sp_addmergealternatepublisher**。  
  
## <a name="see-also"></a>请参阅  
 [sp_dropmergealternatepublisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergealternatepublisher-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
