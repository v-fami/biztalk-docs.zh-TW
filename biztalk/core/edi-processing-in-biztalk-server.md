---
title: BizTalk Server 中的 EDI 處理 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bdc60423-24b6-4920-a870-520f575085ed
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 657b04331c6804c284e2e05fad554780aeeab21c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006455"
---
# <a name="edi-processing-in-biztalk-server"></a><span data-ttu-id="34500-102">BizTalk Server 中的 EDI 處理</span><span class="sxs-lookup"><span data-stu-id="34500-102">EDI Processing in BizTalk Server</span></span>
<span data-ttu-id="34500-103">本主題將提供概觀，介紹在接收端與傳送端進行的 EDI 訊息處理，以及交易夥伴協議如何協助完成 EDI 訊息處理。</span><span class="sxs-lookup"><span data-stu-id="34500-103">This topic provides an overview of receive-side and send-side processing of EDI messages, and how trading partner agreements can help achieve EDI messaging.</span></span>  
  
## <a name="trading-partner-agreements-for-edi-processing"></a><span data-ttu-id="34500-104">適用於 EDI 處理的交易夥伴協議</span><span class="sxs-lookup"><span data-stu-id="34500-104">Trading Partner Agreements for EDI Processing</span></span>  
 <span data-ttu-id="34500-105">交易夥伴協議在 BizTalk Server 中的 EDI 支援中扮演關鍵角色。</span><span class="sxs-lookup"><span data-stu-id="34500-105">Trading partner agreements play a key role in EDI support in BizTalk Server.</span></span> <span data-ttu-id="34500-106">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，大部分與 EDI 處理有關的組態與管理功能都是藉由設定商務設定檔之間的交易夥伴協議來完成。</span><span class="sxs-lookup"><span data-stu-id="34500-106">Most configuration and administrative functions related to EDI processing in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] are performed by configuring the trading partner agreements between business profiles.</span></span> <span data-ttu-id="34500-107">協議會將在雙方合作對象所屬商務設定檔中共同的雙向訊息處理屬性收集在一起。</span><span class="sxs-lookup"><span data-stu-id="34500-107">Agreements bring together common bi-directional message processing properties from specific business profiles of both partners.</span></span> <span data-ttu-id="34500-108">協議是根據針對每個商務設定檔所定義的通訊協定設定而建置。</span><span class="sxs-lookup"><span data-stu-id="34500-108">Agreements are built upon the protocol settings defined for each business profile.</span></span> <span data-ttu-id="34500-109">若要在兩個商務設定檔之間實作交易夥伴協議，您需為每個會交換訊息的商務設定檔定義屬性。</span><span class="sxs-lookup"><span data-stu-id="34500-109">You implement a trading partner agreement between two business profiles by defining properties for each business profile that will be exchanging messages.</span></span> <span data-ttu-id="34500-110">您需為每個做為交換接收者和交換傳送者的商務設定檔設定屬性。</span><span class="sxs-lookup"><span data-stu-id="34500-110">You set properties for each business profile as an interchange receiver and as an interchange sender.</span></span> <span data-ttu-id="34500-111">為了處理內送訊息或產生外寄訊息，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 必須知道訊息會解析成的協議，以及套用至訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="34500-111">To process an incoming message or generate an outgoing message, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] needs to know the agreement that it resolves to, and the schema that applies to the message.</span></span> <span data-ttu-id="34500-112">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 若是無法判斷協議，就會使用 TPM 介面中針對後援交易夥伴協議所定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="34500-112">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot determine the agreement, it will use the properties defined in the TPM interface for the fallback trading partner agreement.</span></span>  
  
 <span data-ttu-id="34500-113">有兩組主要的 TPM 中的通訊協定設定的編碼方式： 一個用於 EDIFACT 屬性，一個適用於 X12 屬性。</span><span class="sxs-lookup"><span data-stu-id="34500-113">There are two major sets of encoding protocol settings in TPM: one for EDIFACT properties and one for X12 properties.</span></span> <span data-ttu-id="34500-114">這兩組屬性近乎相同。</span><span class="sxs-lookup"><span data-stu-id="34500-114">The two sets of properties are closely parallel.</span></span> <span data-ttu-id="34500-115">如需有關通訊協定設定的詳細資訊，請參閱[通訊協定設定](../core/protocol-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="34500-115">For more information about the protocol settings, see [Protocol Settings](../core/protocol-settings.md).</span></span> <span data-ttu-id="34500-116">如需有關協議的詳細資訊，請參閱[交易夥伴協議](../core/trading-partner-agreement.md)。</span><span class="sxs-lookup"><span data-stu-id="34500-116">For more information about agreements, see [Trading Partner Agreement](../core/trading-partner-agreement.md).</span></span> <span data-ttu-id="34500-117">您可以在交易夥伴管理 (TPM) 使用者介面中設定通訊協定設定與交易夥伴協議。</span><span class="sxs-lookup"><span data-stu-id="34500-117">You set the protocol settings and the trading partner agreement in the Trading Partner Management (TPM) user interface.</span></span> <span data-ttu-id="34500-118">TPM 畫面位於**合作對象**節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="34500-118">The TPM screens are in the **Parties** node of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="34500-119">您不需要身為開發人員，就可以設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的 EDI 處理。</span><span class="sxs-lookup"><span data-stu-id="34500-119">You do not have to be a developer to configure EDI processing in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="34500-120">如需有關如何交易夥伴協議進行 EDI 處理的詳細資訊，請參閱 <<c0> [ 角色中協議的 EDI 處理](../core/the-role-of-agreements-in-edi-processing.md)。</span><span class="sxs-lookup"><span data-stu-id="34500-120">For more information about how trading partner agreements help in EDI processing, see [The Role of Agreements in EDI Processing](../core/the-role-of-agreements-in-edi-processing.md).</span></span>  
  
## <a name="edi-receive-side-processing"></a><span data-ttu-id="34500-121">EDI 接收端處理</span><span class="sxs-lookup"><span data-stu-id="34500-121">EDI Receive-Side Processing</span></span>  
 <span data-ttu-id="34500-122">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在收到 EDI 訊息時，會在 EDI 接收管線中處理該訊息。</span><span class="sxs-lookup"><span data-stu-id="34500-122">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives an EDI message, it processes the message in the EDI receive pipeline.</span></span> <span data-ttu-id="34500-123">接收管線會執行下列基本處理：</span><span class="sxs-lookup"><span data-stu-id="34500-123">The receive pipeline performs the following basic processing:</span></span>  
  
- <span data-ttu-id="34500-124">查閱交易夥伴協議及判斷結構描述。</span><span class="sxs-lookup"><span data-stu-id="34500-124">Trading partner agreement lookup and schema determination.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="34500-125">在舊版的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，合作對象定義也包含協議定義。</span><span class="sxs-lookup"><span data-stu-id="34500-125">In the previous versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], a party definition also included the agreement definition.</span></span> <span data-ttu-id="34500-126">因此，接收管線在查閱合作對象屬性時，會在合作對象定義內部尋找協議定義，然後據以處理訊息。</span><span class="sxs-lookup"><span data-stu-id="34500-126">So, when the receive pipeline looked up the party properties, it would internally look for the agreement definition within the party definition and then process the messages accordingly.</span></span> <span data-ttu-id="34500-127">使用 BizTalk Server 中，由於合作對象 （或交易夥伴） 不同於交易夥伴協議中，接收管線會尋找交易夥伴協議特別。</span><span class="sxs-lookup"><span data-stu-id="34500-127">With BizTalk Server, because the party (or trading partner) is distinct from the trading partner agreement, the receive pipeline looks for the trading partner agreement specifically.</span></span>  
  > 
  > [!NOTE]
  >  <span data-ttu-id="34500-128">如果某個訊息所解析的所有目標協議都已停用，就會擱置此訊息。</span><span class="sxs-lookup"><span data-stu-id="34500-128">If all the agreements that a message resolves to are disabled, the message will be suspended.</span></span> <span data-ttu-id="34500-129">此外，事件日誌也會記錄一則警告。</span><span class="sxs-lookup"><span data-stu-id="34500-129">A warning is also logged in the Event log.</span></span>  
  
