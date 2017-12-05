---
title: "傳送 Idoc 至 SAP 使用 WCF 服務模型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service model, sending IDOCs to SAP
- IDOCs, sending to SAP by using the WCF service model
ms.assetid: 84077234-b82b-4e88-b858-ce2cb1383fb4
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d9d550887271e2ba54d858456347ea85825554e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="send-idocs-to-sap-using-the-wcf-service-model"></a><span data-ttu-id="4d18b-102">傳送 Idoc 至 SAP 使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="4d18b-102">Send IDOCs to SAP using the WCF Service Model</span></span>
<span data-ttu-id="4d18b-103">就內部而言，[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]傳送 Idoc 至 SAP 系統，藉由叫用的兩個的下列 Rfc 的其中一個：</span><span class="sxs-lookup"><span data-stu-id="4d18b-103">Internally, the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] sends IDOCs to the SAP system by invoking one of the two following RFCs:</span></span>  
  
-   <span data-ttu-id="4d18b-104">第 3 版 Idoc 的 IDOC_INBOUND_ASYNCHRONOUS。</span><span class="sxs-lookup"><span data-stu-id="4d18b-104">IDOC_INBOUND_ASYNCHRONOUS for version 3 IDOCs.</span></span>  
  
-   <span data-ttu-id="4d18b-105">第 2 版 Idoc 的 INBOUND_IDOC_PROCESS。</span><span class="sxs-lookup"><span data-stu-id="4d18b-105">INBOUND_IDOC_PROCESS for version 2 IDOCs.</span></span>  
  
 <span data-ttu-id="4d18b-106">您可以傳送 IDOC 至配接器的適當 RFC （或 tRFC）; 叫用不過，您也可以傳送 Idoc 至配接器使用兩個下列作業：</span><span class="sxs-lookup"><span data-stu-id="4d18b-106">You can send an IDOC to the adapter by invoking the appropriate RFC (or tRFC); however, you can also use the two following operations to send IDOCs to the adapter:</span></span>  
  
-   <span data-ttu-id="4d18b-107">**SendIdoc** IDOC 根節點正下方會顯示。</span><span class="sxs-lookup"><span data-stu-id="4d18b-107">**SendIdoc** is surfaced directly under the IDOC root node.</span></span> <span data-ttu-id="4d18b-108">SendIdoc 作業的字串 （弱型別） 資料以傳送 IDOC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4d18b-108">The SendIdoc operation sends the IDOC as string (weakly-typed) data to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
-   <span data-ttu-id="4d18b-109">**傳送**會個別顯示每個 idoc。</span><span class="sxs-lookup"><span data-stu-id="4d18b-109">**Send** is surfaced individually for each IDOC.</span></span> <span data-ttu-id="4d18b-110">傳送作業會為強型別資料傳送 IDOC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4d18b-110">The Send operation sends the IDOC as strongly-typed data to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
 <span data-ttu-id="4d18b-111">這些作業，判斷 IDOC 資料傳送至配接器的方式，不如何傳送至 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="4d18b-111">These operations determine how the IDOC data is sent to the adapter, not how it is sent to the SAP system.</span></span> <span data-ttu-id="4d18b-112">配接器一律會依使用適當的 tRFC 傳送 IDOC 至 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="4d18b-112">The adapter always sends the IDOC to the SAP system by using the appropriate tRFC.</span></span>  
  
 <span data-ttu-id="4d18b-113">因為[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]傳送 IDOC tRFC，為傳送及 SendIdoc 作業公開您用來確認 （認可） 的 IDOC GUID 參數。</span><span class="sxs-lookup"><span data-stu-id="4d18b-113">Because the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] sends the IDOC as a tRFC, both the Send and SendIdoc operations expose a GUID parameter that you use to confirm (commit) the IDOC.</span></span> <span data-ttu-id="4d18b-114">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]在內部對應此使用 SAP 交易識別碼 (TID) tRFC 與相關聯的 GUID。</span><span class="sxs-lookup"><span data-stu-id="4d18b-114">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] internally maps this GUID with the SAP transaction ID (TID) that is associated with the tRFC.</span></span> <span data-ttu-id="4d18b-115">您可以確認 IDOC 中有兩種：</span><span class="sxs-lookup"><span data-stu-id="4d18b-115">You can confirm the IDOC in one of two ways:</span></span>  
  
