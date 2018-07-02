---
title: 在 SAP 中使用 SELECT 命令執行查詢 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SELECT command, performing a query
- query, performing by using the SELECT command
ms.assetid: 6f03243c-ef50-4a4a-8fe6-4e525bd7efe3
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5e4edb19c3f69b14dd55219f504a6a3d0cc1688
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971079"
---
# <a name="run-a-query-using-the-select-command-in-sap"></a><span data-ttu-id="a5750-102">在 SAP 中使用 SELECT 命令執行查詢</span><span class="sxs-lookup"><span data-stu-id="a5750-102">Run a Query Using the SELECT Command in SAP</span></span>
<span data-ttu-id="a5750-103">[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]公開為 ADO.NET 資料來源的 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="a5750-103">The [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] exposes the SAP system as an ADO.NET data source.</span></span> <span data-ttu-id="a5750-104">使用[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]，您可以執行 SELECT 陳述式來查詢 SAP 成品。</span><span class="sxs-lookup"><span data-stu-id="a5750-104">With the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)], you can query SAP artifacts by executing a SELECT statement.</span></span>  
  
## <a name="how-to-perform-a-query-by-using-the-select-command"></a><span data-ttu-id="a5750-105">如何使用 SELECT 命令執行查詢</span><span class="sxs-lookup"><span data-stu-id="a5750-105">How to Perform a Query by Using the SELECT Command</span></span>  
 <span data-ttu-id="a5750-106">若要使用的查詢 SAP 成品[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="a5750-106">To query SAP artifacts using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], perform the following steps:</span></span>  
  
#### <a name="to-perform-a-query"></a><span data-ttu-id="a5750-107">若要執行查詢</span><span class="sxs-lookup"><span data-stu-id="a5750-107">To perform a query</span></span>  
  
1. <span data-ttu-id="a5750-108">包含的參考 (和程式碼中使用陳述式) 來**Microsoft.Data.SAPClient**。</span><span class="sxs-lookup"><span data-stu-id="a5750-108">Include a reference (and a using statement in your code) to **Microsoft.Data.SAPClient**.</span></span>  
  
2. <span data-ttu-id="a5750-109">建立**SAPConnection** SAP 連接字串中使用資料提供者的物件。</span><span class="sxs-lookup"><span data-stu-id="a5750-109">Create a **SAPConnection** object by using a Data Provider for SAP connection string.</span></span> <span data-ttu-id="a5750-110">如需有關連接字串的詳細資訊，請參閱 <<c0> [ 閱讀 SAP 連接字串的資料提供者類型](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md)。</span><span class="sxs-lookup"><span data-stu-id="a5750-110">For more information about the connection string, see [Read about Data Provider types for the SAP Connection String](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).</span></span>  
  
3. <span data-ttu-id="a5750-111">開啟 SAP 系統的連線，藉由叫用**開放**上**SAPConnection**。</span><span class="sxs-lookup"><span data-stu-id="a5750-111">Open a connection to the SAP system by invoking **Open** on the **SAPConnection**.</span></span>  
  
4. <span data-ttu-id="a5750-112">建立**SAPCommand**物件**SAPConnection**。</span><span class="sxs-lookup"><span data-stu-id="a5750-112">Create a **SAPCommand** object from the **SAPConnection**.</span></span>  
  
5. <span data-ttu-id="a5750-113">指定的 SELECT 陳述式**CommandText**屬性**SAPCommand**。</span><span class="sxs-lookup"><span data-stu-id="a5750-113">Specify the SELECT statement in the **CommandText** property of the **SAPCommand**.</span></span> <span data-ttu-id="a5750-114">如果有必要，您可以指定使用的參數**SAPParameter**物件。</span><span class="sxs-lookup"><span data-stu-id="a5750-114">If necessary, you can specify parameters using **SAPParameter** objects.</span></span> <span data-ttu-id="a5750-115">如需如何查詢使用 SELECT 陳述式的 SAP 成品的詳細資訊，請參閱[SAP 中的 SELECT 陳述式的語法](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="a5750-115">For more information about how to query SAP artifacts using a SELECT statement, see [Syntax for a SELECT Statement in SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-a-select-statement-in-sap.md).</span></span> <span data-ttu-id="a5750-116">如需如何指定 BAPI 或 RFC 的範例，請參閱[SELECT 陳述式的範例](../../adapters-and-accelerators/adapter-sap/examples-for-select-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="a5750-116">For examples of how to specify a BAPI or RFC, see [Examples for SELECT Statement](../../adapters-and-accelerators/adapter-sap/examples-for-select-statement.md).</span></span>  
  
6. <span data-ttu-id="a5750-117">執行命令，以執行查詢並取得結果**SAPDataReader**。</span><span class="sxs-lookup"><span data-stu-id="a5750-117">Execute the command to perform the query and obtain the results in a **SAPDataReader**.</span></span>  
  
7. <span data-ttu-id="a5750-118">讀取從結果**SAPDataReader**。</span><span class="sxs-lookup"><span data-stu-id="a5750-118">Read the results from the **SAPDataReader**.</span></span>  
  
8. <span data-ttu-id="a5750-119">當您完成使用它們時，關閉 （或 dispose） **SAPConnection**並**SAPDataReader**。</span><span class="sxs-lookup"><span data-stu-id="a5750-119">When you are finished using them, close (or dispose) the **SAPConnection** and the **SAPDataReader**.</span></span>  
  
   <span data-ttu-id="a5750-120">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]也會公開**SAPClientFactory**類別，可用來建立**SAPConnection**， **SAPCommand**和**SAPConnection**物件。</span><span class="sxs-lookup"><span data-stu-id="a5750-120">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] also exposes a **SAPClientFactory** class, which you can use to create **SAPConnection**, **SAPCommand** and **SAPConnection** objects.</span></span> <span data-ttu-id="a5750-121">如需有關 ADO.NET 類別來擴充[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，請參閱 <<c2> [ 與 SAP 配接器擴充 ADO.NET 介面](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="a5750-121">For more information about the ADO.NET classes extended by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Extend ADO.NET Interfaces with the SAP adapter](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5750-122">範例</span><span class="sxs-lookup"><span data-stu-id="a5750-122">Example</span></span>  
 <span data-ttu-id="a5750-123">下列範例會寫入至主控台的參數化的內部聯結陳述式的 select 的結果。</span><span class="sxs-lookup"><span data-stu-id="a5750-123">The following example writes the results of a select on a parameterized inner join statement to the console.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using Microsoft.Data.SAPClient;  
  
namespace SapAdoSelect  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
        /// <summary>  
        /// select top 1 * from sflight inner join spfli on sflight.connid = spfli.connid where spfli.connid = @connid  
        /// </summary>  
  
        string connstr = "TYPE=A; ASHOST=YourSapHost; SYSNR=00; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;";  
  
           using (SAPConnection conn = new SAPConnection(connstr))  
            {  
                conn.Open();  
                using (SAPCommand cmd = conn.CreateCommand())  
                {  
                    cmd.CommandText = "select top 1 * from sflight inner join spfli on sflight.connid = spfli.connid where spfli.connid = @connid";  
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
  
## <a name="see-also"></a><span data-ttu-id="a5750-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5750-124">See Also</span></span>  
 <span data-ttu-id="a5750-125">[使用.NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md) </span><span class="sxs-lookup"><span data-stu-id="a5750-125">[Use the .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md) </span></span>  
 [<span data-ttu-id="a5750-126">範例</span><span class="sxs-lookup"><span data-stu-id="a5750-126">Samples</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)