- <span data-ttu-id="34500-130">如果單一 EDI 訊息包含多個交換，則會分割此交換，分開處理每個交換 (如果啟用此功能的話)。</span><span class="sxs-lookup"><span data-stu-id="34500-130">If a single EDI message contains multiple interchanges, splits the interchanges and processes each interchange separately (if enabled).</span></span> <span data-ttu-id="34500-131">如需詳細資訊，請參閱 <<c0> [ 啟用接收的多個交換單一訊息中](../core/enabling-the-receiving-of-multiple-interchanges-in-a-single-message.md)。</span><span class="sxs-lookup"><span data-stu-id="34500-131">For more information, see [Enabling the Receiving of Multiple Interchanges in a Single Message](../core/enabling-the-receiving-of-multiple-interchanges-in-a-single-message.md).</span></span>  
  
- <span data-ttu-id="34500-132">剖析每個 EDI 交換，並將 X12 或 EDIFACT 編碼資料轉換為 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="34500-132">Parses each EDI interchange, converting the X12- or EDIFACT-encoded data into an XML document.</span></span>  
  
- <span data-ttu-id="34500-133">根據 EDI 標準、夥伴協議和訊息結構描述來驗證信封與其訊息。</span><span class="sxs-lookup"><span data-stu-id="34500-133">Validates the envelope and its message according to the EDI standards, the partner agreement, and the message schemas.</span></span>  
  
