---
title: "叫用中使用 WCF 服務模型的 SAP tRFCs |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tRFCs, invoking by using the WCF service model
- WCF service model, invoking tRFCs
ms.assetid: 456fa869-2f1a-42e0-adbf-86bfe0876846
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f23ee3e863318c9d75be9136e7b7fc0fa37b921
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-trfcs-in-sap-using-the-wcf-service-model"></a><span data-ttu-id="cf233-102">叫用 tRFCs SAP 使用 WCF 服務模型中</span><span class="sxs-lookup"><span data-stu-id="cf233-102">Invoke tRFCs in SAP using the WCF Service Model</span></span>
<span data-ttu-id="cf233-103">交易式遠端函式呼叫 (tRFCs) 保證*單次*RFC，SAP 系統上執行。</span><span class="sxs-lookup"><span data-stu-id="cf233-103">Transactional Remote Function Calls (tRFCs) guarantee a *one-time* execution of an RFC on an SAP system.</span></span> <span data-ttu-id="cf233-104">您可以叫用任何由顯示 Rfc [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] tRFC 為。</span><span class="sxs-lookup"><span data-stu-id="cf233-104">You can invoke any of the RFCs surfaced by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] as a tRFC.</span></span> <span data-ttu-id="cf233-105">叫用 WCF 服務模型中的 tRFC 是類似於叫用的 RFC 具有下列差異：</span><span class="sxs-lookup"><span data-stu-id="cf233-105">Invoking a tRFC in the WCF service model is similar to invoking an RFC with the following differences:</span></span>  
  
-   <span data-ttu-id="cf233-106">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現 tRFCs 的不同節點下 (TRFC) 比 Rfc 建議 (RFC)。</span><span class="sxs-lookup"><span data-stu-id="cf233-106">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces tRFCs under a different node (TRFC) than RFCs (RFC).</span></span>  
  
-   <span data-ttu-id="cf233-107">tRFC 用戶端呼叫不會傳回 SAP 匯出並變更參數的值。</span><span class="sxs-lookup"><span data-stu-id="cf233-107">tRFC client calls do not return values for SAP export and changing parameters.</span></span>  
  
