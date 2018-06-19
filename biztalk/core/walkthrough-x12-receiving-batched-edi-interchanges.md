---
title: 逐步解說 (X12)： 接收批次的 EDI 交換 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f6e6e96-39ec-469d-a845-1bfdce6cc0bf
caps.latest.revision: 34
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 95c4bb48805eb0d2b349a8802c0bc8af1d12925a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25975718"
---
# <a name="walkthrough-x12-receiving-batched-edi-interchanges"></a><span data-ttu-id="3155e-102">逐步解說 (X12)：接收批次 EDI 交換</span><span class="sxs-lookup"><span data-stu-id="3155e-102">Walkthrough (X12): Receiving Batched EDI Interchanges</span></span>
<span data-ttu-id="3155e-103">本逐步解說提供一組逐步執行的程序，來使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 建立可接收 EDI 批次的解決方案。</span><span class="sxs-lookup"><span data-stu-id="3155e-103">This walkthrough provides a set of step-by-step procedures that creates a solution for receiving EDI batches using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="3155e-104">這個解決方案示範了兩種接收批次 EDI 交換的方法。</span><span class="sxs-lookup"><span data-stu-id="3155e-104">This solution demonstrates two ways to receive a batched EDI interchange:</span></span>  
  
-   <span data-ttu-id="3155e-105">透過將批次分割為其構成交易集。</span><span class="sxs-lookup"><span data-stu-id="3155e-105">By splitting the batch into its constituent transaction sets.</span></span>  
  
-   <span data-ttu-id="3155e-106">透過保留交換，做法是以單一文件的方式處理交換而不分割交易集。</span><span class="sxs-lookup"><span data-stu-id="3155e-106">By preserving the interchange by processing the interchange as one document without splitting the transaction sets.</span></span>  
  
 <span data-ttu-id="3155e-107">本逐步解說示範如何同時設定分割和保留批次。</span><span class="sxs-lookup"><span data-stu-id="3155e-107">This walkthrough demonstrates how to configure both splitting and preserving batches.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3155e-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="3155e-108">Prerequisites</span></span>  
 <span data-ttu-id="3155e-109">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="3155e-109">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
## <a name="how-the-solution-splits-received-edi-batches"></a><span data-ttu-id="3155e-110">解決方案如何分割收到的 EDI 批次</span><span class="sxs-lookup"><span data-stu-id="3155e-110">How the Solution Splits Received EDI Batches</span></span>  
 <span data-ttu-id="3155e-111">當您設定解決方案以便將批次交換分割為其組成交易集時，解決方案將會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="3155e-111">When you configure the solution to split the batched interchange into its constituent transaction sets, the solution will do the following:</span></span>  
  
1.  <span data-ttu-id="3155e-112">接收位置從合作對象接收包含多個交易集的批次 EDI 交換。</span><span class="sxs-lookup"><span data-stu-id="3155e-112">The receive location receives a batched EDI interchange containing multiple transaction sets from a party.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3155e-113">這份清單中的事件可能不會按照所示的順序發生。</span><span class="sxs-lookup"><span data-stu-id="3155e-113">The events in this list may not occur in the order shown.</span></span>  
  
2.  <span data-ttu-id="3155e-114">接收管線將收到的交換分割為其組成交易集，並將交易集轉換成內部 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="3155e-114">The receive pipeline splits the received interchange into its constituent transaction sets, converting the transaction sets into internal XML format.</span></span>  
  
3.  <span data-ttu-id="3155e-115">接收管線將整個交易和群組標頭升級至每個從交換分割出來的交易集內容中。</span><span class="sxs-lookup"><span data-stu-id="3155e-115">The receive pipeline promotes the entire interchange and group headers into the context of each transaction set split from the interchange.</span></span> <span data-ttu-id="3155e-116">此外還會升級特定交換和群組標頭，例如 ISA6、GS1 和 GS2，如此就能使用這些欄位進行路由。</span><span class="sxs-lookup"><span data-stu-id="3155e-116">It also promotes certain specific interchange and group headers, such as ISA6, GS1, and GS2, so that these fields can be used for routing.</span></span>  
  
4.  <span data-ttu-id="3155e-117">接收管線將每個交易集 XML 檔案放入 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="3155e-117">The receive pipeline drops each transaction set XML file into the MessageBox.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3155e-118">在這個解決方案中，批次中包含相同訊息類型的多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="3155e-118">In this solution, the batch contains multiple instances of the same message type.</span></span>  
  
5.  <span data-ttu-id="3155e-119">傳送埠透過訂閱適當的內容屬性來收取每個交易集。</span><span class="sxs-lookup"><span data-stu-id="3155e-119">The send port picks up each transaction set by subscribing on an appropriate context property.</span></span>  
  
6.  <span data-ttu-id="3155e-120">傳送管線將每個交易集建置成 EDI 交換，然後將交換傳送至目的地。</span><span class="sxs-lookup"><span data-stu-id="3155e-120">The send pipeline builds each transaction set into an EDI interchange, and then sends the interchange to the destination.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3155e-121">如需有關如何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]分割交易集批次，請參閱[分割批次 EDI 交換](../core/splitting-a-batched-edi-interchange.md)。</span><span class="sxs-lookup"><span data-stu-id="3155e-121">For more information on how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] splits the transaction sets in a batch, see [Splitting a Batched EDI Interchange](../core/splitting-a-batched-edi-interchange.md).</span></span>  
  
 <span data-ttu-id="3155e-122">下圖顯示設定解決方案以分割批次交換中的交易集時，該解決方案的架構和訊息流程。</span><span class="sxs-lookup"><span data-stu-id="3155e-122">The following figure shows the architecture and message flow of the solution when it is configured to split the transaction sets in the batched interchange.</span></span>  
  
 <span data-ttu-id="3155e-123">![分割批次的 EDI 交換](../core/media/ef386df6-e195-45d9-abff-4d0bd3a82a4f.gif "ef386df6-e195-45d9-abff-4d0bd3a82a4f")</span><span class="sxs-lookup"><span data-stu-id="3155e-123">![Splitting batched EDI interchanges](../core/media/ef386df6-e195-45d9-abff-4d0bd3a82a4f.gif "ef386df6-e195-45d9-abff-4d0bd3a82a4f")</span></span>  
  
## <a name="how-the-solution-preserves-received-edi-batches"></a><span data-ttu-id="3155e-124">解決方案如何保留收到的 EDI 批次</span><span class="sxs-lookup"><span data-stu-id="3155e-124">How the Solution Preserves Received EDI Batches</span></span>  
 <span data-ttu-id="3155e-125">當您設定解決方案以保留批次交換時，解決方案將會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="3155e-125">When you configure the solution to preserve the batched interchange, the solution will do the following:</span></span>  
  
1.  <span data-ttu-id="3155e-126">接收位置從合作對象接收包含多個交易集的批次 EDI 交換。</span><span class="sxs-lookup"><span data-stu-id="3155e-126">The receive location receives a batched EDI interchange containing multiple transaction sets from the party.</span></span>  
  
