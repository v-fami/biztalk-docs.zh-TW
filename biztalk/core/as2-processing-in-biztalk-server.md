---
title: "AS2 BizTalk Server 中的處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0027d3db-24a5-459d-9f4e-a75f49d31d82
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11a5bb12d9a7b21a18b92162370d7be14feda8dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="as2-processing-in-biztalk-server"></a><span data-ttu-id="baa9b-102">BizTalk Server 中的 AS2 處理</span><span class="sxs-lookup"><span data-stu-id="baa9b-102">AS2 Processing in BizTalk Server</span></span>
<span data-ttu-id="baa9b-103">本主題將提供概觀，介紹在接收端與傳送端進行的 AS2 訊息處理，以及交易夥伴協議如何協助完成 AS2 訊息處理。</span><span class="sxs-lookup"><span data-stu-id="baa9b-103">This topic provides an overview of receive-side and send-side processing of AS2 messages, and how trading partner agreements can help achieve AS2 messaging.</span></span>  
  
## <a name="trading-partner-agreements-for-as2-processing"></a><span data-ttu-id="baa9b-104">適用於 AS2 處理的交易夥伴協議</span><span class="sxs-lookup"><span data-stu-id="baa9b-104">Trading Partner Agreements for AS2 Processing</span></span>  
 <span data-ttu-id="baa9b-105">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的 AS2 支援中，交易夥伴協議扮演了關鍵的角色。</span><span class="sxs-lookup"><span data-stu-id="baa9b-105">Trading partner agreements play a key role in AS2 support in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="baa9b-106">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，大部分與 AS2 處理有關的組態與管理功能都是藉由設定商務設定檔之間的交易夥伴協議來完成。</span><span class="sxs-lookup"><span data-stu-id="baa9b-106">Most configuration and administrative functions related to AS2 processing in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] are performed by configuring the trading partner agreements between business profiles.</span></span> <span data-ttu-id="baa9b-107">協議會將在雙方合作對象所屬商務設定檔中共同的雙向訊息處理屬性收集在一起。</span><span class="sxs-lookup"><span data-stu-id="baa9b-107">Agreements bring together common bi-directional message processing properties from specific business profiles of both partners.</span></span> <span data-ttu-id="baa9b-108">協議是根據針對每個商務設定檔所定義的通訊協定設定而建置。</span><span class="sxs-lookup"><span data-stu-id="baa9b-108">Agreements are built upon the protocol settings defined for each business profile.</span></span> <span data-ttu-id="baa9b-109">若要在兩個商務設定檔之間實作交易夥伴協議，您需為每個會交換訊息的商務設定檔定義屬性。</span><span class="sxs-lookup"><span data-stu-id="baa9b-109">You implement a trading partner agreement between two business profiles by defining properties for each business profile that will be exchanging messages.</span></span> <span data-ttu-id="baa9b-110">您可以在「交易夥伴管理」(TPM) 使用者介面中，將每個商務設定檔的屬性設定為 AS2 訊息接收者和 AS2 訊息傳送者。</span><span class="sxs-lookup"><span data-stu-id="baa9b-110">You set properties for each business profile as an AS2 message receiver and an AS2 message sender in the Trading Partner Management (TPM) user interface.</span></span> <span data-ttu-id="baa9b-111">TPM 畫面位於**合作對象**節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="baa9b-111">The TPM screens are in the **Parties** node of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span> <span data-ttu-id="baa9b-112">您不需要身為開發人員，就可以設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的 AS2 處理。</span><span class="sxs-lookup"><span data-stu-id="baa9b-112">You do not have to be a developer to configure AS2 processing in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="baa9b-113">您可以將 AS2 屬性指定為商務設定檔之「傳輸通訊協定設定」的一部分，也可以直接在交易夥伴協議中指定 AS2 設定。</span><span class="sxs-lookup"><span data-stu-id="baa9b-113">You can specify the AS2 properties as part of the “transport protocol settings” for a business profile or by directly specifying the AS2 settings in the trading partner agreement.</span></span> <span data-ttu-id="baa9b-114">如需通訊協定設定的詳細資訊，請參閱[通訊協定設定](../core/protocol-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="baa9b-114">For more information about the protocol settings, see [Protocol Settings](../core/protocol-settings.md).</span></span> <span data-ttu-id="baa9b-115">如需協議的詳細資訊，請參閱[交易夥伴協議](../core/trading-partner-agreement.md)。</span><span class="sxs-lookup"><span data-stu-id="baa9b-115">For more information about agreements, see [Trading Partner Agreement](../core/trading-partner-agreement.md).</span></span>  <span data-ttu-id="baa9b-116">您可以透過設定 AS2 特有屬性，設定下列 AS2 功能：</span><span class="sxs-lookup"><span data-stu-id="baa9b-116">You configure the following AS2 functionality by setting the AS2-specific properties:</span></span>  
  
-   <span data-ttu-id="baa9b-117">選取不可否認性儲存選項</span><span class="sxs-lookup"><span data-stu-id="baa9b-117">Select non-repudiation storage options</span></span>  
  
-   <span data-ttu-id="baa9b-118">指定外寄訊息的簽章、壓縮或加密屬性</span><span class="sxs-lookup"><span data-stu-id="baa9b-118">Specify signing, compression, or encryption properties for outgoing messages</span></span>  
  
-   <span data-ttu-id="baa9b-119">要求外寄訊息的 MDN</span><span class="sxs-lookup"><span data-stu-id="baa9b-119">Request MDNs for outgoing messages</span></span>  
  
-   <span data-ttu-id="baa9b-120">透過在 AS2 訊息的標頭中覆寫簽章、壓縮、加密和 MDN 屬性，設定內送 MDN 的屬性。</span><span class="sxs-lookup"><span data-stu-id="baa9b-120">Set properties for incoming MDNs by overriding the signing, compression, encryption, and MDN properties in the header of the AS2 message.</span></span>  
  
 <span data-ttu-id="baa9b-121">如需如何交易夥伴協議，AS2 處理中的詳細資訊，請參閱[中協議的角色中的 AS2 處理](../core/the-role-of-agreements-in-as2-processing.md)。</span><span class="sxs-lookup"><span data-stu-id="baa9b-121">For more information about how trading partner agreements help in AS2 processing, see [The Role of Agreements in AS2 Processing](../core/the-role-of-agreements-in-as2-processing.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="baa9b-122">目前沒有適用於 AS2 處理的全域屬性，如同 EDI 處理。</span><span class="sxs-lookup"><span data-stu-id="baa9b-122">There are no global properties for AS2 processing, as there are for EDI processing.</span></span>  
  
## <a name="as2-receive-side-processing"></a><span data-ttu-id="baa9b-123">AS2 接收端處理</span><span class="sxs-lookup"><span data-stu-id="baa9b-123">AS2 Receive-Side Processing</span></span>  
 <span data-ttu-id="baa9b-124">當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 收到 AS2 訊息時，它會在 AS2 接收管線中處理該訊息。</span><span class="sxs-lookup"><span data-stu-id="baa9b-124">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives an AS2 message, it processes the message in an AS2 receive pipeline.</span></span> <span data-ttu-id="baa9b-125">其中有一個用於透過 AS2 接收 EDI 訊息的管線 (AS2EdiReceive)，它可同時執行 AS2 和 EDI 處理。</span><span class="sxs-lookup"><span data-stu-id="baa9b-125">There is a pipeline for receiving an EDI message over AS2 (AS2EdiReceive), which performs both AS2 and EDI processing.</span></span> <span data-ttu-id="baa9b-126">另一個管線 (AS2Receive) 只會針對透過 AS2 接收的非 EDI 訊息執行 AS2 處理。</span><span class="sxs-lookup"><span data-stu-id="baa9b-126">Another pipeline (AS2Receive) performs only AS2 processing for non-EDI messages received over AS2.</span></span>  
  
 <span data-ttu-id="baa9b-127">AS2 接收端處理包括下列作業：</span><span class="sxs-lookup"><span data-stu-id="baa9b-127">AS2 receive-side processing includes the following:</span></span>  
  
-   <span data-ttu-id="baa9b-128">交易夥伴協議查閱</span><span class="sxs-lookup"><span data-stu-id="baa9b-128">Trading partner agreement lookup</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="baa9b-129">在舊版的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，合作對象定義也包含協議定義。</span><span class="sxs-lookup"><span data-stu-id="baa9b-129">In the previous versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], a party definition also included the agreement definition.</span></span> <span data-ttu-id="baa9b-130">因此，接收管線在查閱合作對象屬性時，會在合作對象定義內部尋找協議定義，然後據以處理訊息。</span><span class="sxs-lookup"><span data-stu-id="baa9b-130">So, when the receive pipeline looked up the party properties, it would internally look for the agreement definition within the party definition and then process the messages accordingly.</span></span> <span data-ttu-id="baa9b-131">使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，由於合作對象 (或交易夥伴) 不同於交易夥伴協議，因此接收管線會特別去尋找交易夥伴協議。</span><span class="sxs-lookup"><span data-stu-id="baa9b-131">With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], because the party (or trading partner) is distinct from the trading partner agreement, the receive pipeline looks for the trading partner agreement specifically.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="baa9b-132">如果某個訊息所解析的所有目標協議都已停用，就會擱置此訊息。</span><span class="sxs-lookup"><span data-stu-id="baa9b-132">If all the agreements that a message resolves to are disabled, the message will be suspended.</span></span>  <span data-ttu-id="baa9b-133">此外，事件日誌也會記錄一則警告。</span><span class="sxs-lookup"><span data-stu-id="baa9b-133">A warning is also logged in the Event log.</span></span>  
  