-   <span data-ttu-id="cf233-108">tRFC 作業包括對應至 SAP 交易識別碼 (TID) 的 GUID 參數的由 tRFC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cf233-108">tRFC operations include a GUID parameter that is mapped to the SAP transaction ID (TID) for the tRFC by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
-   <span data-ttu-id="cf233-109">您叫用 tRFC 之後，您必須叫用確認 （認可） 上的 SAP 系統 tRFC RfcConfirmTransID 操作。</span><span class="sxs-lookup"><span data-stu-id="cf233-109">After you invoke a tRFC, you must invoke the RfcConfirmTransID operation to confirm (commit) the tRFC on the SAP system.</span></span> <span data-ttu-id="cf233-110">這項作業會直接在 TRFC 節點下顯示。</span><span class="sxs-lookup"><span data-stu-id="cf233-110">This operation is surfaced directly under the TRFC node.</span></span>  
  
 <span data-ttu-id="cf233-111">如需 tRFC 作業和 RfcConfirmTransID 作業的詳細資訊，請參閱[tRFCs SAP 中的作業](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="cf233-111">For more information about tRFC operations and the RfcConfirmTransID operation, see [Operations on tRFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).</span></span>  
  
 <span data-ttu-id="cf233-112">下列章節將示範如何使用叫用 SAP 系統上的 tRFCs [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cf233-112">The following sections show you how to invoke tRFCs on the SAP system by using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="cf233-113">WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="cf233-113">The WCF Client Class</span></span>  
 <span data-ttu-id="cf233-114">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現所有 tRFC 作業的單一服務合約，"Trfc"。</span><span class="sxs-lookup"><span data-stu-id="cf233-114">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces all tRFC operations under a single service contract, "Trfc".</span></span> <span data-ttu-id="cf233-115">這表示單一的 WCF 用戶端類別， **TrfcClient**，建立所有您想要叫用的 tRFC 作業。</span><span class="sxs-lookup"><span data-stu-id="cf233-115">This means that a single WCF client class, **TrfcClient**, is created for all of the tRFC operations that you want to invoke.</span></span> <span data-ttu-id="cf233-116">每個目標 tRFC 被以這個類別的方法。</span><span class="sxs-lookup"><span data-stu-id="cf233-116">Each target tRFC is represented as a method of this class.</span></span> <span data-ttu-id="cf233-117">每個方法：</span><span class="sxs-lookup"><span data-stu-id="cf233-117">For each method:</span></span>  
  
-   <span data-ttu-id="cf233-118">複雜的 SAP 類型，例如結構顯示為.NET 類別有屬性對應至 SAP 類型的欄位。</span><span class="sxs-lookup"><span data-stu-id="cf233-118">Complex SAP types such as structures are surfaced as .NET classes with properties that correspond to the fields of the SAP type.</span></span> <span data-ttu-id="cf233-119">這些類別會定義下列命名空間中： **microsoft.lobservices.sap._2007._03.Types.Rfc**。</span><span class="sxs-lookup"><span data-stu-id="cf233-119">These classes are defined in the following namespace: **microsoft.lobservices.sap._2007._03.Types.Rfc**.</span></span>  
  
 <span data-ttu-id="cf233-120">下列程式碼顯示部分**TrfcClient**類別和 SAP 系統叫用 BAPI_SALESORDER_CREATEFROMDAT2 （做為 tRFC) 的方法。</span><span class="sxs-lookup"><span data-stu-id="cf233-120">The following code shows part of the **TrfcClient** class and the method that invokes BAPI_SALESORDER_CREATEFROMDAT2 (as a tRFC) on the SAP system.</span></span> <span data-ttu-id="cf233-121">**TransactionalRfcOperationIdentifier**參數會包含對應至 SAP TID 的 GUID。</span><span class="sxs-lookup"><span data-stu-id="cf233-121">The **TransactionalRfcOperationIdentifier** parameter contains the GUID that is mapped to the SAP TID.</span></span> <span data-ttu-id="cf233-122">不是所有方法的參數都會顯示。</span><span class="sxs-lookup"><span data-stu-id="cf233-122">Not all of the parameters to the method are shown.</span></span>  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class TrfcClient : System.ServiceModel.ClientBase<Trfc>, Trfc {  
  
    ....  
  
    /// <summary>The Metadata for this RFC was generated using the RFC SDK.</summary>  
    public void BAPI_SALESORDER_CREATEFROMDAT2(  
                string BEHAVE_WHEN_ERROR,   
                string BINARY_RELATIONSHIPTYPE,   
                string CONVERT,   
                string INT_NUMBER_ASSIGNMENT,   
                microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDLS LOGIC_SWITCH,   
                microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDHD1 ORDER_HEADER_IN,   
  
                …  
  
               microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIADDR1[] PARTNERADDRESSES,   
                microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIRET2[] RETURN,   
                ref System.Guid TransactionalRfcOperationIdentifier) { ...  }  
}  
```  
  
 <span data-ttu-id="cf233-123">下列程式碼會示範 RfcConfirmTransID 作業所產生的方法。</span><span class="sxs-lookup"><span data-stu-id="cf233-123">The following code shows the method that is generated for the RfcConfirmTransID operation.</span></span> <span data-ttu-id="cf233-124">您必須確定此方法會產生一部分**TrfcClient**。</span><span class="sxs-lookup"><span data-stu-id="cf233-124">You must ensure that this method is generated as part of the **TrfcClient**.</span></span> <span data-ttu-id="cf233-125">RfcConfirmTransID 作業會直接在 TRFC 節點下顯示。</span><span class="sxs-lookup"><span data-stu-id="cf233-125">The RfcConfirmTransID operation is surfaced directly under the TRFC node.</span></span>  
  
```  
public void RfcConfirmTransID(System.Guid TransactionalRfcOperationIdentifier) {…}  
```  
  
## <a name="how-to-create-a-trfc-client-application"></a><span data-ttu-id="cf233-126">如何建立 tRFC 用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="cf233-126">How to Create a tRFC Client Application</span></span>  
 <span data-ttu-id="cf233-127">建立會叫用 tRFCs 的應用程式的步驟如下的步驟類似您遵循下列的例外狀況以叫用 Rfc，：</span><span class="sxs-lookup"><span data-stu-id="cf233-127">The steps to create an application that invokes tRFCs are similar to the steps you follow to invoke RFCs, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="cf233-128">您必須擷取 TRFC 節點下的目標作業。</span><span class="sxs-lookup"><span data-stu-id="cf233-128">You must retrieve the target operations under the TRFC node.</span></span>  
  
-   <span data-ttu-id="cf233-129">您必須擷取 RfcConfirmTransID 作業。</span><span class="sxs-lookup"><span data-stu-id="cf233-129">You must retrieve the RfcConfirmTransID operation.</span></span> <span data-ttu-id="cf233-130">這會顯示一個 TRFC 節點正下方。</span><span class="sxs-lookup"><span data-stu-id="cf233-130">This is surfaced directly under the TRFC node.</span></span>  
  
-   <span data-ttu-id="cf233-131">若要確認 （認可） 上的 SAP 系統的 tRFC 作業，您必須叫用該 tRFC 作業傳回的 GUID RfcConfirmTransID 操作。</span><span class="sxs-lookup"><span data-stu-id="cf233-131">To confirm (commit) a tRFC operation on the SAP system, you must invoke the RfcConfirmTransID operation with the GUID that was returned for that tRFC operation.</span></span>  
  
#### <a name="to-create-a-trfc-client-application"></a><span data-ttu-id="cf233-132">若要建立一個 tRFC 用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="cf233-132">To create a tRFC client application</span></span>  
  
1.  <span data-ttu-id="cf233-133">產生**TrfcClient**類別。</span><span class="sxs-lookup"><span data-stu-id="cf233-133">Generate a **TrfcClient** class.</span></span> <span data-ttu-id="cf233-134">使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生**TrfcClient**為目標的 Rfc，您要使用的類別。</span><span class="sxs-lookup"><span data-stu-id="cf233-134">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a **TrfcClient** class that targets the RFCs with which you want to work.</span></span> <span data-ttu-id="cf233-135">如需如何產生 WCF 用戶端的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約為 SAP 方案成品](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="cf233-135">For more information about how to generate a WCF client, see [Generate a WCF Client or a WCF Service Contract for SAP solution Artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span></span> <span data-ttu-id="cf233-136">請確定 RfcConfirmTransID 作業是否包含在**TrfcClient**類別。</span><span class="sxs-lookup"><span data-stu-id="cf233-136">Ensure that the RfcConfirmTransID operation is included in the **TrfcClient** class.</span></span>  
  
2.  <span data-ttu-id="cf233-137">建立的執行個體**TrfcClient**步驟 1 中所產生類別，並指定用戶端繫結。</span><span class="sxs-lookup"><span data-stu-id="cf233-137">Create an instance of the **TrfcClient** class generated in step 1 and specify a client binding.</span></span> <span data-ttu-id="cf233-138">指定用戶端繫結牽涉到指定的繫結和端點位址， **TrfcClient**將會使用。</span><span class="sxs-lookup"><span data-stu-id="cf233-138">Specifying a client binding involves specifying the binding and endpoint address that the **TrfcClient** will use.</span></span> <span data-ttu-id="cf233-139">您可以在程式碼中以命令方式或是宣告式組態。</span><span class="sxs-lookup"><span data-stu-id="cf233-139">You can do this either imperatively in code or declaratively in configuration.</span></span> <span data-ttu-id="cf233-140">如需如何指定用戶端繫結的詳細資訊，請參閱[SAP 系統設定用戶端繫結](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md)。</span><span class="sxs-lookup"><span data-stu-id="cf233-140">For more information about how to specify a client binding, see [Configure a Client Binding for the SAP System](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md).</span></span> <span data-ttu-id="cf233-141">下列程式碼會初始化**TrfcClient**來自組態和集合 SAP 系統的認證。</span><span class="sxs-lookup"><span data-stu-id="cf233-141">The following code initializes the **TrfcClient** from configuration and sets the credentials for the SAP system.</span></span>  
  
    ```  
    TrfcClient trfcClient = new TrfcClient("SAPBinding_Rfc");  
  
    trfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
    trfcClient.ClientCredentials.UserName.Password = "YourPassword";  
    ```  
  
3.  <span data-ttu-id="cf233-142">開啟**TrfcClient**。</span><span class="sxs-lookup"><span data-stu-id="cf233-142">Open the **TrfcClient**.</span></span>  
  
    ```  
    trfcClient.Open();  
    ```  
  
4.  <span data-ttu-id="cf233-143">在上叫用適當的方法**TrfcClient**在步驟 2 來叫用目標 tRFC SAP 系統上的建立。</span><span class="sxs-lookup"><span data-stu-id="cf233-143">Invoke the appropriate method on the **TrfcClient** created in step 2 to invoke the target tRFC on the SAP system.</span></span> <span data-ttu-id="cf233-144">您可以將傳遞的變數，其中包含一個 GUID，或包含空的 GUID **TransactionalRrcOperationIdentifier**參數。</span><span class="sxs-lookup"><span data-stu-id="cf233-144">You can pass a variable that contains a GUID or that contains an empty GUID for the **TransactionalRrcOperationIdentifier** parameter.</span></span> <span data-ttu-id="cf233-145">如果您要傳入空的 GUID，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會為您產生一個。</span><span class="sxs-lookup"><span data-stu-id="cf233-145">If you pass an empty GUID, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] generates one for you.</span></span> <span data-ttu-id="cf233-146">下列程式碼中，會叫用 BAPI_SALESORDER_CREATEFROMDAT2 為 tRFC （顯示並非所有方法的參數） 的 SAP 系統上。</span><span class="sxs-lookup"><span data-stu-id="cf233-146">The following code invokes BAPI_SALESORDER_CREATEFROMDAT2 as a tRFC on the SAP system (not all parameters to the method are shown).</span></span> <span data-ttu-id="cf233-147">指定的 GUID。</span><span class="sxs-lookup"><span data-stu-id="cf233-147">A GUID is specified.</span></span>  
  
    ```  
    transactionalRfcOperationIdentifier = Guid.NewGuid();  
  
    //invoke RFC_CUSTOMER_GET as a tRFC  
    trfcClient.BAPI_SALESORDER_CREATEFROMDAT2(  
                                    request.BEHAVE_WHEN_ERROR,  
                                    request.BINARY_RELATIONSHIPTYPE,  
                                    request.CONVERT,  
  
                                    ...  
  
                                    ref transactionalRfcOperationIdentifier);  
    ```  
  
5.  <span data-ttu-id="cf233-148">若要確認 TID 與 SAP 系統上 tRFC 相關聯，叫用**RfcConfirmTransID**方法**TrfcClient**。</span><span class="sxs-lookup"><span data-stu-id="cf233-148">To confirm the TID associated with the tRFC on the SAP system, invoke the **RfcConfirmTransID** method on the **TrfcClient**.</span></span> <span data-ttu-id="cf233-149">指定步驟 4 中傳回 GUID **TransactionRfcOperationIdentifier**參數。</span><span class="sxs-lookup"><span data-stu-id="cf233-149">Specify the GUID returned in step 4 for the **TransactionRfcOperationIdentifier**parameter.</span></span>  
  
    ```  
    trfcClient.RfcConfirmTransID(transactionalRfcOperationIdentifier);  
    ```  
  
6.  <span data-ttu-id="cf233-150">關閉**TrfcClient**完成時 （您完成後，叫用所有 tRFCs） 使用它。</span><span class="sxs-lookup"><span data-stu-id="cf233-150">Close the **TrfcClient** when you are done using it (after you have finished invoking all tRFCs).</span></span>  
  
    ```  
    trfcClient.Close();   
    ```  
  
### <a name="example"></a><span data-ttu-id="cf233-151">範例</span><span class="sxs-lookup"><span data-stu-id="cf233-151">Example</span></span>  
 <span data-ttu-id="cf233-152">下列範例會示範如何叫用為 tRFC BAPI_SALESORDER_CREATE。</span><span class="sxs-lookup"><span data-stu-id="cf233-152">The following example shows how to invoke BAPI_SALESORDER_CREATE as a tRFC.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add WCF, the WCF LOB Adapter SDK, and SAP adapter namepaces  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
  
// Include this namespace for WCF LOB Adapter SDK and SAP exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
using microsoft.lobservices.sap._2007._03.Types.Rfc;  
  
// This example demonstrates sending BAPI_SALESORDER_CREATEFROMDAT2 as a tRFC. The client has   
// methods to:  
//      send the BAPI (BAPI_SALESORDER_CREATEFROMDAT2)and to  
//      Confirm the transaction (RfcConfirmTransID)  
// An instance of BAPI_SALESORDER_CREATEFROMDAT2Request (generated)   
// is used to format the BAPI before invoking BAPI_SALESORDER_CREATEFROMDAT2. This   
// is not necessary, but is done to make it easier to read the code.  
// tRFC invocations always includes a ref parameter that contains a GUID. You can optionally   
// set this parameter when you invoke the method; however, you must use the value returned by  
// the adapter when you call RfcConfirmTransID to confirm the transaction on the SAP system.   
// You can call the utility method, SAPAdapterUtilities.ConvertGuidToTid, to get the value  
// of the SAP transaction Id from the GUID that the adapter returns.  
namespace SapTrfcClientSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            TrfcClient sapTrfcClient = null;  
  
            try  
            {  
                Console.WriteLine("SAP TRFC client sample started");  
                Console.WriteLine("Creating the TRFC client");  
                // Create the SAP Trfc Client from configuration  
                sapTrfcClient = new TrfcClient("SAPBinding_Trfc");  
                sapTrfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
                sapTrfcClient.ClientCredentials.UserName.Password = "YourPassword";  
  
                Console.WriteLine("Opening the TRFC client");  
                // Open the Trfc Client  
                sapTrfcClient.Open();  
  
                // Create a GUID -- note: this is optional. If you do not pass a GUID,  
                // for the TransactionalRfcOperationIdentifier parameter, the SAP adapter will   
                // generate one, associate it with the SAP TID, and set the   
                // TransactionalRfcOperationIdentifier parameter.  
                Guid tidGuid = Guid.NewGuid();  
  
                BAPI_SALESORDER_CREATEFROMDAT2Request request = new BAPI_SALESORDER_CREATEFROMDAT2Request();  
  
                request.ORDER_HEADER_IN = new BAPISDHD1();  
                request.ORDER_HEADER_IN.DOC_TYPE = "TA";  
                request.ORDER_HEADER_IN.SALES_ORG = "1000";  
                request.ORDER_HEADER_IN.DISTR_CHAN = "10";  
                request.ORDER_HEADER_IN.DIVISION = "00";  
                request.ORDER_HEADER_IN.SALES_OFF = "1000";  
                request.ORDER_HEADER_IN.REQ_DATE_H = DateTime.Now;  
                request.ORDER_HEADER_IN.PURCH_DATE = DateTime.Now;  
                request.ORDER_HEADER_IN.PURCH_NO_C = "Cust PO";  
                request.ORDER_HEADER_IN.CURRENCY = "EUR";  
  
                BAPISDITM[] orderItems = new BAPISDITM[1];  
                orderItems[0] = new BAPISDITM();  
                orderItems[0].MATERIAL = "P-109";  
                orderItems[0].PLANT = "1000";  
                orderItems[0].TARGET_QU = "ST";  
                request.ORDER_ITEMS_IN = orderItems;  
  
                BAPIPARNR[] orderPartners = new BAPIPARNR[1];  
                orderPartners[0] = new microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIPARNR();  
                orderPartners[0].PARTN_ROLE = "AG";  
                orderPartners[0].PARTN_NUMB = "0000001390";  
                request.ORDER_PARTNERS = orderPartners;  
  
                // Create a GUID -- note: this is optional. If you do not pass a GUID,  
                // for the TransactionalRfcOperationIdentifier parameter, the SAP adapter will   
                // generate one, associate it with the SAP TID, and set the   
                // TransactionalRfcOperationIdentifier parameter.  
                request.TransactionalRfcOperationIdentifier = Guid.NewGuid();  
  
                Console.WriteLine("Invoking BAPI_SALESORDER_CREATEFROMDAT2 as a tRFC");  
  
                //invoke RFC_CUSTOMER_GET as a tRFC  
                sapTrfcClient.BAPI_SALESORDER_CREATEFROMDAT2(request.BEHAVE_WHEN_ERROR,  
                                                                request.BINARY_RELATIONSHIPTYPE,  
                                                                request.CONVERT,  
                                                                request.INT_NUMBER_ASSIGNMENT,  
                                                                request.LOGIC_SWITCH,  
                                                                request.ORDER_HEADER_IN,  
                                                                request.ORDER_HEADER_INX,  
                                                                request.SALESDOCUMENTIN,  
                                                                request.SENDER,  
                                                                request.TESTRUN,  
                                                                request.EXTENSIONIN,  
                                                                request.ORDER_CCARD,  
                                                                request.ORDER_CFGS_BLOB,  
                                                                request.ORDER_CFGS_INST,  
                                                                request.ORDER_CFGS_PART_OF,  
                                                                request.ORDER_CFGS_REF,  
                                                                request.ORDER_CFGS_REFINST,  
                                                                request.ORDER_CFGS_VALUE,  
                                                                request.ORDER_CFGS_VK,  
                                                                request.ORDER_CONDITIONS_IN,  
                                                                request.ORDER_CONDITIONS_INX,  
                                                                request.ORDER_ITEMS_IN,  
                                                                request.ORDER_ITEMS_INX,  
                                                                request.ORDER_KEYS,  
                                                                request.ORDER_PARTNERS,  
                                                                request.ORDER_SCHEDULES_IN,  
                                                                request.ORDER_SCHEDULES_INX,  
                                                                request.ORDER_TEXT,  
                                                                request.PARTNERADDRESSES,  
                                                                request.RETURN,  
                                                                ref request.TransactionalRfcOperationIdentifier);  
  
                string sapTxId = null;  
                sapTxId = SAPAdapterUtilities.ConvertGuidToTid(request.TransactionalRfcOperationIdentifier);  
  
                Console.WriteLine("BAPI_SALESORDER_CREATEFROMDAT2 Sent");  
                Console.WriteLine("The SAP Transaction Id is " + sapTxId);  
  
                // Invoke the RfcConfirmTransID method to confirm (commit) the transaction on  
                // the SAP system. This step is required to complete the transaction. The SAP  
                // adapter will always return a TranactionalRfcOperationIdentifier, whether   
                // one was supplied in the call or not.  
                sapTrfcClient.RfcConfirmTransID(request.TransactionalRfcOperationIdentifier);  
  
                Console.WriteLine("SAP Transaction {0} has been committed", sapTxId);  
  
                Console.WriteLine("\nHit <RETURN> to end");  
                Console.ReadLine();  
  
            }  
            catch (ConnectionException cex)  
            {  
                Console.WriteLine("Exception occurred connecting to the SAP system");  
                Console.WriteLine(cex.InnerException.Message);  
                throw;  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                }  
                throw;  
            }  
            finally  
            {  
                // Close the client  
                if (sapTrfcClient != null)  
                {  
                    if (sapTrfcClient.State == CommunicationState.Opened)  
                        sapTrfcClient.Close();  
                    else  
                        sapTrfcClient.Abort();  
                }  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf233-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf233-153">See Also</span></span>  
<span data-ttu-id="cf233-154">[開發應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md) </span><span class="sxs-lookup"><span data-stu-id="cf233-154">[Develop applications using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md) </span></span>  
 [<span data-ttu-id="cf233-155">TRFCs SAP 中的作業</span><span class="sxs-lookup"><span data-stu-id="cf233-155">Operations on tRFCs in SAP</span></span>](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md)