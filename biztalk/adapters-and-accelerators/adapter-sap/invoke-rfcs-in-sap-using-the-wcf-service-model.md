---
title: 叫用中使用 WCF 服務模型的 SAP Rfc |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- invoking RFCs, using the WCF service model
- WCF service model, invoking RFCs
ms.assetid: 06a373e2-5d16-4480-81ec-611bd0b9749c
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 991fec074369e774a9eef9ab2ae34f10436c6a4f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973695"
---
# <a name="invoke-rfcs-in-sap-using-the-wcf-service-model"></a><span data-ttu-id="536b8-102">叫用中使用 WCF 服務模型的 SAP Rfc</span><span class="sxs-lookup"><span data-stu-id="536b8-102">Invoke RFCs in SAP using the WCF Service Model</span></span>
<span data-ttu-id="536b8-103">[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]呈現 SAP 系統的 Rfc 做為用戶端程式可以叫用的作業。</span><span class="sxs-lookup"><span data-stu-id="536b8-103">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] surfaces RFCs on the SAP system as operations that can be invoked by a client program.</span></span> <span data-ttu-id="536b8-104">在 WCF 服務模型中，這些作業會叫用做為產生的 WCF 用戶端類別的方法。</span><span class="sxs-lookup"><span data-stu-id="536b8-104">In the WCF service model, these operations are invoked as methods of a generated WCF client class.</span></span> <span data-ttu-id="536b8-105">您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]以產生 WCF 用戶端類別，其中包含您想要叫用程式碼中的每個 rfc 的方法。</span><span class="sxs-lookup"><span data-stu-id="536b8-105">You can use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate a WCF client class that contains methods for each RFC that you want to invoke in your code.</span></span> <span data-ttu-id="536b8-106">[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]也會產生封裝的參數和資料類型所使用的每個 RFC 的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="536b8-106">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates .NET types to encapsulate the parameters and data types that are used by each RFC.</span></span> <span data-ttu-id="536b8-107">接著，您可以建立此 WCF 用戶端類別的執行個體，並呼叫其方法來叫用 Rfc 的目標。</span><span class="sxs-lookup"><span data-stu-id="536b8-107">You can then create an instance of this WCF client class and call its methods to invoke the target RFCs.</span></span>  
  
 <span data-ttu-id="536b8-108">下列各節會說明如何使用 SAP 系統上叫用 Rfc [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="536b8-108">The following sections show you how to invoke RFCs on the SAP system by using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="536b8-109">WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="536b8-109">The WCF Client Class</span></span>  
 <span data-ttu-id="536b8-110">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現所有 RFC 作業的單一服務合約，而 「 Rfc"。</span><span class="sxs-lookup"><span data-stu-id="536b8-110">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces all RFC operations under a single service contract, "Rfc".</span></span> <span data-ttu-id="536b8-111">這表示單一的 WCF 用戶端類別， **RfcClient**，系統會為所有您想要叫用 RFC 作業。</span><span class="sxs-lookup"><span data-stu-id="536b8-111">This means that a single WCF client class, **RfcClient**, is created for all of the RFC operations that you want to invoke.</span></span> <span data-ttu-id="536b8-112">每個 RFC 的目標被以這個類別的方法。</span><span class="sxs-lookup"><span data-stu-id="536b8-112">Each target RFC is represented as a method of this class.</span></span> <span data-ttu-id="536b8-113">在每個方法：</span><span class="sxs-lookup"><span data-stu-id="536b8-113">In each method:</span></span>  
  
- <span data-ttu-id="536b8-114">SAP 匯出參數當成**出**參數</span><span class="sxs-lookup"><span data-stu-id="536b8-114">SAP export parameters are surfaced as **out** parameters</span></span>  
  
- <span data-ttu-id="536b8-115">SAP 變更參數當成**ref**參數。</span><span class="sxs-lookup"><span data-stu-id="536b8-115">SAP changing parameters are surfaced as **ref** parameters.</span></span>  
  
- <span data-ttu-id="536b8-116">複雜的 SAP 類型，例如結構顯示為.NET 類別，其屬性會對應到 SAP 類型的欄位。</span><span class="sxs-lookup"><span data-stu-id="536b8-116">Complex SAP types such as structures are surfaced as .NET classes with properties that correspond to the fields of the SAP type.</span></span> <span data-ttu-id="536b8-117">這些類別定義在下列命名空間： microsoft.lobservices.sap._2007._03.Types.Rfc。</span><span class="sxs-lookup"><span data-stu-id="536b8-117">These classes are defined in the following namespace: microsoft.lobservices.sap._2007._03.Types.Rfc.</span></span>  
  
  <span data-ttu-id="536b8-118">下列程式碼顯示的部分**RfcClient**類別和 SAP 系統叫用 SD_RFC_CUSTOMER_GET 方法。</span><span class="sxs-lookup"><span data-stu-id="536b8-118">The following code shows part of the **RfcClient** class and the method that invokes SD_RFC_CUSTOMER_GET on the SAP system.</span></span>  
  
```  
 [System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class RfcClient : System.ServiceModel.ClientBase<Rfc>, Rfc {  
  
    ...  
  
    /// <summary>The metadata for this RFC was generated using the RFC SDK.</summary>  
    /// <param name="KUNNR">Customer number</param>  
    /// <param name="NAME1">Name of the customer</param>  
    /// <param name="CUSTOMER_T">Table of the selected customers</param>  
    /// <returns></returns>  
    public void SD_RFC_CUSTOMER_GET(string KUNNR, string NAME1, ref microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[] CUSTOMER_T) {...}  
}  
```  
  
## <a name="how-to-create-an-rfc-client-application"></a><span data-ttu-id="536b8-119">如何建立 RFC 用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="536b8-119">How to Create an RFC Client Application</span></span>  
 <span data-ttu-id="536b8-120">若要建立的 RFC 用戶端應用程式，請執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="536b8-120">To create an RFC client application, perform the following steps.</span></span>  
  
#### <a name="to-create-an-rfc-client-application"></a><span data-ttu-id="536b8-121">若要建立的 RFC 用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="536b8-121">To create an RFC client application</span></span>  
  
1. <span data-ttu-id="536b8-122">產生**RfcClient**類別。</span><span class="sxs-lookup"><span data-stu-id="536b8-122">Generate an **RfcClient** class.</span></span> <span data-ttu-id="536b8-123">使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生**RfcClient**為目標的 Rfc，您想要使用的類別。</span><span class="sxs-lookup"><span data-stu-id="536b8-123">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate an **RfcClient** class that targets the RFCs with which you want to work.</span></span> <span data-ttu-id="536b8-124">如需如何產生 WCF 用戶端的詳細資訊，請參閱[SAP 解決方案成品產生 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="536b8-124">For more information about how to generate a WCF client, see [Generate a WCF Client or a WCF Service Contract for SAP Solution Artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span></span>  
  
2. <span data-ttu-id="536b8-125">建立的執行個體**RfcClient**類別中產生的步驟 1，並指定用戶端繫結。</span><span class="sxs-lookup"><span data-stu-id="536b8-125">Create an instance of the **RfcClient** class generated in step 1, and specify a client binding.</span></span> <span data-ttu-id="536b8-126">指定用戶端繫結牽涉到指定的繫結和端點位址**RfcClient**會使用。</span><span class="sxs-lookup"><span data-stu-id="536b8-126">Specifying a client binding involves specifying the binding and endpoint address that the **RfcClient** will use.</span></span> <span data-ttu-id="536b8-127">以命令方式在程式碼或是宣告式組態中，您可以這麼做。</span><span class="sxs-lookup"><span data-stu-id="536b8-127">You can do this either imperatively in code or declaratively in configuration.</span></span> <span data-ttu-id="536b8-128">如需如何指定用戶端繫結的詳細資訊，請參閱[SAP 系統的設定用戶端繫結](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md)。</span><span class="sxs-lookup"><span data-stu-id="536b8-128">For more information about how to specify a client binding, see [Configure a Client Binding for the SAP System](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md).</span></span> <span data-ttu-id="536b8-129">下列程式碼會初始化**RfcClient**組態和設定 SAP 系統的認證。</span><span class="sxs-lookup"><span data-stu-id="536b8-129">The following code initializes the **RfcClient** from configuration and sets the credentials for the SAP system.</span></span>  
  
   ```  
   RfcClient rfcClient = new RfcClient("SAPBinding_Rfc");  
  
   rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
   rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
   ```  
  
3. <span data-ttu-id="536b8-130">開啟 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="536b8-130">Open the WCF client.</span></span>  
  
   ```  
   rfcClient.Open();  
   ```  
  
4. <span data-ttu-id="536b8-131">上叫用方法**RfcClient**在步驟 2 來執行 SAP 系統上的作業中建立。</span><span class="sxs-lookup"><span data-stu-id="536b8-131">Invoke methods on the **RfcClient** created in step 2 to perform operations on the SAP system.</span></span> <span data-ttu-id="536b8-132">下列程式碼會叫用**SD_RFC_CUSTOMER_GET**方法**RfcClient**叫用 RFC，SAP 系統上的。</span><span class="sxs-lookup"><span data-stu-id="536b8-132">The following code invokes the **SD_RFC_CUSTOMER_GET** method of the **RfcClient** to invoke the RFC on the SAP system.</span></span>  
  
   ```  
   microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[] customers =   
       new microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[0];  
  
   rfcClient.SD_RFC_CUSTOMER_GET(string.Empty, "AB*", ref customers);  
   ```  
  
5. <span data-ttu-id="536b8-133">關閉 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="536b8-133">Close the WCF client.</span></span>  
  
   ```  
   rfcClient.Close();   
   ```  
  
### <a name="example"></a><span data-ttu-id="536b8-134">範例</span><span class="sxs-lookup"><span data-stu-id="536b8-134">Example</span></span>  
 <span data-ttu-id="536b8-135">以下是完整的程式碼範例，以叫用傳回一份客戶名稱開頭為"AB"SD_RFC_CUSTOMER_GET 然後的名稱和識別碼將每個客戶的寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="536b8-135">The following is a complete code example that invokes SD_RFC_CUSTOMER_GET to return a list of customers with names that begin with "AB" and then writes the name and ID for each customer to the console.</span></span> <span data-ttu-id="536b8-136">這個範例會建立**RfcClient**內**使用**陳述式。</span><span class="sxs-lookup"><span data-stu-id="536b8-136">This example creates the **RfcClient** inside a **using** statement.</span></span> <span data-ttu-id="536b8-137">若要明確地關閉不需要**RfcClient**; 的執行路徑結束內容時將會關閉。</span><span class="sxs-lookup"><span data-stu-id="536b8-137">There is no need to explicitly close the **RfcClient**; it will be closed when the execution path exits the context.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.SAP;  
  
namespace SapRfcClientSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            try  
            {  
                // Create client from configuration  
                using (RfcClient rfcClient = new RfcClient("SAPBinding_Rfc"))  
                {  
  
                    rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
                    rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
  
                    // Open client  
                    rfcClient.Open();  
  
                    microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[] customers = new microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[0];  
  
                    // Invoke SD_RFC_CUSTOMER_GET  
                    rfcClient.SD_RFC_CUSTOMER_GET(string.Empty, "AB*", ref customers);  
  
                    // Write the results to the console  
                    foreach (microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST customer in customers)  
                    {  
                        Console.WriteLine("Customer Name = " + customer.NAME1);  
                        Console.WriteLine("         Id   = " + customer.KUNNR);  
                        Console.WriteLine();  
                    }  
                }  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine(ex.Message);  
                if (ex.InnerException != null)  
                    Console.WriteLine("Inner exception is :" + ex.InnerException);  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="536b8-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="536b8-138">See Also</span></span>  
<span data-ttu-id="536b8-139">[使用 WCF 服務模型開發應用程式](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md) </span><span class="sxs-lookup"><span data-stu-id="536b8-139">[Develop applications using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md) </span></span>  
 [<span data-ttu-id="536b8-140">RFC 作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="536b8-140">Message Schemas for RFC Operations</span></span>](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)