-   <span data-ttu-id="baa9b-134">在不可否認性資料庫中儲存訊息的複本</span><span class="sxs-lookup"><span data-stu-id="baa9b-134">Saving copies of the message in the non-repudiation database</span></span>  
  
-   <span data-ttu-id="baa9b-135">檢查重複的訊息</span><span class="sxs-lookup"><span data-stu-id="baa9b-135">Check for duplicate messages</span></span>  
  
-   <span data-ttu-id="baa9b-136">處理包含多個文件的訊息</span><span class="sxs-lookup"><span data-stu-id="baa9b-136">Processing messages containing multiple documents</span></span>  
  
-   <span data-ttu-id="baa9b-137">從 MIME 信封中擷取文件檔案名稱</span><span class="sxs-lookup"><span data-stu-id="baa9b-137">Retrieving a documents file name from the MIME envelope</span></span>  
  
-   <span data-ttu-id="baa9b-138">解密訊息</span><span class="sxs-lookup"><span data-stu-id="baa9b-138">Decrypting the message</span></span>  
  
-   <span data-ttu-id="baa9b-139">解壓縮訊息</span><span class="sxs-lookup"><span data-stu-id="baa9b-139">Decompressing the message</span></span>  
  
-   <span data-ttu-id="baa9b-140">驗證訊息的數位簽章</span><span class="sxs-lookup"><span data-stu-id="baa9b-140">Verifying the digital signature of the message</span></span>  
  
