---
title: SAP 配接器之 WCF 服務模型的概觀 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF service model, overview of using
ms.assetid: 02a4b43e-ade0-4dba-b8f6-074bca7cbe5c
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da5b2f7cc8e38eb8afd211a2008c0f740760cd4f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22218566"
---
# <a name="overview-of-the-wcf-service-model-with-the-sap-adapter"></a><span data-ttu-id="436de-102">SAP 配接器之 WCF 服務模型的概觀</span><span class="sxs-lookup"><span data-stu-id="436de-102">Overview of the WCF service model with the SAP adapter</span></span>
<span data-ttu-id="436de-103">當您使用作業的[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]介面，您的程式碼做為用戶端或服務給配接器。</span><span class="sxs-lookup"><span data-stu-id="436de-103">When you consume operations that the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] surfaces, your code acts either as a client or a service to the adapter.</span></span>  
  
 <span data-ttu-id="436de-104">您的程式碼做為用戶端來叫用下列種類的 SAP 系統上的作業：</span><span class="sxs-lookup"><span data-stu-id="436de-104">Your code acts as a client to invoke the following kinds of operations on the SAP system:</span></span>  
  
-   <span data-ttu-id="436de-105">叫用的遠端函式呼叫 (RFC)。</span><span class="sxs-lookup"><span data-stu-id="436de-105">Invoke a Remote Function Call (RFC).</span></span>  
  
-   <span data-ttu-id="436de-106">叫用交易式遠端函式呼叫 (tRFC)。</span><span class="sxs-lookup"><span data-stu-id="436de-106">Invoke a Transactional Remote Function Call (tRFC).</span></span>  
  
-   <span data-ttu-id="436de-107">叫用商務應用程式開發介面 」 (BAPI)。</span><span class="sxs-lookup"><span data-stu-id="436de-107">Invoke a Business Application Programming Interface (BAPI).</span></span>  
  
-   <span data-ttu-id="436de-108">傳送的中繼文件 (IDOC)</span><span class="sxs-lookup"><span data-stu-id="436de-108">Send an Intermediate Document (IDOC)</span></span>  
  
 <span data-ttu-id="436de-109">您的程式碼做為服務以接收下列種類的作業：</span><span class="sxs-lookup"><span data-stu-id="436de-109">Your code acts as a service to receive the following kinds of operations:</span></span>  
  
-   <span data-ttu-id="436de-110">接收的 RFC （RFC 伺服器）</span><span class="sxs-lookup"><span data-stu-id="436de-110">Receive an RFC (RFC server)</span></span>  
  
-   <span data-ttu-id="436de-111">接收 tRFC （tRFC 伺服器）</span><span class="sxs-lookup"><span data-stu-id="436de-111">Receive a tRFC (tRFC server)</span></span>  
  