2.  <span data-ttu-id="3155e-127">接收管線處理交換但不分割交易集，並將兩個交易集視為一個單位轉換成內部 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="3155e-127">The receive pipeline process the interchange without splitting the transaction sets, converting the two transaction sets as a unit into internal XML format.</span></span>  
  
3.  <span data-ttu-id="3155e-128">接收管線升級相同的屬性，如同交換不是批次的情況一樣，唯一的不同是它會在產生的 XML 上套用保留標記。</span><span class="sxs-lookup"><span data-stu-id="3155e-128">The receive pipeline promotes the same properties as if the interchange were not a batch, with the exception that it will applied a reserved tag to the XML that it generates.</span></span> <span data-ttu-id="3155e-129">此標記是\<X12InterchangeXml\>針對 X12 編碼的 EDI 交換或\<EdifactInterchangeXml\>針對 EDIFACT 編碼的 EDI 交換。</span><span class="sxs-lookup"><span data-stu-id="3155e-129">This tag is \<X12InterchangeXml\> for an X12-encoded EDI interchange or \<EdifactInterchangeXml\> for an EDIFACT-encoded EDI interchange.</span></span> <span data-ttu-id="3155e-130">EDI 接收管線也會套用內容屬性 `ReuseEnvelope`，以識別保留的交換。</span><span class="sxs-lookup"><span data-stu-id="3155e-130">The EDI receive pipeline also applies the context property `ReuseEnvelope` to identify the interchange as preserved.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3155e-131">EDI 傳送管線會使用\<X12InterchangeXml\>或\<EdifactInterchangeXml\>標記來識別為保留的批次訊息。</span><span class="sxs-lookup"><span data-stu-id="3155e-131">The EDI send pipeline uses the \<X12InterchangeXml\> or \<EdifactInterchangeXml\> tag to identify the message as a preserved batch.</span></span> <span data-ttu-id="3155e-132">`ReuseEnvelope` 內容屬性可讓您建立傳送埠，以訂閱保留的所有批次交換。</span><span class="sxs-lookup"><span data-stu-id="3155e-132">The `ReuseEnvelope` context property enables you to create a send port that subscribes to all batched interchanges that are preserved.</span></span>  
  
4.  <span data-ttu-id="3155e-133">接收管線會將訊息 XML 檔案放置在 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="3155e-133">The receive pipeline drops the message XML file into the MessageBox.</span></span>  
  
5.  <span data-ttu-id="3155e-134">傳送埠透過訂閱適當的內容屬性來收取交換。</span><span class="sxs-lookup"><span data-stu-id="3155e-134">The send port picks up the interchange by subscribing on an appropriate context property.</span></span>  
  
6.  <span data-ttu-id="3155e-135">傳送管線將 XML 檔案中的兩個交易集建置成批次 EDI 交換，然後將交換傳送到目的地。</span><span class="sxs-lookup"><span data-stu-id="3155e-135">The send pipeline builds the two transaction sets in the XML file into a batched EDI interchange, and then sends the interchange to the destination.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3155e-136">如需有關如何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理保留批次，請參閱[保留收到批次 EDI 交換](../core/preserving-a-received-batched-edi-interchange.md)。</span><span class="sxs-lookup"><span data-stu-id="3155e-136">For more information on how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes a preserved batch, see [Preserving a Received Batched EDI Interchange](../core/preserving-a-received-batched-edi-interchange.md).</span></span>  
  
## <a name="functionality-in-this-solution"></a><span data-ttu-id="3155e-137">本解決方案中的功能</span><span class="sxs-lookup"><span data-stu-id="3155e-137">Functionality in this Solution</span></span>  
 <span data-ttu-id="3155e-138">為了完成這個逐步解說，將會啟用下列功能：</span><span class="sxs-lookup"><span data-stu-id="3155e-138">For the purposes of this walkthrough, the following functionality will be enabled:</span></span>  
  
-   <span data-ttu-id="3155e-139">這個解決方案是專為使用 X12 編碼 (而非 EDIFACT 編碼) 的交換所設計。</span><span class="sxs-lookup"><span data-stu-id="3155e-139">The solution is designed for interchanges using X12 encoding, not EDIFACT encoding.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3155e-140">用於 HIPAA 與 EDIFACT 編碼的組態，與用於 X12 編碼的組態近乎相同。</span><span class="sxs-lookup"><span data-stu-id="3155e-140">The configuration used for HIPAA and for EDIFACT encoding is closely parallel to that used for X12 encoding.</span></span>  
  
-   <span data-ttu-id="3155e-141">將不會傳回技術或功能通知，以回應原本收到的交換或任何傳送的批次交換。</span><span class="sxs-lookup"><span data-stu-id="3155e-141">Technical or functional acknowledgments will not be returned in response to the interchange originally received or any batched interchange that is sent.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3155e-142">如需產生 EDI 通知的資訊，請參閱[(X12) 逐步解說： 接收 EDI 交換並傳送傳回通知](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md)。</span><span class="sxs-lookup"><span data-stu-id="3155e-142">For information about generating EDI acknowledgments, see [Walkthrough (X12): Receiving EDI Interchanges and Sending Back an Acknowledgement](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md).</span></span>  
  
-   <span data-ttu-id="3155e-143">這個解決方案會使用單向接收埠和靜態單向傳送埠，</span><span class="sxs-lookup"><span data-stu-id="3155e-143">This solution uses a one-way receive port and a static one-way send port.</span></span> <span data-ttu-id="3155e-144">因此會將這些連接埠設定為 FILE 傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="3155e-144">These ports will be configured with the FILE transport type.</span></span>  
  
-   <span data-ttu-id="3155e-145">將會啟用 EDI 報告。</span><span class="sxs-lookup"><span data-stu-id="3155e-145">EDI reporting will be enabled.</span></span>  
  
-   <span data-ttu-id="3155e-146">將會儲存交易集，以從交換狀態報告中檢視交易集。</span><span class="sxs-lookup"><span data-stu-id="3155e-146">Transaction sets will be saved for viewing from the interchange status report.</span></span>  
  
-   <span data-ttu-id="3155e-147">為了測試目的，解決方案會使用傳送埠將分割的交換或保留批次傳送至本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="3155e-147">For testing purposes, the solution uses a send ports to send the split interchanges or the preserved batch to a local folder.</span></span>  
  
## <a name="configuring-and-testing-the-walkthrough"></a><span data-ttu-id="3155e-148">設定和測試逐步解說</span><span class="sxs-lookup"><span data-stu-id="3155e-148">Configuring and Testing the Walkthrough</span></span>  
 <span data-ttu-id="3155e-149">這個解決方案所需的程序包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="3155e-149">The procedures required for this solution include the following:</span></span>  
  
-   <span data-ttu-id="3155e-150">將必要的訊息結構描述加入 BizTalk 專案，然後建置並部署此專案，因此 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可以使用此結構描述處理訊息。</span><span class="sxs-lookup"><span data-stu-id="3155e-150">Add the required message schema(s) to a BizTalk project, and then build and deploy the project, making the schema(s) available for use by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in processing the messages.</span></span>  
  