-   <span data-ttu-id="baa9b-141">產生 HTTP 回應</span><span class="sxs-lookup"><span data-stu-id="baa9b-141">Generating an HTTP response</span></span>  
  
-   <span data-ttu-id="baa9b-142">產生 MDN 回應</span><span class="sxs-lookup"><span data-stu-id="baa9b-142">Generating an MDN response</span></span>  
  
 <span data-ttu-id="baa9b-143">以下是您在使用 AS2 接收端處理時必須考量的一些事項：</span><span class="sxs-lookup"><span data-stu-id="baa9b-143">Following are some considerations that you must make while using AS2 receive-side processing:</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="baa9b-144"> 會以同步或非同步模式傳回 MDN。</span><span class="sxs-lookup"><span data-stu-id="baa9b-144"> returns an MDN in either synchronous or asynchronous mode.</span></span> <span data-ttu-id="baa9b-145">若 MDN 將以非同步方式傳回，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 就必須透過不同的傳送埠傳送它。</span><span class="sxs-lookup"><span data-stu-id="baa9b-145">If the MDN will be returned asynchronously, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] must send it over a separate send port.</span></span>  
  
-   <span data-ttu-id="baa9b-146">當您透過 AS2 接收非 EDI 檔案 (不是 XML)，而且需要執行非 EDI 內容的解譯時，就必須使用回送機制搭配第二個接收管線。</span><span class="sxs-lookup"><span data-stu-id="baa9b-146">When you receive a non-EDI file (not XML) over AS2, and you need to perform disassembly of the non-EDI payload, you will need to use requires a loopback mechanism with a second receive pipeline.</span></span> <span data-ttu-id="baa9b-147">如需詳細資訊，請參閱[接收端處理透過 AS2 內送的非 EDI 訊息的](../core/receive-side-processing-of-an-incoming-non-edi-message-over-as2.md)。</span><span class="sxs-lookup"><span data-stu-id="baa9b-147">For more information, see [Receive-Side Processing of an Incoming Non-EDI Message over AS2](../core/receive-side-processing-of-an-incoming-non-edi-message-over-as2.md).</span></span>  
  
-   <span data-ttu-id="baa9b-148">接收位置只能使用 HTTP 配接器。</span><span class="sxs-lookup"><span data-stu-id="baa9b-148">The receive location can only use the HTTP adapter.</span></span>  
  
