---
title: "提取 (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FETCH
- FETCH_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- FETCH statement
- cursors [SQL Server], fetching
- Transact-SQL cursors, fetching and scrolling
- retrieving rows
- fetching [SQL Server]
- SCROLL option
- row fetching [SQL Server]
ms.assetid: 5d68dac2-f91b-4342-bb4e-209ee132665f
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1333af6ceba4a4410fefadd1a99d8611fae88a6a
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="fetch-transact-sql"></a>FETCH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  通过 [!INCLUDE[tsql](../../includes/tsql-md.md)] 服务器游标检索特定行。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
FETCH   
          [ [ NEXT | PRIOR | FIRST | LAST   
                    | ABSOLUTE { n | @nvar }   
                    | RELATIVE { n | @nvar }   
               ]   
               FROM   
          ]   
{ { [ GLOBAL ] cursor_name } | @cursor_variable_name }   
[ INTO @variable_name [ ,...n ] ]   
```  
  
## <a name="arguments"></a>参数  
 NEXT  
 紧跟当前行返回结果行，并且当前行递增为返回行。 如果 FETCH NEXT 为对游标的第一次提取操作，则返回结果集中的第一行。 NEXT 为默认的游标提取选项。  
  
 PRIOR  
 返回紧邻当前行前面的结果行，并且当前行递减为返回行。 如果 FETCH PRIOR 为对游标的第一次提取操作，则没有行返回并且游标置于第一行之前。  
  
 FIRST  
 返回游标中的第一行并将其作为当前行。  
  
 LAST  
 返回游标中的最后一行并将其作为当前行。  
  
 绝对 {  *n* | @*nvar*}  
 如果 *n* 或 @*nvar*为正值，则返回的行 *n* 从光标开头的行并将新的当前行的返回的行。 如果 *n* 或 @*nvar*为负，返回一行 *n* 光标结束之前的行并将新的当前行的返回的行。 如果 *n* 或 @*nvar*为 0，则会返回任何行。 *n*必须是整数常量和 @*nvar*必须**smallint**， **tinyint**，或**int**。  
  
 相对 {  *n* | @*nvar*}  
 如果 *n* 或 @*nvar*为正值，则返回的行 *n* 超出当前行的行并将新的当前行的返回的行。 如果 *n* 或 @*nvar*为负，返回一行 *n* 在当前行之前的行并将新的当前行的返回的行。 如果 *n* 或 @*nvar*为 0，则返回当前行。 如果使用的提取相对指定 *n* 或 @*nvar*设置为负数或 0 上完成对游标第一次提取时，会返回任何行。 *n*必须是整数常量和 @*nvar*必须**smallint**， **tinyint**，或**int**。  
  
 GLOBAL  
 指定*cursor_name*指全局游标。  
  
 *cursor_name*  
 要从中进行提取的开放游标的名称。 全局和局部游标是否存在与*cursor_name*作为其名称， *cursor_name*到全局游标如果指定全局和局部游标如果未指定全局。  
  
 @*cursor_variable_name*  
 游标变量名，引用要从中进行提取操作的打开的游标。  
  
 @ INTO*variable_name*[，...*n*]  
 允许将提取操作的列数据放到局部变量中。 列表中的各个变量从左到右与游标结果集中的相应列相关联。 各变量的数据类型必须与相应的结果集列的数据类型匹配，或是结果集列数据类型所支持的隐式转换。 变量的数目必须与游标选择列表中的列数一致。  
  
## <a name="remarks"></a>注释  
 如果 SCROLL 选项未在 ISO 样式的 DECLARE CURSOR 语句中指定，则 NEXT 是唯一支持的 FETCH 选项。 如果在 ISO 样式的 DECLARE CURSOR 语句中指定了 SCROLL 选项，则支持所有 FETCH 选项。  
  
 如果使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] DECLARE 游标扩展插件，则应用下列规则：  
  
-   如果指定了 FORWARD_ONLY 或 FAST_FORWARD，则 NEXT 是唯一受支持的 FETCH 选项。  
  
-   如果未指定 DYNAMIC、FORWARD_ONLY 或 FAST_FORWARD 选项，并且指定了 KEYSET、STATIC 或 SCROLL 中的某一个，则支持所有 FETCH 选项。  
  
-   DYNAMIC SCROLL 游标支持除 ABSOLUTE 以外的所有 FETCH 选项。  
  
 @@FETCH_STATUS函数报告的最后一个的 FETCH 语句的状态。 相同的信息记录在由 sp_describe_cursor 返回的游标中的 fetch_status 列中。 这些状态信息应该用于在对由 FETCH 语句返回的数据进行任何操作之前，以确定这些数据的有效性。 有关详细信息，请参阅[@@FETCH_STATUS &#40;Transact SQL &#41;](../../t-sql/functions/fetch-status-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 FETCH 权限默认授予任何有效的用户。  
  
## <a name="examples"></a>示例  
  
### <a name="a-using-fetch-in-a-simple-cursor"></a>A. 在简单的游标中使用 FETCH  
 以下示例为 `Person.Person` 表中姓氏以字母 `B` 开头的行声明了一个简单的游标，并使用 `FETCH NEXT` 逐个提取这些行。 `FETCH` 语句以单行结果集形式返回在 `DECLARE CURSOR` 中指定的列的值。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE contact_cursor CURSOR FOR  
SELECT LastName FROM Person.Person  
WHERE LastName LIKE 'B%'  
ORDER BY LastName;  
  
OPEN contact_cursor;  
  
-- Perform the first fetch.  
FETCH NEXT FROM contact_cursor;  
  
-- Check @@FETCH_STATUS to see if there are any more rows to fetch.  
WHILE @@FETCH_STATUS = 0  
BEGIN  
   -- This is executed as long as the previous fetch succeeds.  
   FETCH NEXT FROM contact_cursor;  
END  
  
CLOSE contact_cursor;  
DEALLOCATE contact_cursor;  
GO  
```  
  