-   <span data-ttu-id="3155e-151">建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的接收埠，以接收來自合作對象的 EDI X12 編碼 .txt 批次輸入訊息。</span><span class="sxs-lookup"><span data-stu-id="3155e-151">Create a receive port for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to receive the EDI X12-encoded .txt batched input message from a party.</span></span>  
  
-   <span data-ttu-id="3155e-152">建立傳送埠，以供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 利用批次中收到的每個交易集來建置交換 (如果分割批次的話)，或是使用接收之批次中的交易集來建置單一交換 (如果保留批次的話)。</span><span class="sxs-lookup"><span data-stu-id="3155e-152">Create a send port for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to build an interchange out of each transaction sets received in the batch (if splitting the batch), or to build a single interchange from the transaction sets in the received batch (if preserving the batch).</span></span> <span data-ttu-id="3155e-153">接著傳送埠會將交換傳送至目的合作對象。</span><span class="sxs-lookup"><span data-stu-id="3155e-153">The send port then sends the interchange or interchanges to the destination party.</span></span> <span data-ttu-id="3155e-154">此傳送埠將是靜態單向傳送埠。</span><span class="sxs-lookup"><span data-stu-id="3155e-154">This send port will be a static one-way send port.</span></span>  
  
-   <span data-ttu-id="3155e-155">為合作對象 A 與合作對象 B 建立合作對象 (交易夥伴)。</span><span class="sxs-lookup"><span data-stu-id="3155e-155">Create a party (trading partner) for both Party A and Party B.</span></span>  
  
-   <span data-ttu-id="3155e-156">分別為兩個交易夥伴建立商務設定檔。</span><span class="sxs-lookup"><span data-stu-id="3155e-156">Create a business profile each for both the trading partners.</span></span>  
  
-   <span data-ttu-id="3155e-157">透過分割或保留交換，設定 EDI 屬性以接收訊息，在兩個設定檔之間建立協議。</span><span class="sxs-lookup"><span data-stu-id="3155e-157">Create an agreement between the two profiles by configuring the EDI properties to receive the message by splitting or preserving the interchange.</span></span>  
  
-   <span data-ttu-id="3155e-158">將一個批次 EDI 交換放入與接收位置關聯的本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="3155e-158">Drop one batched EDI interchange into the local folder associated with the receive location.</span></span> <span data-ttu-id="3155e-159">接著您可以確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 是否已將接收之批次中的個別交換 (如果分割批次的話) 或單一保留的批次交換 (如果保留批次的話) 放入與傳送埠關聯的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="3155e-159">You can then verify that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] has dropped the separate interchanges from the received batch (if splitting the batch) or the single preserved batched interchange (if preserving the batch) into the folder associated with the send port.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3155e-160">如果您已經執行傳送批次交換逐步解說中的步驟，可以使用來自該解決方案的輸出做為此解決方案的輸入。</span><span class="sxs-lookup"><span data-stu-id="3155e-160">If you have performed the steps in the sending batched interchanges walkthrough, you can use the output from that solution as the input for this solution.</span></span> <span data-ttu-id="3155e-161">該解決方案的輸出是兩則 850 訊息的批次。</span><span class="sxs-lookup"><span data-stu-id="3155e-161">The output from that solution is a batch of two 850 messages.</span></span> <span data-ttu-id="3155e-162">如需詳細資訊，請參閱[(X12) 逐步解說： 傳送批次 EDI 交換](../core/walkthrough-x12-sending-batched-edi-interchanges.md)。</span><span class="sxs-lookup"><span data-stu-id="3155e-162">For more information, see [Walkthrough (X12): Sending Batched EDI Interchanges](../core/walkthrough-x12-sending-batched-edi-interchanges.md).</span></span>  
  
 <span data-ttu-id="3155e-163">本節說明設定逐步解說的程序。</span><span class="sxs-lookup"><span data-stu-id="3155e-163">This section describes the procedures to configure the walkthrough.</span></span>  
  
##### <a name="to-deploy-the-message-schema"></a><span data-ttu-id="3155e-164">若要部署訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="3155e-164">To deploy the message schema</span></span>  
  
1.  <span data-ttu-id="3155e-165">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，建立或開啟 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="3155e-165">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create or open a BizTalk project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3155e-166">本主題假設您已經在「BizTalk EDI 應用程式」中加入了自己應用程式的參考 (包含 EDI 結構描述、管線和協調流程)，</span><span class="sxs-lookup"><span data-stu-id="3155e-166">This topic assumes that you have already added a reference from your application to the BizTalk EDI Application, which contains EDI schemas, pipelines, and orchestrations.</span></span> <span data-ttu-id="3155e-167">如果沒有，請參閱[如何將參考加入至 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。</span><span class="sxs-lookup"><span data-stu-id="3155e-167">If not, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).</span></span>  
  