-   <span data-ttu-id="baa9b-149">如需有關 AS2 接收端處理的詳細資訊，請參閱[如何 BizTalk Server 接收 AS2 訊息](../core/how-biztalk-server-receives-as2-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="baa9b-149">For more information about AS2 receive-side processing, see [How BizTalk Server Receives AS2 Messages](../core/how-biztalk-server-receives-as2-messages.md).</span></span>  
  
-   <span data-ttu-id="baa9b-150">如需有關 AS2 解譯器在接收管線中執行之特定處理的詳細資訊，請參閱[處理內送 AS2 訊息](../core/processing-an-incoming-as2-message.md)。</span><span class="sxs-lookup"><span data-stu-id="baa9b-150">For more information about the specific processing performed by the AS2 Disassembler in the receive pipeline, see [Processing an Incoming AS2 Message](../core/processing-an-incoming-as2-message.md).</span></span>  
  
## <a name="as2-send-side-processing"></a><span data-ttu-id="baa9b-151">AS2 傳送端處理</span><span class="sxs-lookup"><span data-stu-id="baa9b-151">AS2 Send-Side Processing</span></span>  
 <span data-ttu-id="baa9b-152">當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 產生並傳送外寄 AS2 訊息時，它會在 AS2 傳送管線中處理該訊息。</span><span class="sxs-lookup"><span data-stu-id="baa9b-152">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] generates and sends an outgoing AS2 message, it processes the message in an AS2 send pipeline.</span></span> <span data-ttu-id="baa9b-153">其中有一個用於透過 AS2 傳送 EDI 訊息的管線 (AS2EdiSend)，它可同時執行 AS2 和 EDI 處理。</span><span class="sxs-lookup"><span data-stu-id="baa9b-153">There is a pipeline for sending an EDI message over AS2 (AS2EdiSend), which performs both AS2 and EDI processing.</span></span> <span data-ttu-id="baa9b-154">另一個管線 (AS2Send) 只會針對透過 AS2 傳送的非 EDI 訊息執行 AS2 處理。</span><span class="sxs-lookup"><span data-stu-id="baa9b-154">Another pipeline (AS2Send) performs only AS2 processing for non-EDI messages sent over AS2.</span></span>  
  
 <span data-ttu-id="baa9b-155">AS2 傳送端處理包括下列作業：</span><span class="sxs-lookup"><span data-stu-id="baa9b-155">AS2 send-side processing includes the following:</span></span>  
  
-   <span data-ttu-id="baa9b-156">交易夥伴協議查閱</span><span class="sxs-lookup"><span data-stu-id="baa9b-156">Trading partner agreement lookup</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="baa9b-157">在舊版的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，合作對象定義也包含協議定義。</span><span class="sxs-lookup"><span data-stu-id="baa9b-157">In the previous versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], a party definition also included the agreement definition.</span></span> <span data-ttu-id="baa9b-158">因此，傳送管線在查閱合作對象屬性時，會在合作對象定義內部尋找協議定義，然後據以處理訊息。</span><span class="sxs-lookup"><span data-stu-id="baa9b-158">So, when the send pipeline looked up the party properties, it would internally look for the agreement definition within the party definition and then process the messages accordingly.</span></span> <span data-ttu-id="baa9b-159">使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，由於合作對象 (或交易夥伴) 不同於交易夥伴協議，因此傳送管線會特別去尋找交易夥伴協議。</span><span class="sxs-lookup"><span data-stu-id="baa9b-159">With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], because the party (or trading partner) is distinct from the trading partner agreement, the send pipeline looks for the trading partner agreement specifically.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="baa9b-160">如果某個訊息所解析的所有目標協議都已停用，就會擱置此訊息。</span><span class="sxs-lookup"><span data-stu-id="baa9b-160">If all the agreements that a message resolves to are disabled, the message will be suspended.</span></span>  <span data-ttu-id="baa9b-161">此外，事件日誌也會記錄一則警告。</span><span class="sxs-lookup"><span data-stu-id="baa9b-161">A warning is also logged in the Event log.</span></span>  
  
-   <span data-ttu-id="baa9b-162">在不可否認性資料庫中儲存訊息的複本</span><span class="sxs-lookup"><span data-stu-id="baa9b-162">Saving copies of the message in the non-repudiation database</span></span>  
  
-   <span data-ttu-id="baa9b-163">套用 AS2 信封</span><span class="sxs-lookup"><span data-stu-id="baa9b-163">Applying an AS2 envelope</span></span>  
  
-   <span data-ttu-id="baa9b-164">傳送多個文件</span><span class="sxs-lookup"><span data-stu-id="baa9b-164">Sending multiple documents</span></span>  
  
