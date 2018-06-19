---
title: 執行使用 EXECQUERY 命令 SAP 查詢 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 520153bf-9477-4b35-8953-3f5cb444ab9f
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86159a03858ae5aa31bb37da56b6e5ea68dac3ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217206"
---
# <a name="execute-an-sap-query-using-the-execquery-command"></a><span data-ttu-id="03571-102">執行 SAP 查詢使用 EXECQUERY 命令</span><span class="sxs-lookup"><span data-stu-id="03571-102">Execute an SAP Query Using the EXECQUERY Command</span></span>
<span data-ttu-id="03571-103">[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]公開為 ADO.NET 資料來源的 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="03571-103">The [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] exposes the SAP system as an ADO.NET data source.</span></span> <span data-ttu-id="03571-104">與[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，您也可以執行 EXECQUERY 陳述式在 SAP 系統中執行預先定義的查詢。</span><span class="sxs-lookup"><span data-stu-id="03571-104">With the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], you can execute pre-defined queries in the SAP system by executing an EXECQUERY statement.</span></span>  
  
## <a name="how-to-perform-a-query-by-using-the-execquery-command"></a><span data-ttu-id="03571-105">如何使用 EXECQUERY 命令執行查詢</span><span class="sxs-lookup"><span data-stu-id="03571-105">How to Perform a Query by Using the EXECQUERY Command</span></span>  
 <span data-ttu-id="03571-106">若要執行預先定義的 SAP 查詢使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="03571-106">To execute pre-defined SAP queries using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], perform the following steps:</span></span>  
  
#### <a name="to-perform-a-query"></a><span data-ttu-id="03571-107">若要執行查詢</span><span class="sxs-lookup"><span data-stu-id="03571-107">To perform a query</span></span>  
  
1.  <span data-ttu-id="03571-108">包含的參考 (與您的程式碼中使用陳述式) 以**Microsoft.Data.SAPClient**。</span><span class="sxs-lookup"><span data-stu-id="03571-108">Include a reference (and a using statement in your code) to **Microsoft.Data.SAPClient**.</span></span>  
  
2.  <span data-ttu-id="03571-109">建立**SAPConnection** SAP 連接字串中使用資料提供者的物件。</span><span class="sxs-lookup"><span data-stu-id="03571-109">Create a **SAPConnection** object by using a Data Provider for SAP connection string.</span></span> <span data-ttu-id="03571-110">如需有關連接字串的詳細資訊，請參閱[閱讀 SAP 連接字串的資料提供者類型](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md)。</span><span class="sxs-lookup"><span data-stu-id="03571-110">For more information about the connection string, see [Read about Data Provider types for the SAP Connection String](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).</span></span>  
  
3.  <span data-ttu-id="03571-111">開啟 SAP 系統的連線，藉由叫用**開啟**上**SAPConnection**。</span><span class="sxs-lookup"><span data-stu-id="03571-111">Open a connection to the SAP system by invoking **Open** on the **SAPConnection**.</span></span>  
  
4.  <span data-ttu-id="03571-112">建立**SAPCommand**物件從**SAPConnection**。</span><span class="sxs-lookup"><span data-stu-id="03571-112">Create a **SAPCommand** object from the **SAPConnection**.</span></span>  
  
5.  <span data-ttu-id="03571-113">指定的 EXECQUERY 陳述式中**CommandText**屬性**SAPCommand**。</span><span class="sxs-lookup"><span data-stu-id="03571-113">Specify the EXECQUERY statement in the **CommandText** property of the **SAPCommand**.</span></span> <span data-ttu-id="03571-114">如果有必要，您可以指定參數使用**SAPParameter**物件。</span><span class="sxs-lookup"><span data-stu-id="03571-114">If necessary, you can specify parameters using **SAPParameter** objects.</span></span> <span data-ttu-id="03571-115">如需如何執行 SAP 系統使用 EXECQUERY 陳述式中定義查詢的詳細資訊，請參閱[sap EXECQUERY 陳述式語法](../../adapters-and-accelerators/adapter-sap/syntax-for-an-execquery-statement-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="03571-115">For more information about how to execute queries defined in an SAP system using an EXECQUERY statement, see [Syntax for an EXECQUERY Statement in SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-an-execquery-statement-in-sap.md).</span></span>  
  
6.  <span data-ttu-id="03571-116">執行命令，以執行查詢並取得結果**SAPDataReader**。</span><span class="sxs-lookup"><span data-stu-id="03571-116">Execute the command to perform the query and obtain the results in a **SAPDataReader**.</span></span>  
  
7.  <span data-ttu-id="03571-117">了解從結果**SAPDataReader**。</span><span class="sxs-lookup"><span data-stu-id="03571-117">Read the results from the **SAPDataReader**.</span></span>  
  
8.  <span data-ttu-id="03571-118">當您完成使用它們時，關閉 （或處置） **SAPConnection**和**SAPDataReader**。</span><span class="sxs-lookup"><span data-stu-id="03571-118">When you are finished using them, close (or dispose) the **SAPConnection** and the **SAPDataReader**.</span></span>  
  
 <span data-ttu-id="03571-119">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]也會公開**SAPClientFactory**類別，可用來建立**SAPConnection**， **SAPCommand**和**SAPConnection**物件。</span><span class="sxs-lookup"><span data-stu-id="03571-119">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] also exposes a **SAPClientFactory** class, which you can use to create **SAPConnection**, **SAPCommand** and **SAPConnection** objects.</span></span> <span data-ttu-id="03571-120">如需有關 ADO.NET 類別透過擴充[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，請參閱[擴充 SAP 配接器使用的 ADO.NET 介面](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="03571-120">For more information about the ADO.NET classes extended by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Extend ADO.NET Interfaces with the SAP adapter](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="03571-121">範例</span><span class="sxs-lookup"><span data-stu-id="03571-121">Example</span></span>  
 <span data-ttu-id="03571-122">下列範例會將查詢的結果，ZTEST1，寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="03571-122">The following example writes the results of a query, ZTEST1, to the console.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using Microsoft.Data.SAPClient;  
  
namespace SapAdoExecQuery  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
           string connstr = "TYPE=A; ASHOST=YourSapHost; SYSNR=00; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;";  
           using (SAPConnection conn = new SAPConnection(connstr))  
            {  
                conn.Open();  
                using (SAPCommand cmd = conn.CreateCommand())  
                {  
                    cmd.CommandText = "EXECQUERY ZTEST1 @userGRoup='SYSTQV000024',@P1='0000001390',@P2='0000080150'";  
                    cmd.Parameters.Add(new SAPParameter("@connid", 17));                      
                    using (SAPDataReader dr = cmd.ExecuteReader())  
                    {  
                        do  
                        {  
                            int rows = 0;  
                            while (dr.Read())  
                            {  
                                rows++;  
                                StringBuilder b = new StringBuilder();  
                                for (int i = 0; i < dr.FieldCount; i++)  
                                {  
                                    b.Append(dr[i].ToString()+" ");  
                                }  
                                Console.WriteLine("row {0}: {1} ", rows, b.ToString());  
                            }  
                            Console.WriteLine("Number of rows:{0}", rows);  
                        } while (dr.NextResult());  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="03571-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03571-123">See Also</span></span>  
 [<span data-ttu-id="03571-124">使用.NET Framework Data Provider for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="03571-124">Use the .NET Framework Data Provider for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)  
 [<span data-ttu-id="03571-125">範例</span><span class="sxs-lookup"><span data-stu-id="03571-125">Samples</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)