2.  <span data-ttu-id="3155e-168">以滑鼠右鍵按一下您的專案，指向**新增**，然後按一下 **現有項目**。</span><span class="sxs-lookup"><span data-stu-id="3155e-168">Right-click your project, point to **Add**, and then click **Existing Item**.</span></span> <span data-ttu-id="3155e-169">移至**\<磁碟機\>: \Program Files\Microsoft BizTalk Server 2009\XSD_Schema\EDI\X12\00401**，然後按兩下測試訊息的對應結構描述。</span><span class="sxs-lookup"><span data-stu-id="3155e-169">Move to **\<drive\>:\Program Files\Microsoft BizTalk Server 2009\XSD_Schema\EDI\X12\00401**, and then double-click the schema corresponding to your test message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3155e-170">如果 EDI 結構描述尚未解壓縮至 XSD_SchemaEDI 資料夾，執行**MicrosoftEdiXSDTemplates.exe** XSD_SchemaEDI 資料夾結構描述解壓縮至預設資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="3155e-170">If the EDI schemas have not been unzipped into the XSD_SchemaEDI folders, execute the **MicrosoftEdiXSDTemplates.exe** file in the XSD_SchemaEDI folder to unzip the schemas into the default folder.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3155e-171">針對測試訊息，您可以使用傳送批次交換逐步解說中解決方案所產生的批次交換。</span><span class="sxs-lookup"><span data-stu-id="3155e-171">For a test message, you can use the batched interchange generated by the solution in the sending batched interchanges walkthrough.</span></span> <span data-ttu-id="3155e-172">該解決方案的輸出是兩個用於「EDI 介面開發人員」教學課程之 850 範例訊息執行個體的批次。</span><span class="sxs-lookup"><span data-stu-id="3155e-172">The output from that solution is a batch of two instances of the 850 sample message used for the EDI Interface Developer tutorial.</span></span> <span data-ttu-id="3155e-173">如果您這樣做，您必須使用中的結構描述 x12_00401_850.xsd [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDKEDI 介面開發人員 TutorialInbound_EDI。</span><span class="sxs-lookup"><span data-stu-id="3155e-173">If you do so, you must use the schema x12_00401_850.xsd located in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDKEDI Interface Developer TutorialInbound_EDI.</span></span>  
  
3.  <span data-ttu-id="3155e-174">設定組件金鑰檔案，然後建置並部署組件。</span><span class="sxs-lookup"><span data-stu-id="3155e-174">Set the assembly key file, and then build and deploy the assembly.</span></span>  
  
##### <a name="to-create-a-one-way-receive-port-to-receive-the-batched-edi-messages"></a><span data-ttu-id="3155e-175">建立單向接收埠以接收要批次處理的 EDI 訊息</span><span class="sxs-lookup"><span data-stu-id="3155e-175">To create a one-way receive port to receive the batched EDI messages</span></span>  
  
1.  <span data-ttu-id="3155e-176">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**接收埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **單向接收埠。**</span><span class="sxs-lookup"><span data-stu-id="3155e-176">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Receive Ports** node under the **BizTalk Application 1** node, point to **New**, and then click **One-way Receive Port.**</span></span>  
  
2.  <span data-ttu-id="3155e-177">將接收連接埠，再按一下**接收位置**在主控台樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="3155e-177">Name the receive port, and then click **Receive Locations** in the console tree.</span></span>  
  
3.  <span data-ttu-id="3155e-178">按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="3155e-178">Click **New**.</span></span>  
  
4.  <span data-ttu-id="3155e-179">接收位置命名，選取**檔案**如**類型**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="3155e-179">Name the receive location, select **FILE** for **Type**, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="3155e-180">輸入的資料夾**接收資料夾**，和遮罩**檔案遮罩**，例如 **\*.txt**。</span><span class="sxs-lookup"><span data-stu-id="3155e-180">Enter a folder for **Receive folder**, and a mask for **File Mask**, such as **\*.txt**.</span></span>  
  
6.  <span data-ttu-id="3155e-181">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="3155e-181">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="3155e-182">如**接收管線**，選取**EdiReceive**。</span><span class="sxs-lookup"><span data-stu-id="3155e-182">For **Receive pipeline**, select **EdiReceive**.</span></span>  
  
8.  <span data-ttu-id="3155e-183">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="3155e-183">Click **OK**.</span></span>  
  
9. <span data-ttu-id="3155e-184">在主控台樹狀目錄中，按一下**接收位置**。</span><span class="sxs-lookup"><span data-stu-id="3155e-184">In the console tree, click **Receive Locations**.</span></span> <span data-ttu-id="3155e-185">在**接收位置** 窗格中，以滑鼠右鍵按一下您接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="3155e-185">In the **Receive Locations** pane, right-click your receive location, and then click **Enable**.</span></span>  
  
##### <a name="to-create-a-static-one-way-send-port-to-send-the-batched-edi-interchange"></a><span data-ttu-id="3155e-186">若要建立靜態單向傳送埠以傳送批次 EDI 交換</span><span class="sxs-lookup"><span data-stu-id="3155e-186">To create a static one-way send port to send the batched EDI interchange</span></span>  
  
1.  <span data-ttu-id="3155e-187">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **靜態單向傳送埠。**</span><span class="sxs-lookup"><span data-stu-id="3155e-187">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Send Ports** node under the **BizTalk Application 1** node, point to **New**, and then click **Static One-way Send Port.**</span></span>  
  
2.  <span data-ttu-id="3155e-188">在**傳送埠屬性**對話方塊、 傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="3155e-188">In the **Send Port Properties** dialog box, name the send port.</span></span>  
  
3.  <span data-ttu-id="3155e-189">在**傳輸**區段中，選取**檔案**如**類型**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="3155e-189">In the **Transport** section, select **FILE** for **Type**, and then click **Configure**.</span></span>  
  
4.  <span data-ttu-id="3155e-190">輸入的資料夾**目的地資料夾**，和遮罩**檔案遮罩**，例如 **\*.txt**。</span><span class="sxs-lookup"><span data-stu-id="3155e-190">Enter a folder for **Destination folder**, and a mask for **File Mask**, such as **\*.txt**.</span></span>  
  
5.  <span data-ttu-id="3155e-191">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="3155e-191">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="3155e-192">在**傳送管線**，選取**EdiSend**。</span><span class="sxs-lookup"><span data-stu-id="3155e-192">In **Send pipeline**, select **EdiSend**.</span></span>  
  
7.  <span data-ttu-id="3155e-193">在主控台樹狀目錄中，選取**篩選**。</span><span class="sxs-lookup"><span data-stu-id="3155e-193">In the console tree, select **Filters**.</span></span> <span data-ttu-id="3155e-194">在**篩選**頁面上，輸入將訂閱的訊息批次中的篩選條件運算式。</span><span class="sxs-lookup"><span data-stu-id="3155e-194">On the **Filters** page, enter a filter expression that will subscribe to the messages in the batch.</span></span> <span data-ttu-id="3155e-195">例如，選取**BTS。ReceivePortName**如**屬性**，  **==** 如**運算子**，和您剛建立的的接收埠名稱**值**。</span><span class="sxs-lookup"><span data-stu-id="3155e-195">For example, select **BTS.ReceivePortName** for **Property**, **==** for **Operator**, and the name of the receive port that you just created for **Value**.</span></span>  
  
8.  <span data-ttu-id="3155e-196">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="3155e-196">Click **OK**.</span></span>  
  
9. <span data-ttu-id="3155e-197">在主控台樹狀目錄中，按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="3155e-197">In the console tree, click **Send Ports**.</span></span> <span data-ttu-id="3155e-198">在**傳送埠**] 窗格中，以滑鼠右鍵按一下您的傳送埠，然後按一下 [**啟動**。</span><span class="sxs-lookup"><span data-stu-id="3155e-198">In the **Send Ports** pane, right-click your send port, and then click **Start**.</span></span>  
  
##### <a name="to-create-a-party-and-a-business-profile-for-party-a"></a><span data-ttu-id="3155e-199">為合作對象 A 建立合作對象與商務設定檔</span><span class="sxs-lookup"><span data-stu-id="3155e-199">To create a party and a business profile for Party A</span></span>  
  
1.  <span data-ttu-id="3155e-200">以滑鼠右鍵按一下**合作對象**節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下 **合作對象**。</span><span class="sxs-lookup"><span data-stu-id="3155e-200">Right-click the **Parties** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, point to **New**, and then click **Party**.</span></span>  
  
2.  <span data-ttu-id="3155e-201">輸入的名稱中的合作對象**名稱**文字方塊，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="3155e-201">Enter a name for the party in the **Name** text box, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3155e-202">藉由選取**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定正在建立的合作對象為相同的組織同時裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3155e-202">By selecting the **Local BizTalk processes messages received by the Party OR supports sending messages from this party** check box, you can specify that the party being created is for the same organization that is also hosting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="3155e-203">據此，建立協議時將會啟用或停用某些屬性。</span><span class="sxs-lookup"><span data-stu-id="3155e-203">Based on that, some properties will be enabled or disabled when you create an agreement.</span></span> <span data-ttu-id="3155e-204">不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。</span><span class="sxs-lookup"><span data-stu-id="3155e-204">However, for this walkthrough, you can leave this check box selected.</span></span>  
  
3.  <span data-ttu-id="3155e-205">以滑鼠右鍵按一下合作對象名稱，指向**新增**，然後按一下 **商務設定檔**。</span><span class="sxs-lookup"><span data-stu-id="3155e-205">Right-click the party name, point to **New**, and then click **Business Profile**.</span></span>  
  
4.  <span data-ttu-id="3155e-206">在**設定檔屬性**對話方塊**一般**頁面上，輸入**PartyA_Profile**中**名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="3155e-206">In the **Profile Properties** dialog box, on the **General** page, enter **PartyA_Profile** in the **Name** text box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3155e-207">當您建立合作對象時，會同時建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="3155e-207">When you create a party, a profile is also created.</span></span> <span data-ttu-id="3155e-208">您可以重新命名再使用該設定檔，而不需建立新設定檔。</span><span class="sxs-lookup"><span data-stu-id="3155e-208">You can rename and use that profile instead of creating a new one.</span></span> <span data-ttu-id="3155e-209">若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="3155e-209">To rename a profile, right-click the profile and select **Properties**.</span></span> <span data-ttu-id="3155e-210">在**一般**頁面上，指定設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="3155e-210">In the **General** page, specify a name for the profile.</span></span>  
  
##### <a name="to-create-a-party-and-a-business-profile-for-party-b"></a><span data-ttu-id="3155e-211">若要為 Party B 建立合作對象與商務設定檔</span><span class="sxs-lookup"><span data-stu-id="3155e-211">To create a party and a business profile for Party B</span></span>  
  
1.  <span data-ttu-id="3155e-212">以滑鼠右鍵按一下**合作對象**節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下 **合作對象**。</span><span class="sxs-lookup"><span data-stu-id="3155e-212">Right-click the **Parties** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, point to **New**, and then click **Party**.</span></span>  
  
2.  <span data-ttu-id="3155e-213">輸入的名稱中的合作對象**名稱**文字方塊，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="3155e-213">Enter a name for the party in the **Name** text box, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3155e-214">藉由選取**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定正在建立的合作對象為相同的組織同時裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3155e-214">By selecting the **Local BizTalk processes messages received by the Party OR supports sending messages from this party** check box, you can specify that the party being created is for the same organization that is also hosting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="3155e-215">據此，建立協議時將會啟用或停用某些屬性。</span><span class="sxs-lookup"><span data-stu-id="3155e-215">Based on that, some properties will be enabled or disabled when you create an agreement.</span></span> <span data-ttu-id="3155e-216">不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。</span><span class="sxs-lookup"><span data-stu-id="3155e-216">However, for this walkthrough, you can leave this check box selected.</span></span>  
  
3.  <span data-ttu-id="3155e-217">以滑鼠右鍵按一下合作對象名稱，指向**新增**，然後按一下 **商務設定檔**。</span><span class="sxs-lookup"><span data-stu-id="3155e-217">Right-click the party name, point to **New**, and then click **Business Profile**.</span></span>  
  
4.  <span data-ttu-id="3155e-218">在**設定檔屬性**對話方塊**一般**頁面上，輸入**PartyB_Profile**中**名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="3155e-218">In the **Profile Properties** dialog box, on the **General** page, enter **PartyB_Profile** in the **Name** text box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3155e-219">當您建立合作對象時，會同時建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="3155e-219">When you create a party, a profile is also created.</span></span> <span data-ttu-id="3155e-220">您可以重新命名再使用該設定檔，而不需建立新設定檔。</span><span class="sxs-lookup"><span data-stu-id="3155e-220">You can rename and use that profile instead of creating a new one.</span></span> <span data-ttu-id="3155e-221">若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="3155e-221">To rename a profile, right-click the profile and select **Properties**.</span></span> <span data-ttu-id="3155e-222">在**一般**頁面上，指定設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="3155e-222">In the **General** page, specify a name for the profile.</span></span>  
  
##### <a name="to-create-an-agreement-between-the-two-business-profiles"></a><span data-ttu-id="3155e-223">在兩個商務設定檔之間建立協議</span><span class="sxs-lookup"><span data-stu-id="3155e-223">To create an agreement between the two business profiles</span></span>  
  
1.  <span data-ttu-id="3155e-224">以滑鼠右鍵按一下**PartyA_Profile**，指向 **新增**，然後按一下 **協議**。</span><span class="sxs-lookup"><span data-stu-id="3155e-224">Right-click **PartyA_Profile**, point to **New**, and then click **Agreement**.</span></span>  
  
2.  <span data-ttu-id="3155e-225">在**一般屬性** 頁面上，針對**名稱**文字方塊中，輸入協議的名稱。</span><span class="sxs-lookup"><span data-stu-id="3155e-225">In the **General Properties** page, for the **Name** text box, enter a name for the agreement.</span></span>  
  
3.  <span data-ttu-id="3155e-226">從**通訊協定**下拉式清單中，選取**X12**。</span><span class="sxs-lookup"><span data-stu-id="3155e-226">From the **Protocol** drop-down list, select **X12**.</span></span>  
  
4.  <span data-ttu-id="3155e-227">在**第二個夥伴** 區段中，從**名稱**下拉式清單中，選取**Party**。</span><span class="sxs-lookup"><span data-stu-id="3155e-227">In the **Second Partner** section, from the **Name** drop-down list, select **PartyB**.</span></span>  
  
5.  <span data-ttu-id="3155e-228">在**第二個夥伴** 區段中，從**設定檔**下拉式清單中，選取**PartyB_Profile**。</span><span class="sxs-lookup"><span data-stu-id="3155e-228">In the **Second Partner** section, from the **Profile** drop-down list, select **PartyB_Profile**.</span></span>  
  
     <span data-ttu-id="3155e-229">您會發現兩個新的索引標籤取得旁新增**一般** 索引標籤。每個索引標籤各用於設定一個單向協議，而每個單向協議各代表一筆完整的訊息交易 (包含訊息傳輸與通知傳輸)。</span><span class="sxs-lookup"><span data-stu-id="3155e-229">You will notice that two new tabs get added next to the **General** tab. Each tab is for configuring a one-way agreement and each one-way agreement represents one complete transaction of message (including message transfer and acknowledgement transfer).</span></span>  
  
6.  <span data-ttu-id="3155e-230">在**一般**索引標籤**一般屬性**頁面上，於**一般主控件設定**區段中，選取**開啟報告**，然後選取**儲存報告的訊息內容**。</span><span class="sxs-lookup"><span data-stu-id="3155e-230">In the **General** tab, on the **General Properties** page, in the **Common Host Settings** section, select **Turn ON reporting**, and then select **Store message payload for reporting**.</span></span>  
  
7.  <span data-ttu-id="3155e-231">在上執行下列工作**party a-> partyb**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3155e-231">Perform the following tasks on the **PartyA->PartyB** tab.</span></span>  
  
    1.  <span data-ttu-id="3155e-232">在**識別碼**頁面**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，和**ISA8**) 對應到您的測試訊息中標頭欄位的值。</span><span class="sxs-lookup"><span data-stu-id="3155e-232">On the **Identifiers** page under the **Interchange Settings** section, enter values for the qualifier and identifier fields (**ISA5**, **ISA6**, **ISA7**, and **ISA8**) that correspond to the values for those header fields in your test message.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="3155e-233">對於傳送者和接收者，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 需要辨識符號與識別碼欄位，才能執行協議解析。</span><span class="sxs-lookup"><span data-stu-id="3155e-233">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] requires the qualifier and identifier fields for sender and receiver in order to perform agreement resolution.</span></span> <span data-ttu-id="3155e-234">它會比對的值**ISA5**， **ISA6**， **ISA7**，和**ISA8**交換標頭與協議屬性中。</span><span class="sxs-lookup"><span data-stu-id="3155e-234">It will match the values of **ISA5**, **ISA6**, **ISA7**, and **ISA8** in the interchange header with those in the properties of an agreement.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3155e-235">也比對傳送者辨識符號和識別項 （不需接收者辨識符號和識別項） 來解析協議。</span><span class="sxs-lookup"><span data-stu-id="3155e-235"> will also resolve the agreement by matching the sender qualifier and identifier (without the receiver qualifier and identifier).</span></span> <span data-ttu-id="3155e-236">若 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法解析協議，它將會使用後援協議屬性。</span><span class="sxs-lookup"><span data-stu-id="3155e-236">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot resolve the agreement, it will use the fallback agreement properties.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="3155e-237">如果您使用 「 EDI 介面開發人員教學課程 」 中的 SamplePO.txt 檔案做為測試訊息，設定**ISA5**至**ZZ**， **ISA6**至**THEM**， **ISA7**至**ZZ**，和**ISA8**至**美國**。</span><span class="sxs-lookup"><span data-stu-id="3155e-237">If you are using the SamplePO.txt file from the “EDI Interface Developer Tutorial” as your test message, set **ISA5** to **ZZ**, **ISA6** to **THEM**, **ISA7** to **ZZ**, and **ISA8** to **US**.</span></span>  
  
    2.  <span data-ttu-id="3155e-238">在**驗證**頁面**交換設定**區段中，請確定**檢查重複的 ISA13**未選項。</span><span class="sxs-lookup"><span data-stu-id="3155e-238">On the **Validation** page under the **Interchange Settings** section, make sure **Check for duplicate ISA13** option is unchecked.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="3155e-239">清除**檢查重複的 ISA13**屬性可讓您接收相同訊息的多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="3155e-239">Clearing the **Check for duplicate ISA13** property enables you to receive multiple instances of the same message.</span></span>  
  
    3.  <span data-ttu-id="3155e-240">在**字元集和分隔符號**頁面**交換設定**區段中，選取**CR LF**選項。</span><span class="sxs-lookup"><span data-stu-id="3155e-240">On the **Charset and Separators** page under the **Interchange Settings** section, select the **CR LF** option.</span></span>  
  
    4.  <span data-ttu-id="3155e-241">在**本機主機設定**頁面**交換設定**區段的**輸入訊息處理選項**方塊中，選取**分割交換為交易集-發生錯誤時暫停交易集**選項。</span><span class="sxs-lookup"><span data-stu-id="3155e-241">On the **Local Host Settings** page under the **Interchange Settings** section, in the **Inbound Message Processing Option** box, select the **Split Interchange as Transaction Sets - suspend Transaction Sets on Error** option.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="3155e-242">我們在此解決方案中，一開始會選取此選項，來分割交換。</span><span class="sxs-lookup"><span data-stu-id="3155e-242">To start with, in this solution, we will split the interchange by selecting this option.</span></span> <span data-ttu-id="3155e-243">稍後一部分[以測試逐步解說](../core/walkthrough-x12-receiving-batched-edi-interchanges.md#BKMK_Proc)下列程序，我們會將解決方案設定為保留交換。</span><span class="sxs-lookup"><span data-stu-id="3155e-243">Later, as part of [To test the walkthrough](../core/walkthrough-x12-receiving-batched-edi-interchanges.md#BKMK_Proc) procedure below, we will configure the solution to preserve the interchange.</span></span>  
  
    5.  <span data-ttu-id="3155e-244">在**傳送埠**頁面**交換設定**區段中，將您稍早建立的傳送埠產生關聯。</span><span class="sxs-lookup"><span data-stu-id="3155e-244">On the **Send Ports** page under the **Interchange Settings** section, associate the send port that you created earlier.</span></span> <span data-ttu-id="3155e-245">在**傳送埠**方格下方**名稱**資料行，按一下空白儲存格，然後從下拉式清單中，選取 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="3155e-245">In the **Send ports** grid, under the **Name** column, click an empty cell, and from the drop-down list, select the send port.</span></span>  
  
    6.  <span data-ttu-id="3155e-246">在**信封**頁面**交易集設定**區段中，輸入在格線的第一行中的所有資料行的值。</span><span class="sxs-lookup"><span data-stu-id="3155e-246">On the **Envelopes** page under the **Transaction Set Settings** section, enter values for all columns in the first line of the grid.</span></span>  
  
        |<span data-ttu-id="3155e-247">使用</span><span class="sxs-lookup"><span data-stu-id="3155e-247">Use this</span></span>|<span data-ttu-id="3155e-248">動作</span><span class="sxs-lookup"><span data-stu-id="3155e-248">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="3155e-249">**預設值**</span><span class="sxs-lookup"><span data-stu-id="3155e-249">**Default**</span></span>|<span data-ttu-id="3155e-250">選取**預設**。</span><span class="sxs-lookup"><span data-stu-id="3155e-250">Select **Default**.</span></span> <span data-ttu-id="3155e-251">**注意：** 當您選取這個資料列的預設值為**GS1**， **GS2**， **GS3**， **GS7**，和**GS8**可用即使值**交易類型**，**版本/版次**，和**目標命名空間**都不符合訊息。</span><span class="sxs-lookup"><span data-stu-id="3155e-251">**Note:**  When you select this row as the default, the values for **GS1**, **GS2**, **GS3**, **GS7**, and **GS8** are used even if the values for **Transaction Type**, **Version/Release**, and **Target namespace** are not a match for the message.</span></span>|  
        |<span data-ttu-id="3155e-252">**交易類型**</span><span class="sxs-lookup"><span data-stu-id="3155e-252">**Transaction Type**</span></span>|<span data-ttu-id="3155e-253">選取的測試訊息，訊息類型**850-Purchase Order**。</span><span class="sxs-lookup"><span data-stu-id="3155e-253">Select the message type of your test message, **850 - Purchase Order**.</span></span>|  
        |<span data-ttu-id="3155e-254">**版本/版次**</span><span class="sxs-lookup"><span data-stu-id="3155e-254">**Version/Release**</span></span>|<span data-ttu-id="3155e-255">輸入 EDI 版本， **00401**。</span><span class="sxs-lookup"><span data-stu-id="3155e-255">Enter the EDI version, **00401**.</span></span>|  
        |<span data-ttu-id="3155e-256">**目標命名空間**</span><span class="sxs-lookup"><span data-stu-id="3155e-256">**Target namespace**</span></span>|<span data-ttu-id="3155e-257">選取**http://schemas.microsoft.com/Edi/X12**。</span><span class="sxs-lookup"><span data-stu-id="3155e-257">Select **http://schemas.microsoft.com/Edi/X12**.</span></span>|  
        |<span data-ttu-id="3155e-258">**GS1**</span><span class="sxs-lookup"><span data-stu-id="3155e-258">**GS1**</span></span>|<span data-ttu-id="3155e-259">確認已選取測試訊息的訊息類型， **PO-Purchase Order (850)**。</span><span class="sxs-lookup"><span data-stu-id="3155e-259">Verify that the message type of the test message is selected, **PO - Purchase Order (850)**.</span></span>|  
        |<span data-ttu-id="3155e-260">**GS2**</span><span class="sxs-lookup"><span data-stu-id="3155e-260">**GS2**</span></span>|<span data-ttu-id="3155e-261">例如，輸入應用程式傳送者的值**Purchasing**。</span><span class="sxs-lookup"><span data-stu-id="3155e-261">Enter a value for the Application sender, for example, **Purchasing**.</span></span>|  
        |<span data-ttu-id="3155e-262">**GS3**</span><span class="sxs-lookup"><span data-stu-id="3155e-262">**GS3**</span></span>|<span data-ttu-id="3155e-263">例如，應用程式接收者中，輸入的值 **[ordercontrol]**。</span><span class="sxs-lookup"><span data-stu-id="3155e-263">Enter a value for the Application receiver, for example, **OrderControl**.</span></span>|  
        |<span data-ttu-id="3155e-264">**GS4**</span><span class="sxs-lookup"><span data-stu-id="3155e-264">**GS4**</span></span>|<span data-ttu-id="3155e-265">選取您想要的日期格式。</span><span class="sxs-lookup"><span data-stu-id="3155e-265">Select the date format that you want.</span></span> <span data-ttu-id="3155e-266">**注意：** 您必須在下拉式清單中選取值，不只是按一下欄位以顯示預設值。</span><span class="sxs-lookup"><span data-stu-id="3155e-266">**Note:**  You have to select the value in the drop-down list, not just click in the field to display the default.</span></span> <span data-ttu-id="3155e-267">如果您按一下欄位而未從下拉式清單中選取值，實際上不會選取值。</span><span class="sxs-lookup"><span data-stu-id="3155e-267">If you click in the field without selecting the value from the drop-down list, the value will not actually be selected.</span></span>|  
        |<span data-ttu-id="3155e-268">**GS5**</span><span class="sxs-lookup"><span data-stu-id="3155e-268">**GS5**</span></span>|<span data-ttu-id="3155e-269">選擇您要的時間格式。</span><span class="sxs-lookup"><span data-stu-id="3155e-269">Select the time format that you want.</span></span>|  
        |<span data-ttu-id="3155e-270">**GS7**</span><span class="sxs-lookup"><span data-stu-id="3155e-270">**GS7**</span></span>|<span data-ttu-id="3155e-271">選取**X-Accredited 的 Standards Committee X12**。</span><span class="sxs-lookup"><span data-stu-id="3155e-271">Select **X - Accredited Standards Committee X12**.</span></span>|  
        |<span data-ttu-id="3155e-272">**GS8**</span><span class="sxs-lookup"><span data-stu-id="3155e-272">**GS8**</span></span>|<span data-ttu-id="3155e-273">確認已輸入 EDI 版本， **00401**。</span><span class="sxs-lookup"><span data-stu-id="3155e-273">Verify that the EDI version has been entered, **00401**.</span></span>|  
  
        > [!NOTE]
        >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3155e-274">將值，來設定 GS01、 GS02、 GS03、 GS04、 GS05、 GS07 和 GS08 輸出的輸入值為基礎的通知**交易類型**，**版本/版次**，和**目標命名空間**。</span><span class="sxs-lookup"><span data-stu-id="3155e-274"> will set the values for GS01, GS02, GS03, GS04, GS05, GS07, and GS08 of the outbound acknowledgments based on the values entered for **Transaction Type**, **Version/Release**, and **Target namespace**.</span></span> <span data-ttu-id="3155e-275">傳送管線會嘗試將交易集類型、X12 版本和目標命名空間，與訊息標頭中的對應值進行比對。</span><span class="sxs-lookup"><span data-stu-id="3155e-275">The send pipeline attempts to match the transaction set type, the X12 version, and the target namespace with the corresponding values in the header of the message.</span></span> <span data-ttu-id="3155e-276">如果成功，它會使用相關聯的 GS 值**交易類型**，**版本/版次**，和**目標命名空間**值。</span><span class="sxs-lookup"><span data-stu-id="3155e-276">If successful, it uses the GS values associated with the **Transaction Type**, **Version/Release**, and **Target namespace** values.</span></span>  
  
8.  <span data-ttu-id="3155e-277">在上執行下列工作**partyb-> party a**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3155e-277">Perform the following tasks on the **PartyB->PartyA** tab.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3155e-278">在此逐步解說中，我們在索引標籤中指定必要值，以便可以順利地建立協議。</span><span class="sxs-lookup"><span data-stu-id="3155e-278">In this walkthrough, we specify the required value in the tab so that an agreement can be successfully created.</span></span> <span data-ttu-id="3155e-279">若要成功地建立協議，兩個單向協議索引標籤必須已定義的值**ISA5**， **ISA6**， **ISA7**，和**ISA8**。</span><span class="sxs-lookup"><span data-stu-id="3155e-279">To successfully create an agreement, both one-way agreement tabs must have values defined for **ISA5**, **ISA6**, **ISA7**, and **ISA8**.</span></span>  
  
    1.  <span data-ttu-id="3155e-280">在**識別碼**頁面**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，和**ISA8**) 對應到您的測試訊息中標頭欄位的值。</span><span class="sxs-lookup"><span data-stu-id="3155e-280">On the **Identifiers** page under the **Interchange Settings** section, enter values for the qualifier and identifier fields (**ISA5**, **ISA6**, **ISA7**, and **ISA8**) that correspond to the values for those header fields in your test message.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="3155e-281">如果您使用 「 EDI 介面開發人員教學課程 」 中的 SamplePO.txt 檔案做為測試訊息，設定**ISA5**至**ZZ**， **ISA6**至**美國**， **ISA7**至**ZZ**，和**ISA8**至**THEM**。</span><span class="sxs-lookup"><span data-stu-id="3155e-281">If you are using the SamplePO.txt file from the “EDI Interface Developer Tutorial” as your test message, set **ISA5** to **ZZ**, **ISA6** to **US**, **ISA7** to **ZZ**, and **ISA8** to **THEM**.</span></span>  
  
