---
title: "setDate 方法为日期和日历的 int |Microsoft 文档"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerPreparedStatement.setDate (int, java.sql.Date, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2c46f694-6dc4-429f-a037-a3bad369a7c8
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8bcfae333d5adcd665e480b1f06e17ba170f51f7
ms.contentlocale: zh-cn
ms.lasthandoff: 09/09/2017

---
# <a name="setdate-method-int-javasqldate-javautilcalendar"></a>setDate 方法 (int, java.sql.Date, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  将指定参数设置为给定的日期和日历值。  
  
## <a name="syntax"></a>语法  
  
```  
  
public final void setDate(int n,  
                          java.sql.Date x,  
                          java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Parameters  
 *n*  
  
 **Int** ，该值指示参数号。  
  
 *x*  
  
 Date 对象。  
  
 *cal*  
  
 日历对象中。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>注释  
 SetDate 方法 java.sql.PreparedStatement 界面中指定此 setDate 方法。  
  
## <a name="see-also"></a>另请参阅  
 [setDate 方法 &#40;SQLServerPreparedStatement &#41;](../../../connect/jdbc/reference/setdate-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement 成员](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement 类](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  