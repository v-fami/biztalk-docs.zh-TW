---
title: "Siebel 商務元件上執行 SELECT 查詢 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performing operations, selecting data using ADO.NET provider
- how to, select data in business components using ADO.NET provider
ms.assetid: 34a22c2e-6fc9-4760-90a1-131a38ae947b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 92b9bd5645579bb66a338c05802c5016214c9b0b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="run-a-select-query-on-business-components-with-siebel"></a><span data-ttu-id="2829e-102">Siebel 商務元件上執行 SELECT 查詢</span><span class="sxs-lookup"><span data-stu-id="2829e-102">Run a SELECT Query on Business Components with Siebel</span></span>
<span data-ttu-id="2829e-103">本節示範如何從 Siebel 商務元件使用選取的資料[!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2829e-103">This section demonstrates how to select data from a Siebel business component using the [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)].</span></span>  
  
## <a name="selecting-data-from-a-siebel-business-component"></a><span data-ttu-id="2829e-104">選取 Siebel 商務元件中的資料</span><span class="sxs-lookup"><span data-stu-id="2829e-104">Selecting Data from a Siebel Business Component</span></span>  
 <span data-ttu-id="2829e-105">本節示範如何從 Siebel 儲存機制中的 「 帳戶 」 商務元件選取資料。</span><span class="sxs-lookup"><span data-stu-id="2829e-105">This section demonstrates how to select data from the "Account" business component in the Siebel repository.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Data.Common;  
using Microsoft.Adapters.SiebelDbProvider;  
  
namespace SiebelADO  
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
  
         //Here is a list of sample commands. The second command shows how the Siebel ViewMode can be specified in the query.  
         //command.CommandText = "SELECT * from Account.Account where [Name] LIKE '3Com'";  
         //command.CommandText = "Select [Name] from [Account].[Account] where [Name] LIKE '3Com' OPTION ‘ViewMode 1’";  
           command.CommandText = "SELECT [Name], [Postal Code], Id From Account.Account where [Postal Code] != '60626' Order BY Id ASC, Name DESC";  
  
         DbDataReader dbReader = command.ExecuteReader();  
  
         while (dbReader.Read())  
           {  
              for (int i = 0; i < dbReader.FieldCount; i++)  
               {  
                 string name = dbReader.GetName(i);  
                 string val = dbReader[i].ToString();  
                 Console.WriteLine(name + "\t:" + val);  
                 Console.WriteLine("=========================");  
               }  
           }  
             Console.WriteLine("Press any key...");  
             Console.ReadLine();  
       }  
       catch (Exception exp) { Console.WriteLine(exp.Message); }  
       }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2829e-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2829e-106">See Also</span></span>  
 <span data-ttu-id="2829e-107">[使用.NET Framework Data Provider for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md) </span><span class="sxs-lookup"><span data-stu-id="2829e-107">[Use the .NET Framework Data Provider for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md) </span></span>  
 [<span data-ttu-id="2829e-108">執行與 Siebel 商務服務上的執行作業</span><span class="sxs-lookup"><span data-stu-id="2829e-108">Run an EXECUTE Operation on Business Services with Siebel</span></span>](../../adapters-and-accelerators/adapter-siebel/run-an-execute-operation-on-business-services-with-siebel.md)