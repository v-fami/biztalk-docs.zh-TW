---
title: "叫用中使用 BizTalk Server 的 SAP Rfc |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: RFCs, invoking using BizTalk Server
ms.assetid: cc859ca2-aa9a-48fd-a941-ae28bee96f06
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc6738a2b46b3dc28aeee0642c03f92467ef6190
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-rfcs-in-sap-using-biztalk-server"></a><span data-ttu-id="41b2e-102">叫用中使用 BizTalk Server 的 SAP Rfc</span><span class="sxs-lookup"><span data-stu-id="41b2e-102">Invoke RFCs in SAP using BizTalk Server</span></span>
<span data-ttu-id="41b2e-103">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]介面上做為配接器用戶端可以叫用的作業由 SAP 系統的 Rfc。</span><span class="sxs-lookup"><span data-stu-id="41b2e-103">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces the RFCs exposed by an SAP system as operations that can be invoked by an adapter client.</span></span> <span data-ttu-id="41b2e-104">此章節提供的指示以 SAP 系統的 RFC 叫用使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]與 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="41b2e-104">This section provides instructions on invoking an RFC in an SAP system by using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="41b2e-105">如需有關如何[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援叫用 RFC SAP 系統，請參閱[作業中 SAP Rfc](../../adapters-and-accelerators/adapter-sap/operations-on-rfcs-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="41b2e-105">For more information about how the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports invoking an RFC in an SAP system, see [Operations on RFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-rfcs-in-sap.md).</span></span> <span data-ttu-id="41b2e-106">更多的叫用 RFC 的 SOAP 訊息結構的詳細資訊，請參閱[RFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="41b2e-106">For more information about the structure of SOAP message for invoking an RFC, see [Message Schemas for RFC Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md).</span></span>  
  
## <a name="how-to-invoke-an-rfc-in-an-sap-system"></a><span data-ttu-id="41b2e-107">叫用 SAP 系統中的 RFC 如何？</span><span class="sxs-lookup"><span data-stu-id="41b2e-107">How to Invoke an RFC in an SAP system?</span></span>  
 <span data-ttu-id="41b2e-108">執行 SAP 系統使用的作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]牽涉到程序中所述的工作[建立的 SAP 應用程式的建置組塊](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="41b2e-108">Performing an operation on an SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] involves procedural tasks described in [Building blocks to create SAP applications](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md).</span></span> <span data-ttu-id="41b2e-109">要叫用 RFC，SAP 系統中，這些工作包括：</span><span class="sxs-lookup"><span data-stu-id="41b2e-109">To invoke an RFC in an SAP system, these tasks are:</span></span>  
  
1.  <span data-ttu-id="41b2e-110">建立 BizTalk 專案，並產生您想要叫用 SAP 系統中的 RFC 的結構描述。</span><span class="sxs-lookup"><span data-stu-id="41b2e-110">Create a BizTalk project and generate schema for the RFC you want to invoke in the SAP system.</span></span>  
  
2.  <span data-ttu-id="41b2e-111">建立傳送和從 SAP 系統接收訊息的 BizTalk 專案中的訊息。</span><span class="sxs-lookup"><span data-stu-id="41b2e-111">Create messages in the BizTalk project for sending and receiving messages from the SAP system.</span></span>  
  
3.  <span data-ttu-id="41b2e-112">建立協調流程叫用 RFC，SAP 系統中。</span><span class="sxs-lookup"><span data-stu-id="41b2e-112">Create an orchestration to invoke an RFC in the SAP system.</span></span>  
  
4.  <span data-ttu-id="41b2e-113">建置和部署 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="41b2e-113">Build and deploy the BizTalk project.</span></span>  
  
5.  <span data-ttu-id="41b2e-114">設定的 BizTalk 應用程式藉由建立實體傳送和接收埠。</span><span class="sxs-lookup"><span data-stu-id="41b2e-114">Configure the BizTalk application by creating physical send and receive ports.</span></span>  
  
6.  <span data-ttu-id="41b2e-115">啟動 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="41b2e-115">Start the BizTalk application.</span></span>  
  
 <span data-ttu-id="41b2e-116">本主題提供執行這些工作的指示。</span><span class="sxs-lookup"><span data-stu-id="41b2e-116">This topic provides instructions to perform these tasks.</span></span>  
  
## <a name="generating-schema"></a><span data-ttu-id="41b2e-117">產生結構描述</span><span class="sxs-lookup"><span data-stu-id="41b2e-117">Generating Schema</span></span>  
 <span data-ttu-id="41b2e-118">本主題中，以示範如何在 SAP 系統中，叫用 RFC 我們產生的結構描述*RFC_CUSTOMER_GET*。</span><span class="sxs-lookup"><span data-stu-id="41b2e-118">In this topic, to demonstrate how to invoke an RFC in an SAP system, we generate the schema for *RFC_CUSTOMER_GET*.</span></span> <span data-ttu-id="41b2e-119">請參閱[瀏覽、 搜尋和取得中繼資料中 SAP RFC 作業的](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md)如需有關如何產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="41b2e-119">See [Browse, Search, and get Metadata for RFC Operations in SAP](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md) for more information about how to generate schema.</span></span>  
  
## <a name="defining-messages-and-message-types"></a><span data-ttu-id="41b2e-120">定義訊息和訊息類型</span><span class="sxs-lookup"><span data-stu-id="41b2e-120">Defining Messages and Message Types</span></span>  
 <span data-ttu-id="41b2e-121">您先前產生的結構描述會描述 「 類型 」 所需的協調流程中的訊息。</span><span class="sxs-lookup"><span data-stu-id="41b2e-121">The schema that you generated earlier describes the "types" required for the messages in the orchestration.</span></span> <span data-ttu-id="41b2e-122">訊息通常是為其型別由對應的結構描述所定義的變數。</span><span class="sxs-lookup"><span data-stu-id="41b2e-122">A message is typically a variable, the type for which is defined by the corresponding schema.</span></span> <span data-ttu-id="41b2e-123">您必須連結到訊息的您所產生的結構描述之協調流程檢視中的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="41b2e-123">You must link the schema you generated to the messages from the Orchestration view of the BizTalk project.</span></span>  
  
 <span data-ttu-id="41b2e-124">本主題中，您必須建立兩個訊息，其中將要求傳送至 SAP 系統，而另一個則接收回應。</span><span class="sxs-lookup"><span data-stu-id="41b2e-124">For this topic, you must create two messages—one to send a request to the SAP system and the other to receive a response.</span></span>  
  
 <span data-ttu-id="41b2e-125">執行下列步驟來建立訊息，並將其連結至結構描述。</span><span class="sxs-lookup"><span data-stu-id="41b2e-125">Perform the following steps to create messages and link them to the schema.</span></span>  
  
#### <a name="to-create-messages-and-link-to-schema"></a><span data-ttu-id="41b2e-126">建立訊息，以及連結至結構描述</span><span class="sxs-lookup"><span data-stu-id="41b2e-126">To create messages and link to schema</span></span>  
  
1.  <span data-ttu-id="41b2e-127">開啟協調流程檢視 BizTalk 專案中，如果未開啟。</span><span class="sxs-lookup"><span data-stu-id="41b2e-127">Open the orchestration view the BizTalk project, if not already open.</span></span> <span data-ttu-id="41b2e-128">按一下**檢視**，指向 **其他視窗**，然後按一下**協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="41b2e-128">Click **View**, point to **Other Windows**, and click **Orchestration View**.</span></span>  
  
2.  <span data-ttu-id="41b2e-129">在**協調流程檢視**，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。</span><span class="sxs-lookup"><span data-stu-id="41b2e-129">In the **Orchestration View**, right-click **Messages**, and then click **New Message**.</span></span>  
  
3.  <span data-ttu-id="41b2e-130">以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="41b2e-130">Right-click the newly create message and select **Properties Window**.</span></span>  
  
4.  <span data-ttu-id="41b2e-131">在**屬性**窗格**Message_1**，執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="41b2e-131">In the **Properties** pane for **Message_1**, do the following.</span></span>  
  
    |<span data-ttu-id="41b2e-132">使用</span><span class="sxs-lookup"><span data-stu-id="41b2e-132">Use this</span></span>|<span data-ttu-id="41b2e-133">動作</span><span class="sxs-lookup"><span data-stu-id="41b2e-133">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="41b2e-134">識別碼</span><span class="sxs-lookup"><span data-stu-id="41b2e-134">Identifier</span></span>|<span data-ttu-id="41b2e-135">型別**要求**。</span><span class="sxs-lookup"><span data-stu-id="41b2e-135">Type **Request**.</span></span>|  
    |<span data-ttu-id="41b2e-136">訊息類型</span><span class="sxs-lookup"><span data-stu-id="41b2e-136">Message Type</span></span>|<span data-ttu-id="41b2e-137">從下拉式清單中，展開 **結構描述**，然後選取*InvokeRFC.SAPBindingSchema.RFC_CUSTOMER_GET*，其中*InvokeRFC*是您的 BizTalk 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="41b2e-137">From the drop-down list, expand **Schemas**, and select *InvokeRFC.SAPBindingSchema.RFC_CUSTOMER_GET*, where *InvokeRFC* is the name of your BizTalk project.</span></span>  <span data-ttu-id="41b2e-138">*SAPBindingSchema*是針對產生的結構描述*RFC_CUSTOMER_GET*。</span><span class="sxs-lookup"><span data-stu-id="41b2e-138">*SAPBindingSchema* is the schema generated for *RFC_CUSTOMER_GET*.</span></span>|  
  
5.  <span data-ttu-id="41b2e-139">重複上述步驟，建立新的訊息。</span><span class="sxs-lookup"><span data-stu-id="41b2e-139">Repeat the previous step to create a new message.</span></span> <span data-ttu-id="41b2e-140">在**屬性**窗格新訊息中，執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="41b2e-140">In the **Properties** pane for the new message, do the following.</span></span>  
  
    |<span data-ttu-id="41b2e-141">使用</span><span class="sxs-lookup"><span data-stu-id="41b2e-141">Use this</span></span>|<span data-ttu-id="41b2e-142">動作</span><span class="sxs-lookup"><span data-stu-id="41b2e-142">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="41b2e-143">識別碼</span><span class="sxs-lookup"><span data-stu-id="41b2e-143">Identifier</span></span>|<span data-ttu-id="41b2e-144">型別**回應**。</span><span class="sxs-lookup"><span data-stu-id="41b2e-144">Type **Response**.</span></span>|  
    |<span data-ttu-id="41b2e-145">訊息類型</span><span class="sxs-lookup"><span data-stu-id="41b2e-145">Message Type</span></span>|<span data-ttu-id="41b2e-146">從下拉式清單中，展開 **結構描述**，然後選取*InvokeRFC.SAPBindingSchema.RFC_CUSTOMER_GETResponse*。</span><span class="sxs-lookup"><span data-stu-id="41b2e-146">From the drop-down list, expand **Schemas**, and select *InvokeRFC.SAPBindingSchema.RFC_CUSTOMER_GETResponse*.</span></span>|  
  
## <a name="setting-up-the-orchestration"></a><span data-ttu-id="41b2e-147">設定協調流程</span><span class="sxs-lookup"><span data-stu-id="41b2e-147">Setting up the Orchestration</span></span>  
 <span data-ttu-id="41b2e-148">您必須建立 BizTalk 協調流程使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]叫用 Rfc，SAP 系統中。</span><span class="sxs-lookup"><span data-stu-id="41b2e-148">You must create a BizTalk orchestration to use [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] for invoking RFCs in the SAP system.</span></span> <span data-ttu-id="41b2e-149">在此協調流程中，卸除要求訊息已定義的接收位置。</span><span class="sxs-lookup"><span data-stu-id="41b2e-149">In this orchestration, you drop a request message at a defined receive location.</span></span> <span data-ttu-id="41b2e-150">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]取用訊息，並將它傳遞至 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="41b2e-150">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] consumes the message and passes it on to the SAP system.</span></span> <span data-ttu-id="41b2e-151">從 SAP 系統的回應會儲存到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="41b2e-151">The response from the SAP system is saved to another location.</span></span> <span data-ttu-id="41b2e-152">典型的協調流程叫用的 rfc，SAP 系統中會包含：</span><span class="sxs-lookup"><span data-stu-id="41b2e-152">A typical orchestration for invoking RFCs in an SAP system would contain:</span></span>  
  