9. <span data-ttu-id="3155e-282">按一下 **[套用]**。</span><span class="sxs-lookup"><span data-stu-id="3155e-282">Click **Apply**.</span></span>  
  
10. <span data-ttu-id="3155e-283">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="3155e-283">Click **OK**.</span></span> <span data-ttu-id="3155e-284">新增的協議會列在**協議**區段**合作對象與商務設定檔**窗格。</span><span class="sxs-lookup"><span data-stu-id="3155e-284">The newly added agreement is listed in the **Agreements** section of the **Parties and Business Profiles** pane.</span></span> <span data-ttu-id="3155e-285">預設會啟用新增的協議。</span><span class="sxs-lookup"><span data-stu-id="3155e-285">The newly added agreement is enabled by default.</span></span>  
  
### <a name="testing-the-walkthrough"></a><span data-ttu-id="3155e-286">測試逐步解說</span><span class="sxs-lookup"><span data-stu-id="3155e-286">Testing the Walkthrough</span></span>  
 <span data-ttu-id="3155e-287">本節提供關於如何測試逐步解說的資訊。</span><span class="sxs-lookup"><span data-stu-id="3155e-287">This section provides information on how to test the walkthrough.</span></span>  
  
####  <a name="BKMK_Proc"></a><span data-ttu-id="3155e-288">若要測試逐步解說</span><span class="sxs-lookup"><span data-stu-id="3155e-288">To test the walkthrough</span></span>  
  
