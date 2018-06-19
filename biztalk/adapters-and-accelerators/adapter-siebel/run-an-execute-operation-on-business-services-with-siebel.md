---
title: 執行與 Siebel 商務服務上的執行作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- how to, execute business services using ADO.NET Provider
- performing operations, executing business services using ADO.NET Provider
ms.assetid: c8f7888f-72c6-4f20-b592-f233721fbddd
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 644d915998e6c6e6f386d30021629f78dc109864
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22221974"
---
# <a name="run-an-execute-operation-on-business-services-with-siebel"></a><span data-ttu-id="a7e5f-102">執行與 Siebel 商務服務上的執行作業</span><span class="sxs-lookup"><span data-stu-id="a7e5f-102">Run an EXECUTE Operation on Business Services with Siebel</span></span>
<span data-ttu-id="a7e5f-103">本節示範如何執行在 Siebel 商務服務使用的作業[!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a7e5f-103">This section demonstrates how to execute an operation on a Siebel business service using the [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)].</span></span>  
  
## <a name="executing-a-siebel-business-service"></a><span data-ttu-id="a7e5f-104">執行 Siebel 商務服務</span><span class="sxs-lookup"><span data-stu-id="a7e5f-104">Executing a Siebel Business Service</span></span>  
 <span data-ttu-id="a7e5f-105">本節示範如何執行 Siebel 儲存機制中的商務服務上的作業。</span><span class="sxs-lookup"><span data-stu-id="a7e5f-105">This section demonstrates how to execute operations on a business service in the Siebel repository.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Data.Common;  
using System.Data;  
using Microsoft.Adapters.SiebelDbProvider;  
  
namespace SiebelADOBS  
{  
 class Program  
  {  
   static void Main(string[] args)  
    {  
      try  
       {  
        SiebelProviderFactory factory = SiebelProviderFactory.Instance;  
        DbConnection connection = factory.CreateConnection();  
        connection.ConnectionString = "Username=SADMIN;Password=SADMIN;ServiceUri=172.23.115.223:2321;SiebelObjectManager=SSEObjMgr;SiebelEnterpriseServer=ent771;Language=enu;SiebelRepository=Siebel Repository";  
  
        connection.Open();  
        DbCommand command = connection.CreateCommand();  
        command.CommandText = "EXEC ExtractDataService.Echo @In, @InOut, @Out OUTPUT";  
  
        //Add @In  
        DbParameter param1 = command.CreateParameter();  
        param1.ParameterName = "@In";  
        param1.Direction = ParameterDirection.Input;  
        param1.Value = "SomethingElse";  
        command.Parameters.Add(param1);  
  
        //Add @InOut  
        DbParameter param2 = command.CreateParameter();  
        param2.ParameterName = "@InOut";  
        param2.Direction = ParameterDirection.InputOutput;  
        command.Parameters.Add(param2);  
  
        //Add @Out  
        DbParameter outParam = command.CreateParameter();  
        outParam.ParameterName = "@Out";  
        outParam.Direction = ParameterDirection.Output;  
        command.Parameters.Add(outParam);  
  
        DbDataReader dbReader = command.ExecuteReader();  
  
        Console.WriteLine("Param2: " + param2.Value);  
        Console.WriteLine("OutParam: " + outParam.Value);  
  
        Console.WriteLine("Press any key...");  
        Console.ReadLine();  
      }  
     catch (Exception exp) { Console.WriteLine(exp.Message); }  
      }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7e5f-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7e5f-106">See Also</span></span>  
 <span data-ttu-id="a7e5f-107">[使用.NET Framework Data Provider for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md) </span><span class="sxs-lookup"><span data-stu-id="a7e5f-107">[Use the .NET Framework Data Provider for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md) </span></span>  
 [<span data-ttu-id="a7e5f-108">Siebel 商務元件上執行 SELECT 查詢</span><span class="sxs-lookup"><span data-stu-id="a7e5f-108">Run a SELECT Query on Business Components with Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/run-a-select-query-on-business-components-with-siebel.md)