-   <span data-ttu-id="41b2e-153">傳送和接收圖形以將訊息傳送至 SAP 系統，並接收回應。</span><span class="sxs-lookup"><span data-stu-id="41b2e-153">Send and Receive shapes to send messages to the SAP system and receive responses.</span></span>  
  
-   <span data-ttu-id="41b2e-154">單向接收埠以接收要求訊息傳送到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="41b2e-154">A one-way receive port to receive request messages to send to the SAP system.</span></span>  
  
-   <span data-ttu-id="41b2e-155">雙向傳送埠以將要求訊息傳送至 SAP 系統，並接收回應。</span><span class="sxs-lookup"><span data-stu-id="41b2e-155">A two-way send port to send request messages to the SAP system and receive responses.</span></span>  
  
-   <span data-ttu-id="41b2e-156">單向傳送埠，以便從 SAP 系統的回應傳送到資料夾。</span><span class="sxs-lookup"><span data-stu-id="41b2e-156">A one-way send port to send the responses from the SAP system to a folder.</span></span>  
  
 <span data-ttu-id="41b2e-157">範例協調流程如下所示：</span><span class="sxs-lookup"><span data-stu-id="41b2e-157">A sample orchestration resembles the following:</span></span>  
  
 <span data-ttu-id="41b2e-158">![具有連接的連接埠的協調流程](../../adapters-and-accelerators/adapter-sap/media/c228e79f-02e8-4de3-b447-8703caa28d3b.gif "c228e79f-02e8-4de3-b447-8703caa28d3b")</span><span class="sxs-lookup"><span data-stu-id="41b2e-158">![Orchestration with ports connected](../../adapters-and-accelerators/adapter-sap/media/c228e79f-02e8-4de3-b447-8703caa28d3b.gif "c228e79f-02e8-4de3-b447-8703caa28d3b")</span></span>  
  