-   <span data-ttu-id="436de-112">接收 IDOC。</span><span class="sxs-lookup"><span data-stu-id="436de-112">Receive an IDOC.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="436de-113">由於 Bapi 位於商務物件儲存機制 (BOR) 中的商務物件上的 SAP 系統所公開的方法，您就無法接收 Bapi。</span><span class="sxs-lookup"><span data-stu-id="436de-113">Because BAPIs are methods exposed by the SAP system on business objects located in the Business Object Repository (BOR), you cannot receive BAPIs.</span></span>  
  
 <span data-ttu-id="436de-114">在[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型時，用戶端和服務之間存在的服務合約以.NET 介面和作業會表示為此介面上的方法。</span><span class="sxs-lookup"><span data-stu-id="436de-114">In the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] service model, the service contract that exists between a client and a service is represented as a .NET interface, and operations are represented as methods on this interface.</span></span> <span data-ttu-id="436de-115">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]和 WCF 提供的工具，可讓您從配接器會公開的中繼資料產生此介面為目標的作業。</span><span class="sxs-lookup"><span data-stu-id="436de-115">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] and WCF provide tools that enable you to generate this interface for targeted operations from the metadata that the adapter exposes.</span></span> <span data-ttu-id="436de-116">這些工具也會建立 WCF 用戶端類別，可用於叫用的服務介面中公開的作業。</span><span class="sxs-lookup"><span data-stu-id="436de-116">These tools also create a WCF client class that can be used to invoke the operations exposed in the service interface.</span></span> <span data-ttu-id="436de-117">用戶端應用程式可以呼叫 WCF 用戶端類別，來叫用的介面卡上的作業的方法。</span><span class="sxs-lookup"><span data-stu-id="436de-117">A client application can call the methods of the WCF client class to invoke operations on the adapter.</span></span> <span data-ttu-id="436de-118">若要實作接收作業中的從服務[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，實作目標作業產生的介面。</span><span class="sxs-lookup"><span data-stu-id="436de-118">To implement a service to receive operations from the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], you implement the interface generated for the target operation.</span></span>  
  
 <span data-ttu-id="436de-119">下列各節說明如何使用 WCF 服務模型來建立用戶端和服務的程式碼[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="436de-119">The following sections explain how to use the WCF service model to create client and service code for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="creating-a-wcf-client-and-invoking-operations-on-sap"></a><span data-ttu-id="436de-120">建立 WCF 用戶端和叫用 SAP 的作業</span><span class="sxs-lookup"><span data-stu-id="436de-120">Creating a WCF Client and Invoking Operations on SAP</span></span>  
 <span data-ttu-id="436de-121">若要使用 WCF 服務模型上叫用作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，您必須先產生目標作業的 WCF 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="436de-121">To use the WCF service model to invoke operations on the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], you must first generate a WCF client class for the target operations.</span></span> <span data-ttu-id="436de-122">然後，您可以建立 WCF 用戶端，這個類別的執行個體，並呼叫其方法來執行 SAP 系統上的作業。</span><span class="sxs-lookup"><span data-stu-id="436de-122">You can then create an instance of this class, a WCF client, and call its methods to perform operations on the SAP system.</span></span>  
  
#### <a name="to-invoke-operations-on-the-sap-adapter"></a><span data-ttu-id="436de-123">若要 SAP 配接器上叫用作業</span><span class="sxs-lookup"><span data-stu-id="436de-123">To invoke operations on the SAP adapter</span></span>  
  
