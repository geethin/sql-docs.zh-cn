---
title: "Reporting Services 中的 SOAP 角色 |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- SOAP [Reporting Services], role in Reporting Services
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: f229c3ef-f2ca-448f-98f1-b8df350b9992
caps.latest.revision: 34
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: d860d17f29ca39fc5df422e616805c8bc040185d
ms.contentlocale: zh-cn
ms.lasthandoff: 06/13/2017

---
# <a name="the-role-of-soap-in-reporting-services"></a>The Role of SOAP in Reporting Services
  报表服务器 Web 服务使用简单对象访问协议 (SOAP) 消息通过网络发送基于文本的命令。 这些命令采用的形式为使用 HTTP 通过万维网发送的 XML 文本。 通过将 SOAP 用作其通信协议，报表服务器 Web 服务使应用程序和组件能够使用开放和广为接受的基础结构与报表服务器交换数据。 SOAP 标准在 www.w3.org/TR/SOAP 中定义。  
  
 对于任何客户端应用程序，只要它识别 SOAP 且可以发送 SOAP 请求，它就可以充当 SOAP 客户端。 报表管理器就是一个此类 SOAP 客户端。 它向报表服务器数据库（其中存储所有报表和与报表相关的内容）提供了一个接口。 每个用户都可以使用此应用程序对报表服务器命名空间中的报表和文件夹进行浏览和管理。 报表管理器建立在报表服务器 Web 服务基础结构之上。  
  
 报表服务器充当 SOAP 服务器，它是一项识别 SOAP 的服务，可以从 SOAP 客户端接受请求并创建适当的响应。 此服务器处理请求并将经过编码的响应发回到客户端。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中的 SOAP 消息采取许多不同的形式，具体取决于客户端发出的请求类型。 以下示例表示一个简单 SOAP 客户端请求，它请求从报表服务器数据库中删除某个项。  
  
```  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <soap:Body>  
        <DeleteItem xmlns="http://www.microsoft.com/sql/ReportingServer">  
            <item>/Samples/Report1</item>  
        </DeleteItem>  
    </soap:Body>  
</soap:Envelope>  
```  
  
 SOAP 本身需要消息会放入**信封**元素，与中的消息批量**正文**元素。 在本示例中，主体包含对于 <xref:ReportService2010.ReportingService2010.DeleteItem%2A> 方法的调用，该方法采用一个表示待删除项的路径的字符串参数。 你可以创建[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]封装到方法的所有 SOAP 操作的客户端代理类。 以下[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[csprcs](../../includes/csprcs-md.md)]方法表示出更早版本的 SOAP 示例。  
  
```  
public void DeleteItem(string item);  
```  
  
 来自服务器的响应可能如下所示：  
  
```  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <soap:Body>  
        <DeleteItemResponse xmlns="http://www.microsoft.com/sql/ReportingServer" />  
    </soap:Body>  
</soap:Envelope>  
```  
  
 <xref:ReportService2010.ReportingService2010.DeleteItem%2A> 方法不具备返回值，因此返回空响应。  
  
## <a name="see-also"></a>另请参阅  
 [访问 SOAP API](../../reporting-services/report-server-web-service/accessing-the-soap-api.md)   
 [报表管理器（SSRS 本机模式）](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)   
 [Reporting Services 报表服务器](../../reporting-services/report-server-sharepoint/reporting-services-report-server.md)   
 [报表服务器 Web 服务](../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  