### <a name="adding-message-shapes"></a><span data-ttu-id="41b2e-159">新增訊息圖形</span><span class="sxs-lookup"><span data-stu-id="41b2e-159">Adding Message Shapes</span></span>  
 <span data-ttu-id="41b2e-160">請確定您針對每個訊息圖形指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="41b2e-160">Make sure you specify the following properties for each of the message shapes.</span></span> <span data-ttu-id="41b2e-161">所列的名稱*圖形*資料行名稱就是訊息圖形顯示在上述的協調流程中。</span><span class="sxs-lookup"><span data-stu-id="41b2e-161">The names listed in the *Shape* column are the names of the message shapes as displayed in the preceding orchestration.</span></span>  
  
|<span data-ttu-id="41b2e-162">形狀圖</span><span class="sxs-lookup"><span data-stu-id="41b2e-162">Shape</span></span>|<span data-ttu-id="41b2e-163">圖形類型</span><span class="sxs-lookup"><span data-stu-id="41b2e-163">Shape Type</span></span>|<span data-ttu-id="41b2e-164">屬性</span><span class="sxs-lookup"><span data-stu-id="41b2e-164">Properties</span></span>|  
|-----------|----------------|----------------|  
|<span data-ttu-id="41b2e-165">Receive_Request</span><span class="sxs-lookup"><span data-stu-id="41b2e-165">Receive_Request</span></span>|<span data-ttu-id="41b2e-166">Receive</span><span class="sxs-lookup"><span data-stu-id="41b2e-166">Receive</span></span>|<span data-ttu-id="41b2e-167">-設定**名稱**至*Receive_Request*</span><span class="sxs-lookup"><span data-stu-id="41b2e-167">-   Set **Name** to *Receive_Request*</span></span><br /><span data-ttu-id="41b2e-168">-設定**啟動**至*，則為 True*</span><span class="sxs-lookup"><span data-stu-id="41b2e-168">-   Set **Activate** to *True*</span></span>|  
|<span data-ttu-id="41b2e-169">Send_LOB</span><span class="sxs-lookup"><span data-stu-id="41b2e-169">Send_LOB</span></span>|<span data-ttu-id="41b2e-170">Send</span><span class="sxs-lookup"><span data-stu-id="41b2e-170">Send</span></span>|<span data-ttu-id="41b2e-171">-設定**名稱**至*Send_LOB*</span><span class="sxs-lookup"><span data-stu-id="41b2e-171">-   Set **Name** to *Send_LOB*</span></span>|  
|<span data-ttu-id="41b2e-172">Receive_LOB</span><span class="sxs-lookup"><span data-stu-id="41b2e-172">Receive_LOB</span></span>|<span data-ttu-id="41b2e-173">Receive</span><span class="sxs-lookup"><span data-stu-id="41b2e-173">Receive</span></span>|<span data-ttu-id="41b2e-174">-設定**名稱**至*Receive_LOB*</span><span class="sxs-lookup"><span data-stu-id="41b2e-174">-   Set **Name** to *Receive_LOB*</span></span><br /><span data-ttu-id="41b2e-175">-設定**啟動**至*False*</span><span class="sxs-lookup"><span data-stu-id="41b2e-175">-   Set **Activate** to *False*</span></span>|  
|<span data-ttu-id="41b2e-176">Send_Response</span><span class="sxs-lookup"><span data-stu-id="41b2e-176">Send_Response</span></span>|<span data-ttu-id="41b2e-177">Send</span><span class="sxs-lookup"><span data-stu-id="41b2e-177">Send</span></span>|<span data-ttu-id="41b2e-178">-設定**名稱**至*Send_Response*</span><span class="sxs-lookup"><span data-stu-id="41b2e-178">-   Set **Name** to *Send_Response*</span></span>|  
  
