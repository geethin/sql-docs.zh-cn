---
title: "ASSEMBLYPROPERTY (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ASSEMBLYPROPERTY_TSQL
- ASSEMBLYPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- ASSEMBLYPROPERTY statement
- assemblies [CLR integration], properties
ms.assetid: cf03d1b1-724c-48bf-a8df-3fe2586b150a
caps.latest.revision: 40
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9556834a173302e19358f5333b059d7b4f902519
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="assemblyproperty-transact-sql"></a>ASSEMBLYPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

返回有关程序集的属性的信息。
  
![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>语法  
  
```sql
ASSEMBLYPROPERTY('assembly_name', 'property_name')  
```  
  
## <a name="arguments"></a>参数  
*程序集 _ 名称*  
程序集的名称。
  
*property_name*  
要检索其有关信息的属性的名称。 *property_name*可以是以下值之一。
  
|值|Description|  
|---|---|
|**CultureInfo**|程序集的区域设置。|  
|**PublicKey**|程序集的公钥或公钥令牌。|  
|**MvID**|由编译器生成的完整的程序集版本标识号。|  
|**VersionMajor**|由四部分组成的程序集版本标识号的主要组成部分（第一部分）。|  
|**VersionMinor**|由四部分组成的程序集版本标识号的次要组成部分（第二部分）。|  
|**VersionBuild**|由四部分组成的程序集版本标识号的内部版本组成部分（第三部分）。|  
|**VersionRevision**|由四部分组成的程序集版本标识号的修订版组成部分（第四部分）。|  
|**SimpleName**|程序集的简称。|  
|**体系结构**|程序集的处理器体系结构。|  
|**CLRName**|对程序集的简单名称、版本号、区域性、公钥以及体系结构进行编码的规范字符串。 该值唯一地标识公共语言运行时 (CLR) 端的程序集。|  
  
## <a name="return-type"></a>返回类型
**sql_variant**
  
## <a name="examples"></a>示例  
以下示例假定在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库中注册了 `HelloWorld` 程序集。 有关详细信息，请参阅[Hello World 示例](http://msdn.microsoft.com/library/fed6c358-f5ee-4d4c-9ad6-089778383ba7)。
  
```sql
USE AdventureWorks2012;  
GO  
SELECT ASSEMBLYPROPERTY ('HelloWorld' , 'PublicKey');  
```  
  
## <a name="see-also"></a>另请参阅
[CREATE ASSEMBLY (Transact-SQL)](../../t-sql/statements/create-assembly-transact-sql.md)  
[DROP ASSEMBLY (Transact-SQL)](../../t-sql/statements/drop-assembly-transact-sql.md)
  
  