### <a name="b-using-fetch-to-store-values-in-variables"></a>B. 使用 FETCH 将值存入变量  
 以下示例与示例 A 相似，但 `FETCH` 语句的输出存储于局部变量而不是直接返回到客户端。 `PRINT` 语句将变量组合成单一字符串并将其返回到客户端。  
  
```  
USE AdventureWorks2012;  
GO  
-- Declare the variables to store the values returned by FETCH.  
DECLARE @LastName varchar(50), @FirstName varchar(50);  
  
DECLARE contact_cursor CURSOR FOR  
SELECT LastName, FirstName FROM Person.Person  
WHERE LastName LIKE 'B%'  
ORDER BY LastName, FirstName;  
  
OPEN contact_cursor;  
  
-- Perform the first fetch and store the values in variables.  
-- Note: The variables are in the same order as the columns  
-- in the SELECT statement.   
  
FETCH NEXT FROM contact_cursor  
INTO @LastName, @FirstName;  
  
-- Check @@FETCH_STATUS to see if there are any more rows to fetch.  
WHILE @@FETCH_STATUS = 0  
BEGIN  
  
   -- Concatenate and display the current values in the variables.  
   PRINT 'Contact Name: ' + @FirstName + ' ' +  @LastName  
  
   -- This is executed as long as the previous fetch succeeds.  
   FETCH NEXT FROM contact_cursor  
   INTO @LastName, @FirstName;  
END  
  
CLOSE contact_cursor;  
DEALLOCATE contact_cursor;  
GO  
```  
  
### <a name="c-declaring-a-scroll-cursor-and-using-the-other-fetch-options"></a>C. 声明 SCROLL 游标并使用其他 FETCH 选项  
 以下示例创建一个 `SCROLL` 游标，使其通过 `LAST`、`PRIOR`、`RELATIVE` 和 `ABSOLUTE` 选项支持全部滚动功能。  
  
```  
USE AdventureWorks2012;  
GO  
-- Execute the SELECT statement alone to show the   
-- full result set that is used by the cursor.  
SELECT LastName, FirstName FROM Person.Person  
ORDER BY LastName, FirstName;  
  
-- Declare the cursor.  
DECLARE contact_cursor SCROLL CURSOR FOR  
SELECT LastName, FirstName FROM Person.Person  
ORDER BY LastName, FirstName;  
  
OPEN contact_cursor;  
  
-- Fetch the last row in the cursor.  
FETCH LAST FROM contact_cursor;  
  
-- Fetch the row immediately prior to the current row in the cursor.  
FETCH PRIOR FROM contact_cursor;  
  
-- Fetch the second row in the cursor.  
FETCH ABSOLUTE 2 FROM contact_cursor;  
  
-- Fetch the row that is three rows after the current row.  
FETCH RELATIVE 3 FROM contact_cursor;  
  
-- Fetch the row that is two rows prior to the current row.  
FETCH RELATIVE -2 FROM contact_cursor;  
  
CLOSE contact_cursor;  
DEALLOCATE contact_cursor;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [关闭 &#40;Transact SQL &#41;](../../t-sql/language-elements/close-transact-sql.md)   
 [释放 &#40;Transact SQL &#41;](../../t-sql/language-elements/deallocate-transact-sql.md)   
 [DECLARE CURSOR (Transact-SQL)](../../t-sql/language-elements/declare-cursor-transact-sql.md)   
 [打开 &#40;Transact SQL &#41;](../../t-sql/language-elements/open-transact-sql.md)  
  
  