- <span data-ttu-id="34500-134">如果已批次處理交換，則會分割此批次交換 (包括為每個交易集建立 XML 檔案，以及升級批次處理所需的屬性) 或保留交換。</span><span class="sxs-lookup"><span data-stu-id="34500-134">If the interchange is batched, either splits the batched interchange, creating an XML file for each transaction set and promoting properties required for batch processing, or preserves the interchange.</span></span>  
  
- <span data-ttu-id="34500-135">產生通知。</span><span class="sxs-lookup"><span data-stu-id="34500-135">Generates an acknowledgment.</span></span>  
  
- <span data-ttu-id="34500-136">將 EDI 信封轉換為內容屬性，以及升級 EDI 處理的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="34500-136">Converts the EDI envelope into context properties, and promotes other properties for EDI processing.</span></span>  
  
- <span data-ttu-id="34500-137">升級可控制批次處理的屬性，</span><span class="sxs-lookup"><span data-stu-id="34500-137">Promotes properties that control batch processing.</span></span> <span data-ttu-id="34500-138">這包含將解除批次的交易集傳送至多個合作對象。</span><span class="sxs-lookup"><span data-stu-id="34500-138">This can include sending debatched transaction sets to multiple parties.</span></span>  
  
  <span data-ttu-id="34500-139">以下是您在使用 EDI 接收端處理時必須考量的一些事項：</span><span class="sxs-lookup"><span data-stu-id="34500-139">Following are some considerations that you must make while using EDI receive-side processing:</span></span>  
  
- <span data-ttu-id="34500-140">接收位置可以使用任何類型的傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="34500-140">The receive location can use any type of transport type.</span></span>  
  
