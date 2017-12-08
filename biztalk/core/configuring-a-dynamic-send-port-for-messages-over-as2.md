---
title: "透過 AS2 的訊息設定動態傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 246d64e8-70ca-48f4-8b72-d43b0964dbb4
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de6df553a3f03e9d2e60b78de9877ad6113b04e3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-a-dynamic-send-port-for-messages-over-as2"></a><span data-ttu-id="3775f-102">為透過 AS2 的訊息設定動態傳送埠</span><span class="sxs-lookup"><span data-stu-id="3775f-102">Configuring a Dynamic Send Port for Messages over AS2</span></span>
<span data-ttu-id="3775f-103">本主題將說明如何設定讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 透過動態傳送埠傳送 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="3775f-103">This topic describes how to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to send AS2 messages over a dynamic send port.</span></span> <span data-ttu-id="3775f-104">這項設定包括建立動態傳送埠，以及設定後端應用程式以設定適當的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="3775f-104">This configuration includes creating the dynamic send port and configuring a backend application to set the appropriate context properties.</span></span> <span data-ttu-id="3775f-105">在建立動態傳送埠以傳送 AS2 訊息時，您必須升級部分屬性，傳送埠才能運作。</span><span class="sxs-lookup"><span data-stu-id="3775f-105">When you create a dynamic send port to send an AS2 message, you must promote certain properties for the send port to work.</span></span> <span data-ttu-id="3775f-106">如需詳細資訊，請參閱[設定 BizTalk Server 傳送 AS2 訊息透過動態傳送埠](../core/configuring-a-dynamic-send-port-for-messages-over-as2.md#BKMK_Proc)下方。</span><span class="sxs-lookup"><span data-stu-id="3775f-106">For more information, see [To configure BizTalk Server to send AS2 messages over a dynamic send port](../core/configuring-a-dynamic-send-port-for-messages-over-as2.md#BKMK_Proc) below.</span></span>  
  
 <span data-ttu-id="3775f-107">動態傳送埠可以讓您將訊息傳送給多個合作對象，而不用將合作對象組態寫入程式碼。</span><span class="sxs-lookup"><span data-stu-id="3775f-107">A dynamic send port enables you to send messages to multiple parties without hard-coding the party configuration.</span></span> <span data-ttu-id="3775f-108">透過內容屬性，動態地決定傳送訊息所使用的協議與目的地。</span><span class="sxs-lookup"><span data-stu-id="3775f-108">The agreement and destination to be used in sending the message are determined dynamically through context properties.</span></span> <span data-ttu-id="3775f-109">您不需要為每個個別的客戶建立靜態傳送埠。</span><span class="sxs-lookup"><span data-stu-id="3775f-109">You do not have to create a static send port for each individual customer.</span></span>  
  
 <span data-ttu-id="3775f-110">若要傳送具有 EDI 或非 EDI 訊息或 EDI 通知的 AS2 訊息，請使用下列組態建立動態回應 HTTP 傳送埠：</span><span class="sxs-lookup"><span data-stu-id="3775f-110">To send an AS2 message with an EDI or non-EDI message or an EDI acknowledgment, create a dynamic response HTTP send port with the following configuration:</span></span>  
  
|<span data-ttu-id="3775f-111">位置</span><span class="sxs-lookup"><span data-stu-id="3775f-111">Location</span></span>|<span data-ttu-id="3775f-112">屬性</span><span class="sxs-lookup"><span data-stu-id="3775f-112">Property</span></span>|<span data-ttu-id="3775f-113">設定</span><span class="sxs-lookup"><span data-stu-id="3775f-113">Setting</span></span>|  
|--------------|--------------|-------------|  
|<span data-ttu-id="3775f-114">**傳送埠屬性： 一般**</span><span class="sxs-lookup"><span data-stu-id="3775f-114">**Send Port Properties: General**</span></span>|<span data-ttu-id="3775f-115">連接埠類型</span><span class="sxs-lookup"><span data-stu-id="3775f-115">Port Type</span></span>|<span data-ttu-id="3775f-116">-動態請求回應 (如果在 要求 MDN**通知 (Mdn)**選取頁面的單向協議索引標籤)</span><span class="sxs-lookup"><span data-stu-id="3775f-116">- Dynamic Solicit Response (if Request MDN in **Acknowledgements (MDNs)** page in the one-way agreement tab is selected)</span></span><br /><br /> <span data-ttu-id="3775f-117">-動態單向傳送埠 (如果在 要求 MDN**通知 (Mdn)**清除頁面的單向協議索引標籤)</span><span class="sxs-lookup"><span data-stu-id="3775f-117">- Dynamic One-way Send Port (if Request MDN in **Acknowledgements (MDNs)** page in the one-way agreement tab is cleared)</span></span>|  
|<span data-ttu-id="3775f-118">**傳送埠屬性： 一般**</span><span class="sxs-lookup"><span data-stu-id="3775f-118">**Send Port Properties: General**</span></span>|<span data-ttu-id="3775f-119">傳送管線</span><span class="sxs-lookup"><span data-stu-id="3775f-119">Send pipeline</span></span>|<span data-ttu-id="3775f-120">-AS2EdiSend （用於 EDI 編碼訊息）</span><span class="sxs-lookup"><span data-stu-id="3775f-120">- AS2EdiSend (for EDI-encoded messages)</span></span><br /><br /> <span data-ttu-id="3775f-121">-AS2Send （用於非 EDI 訊息）</span><span class="sxs-lookup"><span data-stu-id="3775f-121">- AS2Send (for non-EDI messages)</span></span>|  
|<span data-ttu-id="3775f-122">**傳送埠屬性： 一般**</span><span class="sxs-lookup"><span data-stu-id="3775f-122">**Send Port Properties: General**</span></span>|<span data-ttu-id="3775f-123">接收管線</span><span class="sxs-lookup"><span data-stu-id="3775f-123">Receive pipeline</span></span><br /><br /> <span data-ttu-id="3775f-124">(如果在 要求 MDN**通知 (Mdn)**選取頁面的單向協議索引標籤)</span><span class="sxs-lookup"><span data-stu-id="3775f-124">(if Request MDN in **Acknowledgements (MDNs)** page in the one-way agreement tab is selected)</span></span>|<span data-ttu-id="3775f-125">AS2Receive (用於動態請求回應傳送埠)</span><span class="sxs-lookup"><span data-stu-id="3775f-125">AS2Receive (for dynamic solicit response send port)</span></span>|  
|<span data-ttu-id="3775f-126">**傳送埠屬性： 篩選**</span><span class="sxs-lookup"><span data-stu-id="3775f-126">**Send Port Properties: Filters**</span></span>|<span data-ttu-id="3775f-127">屬性</span><span class="sxs-lookup"><span data-stu-id="3775f-127">Property</span></span>|<span data-ttu-id="3775f-128">BTS.MessageType</span><span class="sxs-lookup"><span data-stu-id="3775f-128">BTS.MessageType</span></span>|  
|<span data-ttu-id="3775f-129">**傳送埠屬性： 篩選**</span><span class="sxs-lookup"><span data-stu-id="3775f-129">**Send Port Properties: Filters**</span></span>|<span data-ttu-id="3775f-130">運算子</span><span class="sxs-lookup"><span data-stu-id="3775f-130">Operator</span></span>|==|  
|<span data-ttu-id="3775f-131">**傳送埠屬性： 篩選**</span><span class="sxs-lookup"><span data-stu-id="3775f-131">**Send Port Properties: Filters**</span></span>|<span data-ttu-id="3775f-132">值</span><span class="sxs-lookup"><span data-stu-id="3775f-132">Value</span></span>|<span data-ttu-id="3775f-133">- `http://schemas.microsoft.com/BizTalk/EDI/X12/2006#<schema name>`（適用於 EDI 訊息）</span><span class="sxs-lookup"><span data-stu-id="3775f-133">- `http://schemas.microsoft.com/BizTalk/EDI/X12/2006#<schema name>` (for an EDI message)</span></span><br /><br /> <span data-ttu-id="3775f-134">- `http://schemas.microsoft.com/Edi/X12#X12_<997 or TA1>_Root`(對於 X12 通知)</span><span class="sxs-lookup"><span data-stu-id="3775f-134">- `http://schemas.microsoft.com/Edi/X12#X12_<997 or TA1>_Root` (for an X12 acknowledgment)</span></span><br /><br /> <span data-ttu-id="3775f-135">- `http://schemas.microsoft.com/Edi/Efact#Efact_Contrl_Root`（適用於 EDIFACT 通知）</span><span class="sxs-lookup"><span data-stu-id="3775f-135">- `http://schemas.microsoft.com/Edi/Efact#Efact_Contrl_Root` (for an EDIFACT acknowledgment)</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="3775f-136">必要條件</span><span class="sxs-lookup"><span data-stu-id="3775f-136">Prerequisites</span></span>  
 <span data-ttu-id="3775f-137">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="3775f-137">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
##  <a name="BKMK_Proc"></a><span data-ttu-id="3775f-138">若要設定 BizTalk Server 傳送 AS2 訊息透過動態傳送埠</span><span class="sxs-lookup"><span data-stu-id="3775f-138">To configure BizTalk Server to send AS2 messages over a dynamic send port</span></span>  
  
1.  <span data-ttu-id="3775f-139">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，使用上述組態，建立動態單向傳送埠 (如果未要求 MDN) 或動態請求回應傳送埠 (如果有要求 MDN)。</span><span class="sxs-lookup"><span data-stu-id="3775f-139">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, create a dynamic one-way send port (if an MDN is not requested) or a dynamic solicit response send port (if an MDN is requested) with the above configuration.</span></span>  
  
2.  <span data-ttu-id="3775f-140">對於適用這個訊息的協議，設定必要的 AS2 與 EDI 屬性。</span><span class="sxs-lookup"><span data-stu-id="3775f-140">For the agreement that applies to this message, set the AS2 and EDI properties required.</span></span>  
  
3.  <span data-ttu-id="3775f-141">升級訊息內容的下列屬性：</span><span class="sxs-lookup"><span data-stu-id="3775f-141">Promote the following properties to the message context:</span></span>  
  
    -   `BTS.MessageType`  
  
    -   `EdiIntAS.MessageID`  
  
4.  <span data-ttu-id="3775f-142">在後端應用程式加入功能，以寫入下列訊息內容屬性，並設定為適當值：</span><span class="sxs-lookup"><span data-stu-id="3775f-142">Add functionality to a backend application to write the following properties to the message context, setting them to the appropriate values:</span></span>  
  
    -   `EdiIntAS.AS2To`  
  
    -   `BTS.OutboundTransportLocation`  
  
    -   `HTTP.EnableChunkedEncoding`  
  
    -   `BTS.EncryptionCert`  
  
    > [!NOTE]
    >  <span data-ttu-id="3775f-143">`AS2To` 內容屬性與 `OutboundTransportLocation` 內容屬性必須寫入訊息內容中，動態傳送埠才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="3775f-143">The `AS2To` context property and the `OutboundTransportLocation` context property must be written to the message context for the dynamic send port to function properly.</span></span> <span data-ttu-id="3775f-144">在處理外寄訊息時，連接埠需要有 `AS2To` 屬性才能決定要使用的協議，而傳送埠需要有 `OutboundTransportLocation` 屬性才能決定訊息目的地。</span><span class="sxs-lookup"><span data-stu-id="3775f-144">The `AS2To` property is required for the port to determine the agreement to use in processing the outgoing message and the `OutboundTransportLocation` property is required for the send port to determine the destination of the message.</span></span> <span data-ttu-id="3775f-145">如需詳細資訊，請參閱[產生外寄 AS2 訊息](../core/generating-an-outgoing-as2-message.md)。</span><span class="sxs-lookup"><span data-stu-id="3775f-145">For more information, see [Generating an Outgoing AS2 Message](../core/generating-an-outgoing-as2-message.md).</span></span>  
  
## <a name="functionality"></a><span data-ttu-id="3775f-146">功能</span><span class="sxs-lookup"><span data-stu-id="3775f-146">Functionality</span></span>  
 <span data-ttu-id="3775f-147">動態傳送埠和管線會執行下列操作，透過 AS2 傳送同步 EDI 或非 EDI 訊息或通知，以及處理傳回的 MDN：</span><span class="sxs-lookup"><span data-stu-id="3775f-147">The dynamic send port and pipeline does the following to send a synchronous EDI or non-EDI message or acknowledgment over AS2 and process the returned MDN:</span></span>  
  
-   <span data-ttu-id="3775f-148">如果要傳送 EDI 訊息，請挑選 EDI 訊息，方法是透過篩選在 `BTS.MessageType` 中設為訊息結構描述 (例如，864 訊息為 X12_00401_864) 的 `http://schemas.microsoft.com/BizTalk/EDI/X12/2006 namespace` 屬性。</span><span class="sxs-lookup"><span data-stu-id="3775f-148">If sending an EDI message, picks up the EDI message by filtering on the property `BTS.MessageType` set to the message schema in the `http://schemas.microsoft.com/BizTalk/EDI/X12/2006 namespace` (for example, X12_00401_864 for an 864 message).</span></span>  
  
-   <span data-ttu-id="3775f-149">如果要傳送 EDI 通知，請挑選通知，方法是透過篩選設為下列其中一個控制結構描述的 `BTS.MessageType` 屬性：</span><span class="sxs-lookup"><span data-stu-id="3775f-149">If sending an EDI acknowledgment, picks up the acknowledgment by filtering on the property `BTS.MessageType` set to one of the following control schema:</span></span>  
  
    -   <span data-ttu-id="3775f-150">997 通知為 `http://schemas.microsoft.com/BizTalk/EDI/X12#X12_997_Root`</span><span class="sxs-lookup"><span data-stu-id="3775f-150">`http://schemas.microsoft.com/BizTalk/EDI/X12#X12_997_Root` for a 997 acknowledgment</span></span>  
  
    -   <span data-ttu-id="3775f-151">TA1 通知為 `http://schemas.microsoft.com/BizTalk/EDI/X12#X12_TA1_Root`</span><span class="sxs-lookup"><span data-stu-id="3775f-151">`http://schemas.microsoft.com/BizTalk/EDI/X12#X12_TA1_Root` for a TA1 acknowledgment</span></span>  
  
    -   <span data-ttu-id="3775f-152">CONTRL 通知為 `http://schemas.microsoft.com/BizTalk/EDI/Efact#Efact_Contrl_Root`</span><span class="sxs-lookup"><span data-stu-id="3775f-152">`http://schemas.microsoft.com/BizTalk/EDI/Efact#Efact_Contrl_Root` for a CONTRL acknowledgment</span></span>  
  
-   <span data-ttu-id="3775f-153">如果要傳送非 EDI 訊息，則使用適當的篩選條件挑選訊息。</span><span class="sxs-lookup"><span data-stu-id="3775f-153">If sending a non-EDI message, picks up the message using an appropriate filter.</span></span>  
  
-   <span data-ttu-id="3775f-154">建置 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="3775f-154">Builds an AS2 message.</span></span> <span data-ttu-id="3775f-155">如需此程序的詳細資訊，請參閱[產生外寄 AS2 訊息](../core/generating-an-outgoing-as2-message.md)。</span><span class="sxs-lookup"><span data-stu-id="3775f-155">For more information about this process, see [Generating an Outgoing AS2 Message](../core/generating-an-outgoing-as2-message.md).</span></span>  
  
    > [!NOTE]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3775f-156"> 會由 URL 的格式 (例如 http、smtp 以及 ftp 等) 來決定動態傳送埠所使用的傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="3775f-156"> determines the transport type to be used by the dynamic send port from the format of the URL, i.e., http, smtp, ftp, etc.</span></span>  
  
-   <span data-ttu-id="3775f-157">路由傳送訊息或通知至傳送埠的目的地 URL。</span><span class="sxs-lookup"><span data-stu-id="3775f-157">Routes the message or acknowledgment to the destination URL for the send port.</span></span>  
  
-   <span data-ttu-id="3775f-158">接收訊息或通知的 MDN 回應 (在有啟用且為請求-回應傳送埠的情況下)。</span><span class="sxs-lookup"><span data-stu-id="3775f-158">Receives the MDN response to the message or acknowledgment, if enabled and if a solicit-response send port.</span></span> <span data-ttu-id="3775f-159">如需此程序的詳細資訊，請參閱[處理內送 MDN](../core/processing-an-incoming-mdn.md)。</span><span class="sxs-lookup"><span data-stu-id="3775f-159">For more information about this process, see [Processing an Incoming MDN](../core/processing-an-incoming-mdn.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3775f-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3775f-160">See Also</span></span>  
 [<span data-ttu-id="3775f-161">設定 AS2 方案的連接埠</span><span class="sxs-lookup"><span data-stu-id="3775f-161">Configuring Ports for an AS2 Solution</span></span>](../core/configuring-ports-for-an-as2-solution.md)