1.  <span data-ttu-id="3155e-289">在 [Windows 檔案總管] 中，開啟與接收位置相關聯的本機資料夾，將測試批次 EDI 交換放置在該資料夾中。</span><span class="sxs-lookup"><span data-stu-id="3155e-289">In Windows Explorer, open the local folder associated with the receive location, and drop a test batched EDI interchange into the folder.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3155e-290">針對測試訊息，您可以使用傳送批次交換逐步解說中解決方案所產生的批次交換輸出。</span><span class="sxs-lookup"><span data-stu-id="3155e-290">For a test message, you can use the batched interchange output generated by the solution in the sending batched interchanges walkthrough.</span></span> <span data-ttu-id="3155e-291">此範例訊息包含兩個交易集。</span><span class="sxs-lookup"><span data-stu-id="3155e-291">This sample message would contain two transaction sets.</span></span>  
  
2.  <span data-ttu-id="3155e-292">開啟與先前建立之傳送埠相關聯的資料夾。</span><span class="sxs-lookup"><span data-stu-id="3155e-292">Open the folder that you associated with the send port that you created above.</span></span> <span data-ttu-id="3155e-293">確認資料夾中包含兩個新檔案，而且每個檔案都是 850 交換，內含測試批次訊息中的其中一個交易集。</span><span class="sxs-lookup"><span data-stu-id="3155e-293">Verify that the folder contains two new files, and that each file is an 850 interchange containing one of the transaction sets in the test batched message.</span></span>  
  