- <span data-ttu-id="34500-141">如需有關 EDI 接收端處理的詳細資訊，請參閱 <<c0> [ 如何 BizTalk Server 接收 EDI 訊息](../core/how-biztalk-server-receives-edi-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="34500-141">For more information about EDI receive-side processing, see [How BizTalk Server Receives EDI Messages](../core/how-biztalk-server-receives-edi-messages.md).</span></span>  
  
- <span data-ttu-id="34500-142">如需有關 EDI 解譯器會在接收管線中執行之特定處理的詳細資訊，請參閱[EDI 解譯器的運作方式](../core/how-the-edi-disassembler-works.md)。</span><span class="sxs-lookup"><span data-stu-id="34500-142">For more information about the specific processing performed by the EDI Disassembler in the receive pipeline, see [How the EDI Disassembler Works](../core/how-the-edi-disassembler-works.md).</span></span>  
  
## <a name="edi-batch-processing"></a><span data-ttu-id="34500-143">EDI 批次處理</span><span class="sxs-lookup"><span data-stu-id="34500-143">EDI Batch Processing</span></span>  
 <span data-ttu-id="34500-144">如果內送訊息為已批次處理的交換，則 EDI 接收管線會根據組態將此批次交換分割為其組成交易集，或保留此批次交換。</span><span class="sxs-lookup"><span data-stu-id="34500-144">If the incoming message is a batch, the EDI receive pipeline will either split the batched interchange into its constituent transaction sets, or preserve the batched interchange, depending on the configuration.</span></span> <span data-ttu-id="34500-145">EDIReceive 管線會使用 BatchMarker 管線元件，將要批次處理的任何交換路由傳送至批次處理協調流程或路由協調流程。</span><span class="sxs-lookup"><span data-stu-id="34500-145">The EDIReceive pipeline uses the BatchMarker pipeline component to route any interchanges that are to be batched to the batching orchestration or the routing orchestration.</span></span>  
  
 <span data-ttu-id="34500-146">在接收端處理之後，批次處理協調流程會對交易集進行批次處理以供傳送。</span><span class="sxs-lookup"><span data-stu-id="34500-146">After receive-side processing, transaction sets to be batched for sending will be processed by the batching orchestration.</span></span> <span data-ttu-id="34500-147">批次處理協調流程會根據篩選準則、啟動範圍和釋放準則來建立批次。</span><span class="sxs-lookup"><span data-stu-id="34500-147">The batching orchestration will create a batch based upon filter criteria, an activation range, and release criteria.</span></span>  
  
 <span data-ttu-id="34500-148">如果需要將未批次處理的 EDI 交易集傳送至批次，則路由協調流程會處理這些交易集。</span><span class="sxs-lookup"><span data-stu-id="34500-148">If unbatched EDI transaction sets need to be sent to batches, a routing orchestration will process the transaction sets.</span></span> <span data-ttu-id="34500-149">此時會為每個相符的批次各建立交易集的一個複本。</span><span class="sxs-lookup"><span data-stu-id="34500-149">A copy of the transaction set will be created for each matching batch.</span></span>  
  
 <span data-ttu-id="34500-150">如需有關在批次處理中執行之特定處理的詳細資訊，請參閱 <<c0> [ 處理內送批次](../core/processing-incoming-batches.md)或是[批次處理外寄 EDI 訊息](../core/batching-outgoing-edi-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="34500-150">For more information about the specific processing performed in batching, see [Processing Incoming Batches](../core/processing-incoming-batches.md) or [Batching Outgoing EDI Messages](../core/batching-outgoing-edi-messages.md).</span></span>  
  
## <a name="edi-send-side-processing"></a><span data-ttu-id="34500-151">EDI 傳送端處理</span><span class="sxs-lookup"><span data-stu-id="34500-151">EDI Send-Side Processing</span></span>  
 <span data-ttu-id="34500-152">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在產生並傳送外寄 EDI 訊息時，會在 EDI 傳送管線中處理該訊息。</span><span class="sxs-lookup"><span data-stu-id="34500-152">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] generates and sends an outgoing EDI message, it processes the message in the EDI send pipeline.</span></span> <span data-ttu-id="34500-153">傳送管線會執行下列基本處理：</span><span class="sxs-lookup"><span data-stu-id="34500-153">The send pipeline performs the following processing:</span></span>  
  
- <span data-ttu-id="34500-154">查閱交易夥伴協議及判斷結構描述。</span><span class="sxs-lookup"><span data-stu-id="34500-154">Trading partner agreement lookup and schema determination.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="34500-155">在舊版的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，合作對象定義也包含協議定義。</span><span class="sxs-lookup"><span data-stu-id="34500-155">In the previous versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], a party definition also included the agreement definition.</span></span> <span data-ttu-id="34500-156">因此，傳送管線在查閱合作對象屬性時，會在合作對象定義內部尋找協議定義，然後據以處理訊息。</span><span class="sxs-lookup"><span data-stu-id="34500-156">So, when the send pipeline looked up the party properties, it would internally look for the agreement definition within the party definition and then process the messages accordingly.</span></span> <span data-ttu-id="34500-157">使用 BizTalk Server 中，由於合作對象 （或交易夥伴） 不同於交易夥伴協議，傳送管線會尋找交易夥伴協議特別。</span><span class="sxs-lookup"><span data-stu-id="34500-157">With BizTalk Server, because the party (or trading partner) is distinct from the trading partner agreement, the send pipeline looks for the trading partner agreement specifically.</span></span>  
  > 
  > [!NOTE]
  >  <span data-ttu-id="34500-158">如果某個訊息所解析的所有目標協議都已停用，就會擱置此訊息。</span><span class="sxs-lookup"><span data-stu-id="34500-158">If all the agreements that a message resolves to are disabled, the message will be suspended.</span></span>  <span data-ttu-id="34500-159">此外，事件日誌也會記錄一則警告。</span><span class="sxs-lookup"><span data-stu-id="34500-159">A warning is also logged in the Event log.</span></span>  
  
- <span data-ttu-id="34500-160">序列化 EDI 訊息，並將 XML 文件轉換為 X12 或 EDIFACT 編碼資料。</span><span class="sxs-lookup"><span data-stu-id="34500-160">Serializes the EDI message, converting the XML document into X12- or EDIFACT-encoded data.</span></span>  
  
- <span data-ttu-id="34500-161">如果訊息資料中有些字元同時也是 X12 分隔符號，您可以設定傳送管線，以其他字元取代內容中的這些字元。</span><span class="sxs-lookup"><span data-stu-id="34500-161">If the message data contains characters that are also used as X12 separators, the send pipeline can be configured to replace the characters in the payload with another character.</span></span>  
  