1.  <span data-ttu-id="436de-124">產生 WCF 用戶端類別和協助程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="436de-124">Generate a WCF client class and helper code.</span></span> <span data-ttu-id="436de-125">使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生 WCF 用戶端類別為目標的 SAP 系統成品想要使用。</span><span class="sxs-lookup"><span data-stu-id="436de-125">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF client class targeted at the SAP system artifacts with which you want to work.</span></span> <span data-ttu-id="436de-126">如需如何產生 WCF 用戶端的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SAP 方案成品](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="436de-126">For more information about how to generate a WCF client, see [Generate a WCF client or a WCF service contract for SAP solution artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span></span>  
  
2.  <span data-ttu-id="436de-127">指定用戶端繫結，以建立 WCF 用戶端執行個體。</span><span class="sxs-lookup"><span data-stu-id="436de-127">Create a WCF client instance by specifying a client binding.</span></span> <span data-ttu-id="436de-128">指定用戶端繫結牽涉到指定的繫結和 WCF 用戶端會使用的端點位址。</span><span class="sxs-lookup"><span data-stu-id="436de-128">Specifying a client binding involves specifying the binding and endpoint address that the WCF client will use.</span></span> <span data-ttu-id="436de-129">您可以在程式碼中以命令方式或是宣告式組態。</span><span class="sxs-lookup"><span data-stu-id="436de-129">You can do this either imperatively in code or declaratively in configuration.</span></span> <span data-ttu-id="436de-130">如需如何指定用戶端繫結的詳細資訊，請參閱[SAP 系統的繫結的用戶端設定](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md)。</span><span class="sxs-lookup"><span data-stu-id="436de-130">For more information about how to specify a client binding, see [Configure a client binding for the SAP system](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md).</span></span> <span data-ttu-id="436de-131">下列程式碼會建立 WCF 用戶端可以用來叫用的 RFC，SAP 系統上。</span><span class="sxs-lookup"><span data-stu-id="436de-131">The following code creates a WCF client that can be used to invoke an RFC on the SAP system.</span></span> <span data-ttu-id="436de-132">它也會設定為 SAP 系統的認證。</span><span class="sxs-lookup"><span data-stu-id="436de-132">It also sets the credentials for the SAP system.</span></span> <span data-ttu-id="436de-133">WCF 用戶端會從設定初始化。</span><span class="sxs-lookup"><span data-stu-id="436de-133">The WCF client is initialized from configuration.</span></span>  
  
    ```  
    RfcClient rfcClient = new RfcClient("SAPBinding_Rfc");  
  
    rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
    rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
    ```  
  
3.  <span data-ttu-id="436de-134">開啟 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="436de-134">Open the WCF client.</span></span>  
  
    ```  
    rfcClient.Open();  
    ```  
  
4.  <span data-ttu-id="436de-135">叫用 WCF 用戶端上步驟 2 中建立 SAP 系統上執行作業的方法。</span><span class="sxs-lookup"><span data-stu-id="436de-135">Invoke methods on the WCF client created in step 2 to perform operations on the SAP system.</span></span> <span data-ttu-id="436de-136">下列程式碼會叫用**SD_RFC_CUSTOMER_GET** WCF 用戶端來叫用的 RFC，SAP 系統上的方法。</span><span class="sxs-lookup"><span data-stu-id="436de-136">The following code invokes the **SD_RFC_CUSTOMER_GET** method of the WCF client to invoke the RFC on the SAP system.</span></span>  
  
    ```  
    microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[] customers =   
        new microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[0];  
  
    rfcClient.SD_RFC_CUSTOMER_GET(string.Empty, "AB*", ref customers);  
    ```  
  
5.  <span data-ttu-id="436de-137">關閉 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="436de-137">Close the WCF client.</span></span>  
  
    ```  
    rfcClient.Close();  
  
    ```  
  
## <a name="creating-and-implementing-a-wcf-service-by-using-the-sap-adapter"></a><span data-ttu-id="436de-138">建立和使用 SAP 配接器實作 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="436de-138">Creating and Implementing a WCF Service by Using the SAP Adapter</span></span>  
 <span data-ttu-id="436de-139">若要使用 WCF 服務模型來接收作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，您必須先產生代表服務合約所公開的.NET 介面 （也稱為 WCF 服務合約）[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]作業。</span><span class="sxs-lookup"><span data-stu-id="436de-139">To use the WCF service model to receive operations from the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], you must first generate the .NET interface (also called the WCF service contract) that represents the service contract exposed by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] for the operation.</span></span> <span data-ttu-id="436de-140">如需如何執行這項操作的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SAP 方案成品](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="436de-140">For more information about how to do this, see [Generate a WCF client or a WCF service contract for SAP solution artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span></span>  
  
 <span data-ttu-id="436de-141">然後，您會實作 WCF 服務實作產生的介面。</span><span class="sxs-lookup"><span data-stu-id="436de-141">You then implement a WCF service by implementing the generated interface.</span></span> <span data-ttu-id="436de-142">這個類別包含商務邏輯來處理作業，並傳回至配接器的回應。</span><span class="sxs-lookup"><span data-stu-id="436de-142">This class contains the business logic to process the operation and return a response to the adapter.</span></span> <span data-ttu-id="436de-143">然後使用服務主機 (**system.servicemodel.servicehost 內**) 來裝載此服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="436de-143">Then you use a service host (**System.ServiceModel.ServiceHost**) to host an instance of this service.</span></span>  
  
#### <a name="to-create-and-implement-a-wcf-service"></a><span data-ttu-id="436de-144">若要建立及實作 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="436de-144">To create and implement a WCF service</span></span>  
  
1.  <span data-ttu-id="436de-145">產生 WCF 服務合約和協助程式類別。</span><span class="sxs-lookup"><span data-stu-id="436de-145">Generate a WCF service contract and helper classes.</span></span> <span data-ttu-id="436de-146">使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或 svcutil.exe 產生 WCF 服務合約 （介面） 為目標的想要使用的 SAP 系統成品。</span><span class="sxs-lookup"><span data-stu-id="436de-146">Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or svcutil.exe to generate a WCF service contract (interface) targeted at the SAP system artifacts with which you want to work.</span></span> <span data-ttu-id="436de-147">如需如何產生 WCF 用戶端的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SAP 方案成品](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="436de-147">For more information about how to generate a WCF client, see [Generate a WCF client or a WCF service contract for SAP solution artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span></span>  
  
2.  <span data-ttu-id="436de-148">實作 WCF 服務，從步驟 1 中所產生的介面和協助程式類別。</span><span class="sxs-lookup"><span data-stu-id="436de-148">Implement a WCF service from the interface and helper classes generated in step 1.</span></span> <span data-ttu-id="436de-149">如果處理作業的資料發生錯誤，處理該作業的方法可以擲回例外狀況傳回錯誤給 SAP 系統。否則此方法必須傳回作業的適當 （產生） 的回應類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="436de-149">If an error is encountered processing the data for the operation, the method that handles that operation can throw an exception to return a fault to the SAP system; otherwise the method must return an instance of the appropriate (generated) response class for the operation.</span></span> <span data-ttu-id="436de-150">您必須屬性 WCF 服務類別，如下所示：</span><span class="sxs-lookup"><span data-stu-id="436de-150">You must attribute the WCF service class as follows:</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    ```  
  
    1.  <span data-ttu-id="436de-151">如果您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生介面，您可以直接在適當的方法，在產生實作您的邏輯**SAPBindingService**類別。</span><span class="sxs-lookup"><span data-stu-id="436de-151">If you used the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate the interface, you can implement your logic directly in the appropriate method in the generated **SAPBindingService** class.</span></span> <span data-ttu-id="436de-152">這個類別可以 SAPBindingService.cs 中找到。</span><span class="sxs-lookup"><span data-stu-id="436de-152">This class can be found in SAPBindingService.cs.</span></span> <span data-ttu-id="436de-153">下列程式碼的子類別**SAPBindingService**類別。</span><span class="sxs-lookup"><span data-stu-id="436de-153">The following code sub-classes the **SAPBindingService** class.</span></span>  
  
        ```  
        [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single,UseSynchronizationContext = false)]  
        class RfcServerClass : SAPBindingNamespace.SAPBindingService  
        {  
            public override Z_RFC_MKD_ADDResponse Z_RFC_MKD_ADD(Z_RFC_MKD_ADDRequest request)  
            {  
                // If either parameter is null throw an exception   
                if (request.X == null || request.Y == null)  
                    throw new System.ArgumentNullException();  
  
                // Add the two operands  
                int result = (int) (request.X + request.Y);  
  
                return new Z_RFC_MKD_ADDResponse(result);  
            }  
        }  
        ```  
  
    2.  <span data-ttu-id="436de-154">如果您使用 svcutil.exe 來產生介面時，您必須建立實作介面的類別，並在這個類別的 appropriatemethod 中實作您的邏輯。</span><span class="sxs-lookup"><span data-stu-id="436de-154">If you used svcutil.exe to generate the interface, you must create a class that implements the interface and implement your logic in the appropriatemethod of this class.</span></span>  
  
3.  <span data-ttu-id="436de-155">建立在步驟 2 中建立的 WCF 服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="436de-155">Create an instance of the WCF service created in step 2.</span></span>  
  
    ```  
    // create service instance  
    RfcServerClass rfcServerInstance = new RfcServerClass();  
    ```  
  
4.  <span data-ttu-id="436de-156">建立的執行個體**system.servicemodel.servicehost 內**使用 WCF 服務和基底的連線 URI。</span><span class="sxs-lookup"><span data-stu-id="436de-156">Create an instance of **System.ServiceModel.ServiceHost** by using the WCF service and a base connection URI.</span></span> <span data-ttu-id="436de-157">基底的連線 URI 不能包含 userinfoparams 或 query_string。</span><span class="sxs-lookup"><span data-stu-id="436de-157">The base connection URI cannot contain userinfoparams or a query_string.</span></span>  
  
    ```  
    // Enable service host  
    Uri[] baseUri = new Uri[] { new Uri("sap://a/YourSAPHost/00") };  
    ServiceHost srvHost = new ServiceHost(pollingInstance, baseUri);  
    ```  
  
5.  <span data-ttu-id="436de-158">建立**SAPBinding**並將它設定為作業設定其繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="436de-158">Create an **SAPBinding** and configure it for the operation by setting its binding properties.</span></span> <span data-ttu-id="436de-159">您可以在程式碼中明確或是宣告式組態。</span><span class="sxs-lookup"><span data-stu-id="436de-159">You can do this either explicitly in code or declaratively in configuration.</span></span> <span data-ttu-id="436de-160">最少，您必須設定**AcceptCredentialsInUri**至**true**。</span><span class="sxs-lookup"><span data-stu-id="436de-160">At a minimum, you must set **AcceptCredentialsInUri** to **true**.</span></span>  
  
    ```  
    // Create and configure a binding for the service endpoint. NOTE: binding  
    // parameters are set here for clarity, but these are already set in the  
    // the generated configuration file  
    SAPBinding binding = new SAPBinding();  
  
    // The credentials are included in the connection URI, so set this property to true  
    binding.AcceptCredentialsInUri = true;  
    ```  
  
6.  <span data-ttu-id="436de-161">將服務端點加入至服務主機。</span><span class="sxs-lookup"><span data-stu-id="436de-161">Add a service endpoint to the service host.</span></span> <span data-ttu-id="436de-162">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="436de-162">To do this:</span></span>  
  
    -   <span data-ttu-id="436de-163">使用步驟 5 中建立的繫結。</span><span class="sxs-lookup"><span data-stu-id="436de-163">Use the binding created in step 5.</span></span>  
  
    -   <span data-ttu-id="436de-164">指定連線 URI，其中包含的認證，並指定接聽程式連接 （SAP 閘道，閘道服務和程式識別碼） query_string 中。</span><span class="sxs-lookup"><span data-stu-id="436de-164">Specify a connection URI that contains credentials and specifies a listener connection (SAP gateway, gateway service and program ID) in the query_string.</span></span> <span data-ttu-id="436de-165">如需有關 SAP 連線 URI 的詳細資訊，請參閱[建立 SAP 系統連接 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="436de-165">For more information about the SAP connection URI, see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span>  
  
    -   <span data-ttu-id="436de-166">指定服務合約。</span><span class="sxs-lookup"><span data-stu-id="436de-166">Specify the service contract.</span></span> <span data-ttu-id="436de-167">這是表示的 WCF 服務合約介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="436de-167">This is the name of the interface that represents the WCF service contract.</span></span> <span data-ttu-id="436de-168">Rfc，對於"Rfc"。</span><span class="sxs-lookup"><span data-stu-id="436de-168">For RFCs, it is "Rfc".</span></span>  
  
    ```  
    // Add service endpoint   
    // NOTE: The contract for the service endpoint is "Rfc".  
    //       This is the generated WCF service contract (interface) -- see SAPBindingInterface.cs.  
    Uri serviceUri = new Uri("sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?ListenerGwServ=SAPGW00&ListenerGwHost=YourSapHost&ListenerProgramId=SAPAdapter");  
    srvHost.AddServiceEndpoint("Rfc", binding, serviceUri);  
    ```  
  
7.  <span data-ttu-id="436de-169">若要從 SAP 系統接收作業，開啟服務主機。</span><span class="sxs-lookup"><span data-stu-id="436de-169">To receive the operation from the SAP system, open the service host.</span></span> <span data-ttu-id="436de-170">SAP 系統會叫用程式 ID 和系統服務 URI，在步驟 6 中所指定的作業時，會叫用您的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="436de-170">Your WCF service will be invoked whenever the SAP system invokes the operation on the program ID and system specified in the service URI in step 6.</span></span>  
  
    ```  
    // Open the service host to begin receiving the operation.  
    srvHost.Open();  
    ```  
  
8.  <span data-ttu-id="436de-171">若要停止接收作業，關閉服務主機。</span><span class="sxs-lookup"><span data-stu-id="436de-171">To stop receiving the operation, close the service host.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="436de-172">配接器會繼續接收作業，直到關閉服務主機。</span><span class="sxs-lookup"><span data-stu-id="436de-172">The adapter will continue to receive the operation until the service host is closed.</span></span> <span data-ttu-id="436de-173">當您不再想要接收作業時，您應該一律關閉服務主機。</span><span class="sxs-lookup"><span data-stu-id="436de-173">You should always close the service host when you no longer want to receive the operation.</span></span>  
  
    ```  
    srvHost.Close();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="436de-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="436de-174">See Also</span></span>  
[<span data-ttu-id="436de-175">開發使用 WCF 服務模型的 SAP 應用程式</span><span class="sxs-lookup"><span data-stu-id="436de-175">Develop SAP applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)