-   <span data-ttu-id="4d18b-116">使用**AutoConfirmSentIdocs**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="4d18b-116">By using the **AutoConfirmSentIdocs** binding property.</span></span> <span data-ttu-id="4d18b-117">如果這個繫結屬性設為**true**，配接器會自動確認用來傳送 IDOC tRFC。</span><span class="sxs-lookup"><span data-stu-id="4d18b-117">If this binding property is set to **true**, the adapter automatically confirms the tRFC used to send the IDOC.</span></span>  
  
-   <span data-ttu-id="4d18b-118">藉由叫用 RfcConfirmTransID。</span><span class="sxs-lookup"><span data-stu-id="4d18b-118">By invoking RfcConfirmTransID.</span></span> <span data-ttu-id="4d18b-119">您可以呼叫這項作業 IDOC 相關聯的 guid。</span><span class="sxs-lookup"><span data-stu-id="4d18b-119">You invoke this operation with the GUID associated with the IDOC.</span></span>  
  
 <span data-ttu-id="4d18b-120">下列各節將說明如何傳送 Idoc 至 SAP 系統中，使用 SendIdoc 和傳送作業。</span><span class="sxs-lookup"><span data-stu-id="4d18b-120">The following sections show you how to send IDOCs to an SAP system by using the SendIdoc and Send operations.</span></span> <span data-ttu-id="4d18b-121">如需可協助您以 tRFC 傳送 IDOC 的詳細資訊，請參閱[使用 WCF 服務模型來叫用 sap tRFCs](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="4d18b-121">For more information to help you send an IDOC as a tRFC, see [Invoke tRFCs in SAP by using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-the-wcf-service-model.md).</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="4d18b-122">WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="4d18b-122">The WCF Client Class</span></span>  
  
### <a name="the-sendidoc-operation"></a><span data-ttu-id="4d18b-123">SendIdoc 作業</span><span class="sxs-lookup"><span data-stu-id="4d18b-123">The SendIdoc Operation</span></span>  
 <span data-ttu-id="4d18b-124">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現以字串格式傳送 IDOC 的單一作業 （和服務合約）。</span><span class="sxs-lookup"><span data-stu-id="4d18b-124">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces a single operation (and service contract) to send an IDOC in string format.</span></span> <span data-ttu-id="4d18b-125">服務合約的名稱是"Idoc"，而 WCF 用戶端類別是**IdocClient**。</span><span class="sxs-lookup"><span data-stu-id="4d18b-125">The name of the service contract is "Idoc" and the WCF client class is **IdocClient**.</span></span>  
  
 <span data-ttu-id="4d18b-126">您可以使用此用戶端，對 SAP 傳送任何 IDOC。</span><span class="sxs-lookup"><span data-stu-id="4d18b-126">You can send any IDOC to SAP by using this client.</span></span> <span data-ttu-id="4d18b-127">它包含單一方法**SendIdoc**，採用兩個參數：</span><span class="sxs-lookup"><span data-stu-id="4d18b-127">It contains a single method, **SendIdoc**, that takes two parameters:</span></span>  
  
-   <span data-ttu-id="4d18b-128">**idocData**是一個字串，包含 IDOC 資料</span><span class="sxs-lookup"><span data-stu-id="4d18b-128">**idocData** is a string that contains the IDOC data</span></span>  
  
-   <span data-ttu-id="4d18b-129">**guid**是對應到 SAP TID 的 GUID。</span><span class="sxs-lookup"><span data-stu-id="4d18b-129">**guid** is the GUID that is mapped to the SAP TID.</span></span>  
  
 <span data-ttu-id="4d18b-130">下列程式碼顯示針對 SendIdoc 作業所產生 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="4d18b-130">The following code shows the WCF client that is generated for the SendIdoc operation.</span></span>  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class IdocClient : System.ServiceModel.ClientBase<Idoc>, Idoc {  
  
    public void SendIdoc(string idocData, ref System.Nullable\<System.Guid\> guid) {…}  
}  
```  
  
### <a name="the-send-operation"></a><span data-ttu-id="4d18b-131">傳送作業</span><span class="sxs-lookup"><span data-stu-id="4d18b-131">The Send Operation</span></span>  
 <span data-ttu-id="4d18b-132">傳送作業會使用強型別資料，因為[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現每個 IDOC 的唯一的服務合約。</span><span class="sxs-lookup"><span data-stu-id="4d18b-132">Because the Send operation uses strongly-typed data, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces a unique service contract for each IDOC.</span></span> <span data-ttu-id="4d18b-133">這個合約為基礎的 IDOC 類型、 版本、 版次號碼和 CIM 類型 （如果適當的話），就會產生介面 （和 WCF 用戶端類別） 的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d18b-133">The name of the interface (and the WCF client class) generated for this contract is based on the IDOC type, version, release number, and CIM type (if relevant).</span></span> <span data-ttu-id="4d18b-134">例如 ORDERS03.v3.620 idoc，介面名稱為"IdocORDERS03V3R620"且 WCF 用戶端類別為**IdocORDERS03V3R620Client**。</span><span class="sxs-lookup"><span data-stu-id="4d18b-134">For example for the ORDERS03.v3.620 IDOC, the interface is named "IdocORDERS03V3R620" and the WCF client class is **IdocORDERS03V3R620Client**.</span></span>  
  
 <span data-ttu-id="4d18b-135">您必須產生唯一的用戶端的各種不同類型的 IDOC。</span><span class="sxs-lookup"><span data-stu-id="4d18b-135">You must generate a unique client for each different type of IDOC.</span></span> <span data-ttu-id="4d18b-136">此用戶端包含單一方法**傳送**，採用兩個參數：</span><span class="sxs-lookup"><span data-stu-id="4d18b-136">This client contains a single method, **Send**, that takes two parameters:</span></span>  
  
-   <span data-ttu-id="4d18b-137">**idocData**是表示強型別 IDOC 資料的類別。</span><span class="sxs-lookup"><span data-stu-id="4d18b-137">**idocData** is a class that represents the strongly-typed IDOC data.</span></span>  
  
-   <span data-ttu-id="4d18b-138">**guid**是對應到 SAP TID 之 guid 的字串表示。</span><span class="sxs-lookup"><span data-stu-id="4d18b-138">**guid** is a string representation of the GUID that is mapped to the SAP TID.</span></span>  
  
 <span data-ttu-id="4d18b-139">下列程式碼顯示針對提出 ORDERS03.v3.620 IDOC 的傳送作業所產生 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="4d18b-139">The following code shows the WCF client that is generated for the Send operation surfaced for the ORDERS03.v3.620 IDOC.</span></span>  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class IdocORDERS03V3R620Client : System.ServiceModel.ClientBase<IdocORDERS03V3R620>, IdocORDERS03V3R620 {  
  
    ...  
  
    public void Send(ORDERS03 idocData, ref string guid) { ... }  
}  
```  
  
## <a name="how-to-create-an-application-to-send-idocs"></a><span data-ttu-id="4d18b-140">如何建立傳送 Idoc 的應用程式</span><span class="sxs-lookup"><span data-stu-id="4d18b-140">How to Create an Application to Send IDOCs</span></span>  
 <span data-ttu-id="4d18b-141">若要傳送 IDOC 到 SAP 系統，執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="4d18b-141">To send an IDOC to an SAP system, perform the following steps.</span></span>  
  
#### <a name="to-send-an-idoc-to-an-sap-system"></a><span data-ttu-id="4d18b-142">若要傳送 IDOC 至 SAP 系統</span><span class="sxs-lookup"><span data-stu-id="4d18b-142">To send an IDOC to an SAP system</span></span>  
  
1.  <span data-ttu-id="4d18b-143">產生 WCF 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="4d18b-143">Generate a WCF client class.</span></span> <span data-ttu-id="4d18b-144">使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生 WCF 用戶端類別為目標想要使用的 Idoc。</span><span class="sxs-lookup"><span data-stu-id="4d18b-144">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate the WCF client class that targets the IDOCs with which you want to work.</span></span> <span data-ttu-id="4d18b-145">如需如何產生 WCF 用戶端的詳細資訊，請參閱[SAP 方案成品產生 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="4d18b-145">For more information about how to generate a WCF client, see [Generating a WCF Client or a WCF Service Contract for SAP Solution Artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span></span> <span data-ttu-id="4d18b-146">如果您想要明確地確認 Idoc，請確定您會產生 WCF 用戶端 RfcConfirmTransID 作業。</span><span class="sxs-lookup"><span data-stu-id="4d18b-146">If you want to explicitly confirm IDOCs, make sure that you generate the WCF client for the RfcConfirmTransID operation.</span></span> <span data-ttu-id="4d18b-147">作業可以找到下的下列節點：</span><span class="sxs-lookup"><span data-stu-id="4d18b-147">Operations can be found under the following nodes:</span></span>  
  
    -   <span data-ttu-id="4d18b-148">SendIdoc 作業。</span><span class="sxs-lookup"><span data-stu-id="4d18b-148">SendIdoc operation.</span></span> <span data-ttu-id="4d18b-149">直接在 IDOC 節點下。</span><span class="sxs-lookup"><span data-stu-id="4d18b-149">Directly under the IDOC node.</span></span>  
  
    -   <span data-ttu-id="4d18b-150">傳送作業。</span><span class="sxs-lookup"><span data-stu-id="4d18b-150">Send operation.</span></span> <span data-ttu-id="4d18b-151">底下的節點對應至目標 IDOC 類型、 版本和版次數目。</span><span class="sxs-lookup"><span data-stu-id="4d18b-151">Under the node corresponding to the type, version and release number of the target IDOC.</span></span>  
  
    -   <span data-ttu-id="4d18b-152">RfcConfirmTransID 作業。</span><span class="sxs-lookup"><span data-stu-id="4d18b-152">RfcConfirmTransID operation.</span></span> <span data-ttu-id="4d18b-153">直接在 TRFC 節點下。</span><span class="sxs-lookup"><span data-stu-id="4d18b-153">Directly under the TRFC node.</span></span>  
  
2.  <span data-ttu-id="4d18b-154">建立在步驟 1 所產生的 WCF 用戶端類別的執行個體，並指定用戶端繫結。</span><span class="sxs-lookup"><span data-stu-id="4d18b-154">Create an instance of the WCF client class generated in step 1, and specify a client binding.</span></span> <span data-ttu-id="4d18b-155">指定用戶端繫結牽涉到指定的繫結和 WCF 用戶端會使用的端點位址。</span><span class="sxs-lookup"><span data-stu-id="4d18b-155">Specifying a client binding involves specifying the binding and endpoint address that the WCF client will use.</span></span> <span data-ttu-id="4d18b-156">您可以在程式碼中以命令方式或是宣告式組態。</span><span class="sxs-lookup"><span data-stu-id="4d18b-156">You can do this either imperatively in code or declaratively in configuration.</span></span> <span data-ttu-id="4d18b-157">如需如何指定用戶端繫結的詳細資訊，請參閱[SAP 系統設定用戶端繫結](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md)。</span><span class="sxs-lookup"><span data-stu-id="4d18b-157">For more information about how to specify a client binding, see [Configure a Client Binding for the SAP System](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md).</span></span> <span data-ttu-id="4d18b-158">下列程式碼初始化從組態 IdocClient （適用於傳送作業中），以及設定 SAP 系統的認證。</span><span class="sxs-lookup"><span data-stu-id="4d18b-158">The following code initializes an IdocClient (for the Send operation) from configuration and sets the credentials for the SAP system.</span></span>  
  
    ```  
    SAPBinding binding = new SAPBinding();  
  
    // Set endpoint address  
    EndpointAddress endpointAddress = new EndpointAddress("sap://CLIENT=800;LANG=EN;@a/YourSAPHost/00?RfcSdkTrace=False&AbapDebug=False&UseSapGui=Without");  
  
    // Create client and set credentials  
    idocClient = new IdocClient(binding, endpointAddress);  
    idocClient.ClientCredentials.UserName.UserName = "YourUserName";  
    idocClient.ClientCredentials.UserName.Password = "YourPassword";;  
    ```  
  
3.  <span data-ttu-id="4d18b-159">如果您想要確認 tRFC 之後 SAP 系統上的介面卡傳送 IDOC，設定**AutoConfirmSentIdocs**內容繫結至**true**。</span><span class="sxs-lookup"><span data-stu-id="4d18b-159">If you want the adapter to confirm the tRFC on the SAP system after it sends the IDOC, set the **AutoConfirmSentIdocs** binding property to **true**.</span></span> <span data-ttu-id="4d18b-160">開啟 WCF 用戶端之前，您必須這麼做。</span><span class="sxs-lookup"><span data-stu-id="4d18b-160">You must do this before you open the WCF client.</span></span>  
  
    ```  
    // Set AutoConfirmSentIdocs property to true  
    binding.AutoConfirmSentIdocs = true;  
    ```  
  
4.  <span data-ttu-id="4d18b-161">開啟 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="4d18b-161">Open the WCF client.</span></span>  
  
    ```  
    idocClient.Open();  
    ```  
  
5.  <span data-ttu-id="4d18b-162">叫用 WCF 用戶端在步驟 2 中建立可傳送 IDOC 至 SAP 系統上的適當方法。</span><span class="sxs-lookup"><span data-stu-id="4d18b-162">Invoke the appropriate method on the WCF client created in step 2 to send the IDOC to the SAP system.</span></span> <span data-ttu-id="4d18b-163">您可以將傳遞的變數，其中包含的 GUID，或者設定為**null**如**guid**參數。</span><span class="sxs-lookup"><span data-stu-id="4d18b-163">You can pass a variable that contains a GUID or that is set to **null** for the **guid** parameter.</span></span> <span data-ttu-id="4d18b-164">如果您未指定 GUID[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]產生作業的其中一種 (**guid**是**ref**參數)。</span><span class="sxs-lookup"><span data-stu-id="4d18b-164">If you do not specify a GUID, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] generates one for the operation (**guid** is a **ref** parameter).</span></span> <span data-ttu-id="4d18b-165">下列程式碼會從檔案讀取 IDOC （以字串格式），並使用 SendIdoc 作業以將它傳送至 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="4d18b-165">The following code reads an IDOC (in string format) from a file and sends it to the SAP system by using the SendIdoc operation.</span></span>  
  
    ```  
    // Read IDOC into string variable  
    using (StreamReader reader = new StreamReader("ORDERS03.txt"))  
    {  
    idocData = reader.ReadToEnd();  
    }  
  
    //Get a new GUID to pass to SendIdoc. You can also assign a null  
    //value to have the adapter generate a GUID.  
    adapterTxGuid = Guid.NewGuid();  
  
    //Invoke SendIdoc on the client to send the IDOC to the SAP system  
    idocClient.SendIdoc(idocData, ref adapterTxGuid);  
    ```  
  
6.  <span data-ttu-id="4d18b-166">如果您未設定**AutoConfirmSentIdocs**內容繫結至**true** （在步驟 3），然後您必須確認 tRFC SAP 系統上的。</span><span class="sxs-lookup"><span data-stu-id="4d18b-166">If you did not set the **AutoConfirmSentIdocs** binding property to **true** (in step 3), then you must confirm the tRFC on the SAP system.</span></span> <span data-ttu-id="4d18b-167">若要這樣做您必須叫用**RfcConfirmTransID**方法**TrfcClient** （不會顯示建立）。</span><span class="sxs-lookup"><span data-stu-id="4d18b-167">To do this you must invoke the **RfcConfirmTransID** method on a **TrfcClient** (creation not shown).</span></span> <span data-ttu-id="4d18b-168">指定在步驟 4 參數中傳回 GUID。</span><span class="sxs-lookup"><span data-stu-id="4d18b-168">Specify the GUID returned in step 4 for the parameter.</span></span>  
  
    ```  
    trfcClient.RfcConfirmTransID(adapterTxGuid);  
    ```  
  
7.  <span data-ttu-id="4d18b-169">關閉 WCF 用戶端 (和**TrfcClient**，如果使用) 完成時 （您完成後，傳送 Idoc） 使用它。</span><span class="sxs-lookup"><span data-stu-id="4d18b-169">Close the WCF client (and **TrfcClient**, if used) when you are done using it (after you have finished sending IDOCs).</span></span>  
  
    ```  
    idocClient.Close();   
    ```  
  
### <a name="example"></a><span data-ttu-id="4d18b-170">範例</span><span class="sxs-lookup"><span data-stu-id="4d18b-170">Example</span></span>  
 <span data-ttu-id="4d18b-171">下列範例會傳送 IDOC 到 SAP 系統使用 SendIdoc 方法。</span><span class="sxs-lookup"><span data-stu-id="4d18b-171">The following example sends an IDOC to an SAP system by using the SendIdoc method.</span></span> <span data-ttu-id="4d18b-172">IDOC 是從檔案讀取，ORDERS03.txt。</span><span class="sxs-lookup"><span data-stu-id="4d18b-172">The IDOC is read from a file, ORDERS03.txt.</span></span> <span data-ttu-id="4d18b-173">此檔案包含 ORDERS03。V3.620 IDOC 和隨附的範例。不過，SendIdoc 作業可以用來傳送任何 IDOC。</span><span class="sxs-lookup"><span data-stu-id="4d18b-173">This file contains an ORDERS03.V3.620 IDOC and is included with the samples; however, the SendIdoc operation can be used to send any IDOC.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.IO;  
  
// Add WCF, WCF LOB Adapter SDK, and SAP adapter namepaces  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
  
// Include this namespace for WCF LOB Adapter SDK and SAP exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
// This example sends a flat IDOC to the SAP system by using the SendIdoc operation.  
namespace SapIdocStringClientSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // variable for the IDOC client  
            IdocClient idocClient = null;  
  
            Console.WriteLine("IDOC string client sample started");  
            try  
            {  
                // Variable for the GUID  
                System.Nullable<System.Guid> adapterTxGuid;  
                // string to hold the Idoc data  
                string idocData;  
                // string to hold the SAP transaction ID (TID)  
                string sapTxId;  
  
                // The client can be configured from app.config, but it is   
                // explicitly configured here for demonstration.  
                // set AutoConfirmSentIdocs property to true  
                SAPBinding binding = new SAPBinding();  
                binding.AutoConfirmSentIdocs = true;  
  
                // Set endpoint address  
                EndpointAddress endpointAddress = new EndpointAddress("sap://CLIENT=800;LANG=EN;@a/YourSAPServer/00?RfcSdkTrace=False&AbapDebug=False&UseSapGui=Without");  
  
                // Create client and set credentials  
                idocClient = new IdocClient(binding, endpointAddress);  
                idocClient.ClientCredentials.UserName.UserName = "YourUserName";  
                idocClient.ClientCredentials.UserName.Password = "YourPassword";  
  
                // Open the client and send the Idoc  
                idocClient.Open();  
  
                // Read IDOC into string variable  
                using (StreamReader reader = new StreamReader("ORDERS03.txt"))  
                {  
                    idocData = reader.ReadToEnd();  
                }  
  
                //Get a new GUID to pass to SendIdoc. You can also assign a null.  
                //value to have the adapter generate a GUID.  
                adapterTxGuid = Guid.NewGuid();  
  
                //Invoke SendIdoc on the client to send the IDOC to the SAP system.  
                idocClient.SendIdoc(idocData, ref adapterTxGuid);  
  
                // The AutoConfirmSentIdocs binding property is set to true, so there is no need to  
                // confirm the IDOC. If this property is not set to true, you must call the   
                // RfcConfirmTransID method of a TrfcClient with adapterTxGuid to   
                // confirm the transaction on the SAP system.   
  
                // Get SAP tx id from GUID  
                sapTxId = SAPAdapterUtilities.ConvertGuidToTid((Guid) adapterTxGuid);  
  
                Console.WriteLine("IDOC sent");  
                Console.WriteLine("The SAP Transaction Id is : " + sapTxId);  
  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                }  
            }  
            finally  
            {  
                // Close the IDOC client  
                if (idocClient != null)  
                {  
                    if (idocClient.State == CommunicationState.Opened)  
                        idocClient.Close();  
                    else  
                        idocClient.Abort();  
                }  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d18b-174">請參閱</span><span class="sxs-lookup"><span data-stu-id="4d18b-174">See Also</span></span>  
[<span data-ttu-id="4d18b-175">使用 WCF 服務模型開發應用程式</span><span class="sxs-lookup"><span data-stu-id="4d18b-175">Develop applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)