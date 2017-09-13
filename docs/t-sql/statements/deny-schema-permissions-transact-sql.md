---
title: "DENY 架构权限 (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- denying permissions [SQL Server], schemas
- schemas [SQL Server], permissions
- permissions [SQL Server], schemas
- DENY statement, schemas
ms.assetid: 300a67c4-d226-4653-9e9f-7ae4d53fcf33
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7d4d3e3709ff4ad38d8b033afe1569d9c234bfa2
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="deny-schema-permissions-transact-sql"></a>DENY 架构权限 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  拒绝授予架构权限。  
  

 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
DENY permission  [ ,...n ] } ON SCHEMA :: schema_name  
    TO database_principal [ ,...n ]   
    [ CASCADE ]  
        [ AS denying_principal ]  
```  
  
## <a name="arguments"></a>参数  
 *权限*  
 指定可拒绝授予架构的权限。 有关这些权限的列表，请参阅本主题后面的“备注”部分。  
  
 ON 架构**::**架构*_name*  
 指定拒绝将其权限授予他人的架构。 作用域限定符**::**是必需的。  
  
 *database_principal*  
 指定要对其拒绝权限的主体。 *database_principal*可以是以下之一：  
  
-   数据库用户  
-   数据库角色  
-   应用程序角色  
-   映射到 Windows 登录名的数据库用户  
-   映射到 Windows 组的数据库用户  
-   映射到证书的数据库用户  
-   映射到非对称密钥的数据库用户  
-   未映射到服务器主体的数据库用户  
  
CASCADE  
 指示要拒绝的权限也会被对此主体授予该权限的其他主体拒绝。  
  
*denying_principal*  
 指定一个主体，执行该查询的主体从该主体获得拒绝授予该权限的权利。 *denying_principal*可以是以下之一：  
  
-   数据库用户  
-   数据库角色  
-   应用程序角色  
-   映射到 Windows 登录名的数据库用户  
-   映射到 Windows 组的数据库用户  
-   映射到证书的数据库用户  
-   映射到非对称密钥的数据库用户  
-   未映射到服务器主体的数据库用户  
  
## <a name="remarks"></a>注释  
 架构是权限层次结构中其父级数据库包含的数据库级安全对象。 下表列出了可拒绝的对架构最为具体的限定权限，以及隐含这些权限的更为通用的权限。  
  
|架构权限|架构权限隐含的权限|数据库权限隐含的权限|  
|-----------------------|----------------------------------|------------------------------------|  
|ALTER|CONTROL|ALTER ANY SCHEMA|  
|CONTROL|CONTROL|CONTROL|  
|CREATE SEQUENCE|ALTER|ALTER ANY SCHEMA|  
|DELETE|CONTROL|DELETE|  
|在运行 CREATE 语句前执行|CONTROL|在运行 CREATE 语句前执行|  
|Insert|CONTROL|Insert|  
|REFERENCES|CONTROL|REFERENCES|  
|SELECT|CONTROL|SELECT|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|UPDATE|CONTROL|UPDATE|  
|VIEW CHANGE TRACKING|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 需要对架构具有 CONTROL 权限。 如果要使用 AS 选项，则指定的主体必须拥有架构。  
  
## <a name="see-also"></a>另请参阅  
 [创建架构 &#40;Transact SQL &#41;](../../t-sql/statements/create-schema-transact-sql.md)   
 [DENY (Transact-SQL)](../../t-sql/statements/deny-transact-sql.md)   
 [权限（数据库引擎）](../../relational-databases/security/permissions-database-engine.md)   
 [主体（数据库引擎）](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [sys.fn_builtin_permissions (Transact-SQL)](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [sys.fn_my_permissions &#40;Transact SQL &#41;](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME (Transact-SQL)](../../t-sql/functions/has-perms-by-name-transact-sql.md)  
  
  