- <span data-ttu-id="34500-162">如果 EDI 訊息是已批次處理的交換，在批次處理協調流程建置批次之後，傳送管線會從 BizTalk MessageBox 取用此交換。</span><span class="sxs-lookup"><span data-stu-id="34500-162">If the EDI message is a batched interchange, the send pipeline picks up the interchange from the BizTalk MessageBox after the batching orchestration has built the batch.</span></span>  
  
- <span data-ttu-id="34500-163">驗證外寄訊息。</span><span class="sxs-lookup"><span data-stu-id="34500-163">Validates the outgoing message.</span></span>  
  
- <span data-ttu-id="34500-164">根據在執行階段指定的合作對象屬性或 EDI 信封屬性，建立 EDI 信封。</span><span class="sxs-lookup"><span data-stu-id="34500-164">Creates the EDI envelope according to the party properties or EDI envelope properties specified at runtime.</span></span>  
  
- <span data-ttu-id="34500-165">處理接收的通知。</span><span class="sxs-lookup"><span data-stu-id="34500-165">Processes acknowledgments received.</span></span>  
  
  <span data-ttu-id="34500-166">以下是您在使用 EDI 傳送端處理時必須考量的一些事項：</span><span class="sxs-lookup"><span data-stu-id="34500-166">Following are some considerations that you must make while using EDI send-side processing:</span></span>  
  
- <span data-ttu-id="34500-167">傳送埠可以使用任何類型的傳輸。</span><span class="sxs-lookup"><span data-stu-id="34500-167">The send port can use any type of transport.</span></span>  
  
- <span data-ttu-id="34500-168">如需有關 EDI 傳送端處理的詳細資訊，請參閱 <<c0> [ 如何 BizTalk Server 傳送 EDI 訊息](../core/how-biztalk-server-sends-edi-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="34500-168">For more information about EDI send-side processing, see [How BizTalk Server Sends EDI Messages](../core/how-biztalk-server-sends-edi-messages.md).</span></span>  
  
- <span data-ttu-id="34500-169">如需在傳送管線中執行之特定處理的詳細資訊，請參閱[EDI 組合器的運作方式](../core/how-the-edi-assembler-works.md)。</span><span class="sxs-lookup"><span data-stu-id="34500-169">For more information about the specific processing performed in the send pipeline, see [How the EDI Assembler Works](../core/how-the-edi-assembler-works.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34500-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34500-170">See Also</span></span>  
 <span data-ttu-id="34500-171">[BizTalk Server 中的 EDI 支援](../core/edi-support-in-biztalk-server1.md) </span><span class="sxs-lookup"><span data-stu-id="34500-171">[EDI Support in BizTalk Server](../core/edi-support-in-biztalk-server1.md) </span></span>  
 <span data-ttu-id="34500-172">[EDI 支援問題](../core/edi-support-issues.md) </span><span class="sxs-lookup"><span data-stu-id="34500-172">[EDI Support Issues](../core/edi-support-issues.md) </span></span>  
 <span data-ttu-id="34500-173">[中協議 EDI 處理的角色](../core/the-role-of-agreements-in-edi-processing.md) </span><span class="sxs-lookup"><span data-stu-id="34500-173">[The Role of Agreements in EDI Processing](../core/the-role-of-agreements-in-edi-processing.md) </span></span>  
 <span data-ttu-id="34500-174">[BizTalk Server 如何接收 EDI 訊息](../core/how-biztalk-server-receives-edi-messages.md) </span><span class="sxs-lookup"><span data-stu-id="34500-174">[How BizTalk Server Receives EDI Messages](../core/how-biztalk-server-receives-edi-messages.md) </span></span>  
 <span data-ttu-id="34500-175">[BizTalk Server 如何傳送 EDI 訊息](../core/how-biztalk-server-sends-edi-messages.md) </span><span class="sxs-lookup"><span data-stu-id="34500-175">[How BizTalk Server Sends EDI Messages](../core/how-biztalk-server-sends-edi-messages.md) </span></span>  
 [<span data-ttu-id="34500-176">開發和設定 BizTalk Server EDI 解決方案</span><span class="sxs-lookup"><span data-stu-id="34500-176">Developing and Configuring BizTalk Server EDI Solutions</span></span>](../core/developing-and-configuring-biztalk-server-edi-solutions.md)