### <a name="adding-ports"></a><span data-ttu-id="41b2e-179">新增連接埠</span><span class="sxs-lookup"><span data-stu-id="41b2e-179">Adding Ports</span></span>  
 <span data-ttu-id="41b2e-180">針對每個邏輯連接埠中指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="41b2e-180">Specify the following properties for each of the logical ports.</span></span> <span data-ttu-id="41b2e-181">所列的名稱*連接埠*資料行是連接埠的名稱，顯示在 協調流程中。</span><span class="sxs-lookup"><span data-stu-id="41b2e-181">The names listed in the *Port* column are the names of the ports as displayed in the orchestration.</span></span>  
  
|<span data-ttu-id="41b2e-182">通訊埠</span><span class="sxs-lookup"><span data-stu-id="41b2e-182">Port</span></span>|<span data-ttu-id="41b2e-183">屬性</span><span class="sxs-lookup"><span data-stu-id="41b2e-183">Properties</span></span>|  
|----------|----------------|  
|<span data-ttu-id="41b2e-184">ReceiveMsgPort</span><span class="sxs-lookup"><span data-stu-id="41b2e-184">ReceiveMsgPort</span></span>|<span data-ttu-id="41b2e-185">-設定**識別碼**至*ReceiveMsgPort*</span><span class="sxs-lookup"><span data-stu-id="41b2e-185">-   Set **Identifier** to *ReceiveMsgPort*</span></span><br /><span data-ttu-id="41b2e-186">-設定**類型**至*ReceiveMsgPortType*</span><span class="sxs-lookup"><span data-stu-id="41b2e-186">-   Set **Type** to *ReceiveMsgPortType*</span></span><br /><span data-ttu-id="41b2e-187">-設定**通訊模式**至*單向*</span><span class="sxs-lookup"><span data-stu-id="41b2e-187">-   Set **Communication Pattern** to *One-Way*</span></span><br /><span data-ttu-id="41b2e-188">-設定**通訊方向**至*接收*</span><span class="sxs-lookup"><span data-stu-id="41b2e-188">-   Set **Communication Direction** to *Receive*</span></span>|  
|<span data-ttu-id="41b2e-189">SendToLOBPort</span><span class="sxs-lookup"><span data-stu-id="41b2e-189">SendToLOBPort</span></span>|<span data-ttu-id="41b2e-190">-設定**識別碼**至*SendToLOBPort*</span><span class="sxs-lookup"><span data-stu-id="41b2e-190">-   Set **Identifier** to *SendToLOBPort*</span></span><br /><span data-ttu-id="41b2e-191">-設定**類型**至*SendToLOBPortType*</span><span class="sxs-lookup"><span data-stu-id="41b2e-191">-   Set **Type** to *SendToLOBPortType*</span></span><br /><span data-ttu-id="41b2e-192">-設定**通訊模式**至*要求-回應*</span><span class="sxs-lookup"><span data-stu-id="41b2e-192">-   Set **Communication Pattern** to *Request-Response*</span></span><br /><span data-ttu-id="41b2e-193">-設定**通訊方向**至*傳送接收*</span><span class="sxs-lookup"><span data-stu-id="41b2e-193">-   Set **Communication Direction** to *Send-Receive*</span></span>|  
|<span data-ttu-id="41b2e-194">SendMsgPort</span><span class="sxs-lookup"><span data-stu-id="41b2e-194">SendMsgPort</span></span>|<span data-ttu-id="41b2e-195">-設定**識別碼**至*SendMsgPort*</span><span class="sxs-lookup"><span data-stu-id="41b2e-195">-   Set **Identifier** to *SendMsgPort*</span></span><br /><span data-ttu-id="41b2e-196">-設定**類型**至*SendMsgPortType*</span><span class="sxs-lookup"><span data-stu-id="41b2e-196">-   Set **Type** to *SendMsgPortType*</span></span><br /><span data-ttu-id="41b2e-197">-設定**通訊模式**至*單向*</span><span class="sxs-lookup"><span data-stu-id="41b2e-197">-   Set **Communication Pattern** to *One-Way*</span></span><br /><span data-ttu-id="41b2e-198">-設定**通訊方向**至*傳送*</span><span class="sxs-lookup"><span data-stu-id="41b2e-198">-   Set **Communication Direction** to *Send*</span></span>|  
  