3.  <span data-ttu-id="3155e-294">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下 **合作對象**節點中，按一下任何稍早建立的協議一部分的兩個商務設定檔。</span><span class="sxs-lookup"><span data-stu-id="3155e-294">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click the **Parties** node, click any of the two business profiles that are part of the agreement created earlier.</span></span> <span data-ttu-id="3155e-295">在**協議**區段中，以滑鼠右鍵按一下 協議，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="3155e-295">In the **Agreements** section, right-click the agreement, and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="3155e-296">在**協議屬性**對話方塊**本機主機設定**頁面**交換設定**區段的**輸入訊息處理選項**方塊中，選取 **保留交換-發生錯誤時暫停交換**或**保留交換-發生錯誤時暫停交易集**按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="3155e-296">In the **Agreement Properties** dialog box, on the **Local Host Settings** page under the **Interchange Settings** section, in the **Inbound Message Processing Option** box, select either **Preserve Interchange - suspend Interchange on Error** or **Preserve Interchange - suspend Transaction Sets on Error** and click **OK**.</span></span>  
  
5.  <span data-ttu-id="3155e-297">按一下**主控件執行個體**下**平台設定**] 節點，以滑鼠右鍵按一下**BizTalkServerApplication**，然後按一下 [**重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="3155e-297">Click **Host Instances** under the **Platform Settings** node, right-click **BizTalkServerApplication**, and then click **Restart**.</span></span>  
  
6.  <span data-ttu-id="3155e-298">在 Windows 檔案總管中，開啟與接收位置相關聯的本機資料夾，然後再次將相同的測試批次 EDI 交換放入該資料夾中。</span><span class="sxs-lookup"><span data-stu-id="3155e-298">In Windows Explorer, open the local folder associated with the receive location, and once again drop the same test batched EDI interchange into the folder.</span></span>  
  
7.  <span data-ttu-id="3155e-299">在 [Windows 檔案總管] 中，開啟與先前建立之傳送埠相關聯的資料夾。</span><span class="sxs-lookup"><span data-stu-id="3155e-299">In Windows Explorer, open the folder that you associated with the send port that you created above.</span></span> <span data-ttu-id="3155e-300">確認資料夾中現在只包含一個新檔案，而且該檔案是交換，內含測試批次訊息中的兩個 850 交易集。</span><span class="sxs-lookup"><span data-stu-id="3155e-300">Verify that the folder now contains only one new file, and that the file is an interchange containing the two 850 transaction sets that were in the test batched message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3155e-301">請參閱</span><span class="sxs-lookup"><span data-stu-id="3155e-301">See Also</span></span>  
 <span data-ttu-id="3155e-302">[開發和設定 BizTalk Server EDI 解決方案](../core/developing-and-configuring-biztalk-server-edi-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="3155e-302">[Developing and Configuring BizTalk Server EDI Solutions](../core/developing-and-configuring-biztalk-server-edi-solutions.md) </span></span>  
 <span data-ttu-id="3155e-303">[分割批次的 EDI 交換](../core/splitting-a-batched-edi-interchange.md) </span><span class="sxs-lookup"><span data-stu-id="3155e-303">[Splitting a Batched EDI Interchange](../core/splitting-a-batched-edi-interchange.md) </span></span>  
 <span data-ttu-id="3155e-304">[分割 HIPAA 子文件](../core/splitting-hipaa-subdocuments.md) </span><span class="sxs-lookup"><span data-stu-id="3155e-304">[Splitting HIPAA Subdocuments](../core/splitting-hipaa-subdocuments.md) </span></span>  
 <span data-ttu-id="3155e-305">[保留收到的批次 EDI 交換](../core/preserving-a-received-batched-edi-interchange.md) </span><span class="sxs-lookup"><span data-stu-id="3155e-305">[Preserving a Received Batched EDI Interchange](../core/preserving-a-received-batched-edi-interchange.md) </span></span>  
 <span data-ttu-id="3155e-306">[逐步解說 (X12)： 傳送批次的 EDI 交換](../core/walkthrough-x12-sending-batched-edi-interchanges.md) </span><span class="sxs-lookup"><span data-stu-id="3155e-306">[Walkthrough (X12): Sending Batched EDI Interchanges](../core/walkthrough-x12-sending-batched-edi-interchanges.md) </span></span>  
 <span data-ttu-id="3155e-307">[逐步解說 (X12)： 接收 EDI 交換並傳回通知](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md) </span><span class="sxs-lookup"><span data-stu-id="3155e-307">[Walkthrough (X12): Receiving EDI Interchanges and Sending Back an Acknowledgement](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md) </span></span>  
 [<span data-ttu-id="3155e-308">逐步解說 (X12)：傳送 EDI 交換</span><span class="sxs-lookup"><span data-stu-id="3155e-308">Walkthrough (X12): Sending EDI Interchanges</span></span>](../core/walkthrough-x12-sending-edi-interchanges.md)