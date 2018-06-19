---
title: 完成使用 WCF 服務模型的 Oracle 資料庫中的大型資料類型的資料表作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF service model, performing operations on tables and views
- how to, invoke the ReadLOB and UpdateLOB operations
ms.assetid: 5d0e84d3-7ffa-47c7-aaf2-a1007f7a71a2
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88ae5a616e71e27a4d6fa8cd27473665f7bc96b3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215606"
---
# <a name="complete-operations-on-tables-with-large-data-types-in-oracle-database-using-the-wcf-service-model"></a><span data-ttu-id="68d28-102">完成資料表的作業與使用 WCF 服務模型的 Oracle 資料庫中的大型資料類型</span><span class="sxs-lookup"><span data-stu-id="68d28-102">Complete operations on tables with large data types in Oracle Database using the WCF service model</span></span>
<span data-ttu-id="68d28-103">本節包含如何叫用的 ReadLOB 和 UpdateLOB 作業從 WCF 服務模型的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="68d28-103">This section contains information about how to invoke the ReadLOB and UpdateLOB operations from the WCF service model.</span></span> <span data-ttu-id="68d28-104">ReadLOB 和 UpdateLOB 作業便會顯示資料表和檢視表包含 LOB 資料行。這是用來儲存 Oracle 大型物件 (LOB) 資料的資料行。</span><span class="sxs-lookup"><span data-stu-id="68d28-104">The ReadLOB and UpdateLOB operations are surfaced for tables and views that contain LOB columns; that is columns that are used to store Oracle large object (LOB) data.</span></span> <span data-ttu-id="68d28-105">如需所支援的 Oracle LOB 資料類型的概觀[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]和 ReadLOB 和 UpdateLOB 作業，請參閱[資料表和檢視表，包含 LOB 資料 Oracle 資料庫中的作業](../../adapters-and-accelerators/adapter-oracle-database/operations-on-tables-and-views-that-contain-lob-data-in-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="68d28-105">For an overview of the Oracle LOB data types supported by the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] and of the ReadLOB and UpdateLOB operations, see [Operations on Tables and Views That Contain LOB Data in Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/operations-on-tables-and-views-that-contain-lob-data-in-oracle-database.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="68d28-106">LOB 資料行可以包含大量的資料，最多為 4 gb (GB)。</span><span class="sxs-lookup"><span data-stu-id="68d28-106">LOB data columns can contain large amounts of data—up to 4 gigabytes (GB).</span></span> <span data-ttu-id="68d28-107">使用 WCF 用戶端操作 LOB 資料行上的是重要的限制是 WCF 服務模型只支援資料流在 ReadLOB 作業，不能在 UpdateLOB 作業。</span><span class="sxs-lookup"><span data-stu-id="68d28-107">A significant limitation of using a WCF client to operate on LOB columns is that the WCF service model only supports data streaming on the ReadLOB operation, not on the UpdateLOB operation.</span></span> <span data-ttu-id="68d28-108">這是因為 WCF 要求進行串流處理從服務模型、 串流處理參數都必須在其方向的唯一參數。</span><span class="sxs-lookup"><span data-stu-id="68d28-108">This is because WCF requires that for streaming to work from service model, the parameter to be streamed must be the only parameter in its direction.</span></span> <span data-ttu-id="68d28-109">UpdateLOB 作業有兩個其他 IN 參數 （資料行名稱和資料列篩選） 除了 LOB 資料;基於這個理由，資料流不支援在 WCF 服務模型中。</span><span class="sxs-lookup"><span data-stu-id="68d28-109">The UpdateLOB operation has two other IN parameters (a column name and row filter) in addition to the LOB data; for this reason, streaming is not supported on it in the WCF service model.</span></span> <span data-ttu-id="68d28-110">因此，如果您要使用大量的資料來更新 LOB 資料行，您可以使用 WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="68d28-110">Therefore, if you are updating a LOB column with a large amount of data, you might want to use the WCF channel model.</span></span> <span data-ttu-id="68d28-111">如需有關如何使用 WCF 通道模型的資料流使用 UpdateLOB 作業的 LOB 資料的詳細資訊，請參閱[串流處理 Oracle LOB 資料類型使用的 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md)。</span><span class="sxs-lookup"><span data-stu-id="68d28-111">For more information on how to use the WCF channel model to stream LOB data using the UpdateLOB operation, see [Streaming Oracle LOB Data Types by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="68d28-112">關於本主題中使用的範例</span><span class="sxs-lookup"><span data-stu-id="68d28-112">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="68d28-113">本主題中的範例使用 /SCOTT/CUSTOMER 資料表。</span><span class="sxs-lookup"><span data-stu-id="68d28-113">The examples in this topic use the /SCOTT/CUSTOMER table.</span></span> <span data-ttu-id="68d28-114">此資料表包含名為相片的 BLOB 資料行。指令碼來產生這個資料表所提供的 SDK 範例。</span><span class="sxs-lookup"><span data-stu-id="68d28-114">This table contains a BLOB column named PHOTO.A script to generate this table is supplied with the SDK samples.</span></span> <span data-ttu-id="68d28-115">如需 SDK 範例的詳細資訊，請參閱[SDK 中的範例](../../core/samples-in-the-sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="68d28-115">For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="68d28-116">WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="68d28-116">The WCF Client Class</span></span>  
 <span data-ttu-id="68d28-117">下列範例會示範 ReadLOB 和 UpdateLOB 作業 /SCOTT/CUSTOMER 資料表上產生 WCF 用戶端類別的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="68d28-117">The following example shows the method signatures for a WCF client class generated for the ReadLOB and UpdateLOB operations on the /SCOTT/CUSTOMER table.</span></span>  
  
```  
public partial class SCOTTTableCUSTOMERClient : System.ServiceModel.ClientBase<SCOTTTableCUSTOMER>,   
                                                SCOTTTableCUSTOMER   
{  
    public System.IO.Stream ReadLOB(string LOB_COLUMN, string FILTER);   
  
    public void UpdateLOB(string LOB_COLUMN, string FILTER, byte[] Stream);  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="68d28-118">請注意， **ReadLOB**傳回資料流，但**UpdateLOB**不會在資料流上運作。</span><span class="sxs-lookup"><span data-stu-id="68d28-118">Note that **ReadLOB** returns a data stream, but that **UpdateLOB** does not operate on a stream.</span></span>  
  
## <a name="invoking-the-readlob-and-updatelob-operations"></a><span data-ttu-id="68d28-119">叫用的 ReadLOB 和 UpdateLOB 作業</span><span class="sxs-lookup"><span data-stu-id="68d28-119">Invoking the ReadLOB and UpdateLOB Operations</span></span>  
 <span data-ttu-id="68d28-120">這兩個**ReadLOB**和**UpdateLOB**方法可以只在單一資料庫的資料列的單一 LOB 資料行上操作。</span><span class="sxs-lookup"><span data-stu-id="68d28-120">Both the **ReadLOB** and **UpdateLOB** methods can operate only on a single LOB column in a single database row.</span></span> <span data-ttu-id="68d28-121">您設定下列參數來識別目標資料行/資料列。</span><span class="sxs-lookup"><span data-stu-id="68d28-121">You set the following parameters to identify the target column/row.</span></span>  
  
|<span data-ttu-id="68d28-122">參數</span><span class="sxs-lookup"><span data-stu-id="68d28-122">Parameter</span></span>|<span data-ttu-id="68d28-123">定義</span><span class="sxs-lookup"><span data-stu-id="68d28-123">Definition</span></span>|  
|---------------|----------------|  
|<span data-ttu-id="68d28-124">LOB_COLUMN</span><span class="sxs-lookup"><span data-stu-id="68d28-124">LOB_COLUMN</span></span>|<span data-ttu-id="68d28-125">在篩選參數; 所識別的資料列中的目標資料行名稱例如，「 相片。 」</span><span class="sxs-lookup"><span data-stu-id="68d28-125">The name of the target column within the row identified by the FILTER parameter; for example, "PHOTO".</span></span>|  
|<span data-ttu-id="68d28-126">FILTER</span><span class="sxs-lookup"><span data-stu-id="68d28-126">FILTER</span></span>|<span data-ttu-id="68d28-127">SQL SELECT 陳述式 WHERE 子句，指定目標資料列，其中的內容例如，「 名稱 =' 張彥 ' 」。</span><span class="sxs-lookup"><span data-stu-id="68d28-127">The contents of a SQL SELECT statement WHERE clause that specifies the target row; for example, "NAME='Kim Ralls'".</span></span> <span data-ttu-id="68d28-128">篩選條件必須指定一個並只有一個資料列。</span><span class="sxs-lookup"><span data-stu-id="68d28-128">The filter must specify one and only one row.</span></span> <span data-ttu-id="68d28-129">如果篩選條件符合多個資料列：</span><span class="sxs-lookup"><span data-stu-id="68d28-129">If the filter matches more than one row:</span></span><br /><br /> <span data-ttu-id="68d28-130">-   **ReadLOB**傳回第一個相符的資料列的 LOB 資料。</span><span class="sxs-lookup"><span data-stu-id="68d28-130">-   **ReadLOB** returns LOB data for the first matching row.</span></span><br /><span data-ttu-id="68d28-131">-   **UpdateLOB**擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="68d28-131">-   **UpdateLOB** throws an exception.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="68d28-132">傳回的資料流**ReadLOB**不支援**搜尋**。</span><span class="sxs-lookup"><span data-stu-id="68d28-132">The stream returned by **ReadLOB** does not support **Seek**.</span></span> <span data-ttu-id="68d28-133">這表示屬性，例如**長度**不支援，可能是。</span><span class="sxs-lookup"><span data-stu-id="68d28-133">This means that properties such as **Length** are not supported, either.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="68d28-134">**UpdateLOB**作業必須在交易範圍內執行。</span><span class="sxs-lookup"><span data-stu-id="68d28-134">The **UpdateLOB** operation must be performed within a transaction scope.</span></span> <span data-ttu-id="68d28-135">此外， **UseAmbientTransaction**繫結屬性必須設定為**true**執行之前**UpdateLOB**作業。</span><span class="sxs-lookup"><span data-stu-id="68d28-135">Also, the **UseAmbientTransaction** binding property must be set to **true** before performing the **UpdateLOB** operation.</span></span>  
  
 <span data-ttu-id="68d28-136">下列程式碼會示範如何使用 WCF 用戶端，以更新 BLOB 相片中的資料行 /SCOTT/CUSTOMER 表格，從檔案和讀取檔案到新的資料行資料。</span><span class="sxs-lookup"><span data-stu-id="68d28-136">The following code shows how to use a WCF client to update the BLOB PHOTO column in the /SCOTT/CUSTOMER table from a file and read the new column data back to a file.</span></span> <span data-ttu-id="68d28-137">SDK 範例中，您可以找到完整的範例。</span><span class="sxs-lookup"><span data-stu-id="68d28-137">You can find a full sample in the SDK samples.</span></span> <span data-ttu-id="68d28-138">如需 SDK 範例的詳細資訊，請參閱[SDK 中的範例](../../core/samples-in-the-sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="68d28-138">For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Transaction;  
  
// Include for file streaming  
using System.IO;  
  
// Add WCF, WCF LOB Adapter SDK, and Oracle Database adapter namepaces  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
// Include this namespace for the WCF channel model  
using System.ServiceModel.Channels;  
  
// Include this namespace for the WCF LOB Adapter SDK and Oracle Database adapter exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
using CustomerTablens = microsoft.lobservices.oracledb._2007._03;  
  
namespace OracleLobOpsSnippetSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            try  
            {  
                OracleDBBinding binding = new OracleDBBinding();  
                binding.UseAmbientTransaction = true; //set this to true for UpdateLOB operation  
  
                EndpointAddress endpointAddress = new EndpointAddress("oracleDB://ADAPTER");  
  
                using (SCOTTTableCUSTOMERClient customerTableClient =  
                    new SCOTTTableCUSTOMERClient(binding, endpointAddress))  
                {  
                    customerTableClient.ClientCredentials.UserName.UserName = "SCOTT";  
                    customerTableClient.ClientCredentials.UserName.Password = "TIGER";  
  
                    // Open the client to read the LOB data back  
                    customerTableClient.Open();  
  
                    // Add a photo to the customer record    
                    using (FileStream fs = new FileStream("SamplePhoto.jpg", FileMode.Open))  
                    {  
                        Console.WriteLine("Updating photo");  
                        int count = 0;  
                        byte[] photo = new byte[fs.Length];  
                        while ((count += fs.Read(photo, count, (int) (((fs.Length-count)>4096)? 4096:fs.Length-count))) \< fs.Length) ;  
  
                        // UpdateLOB operation must be performed within a transaction scope  
                        using(TransactionScope tx = new TransactionScope())  
                        {  
                           customerTableClient.UpdateLOB("PHOTO", "NAME='Kim Ralls'", photo);  
                           Console.WriteLine("Photo updated");  
                           tx.Complete();  
                        }  
                    }  
  
                    // Read the data back and store it to another file  
                    using (FileStream fs = new FileStream("PhotoCopy.jpg", FileMode.Create))  
                    {  
                        Console.WriteLine("Reading photo data");  
                        Stream photoStream = customerTableClient.ReadLOB("PHOTO", "NAME='Kim Ralls'");  
                        Console.WriteLine("Photo data read -- writing to PhotoCopy.jpg");  
  
                        int count;  
                        int length = 0;  
                        byte[] buffer = new byte[4096];  
                        while ((count = photoStream.Read(buffer, 0, 4096)) > 0)  
                        {  
                            fs.Write(buffer, 0, count);  
                            length+=count;  
                        }  
                        Console.WriteLine("{0} bytes written to PhotoCopy.jpg", length);  
                    }  
  
                }  
  
                Console.WriteLine("Photo updated and read back -- Hit <RETURN> to end");  
                Console.ReadLine();  
  
            }  
            catch (Exception ex)  
            {  
                // handle exception  
                Console.WriteLine("Exception caught: " + ex.Message);  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="68d28-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68d28-139">See Also</span></span>  
 [<span data-ttu-id="68d28-140">Oracle 資料庫使用開發應用程式的 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="68d28-140">Develop Oracle Database Applications Using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)