-   <span data-ttu-id="baa9b-165">將每個文件檔案名稱儲存成 MIME 信封的一部分</span><span class="sxs-lookup"><span data-stu-id="baa9b-165">Storing each documents filename as part of the MIME envelope</span></span>  
  
-   <span data-ttu-id="baa9b-166">簽署訊息</span><span class="sxs-lookup"><span data-stu-id="baa9b-166">Signing the message</span></span>  
  
    > [!NOTE]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="baa9b-167"> 可讓您覆寫預設的簽章憑證，並改用協議中同意的憑證。</span><span class="sxs-lookup"><span data-stu-id="baa9b-167"> enables you to override the default signing certificate and instead use a certificate agreed upon in the agreement.</span></span> <span data-ttu-id="baa9b-168">如需覆寫預設憑證簽署外寄訊息的指示，請參閱[設定 AS2 屬性](../core/configuring-as2-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="baa9b-168">For instructions on overriding default certificate for signing outgoing messages, see [Configuring AS2 Properties](../core/configuring-as2-properties.md).</span></span>  
  
-   <span data-ttu-id="baa9b-169">壓縮訊息</span><span class="sxs-lookup"><span data-stu-id="baa9b-169">Compressing the message</span></span>  
  
-   <span data-ttu-id="baa9b-170">加密訊息</span><span class="sxs-lookup"><span data-stu-id="baa9b-170">Encrypting the message</span></span>  
  
-   <span data-ttu-id="baa9b-171">計算 MDN 的 MIC 值</span><span class="sxs-lookup"><span data-stu-id="baa9b-171">Computing an MIC value for the MDN</span></span>  
  
-   <span data-ttu-id="baa9b-172">處理內送 MDN (在同步 MDN 的情況下)</span><span class="sxs-lookup"><span data-stu-id="baa9b-172">Processing an incoming MDN (in the case of a synchronous MDN)</span></span>  
  
-   <span data-ttu-id="baa9b-173">重新傳送訊息 (如果沒有收到任何 MDN 的話)</span><span class="sxs-lookup"><span data-stu-id="baa9b-173">Resending the message if no MDN is received</span></span>  
  
 <span data-ttu-id="baa9b-174">以下是您在使用 AS2 接收端處理時必須考量的一些事項：</span><span class="sxs-lookup"><span data-stu-id="baa9b-174">Following are some considerations that you must make while using AS2 receive-side processing:</span></span>  
  
-   <span data-ttu-id="baa9b-175">傳送埠只能使用 HTTP 配接器。</span><span class="sxs-lookup"><span data-stu-id="baa9b-175">The send port can only use the HTTP adapter.</span></span>  
  
-   <span data-ttu-id="baa9b-176">如需有關 AS2 傳送端處理的詳細資訊，請參閱[如何 BizTalk Server 傳送 AS2 訊息](../core/how-biztalk-server-sends-as2-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="baa9b-176">For more information about AS2 send-side processing, see [How BizTalk Server Sends AS2 Messages](../core/how-biztalk-server-sends-as2-messages.md).</span></span>  
  
-   <span data-ttu-id="baa9b-177">如需在傳送管線中執行之特定處理的詳細資訊，請參閱[產生外寄 AS2 訊息](../core/generating-an-outgoing-as2-message.md)。</span><span class="sxs-lookup"><span data-stu-id="baa9b-177">For more information about the specific processing performed in the send pipeline, see [Generating an Outgoing AS2 Message](../core/generating-an-outgoing-as2-message.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baa9b-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="baa9b-178">See Also</span></span>  
 <span data-ttu-id="baa9b-179">[中協議的 AS2 處理的角色](../core/the-role-of-agreements-in-as2-processing.md) </span><span class="sxs-lookup"><span data-stu-id="baa9b-179">[The Role of Agreements in AS2 Processing](../core/the-role-of-agreements-in-as2-processing.md) </span></span>  
 <span data-ttu-id="baa9b-180">[BizTalk Server 如何接收 AS2 訊息](../core/how-biztalk-server-receives-as2-messages.md) </span><span class="sxs-lookup"><span data-stu-id="baa9b-180">[How BizTalk Server Receives AS2 Messages](../core/how-biztalk-server-receives-as2-messages.md) </span></span>  
 [<span data-ttu-id="baa9b-181">BizTalk Server 傳送 AS2 訊息的方式</span><span class="sxs-lookup"><span data-stu-id="baa9b-181">How BizTalk Server Sends AS2 Messages</span></span>](../core/how-biztalk-server-sends-as2-messages.md)