## <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a><span data-ttu-id="41b2e-199">指定動作圖形訊息並連接至連接埠</span><span class="sxs-lookup"><span data-stu-id="41b2e-199">Specify Messages for Action Shapes and Connect to Ports</span></span>  
 <span data-ttu-id="41b2e-200">下表指定屬性和其值設為指定的動作圖形，並將它們連結至連接埠的訊息。</span><span class="sxs-lookup"><span data-stu-id="41b2e-200">The following table specifies the properties and their values to be set to specify messages for action shapes and linking them to the ports.</span></span> <span data-ttu-id="41b2e-201">所列的名稱*圖形*資料行名稱就是訊息圖形顯示在上述的協調流程中。</span><span class="sxs-lookup"><span data-stu-id="41b2e-201">The names listed in the *Shape* column are the names of the message shapes as displayed in the preceding orchestration.</span></span>  
  
|<span data-ttu-id="41b2e-202">形狀圖</span><span class="sxs-lookup"><span data-stu-id="41b2e-202">Shape</span></span>|<span data-ttu-id="41b2e-203">屬性</span><span class="sxs-lookup"><span data-stu-id="41b2e-203">Properties</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="41b2e-204">Receive_Request</span><span class="sxs-lookup"><span data-stu-id="41b2e-204">Receive_Request</span></span>|<span data-ttu-id="41b2e-205">-設定**訊息**至*要求*</span><span class="sxs-lookup"><span data-stu-id="41b2e-205">-   Set **Message** to *Request*</span></span><br /><span data-ttu-id="41b2e-206">-設定**作業**至*ReceiveMsgPort.Operation_1.Request*</span><span class="sxs-lookup"><span data-stu-id="41b2e-206">-   Set **Operation** to *ReceiveMsgPort.Operation_1.Request*</span></span>|  
|<span data-ttu-id="41b2e-207">Send_LOB</span><span class="sxs-lookup"><span data-stu-id="41b2e-207">Send_LOB</span></span>|<span data-ttu-id="41b2e-208">-設定**訊息**至*要求*</span><span class="sxs-lookup"><span data-stu-id="41b2e-208">-   Set **Message** to *Request*</span></span><br /><span data-ttu-id="41b2e-209">-設定**作業**至*SendToLOBPort.Operation_1.Request*</span><span class="sxs-lookup"><span data-stu-id="41b2e-209">-   Set **Operation** to *SendToLOBPort.Operation_1.Request*</span></span>|  
|<span data-ttu-id="41b2e-210">Receive_LOB</span><span class="sxs-lookup"><span data-stu-id="41b2e-210">Receive_LOB</span></span>|<span data-ttu-id="41b2e-211">-設定**訊息**至*回應*</span><span class="sxs-lookup"><span data-stu-id="41b2e-211">-   Set **Message** to *Response*</span></span><br /><span data-ttu-id="41b2e-212">-設定**作業**至*SendToLOBPort.Operation_1.Response*</span><span class="sxs-lookup"><span data-stu-id="41b2e-212">-   Set **Operation** to *SendToLOBPort.Operation_1.Response*</span></span>|  
|<span data-ttu-id="41b2e-213">Send_Response</span><span class="sxs-lookup"><span data-stu-id="41b2e-213">Send_Response</span></span>|<span data-ttu-id="41b2e-214">-設定**訊息**至*回應*</span><span class="sxs-lookup"><span data-stu-id="41b2e-214">-   Set **Message** to *Response*</span></span><br /><span data-ttu-id="41b2e-215">-設定**作業**至*SendMsgPort.Operation_1.Request*</span><span class="sxs-lookup"><span data-stu-id="41b2e-215">-   Set **Operation** to *SendMsgPort.Operation_1.Request*</span></span>|  
  
 <span data-ttu-id="41b2e-216">您指定這些屬性之後，連接的訊息 圖形和連接埠，而且您的協調流程已完成。</span><span class="sxs-lookup"><span data-stu-id="41b2e-216">After you have specified these properties, the message shapes and ports are connected and your orchestration is complete.</span></span>  
  
 <span data-ttu-id="41b2e-217">您現在必須建置 BizTalk 方案，並部署到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="41b2e-217">You must now build the BizTalk solution and deploy it to a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="41b2e-218">如需詳細資訊，請參閱[建置和執行協調流程](../../core/building-and-running-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="41b2e-218">For more information, see [Building and Running Orchestrations](../../core/building-and-running-orchestrations.md).</span></span>
  
## <a name="configuring-the-biztalk-application"></a><span data-ttu-id="41b2e-219">設定 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="41b2e-219">Configuring the BizTalk Application</span></span>  
 <span data-ttu-id="41b2e-220">部署 BizTalk 專案之後，您稍早建立的協調流程會列在**協調流程**BizTalk Server 管理主控台 窗格。</span><span class="sxs-lookup"><span data-stu-id="41b2e-220">After you have deployed the BizTalk project, the orchestration you created earlier is listed under the **Orchestrations** pane in the BizTalk Server Administration console.</span></span> <span data-ttu-id="41b2e-221">您必須使用 BizTalk Server 管理主控台來設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="41b2e-221">You must use the BizTalk Server Administration console to configure the application.</span></span> <span data-ttu-id="41b2e-222">如需有關如何設定應用程式的詳細資訊，請參閱[如何設定應用程式](../../core/how-to-configure-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="41b2e-222">For more information about configuring an application, see [How to Configure an Application](../../core/how-to-configure-an-application.md).</span></span>
  
 <span data-ttu-id="41b2e-223">設定應用程式包括：</span><span class="sxs-lookup"><span data-stu-id="41b2e-223">Configuring an application involves:</span></span>  
  
-   <span data-ttu-id="41b2e-224">選取應用程式的主機。</span><span class="sxs-lookup"><span data-stu-id="41b2e-224">Selecting a host for the application.</span></span>  
  
-   <span data-ttu-id="41b2e-225">對應至 BizTalk Server 管理主控台中的實體連接埠在協調流程中建立的連接埠。</span><span class="sxs-lookup"><span data-stu-id="41b2e-225">Mapping the ports that you created in your orchestration to physical ports in the BizTalk Server Administration console.</span></span> <span data-ttu-id="41b2e-226">此協調流程中，您必須：</span><span class="sxs-lookup"><span data-stu-id="41b2e-226">For this orchestration you must:</span></span>  
  
    -   <span data-ttu-id="41b2e-227">定義位置上的硬碟和對應的檔案連接埠，您將在此置放要求訊息。</span><span class="sxs-lookup"><span data-stu-id="41b2e-227">Define a location on the hard disk and a corresponding file port where you will drop a request message.</span></span> <span data-ttu-id="41b2e-228">BizTalk 協調流程會使用要求訊息，並將它傳送至 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="41b2e-228">The BizTalk orchestration will consume the request message and send it to the SAP system.</span></span>  
  
    -   <span data-ttu-id="41b2e-229">定義位置上的硬碟和對應的檔案連接埠，BizTalk 協調流程將會卸除包含 SAP 系統從回應的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="41b2e-229">Define a location on the hard disk and a corresponding file port where the BizTalk orchestration will drop the response message containing the response from the SAP system.</span></span>  
  
    -   <span data-ttu-id="41b2e-230">定義將訊息傳送至 SAP 系統實體 Wcf-custom 或 WCF SAP 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="41b2e-230">Define a physical WCF-Custom or WCF-SAP send port to send messages to the SAP system.</span></span> <span data-ttu-id="41b2e-231">您也必須在傳送埠中指定的動作。</span><span class="sxs-lookup"><span data-stu-id="41b2e-231">You must also specify the action in the send port.</span></span> <span data-ttu-id="41b2e-232">如需如何建立連接埠相關資訊，請參閱[以手動方式設定 SAP 配接器的實體連接埠繫結](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="41b2e-232">For information about how to create ports, see [Manually configure a physical port binding to the SAP adapter](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md).</span></span>
  
        > [!NOTE]
        >  <span data-ttu-id="41b2e-233">產生結構描述使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]也會建立包含連接埠與那些連接埠的設定動作的相關資訊的繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="41b2e-233">Generating the schema using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] also creates a binding file containing information about the ports and the actions to be set for those ports.</span></span> <span data-ttu-id="41b2e-234">您可以從 BizTalk Server 管理主控台來建立 （適用於傳出呼叫） 的傳送埠或接收埠 （適用於進行傳入呼叫時），以匯入此繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="41b2e-234">You can import this binding file from the BizTalk Server Administration console to create send ports (for outbound calls) or receive ports (for inbound calls).</span></span> <span data-ttu-id="41b2e-235">如需詳細資訊，請參閱[設定實體連接埠繫結使用連接埠繫結檔案至 SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="41b2e-235">For more information, see [Configure a physical port binding using a port binding file to SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md).</span></span>
  
## <a name="starting-the-application"></a><span data-ttu-id="41b2e-236">啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="41b2e-236">Starting the Application</span></span>  
 <span data-ttu-id="41b2e-237">您必須啟動叫用 RFC，SAP 系統中的 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="41b2e-237">You must start the BizTalk application for invoking an RFC in the SAP system.</span></span> <span data-ttu-id="41b2e-238">如需啟動 BizTalk 應用程式的指示，請參閱[如何啟動協調流程](../../core/how-to-start-an-orchestration.md)或[如何啟動應用程式](../../core/how-to-start-and-stop-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="41b2e-238">For instructions on starting a BizTalk application, see [How to Start an Orchestration](../../core/how-to-start-an-orchestration.md) or [how to start an application](../../core/how-to-start-and-stop-a-biztalk-application.md).</span></span>
  
 <span data-ttu-id="41b2e-239">在這個階段，請確定：</span><span class="sxs-lookup"><span data-stu-id="41b2e-239">At this stage, make sure:</span></span>  
  
-   <span data-ttu-id="41b2e-240">FILE 接收埠以接收要求訊息的協調流程執行。</span><span class="sxs-lookup"><span data-stu-id="41b2e-240">The FILE receive port to receive request messages for the orchestration is running.</span></span>  
  
-   <span data-ttu-id="41b2e-241">FILE 傳送埠，以接收回應訊息從協調流程正在執行。</span><span class="sxs-lookup"><span data-stu-id="41b2e-241">The FILE send port to receive the response messages from the orchestration is running.</span></span>  
  
-   <span data-ttu-id="41b2e-242">Wcf-custom 或 WCF SAP 傳送埠將訊息傳送至 SAP 系統正在執行。</span><span class="sxs-lookup"><span data-stu-id="41b2e-242">The WCF-Custom or WCF-SAP send port to send messages to the SAP system is running.</span></span>  
  
-   <span data-ttu-id="41b2e-243">BizTalk 協調流程的作業正在執行。</span><span class="sxs-lookup"><span data-stu-id="41b2e-243">The BizTalk orchestration for the operation is running.</span></span>  
  
## <a name="executing-the-operation"></a><span data-ttu-id="41b2e-244">執行作業</span><span class="sxs-lookup"><span data-stu-id="41b2e-244">Executing the Operation</span></span>  
 <span data-ttu-id="41b2e-245">執行應用程式之後，您必須在預先定義的位置中卸除協調流程的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="41b2e-245">After you run the application, you must drop a request message for the orchestration at a predefined location.</span></span> <span data-ttu-id="41b2e-246">請參閱[RFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)知道 SAP 系統中叫用 RFC 的要求訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="41b2e-246">See [Message Schemas for RFC Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md) to know about the schema for the request message for invoking an RFC in an SAP system.</span></span> <span data-ttu-id="41b2e-247">例如，要叫用 RFC_CUSTOMER_GET 的要求訊息是：</span><span class="sxs-lookup"><span data-stu-id="41b2e-247">For example, the request message to invoke RFC_CUSTOMER_GET is:</span></span>  
  
```  
<RFC_CUSTOMER_GET xmlns="http://Microsoft.LobServices.Sap/2007/03/Rfc/">  
  <KUNNR>0000001390</KUNNR>  
  <NAME1>*</NAME1>  
  <CUSTOMER_T/>  
</RFC_CUSTOMER_GET>  
```  
  
 <span data-ttu-id="41b2e-248">協調流程取用訊息，並將它傳送至 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="41b2e-248">The orchestration consumes the message and sends it to the SAP system.</span></span> <span data-ttu-id="41b2e-249">從 SAP 系統的回應會儲存在其他的協調流程中定義的檔案位置。</span><span class="sxs-lookup"><span data-stu-id="41b2e-249">The response from the SAP system is saved at other file location defined as part of the orchestration.</span></span> <span data-ttu-id="41b2e-250">比方說，是來自上述的要求訊息的 SAP 系統的回應：</span><span class="sxs-lookup"><span data-stu-id="41b2e-250">For example, the response from the SAP system for the above request message is:</span></span>  
  
```  
\<?xml version="1.0" encoding="utf-8" ?>   
<RFC_CUSTOMER_GETResponse xmlns="http://Microsoft.LobServices.Sap/2007/03/Rfc/">  
  <CUSTOMER_T>  
    <RFCCUST xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
      <KUNNR>0000001390</KUNNR>   
      <ANRED>Firma</ANRED>   
      <NAME1>Contoso, Ltd.</NAME1>   
      <PFACH />   
      <STRAS>4567 Main Street</STRAS>   
      <PSTLZ>98052</PSTLZ>   
      <ORT01>USA</ORT01>   
      <TELF1>555-0101</TELF1>   
      <TELFX>555-0102</TELFX>   
    </RFCCUST>  
  </CUSTOMER_T>  
</RFC_CUSTOMER_GETResponse>  
```  
  
## <a name="possible-exceptions"></a><span data-ttu-id="41b2e-251">可能的例外狀況</span><span class="sxs-lookup"><span data-stu-id="41b2e-251">Possible Exceptions</span></span>  
 <span data-ttu-id="41b2e-252">如需時叫用 RFC，SAP 系統使用 BizTalk Server 中可能會遇到的例外狀況資訊，請參閱[例外狀況和錯誤處理與 SAP 配接器](../../adapters-and-accelerators/adapter-sap/exceptions-and-error-handling-with-the-sap-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="41b2e-252">For information about the exceptions you might encounter while invoking an RFC in an SAP system using BizTalk Server, see [Exceptions and Error Handling with the SAP adapter](../../adapters-and-accelerators/adapter-sap/exceptions-and-error-handling-with-the-sap-adapter.md).</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="41b2e-253">最佳作法</span><span class="sxs-lookup"><span data-stu-id="41b2e-253">Best Practices</span></span>  
 <span data-ttu-id="41b2e-254">您部署和設定 BizTalk 專案之後，您可以為 XML 檔案，稱為繫結檔案匯出組態設定。</span><span class="sxs-lookup"><span data-stu-id="41b2e-254">After you have deployed and configured the BizTalk project, you can export configuration settings to an XML file called the bindings file.</span></span> <span data-ttu-id="41b2e-255">一旦產生繫結檔案時，您可以匯入組態設定從檔案，因此您不需要建立傳送埠、 接收埠，等。 針對相同的協調流程。</span><span class="sxs-lookup"><span data-stu-id="41b2e-255">Once you generate a bindings file, you can import the configuration settings from the file so that you do not need to create the send ports, receive ports, etc. for the same orchestration.</span></span> <span data-ttu-id="41b2e-256">如需繫結檔案的詳細資訊，請參閱[重複使用的 SAP 配接器繫結](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="41b2e-256">For more information about binding files, see [Reuse SAP adapter bindings](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41b2e-257">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41b2e-257">See Also</span></span>  
[<span data-ttu-id="41b2e-258">開發 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="41b2e-258">Develop BizTalk applications</span></span>](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)