---
title: "BizTalk 訊息佇列大型訊息延伸模組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Message Queuing Large Message Extension
- utilities, BizTalk Message Queuing Large Message Extension
ms.assetid: 5d6892d3-fda8-41a3-8111-d28c11bd71fb
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 399c8e02d59a931dbf30bfa31ca28980dfa312be
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="biztalk-message-queuing-large-message-extension"></a><span data-ttu-id="00cd1-102">BizTalk 訊息佇列大型訊息延伸模組</span><span class="sxs-lookup"><span data-stu-id="00cd1-102">BizTalk Message Queuing Large Message Extension</span></span>
<span data-ttu-id="00cd1-103">原生訊息佇列無法處理的訊息內文大於 4megabytes (MB)。</span><span class="sxs-lookup"><span data-stu-id="00cd1-103">Native message queuing cannot process a message with a body larger than 4megabytes (MB).</span></span> <span data-ttu-id="00cd1-104">不過，Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]包含原生訊息佇列的附加元件可以處理大於 4 MB 的訊息。</span><span class="sxs-lookup"><span data-stu-id="00cd1-104">However, Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes an add-on for native message queuing that permits processing messages larger than 4 MB.</span></span> <span data-ttu-id="00cd1-105">此附加元件當做 Mqrtlarge.dll 檔案，會傳遞，而且會公開**MQSendLargeMessage**和**MQReceiveLargeMessage**應用程式發展介面 (Api)，以及類似的 COM 模型。</span><span class="sxs-lookup"><span data-stu-id="00cd1-105">This add-on is delivered as the Mqrtlarge.dll file, and exposes the **MQSendLargeMessage** and **MQReceiveLargeMessage** application programming interfaces (APIs), and the analogous COM model.</span></span> <span data-ttu-id="00cd1-106">這些函式會實作為標準訊息佇列應用程式開發介面， **MQSendMessage**和**MQReceiveMessage**分別。</span><span class="sxs-lookup"><span data-stu-id="00cd1-106">These functions are implemented as standard message queuing APIs, **MQSendMessage** and **MQReceiveMessage** respectively.</span></span>  
  
 <span data-ttu-id="00cd1-107">若要參與大型訊息交換，訊息佇列電腦必須安裝 Mqrtlarge.dll 檔案，而且訊息佇列應用程式必須使用附加元件 API。</span><span class="sxs-lookup"><span data-stu-id="00cd1-107">To participate in large message exchanges, the message queuing computer must have the Mqrtlarge.dll file installed, and the message queuing application should use the add-on APIs.</span></span> <span data-ttu-id="00cd1-108">否則，完整訊息會被分割。</span><span class="sxs-lookup"><span data-stu-id="00cd1-108">Otherwise, complete messages will be fragmented.</span></span>  
  
 <span data-ttu-id="00cd1-109">**SDK 中的位置**</span><span class="sxs-lookup"><span data-stu-id="00cd1-109">**Location in SDK**</span></span>  
  
 <span data-ttu-id="00cd1-110">\<*安裝路徑*\>\SDK\ Mqrtlarge.dll</span><span class="sxs-lookup"><span data-stu-id="00cd1-110">\<*Installation Path*\>\SDK\ Mqrtlarge.dll</span></span>  
  
 <span data-ttu-id="00cd1-111">**檔案庫存**</span><span class="sxs-lookup"><span data-stu-id="00cd1-111">**File Inventory**</span></span>  
  
 <span data-ttu-id="00cd1-112">下表顯示此公用程式所使用的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="00cd1-112">The following table shows the file this utility uses and describes its purpose.</span></span>  
  
|<span data-ttu-id="00cd1-113">檔案</span><span class="sxs-lookup"><span data-stu-id="00cd1-113">File(s)</span></span>|<span data-ttu-id="00cd1-114">Description</span><span class="sxs-lookup"><span data-stu-id="00cd1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="00cd1-115">Mqrtlarge.dll</span><span class="sxs-lookup"><span data-stu-id="00cd1-115">Mqrtlarge.dll</span></span>|<span data-ttu-id="00cd1-116">公開的 Win32 動態連結程式庫**MQSendLargeMessage**和**MQReceiveLargeMessage**。</span><span class="sxs-lookup"><span data-stu-id="00cd1-116">A Win32 dynamic-link library that exposes **MQSendLargeMessage** and **MQReceiveLargeMessage**.</span></span><br /><br /> <span data-ttu-id="00cd1-117">標頭檔位於*\<安裝路徑\>*\SDK\Include 目錄。</span><span class="sxs-lookup"><span data-stu-id="00cd1-117">The header files are located in the *\<Installation Path\>*\SDK\Include directory.</span></span> <span data-ttu-id="00cd1-118">**注意：**必須安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]到 64 位元版本的 Windows，才能存取 64 位元版本的 Mqrtlarge.dll。</span><span class="sxs-lookup"><span data-stu-id="00cd1-118">**Note:**  You must install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] onto a 64 bit version of Windows in order to access the 64 bit version of Mqrtlarge.dll.</span></span>|  
  
 <span data-ttu-id="00cd1-119">**使用此公用程式**</span><span class="sxs-lookup"><span data-stu-id="00cd1-119">**Using This Utility**</span></span>  
  
 <span data-ttu-id="00cd1-120">請依照下列程序執行 Mqrtlarge.dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="00cd1-120">Use the following procedure to run the Mqrtlarge.dll file.</span></span>  
  
### <a name="to-use-the-mqrtlargedll-file"></a><span data-ttu-id="00cd1-121">若要使用 Mqrtlarge.dll 檔案</span><span class="sxs-lookup"><span data-stu-id="00cd1-121">To use the Mqrtlarge.dll file</span></span>  
  
1.  > [!NOTE]
    >  <span data-ttu-id="00cd1-122">MSMQ 未搭配 BizTalk Server 解決方案，MQRTLarge.dll 可能仍正常運作。</span><span class="sxs-lookup"><span data-stu-id="00cd1-122">For an MSMQ solution without BizTalk Server, the MQRTLarge.dll may still function correctly.</span></span> <span data-ttu-id="00cd1-123">不過，這不是建議的設定，Microsoft 支援，而且如果在 BizTalk Server 環境之外使用，可能會發生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="00cd1-123">However, this is not a recommended configuration that Microsoft supports, and unexpected results may occur if used outside of the BizTalk Server environment.</span></span>  
  
     <span data-ttu-id="00cd1-124">將 Mqrtlarge.dll 檔案新增至不包含 BizTalk Server 安裝的電腦。</span><span class="sxs-lookup"><span data-stu-id="00cd1-124">Add the file Mqrtlarge.dll to the computer that does not contain an installation of BizTalk Server.</span></span> <span data-ttu-id="00cd1-125">「訊息佇列」會使用 Mqrtlarge.dll，傳送訊息至 BizTalk Server 或從其接收訊息。</span><span class="sxs-lookup"><span data-stu-id="00cd1-125">Message Queuing uses Mqrtlarge.dll to send or receive messages to or from BizTalk Server.</span></span>  
  
2.  <span data-ttu-id="00cd1-126">若要存取 Mqrtlarge.dll 檔案中的 API，請在傳送訊息至連接 BizTalk「訊息佇列」結束點的其他電腦或從中接收訊息的應用程式中，新增 Mqrtlarge.dll 檔案的參考。</span><span class="sxs-lookup"><span data-stu-id="00cd1-126">To access the APIs in the Mqrtlarge.dll file, add a reference to the Mqrtlarge.dll file in the applications that send or receive messages to or from other computers to the BizTalk Message Queuing endpoint.</span></span>  
  
 <span data-ttu-id="00cd1-127">**註解**</span><span class="sxs-lookup"><span data-stu-id="00cd1-127">**Remarks**</span></span>  
  
 <span data-ttu-id="00cd1-128">大型訊息會傳送至標準「訊息佇列」(也稱為 MSMQ) 佇列。</span><span class="sxs-lookup"><span data-stu-id="00cd1-128">Large messages are sent to standard Message Queuing (also known as MSMQ) queues.</span></span> <span data-ttu-id="00cd1-129">您只能在這些佇列上使用大型訊息 API，但這並非強制性。</span><span class="sxs-lookup"><span data-stu-id="00cd1-129">You should use only the large message APIs on such queues, although this is not enforced.</span></span>  
  
 <span data-ttu-id="00cd1-130">您仍然可以使用**MQSendMessage**將訊息傳送至您傳送大型訊息的佇列。</span><span class="sxs-lookup"><span data-stu-id="00cd1-130">You can still use **MQSendMessage** to send messages to a queue to which you sent large messages.</span></span> <span data-ttu-id="00cd1-131">同樣地，您可以使用**MQReceiveMessage** ，從這些佇列接收訊息，但不建議因為它可能會影響效能的**MQReceiveLargeMessage**應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="00cd1-131">Likewise, you can use **MQReceiveMessage** to receive messages from such queues, although it is not recommended because it may impact the performance of the **MQReceiveLargeMessage** API.</span></span>  
  
 <span data-ttu-id="00cd1-132">進行復原，建議您改用**DEAD_LETTER**日誌。</span><span class="sxs-lookup"><span data-stu-id="00cd1-132">For recovery purposes, it is recommended that you use **DEAD_LETTER** journaling.</span></span>  
  
 <span data-ttu-id="00cd1-133">**片段**</span><span class="sxs-lookup"><span data-stu-id="00cd1-133">**Fragmentation**</span></span>  
  
 <span data-ttu-id="00cd1-134">一般而言，大型訊息會分割成數個訊息，每個訊息都小於 4 MB。</span><span class="sxs-lookup"><span data-stu-id="00cd1-134">In general, a large message will be fragmented into numerous messages, each smaller than 4 MB.</span></span> <span data-ttu-id="00cd1-135">只分割內文，瞭解這一點非常重要。</span><span class="sxs-lookup"><span data-stu-id="00cd1-135">It is important to understand that only the body is fragmented.</span></span> <span data-ttu-id="00cd1-136">其餘的屬性會隨著每個片段傳送。</span><span class="sxs-lookup"><span data-stu-id="00cd1-136">The rest of the properties are sent with each fragment.</span></span>  
  
 <span data-ttu-id="00cd1-137">片段數目是由訊息大小和片段大小所定義。</span><span class="sxs-lookup"><span data-stu-id="00cd1-137">The number of fragments is defined by the size of the message and the size of the fragments.</span></span> <span data-ttu-id="00cd1-138">Mqrtlarge.dll 檔案或 BizTalk「訊息佇列」的適當部分可能會自動決定片段大小。</span><span class="sxs-lookup"><span data-stu-id="00cd1-138">The fragment size may be automatically determined by the file Mqrtlarge.dll or the appropriate part of BizTalk Message Queuing.</span></span> <span data-ttu-id="00cd1-139">應用程式也可以明確地指定片段大小。</span><span class="sxs-lookup"><span data-stu-id="00cd1-139">Applications can also explicitly specify the fragment size.</span></span>  
  
 <span data-ttu-id="00cd1-140">請注意，大型訊息延伸模組需要新增常數大小的額外內部資料，以便延伸訊息。</span><span class="sxs-lookup"><span data-stu-id="00cd1-140">Note that the large message extension requires extending the message by adding additional internal data of a constant size.</span></span>  
  
 <span data-ttu-id="00cd1-141">**PROPID_M_EXTENSION**</span><span class="sxs-lookup"><span data-stu-id="00cd1-141">**PROPID_M_EXTENSION**</span></span>  
  
 <span data-ttu-id="00cd1-142">您可以使用**PROPID_M_EXTENSION/PROPID_M_EXTENSION_LEN**屬性來簽署訊息。</span><span class="sxs-lookup"><span data-stu-id="00cd1-142">You can use the **PROPID_M_EXTENSION/PROPID_M_EXTENSION_LEN** properties to sign the message.</span></span> <span data-ttu-id="00cd1-143">簽章包含 40 位元組 (B)。</span><span class="sxs-lookup"><span data-stu-id="00cd1-143">The signature comprises 40 bytes (B).</span></span> <span data-ttu-id="00cd1-144">下表顯示簽章片段。</span><span class="sxs-lookup"><span data-stu-id="00cd1-144">The following table shows signature fragments.</span></span>  
  
|<span data-ttu-id="00cd1-145">Description</span><span class="sxs-lookup"><span data-stu-id="00cd1-145">Description</span></span>|<span data-ttu-id="00cd1-146">大小</span><span class="sxs-lookup"><span data-stu-id="00cd1-146">Size</span></span>|  
|-----------------|----------|  
|<span data-ttu-id="00cd1-147">此項表示應使用傳送此訊息的全域唯一識別碼 (GUID) **MQSendLargeMessage**</span><span class="sxs-lookup"><span data-stu-id="00cd1-147">Globally unique identifier (GUID) denoting that this message was sent using **MQSendLargeMessage**</span></span>|<span data-ttu-id="00cd1-148">16 B</span><span class="sxs-lookup"><span data-stu-id="00cd1-148">16 B</span></span>|  
|<span data-ttu-id="00cd1-149">訊息的 GUID： 通用於所有訊息部分的唯一的每個大型訊息識別碼</span><span class="sxs-lookup"><span data-stu-id="00cd1-149">GUID for the message: unique per-large message ID that is common to all parts of the message</span></span>|<span data-ttu-id="00cd1-150">16 B</span><span class="sxs-lookup"><span data-stu-id="00cd1-150">16 B</span></span>|  
|<span data-ttu-id="00cd1-151">大型訊息的總大小</span><span class="sxs-lookup"><span data-stu-id="00cd1-151">Total size of the large message</span></span>|<span data-ttu-id="00cd1-152">4 B</span><span class="sxs-lookup"><span data-stu-id="00cd1-152">4 B</span></span>|  
|<span data-ttu-id="00cd1-153">部分編號</span><span class="sxs-lookup"><span data-stu-id="00cd1-153">Part number</span></span>|<span data-ttu-id="00cd1-154">2 B</span><span class="sxs-lookup"><span data-stu-id="00cd1-154">2 B</span></span>|  
|<span data-ttu-id="00cd1-155">訊息部分數目</span><span class="sxs-lookup"><span data-stu-id="00cd1-155">Number of message parts</span></span>|<span data-ttu-id="00cd1-156">2 B</span><span class="sxs-lookup"><span data-stu-id="00cd1-156">2 B</span></span>|  
  
 <span data-ttu-id="00cd1-157">在決定来使用**PROPID_M_EXTENSION**還有其他。</span><span class="sxs-lookup"><span data-stu-id="00cd1-157">The decision to use **PROPID_M_EXTENSION** has an additional implication.</span></span> <span data-ttu-id="00cd1-158">Microsoft Host Integration Server MSMQ-MQSeries Bridge 會使用此屬性，傳遞包含 MQSeries 和訊息佇列訊息之間未直接對應之屬性的結構。</span><span class="sxs-lookup"><span data-stu-id="00cd1-158">The Microsoft Host Integration Server MSMQ-MQSeries Bridge uses this property to pass a structure that contains properties that are not mapped directly between MQSeries and Message Queuing messages.</span></span> <span data-ttu-id="00cd1-159">將訊息明確或隱含傳送至 MQSeries 或從中接收訊息的應用程式會使用此結構。</span><span class="sxs-lookup"><span data-stu-id="00cd1-159">Applications that send messages to and from MQSeries explicitly or implicitly use this structure.</span></span> <span data-ttu-id="00cd1-160">當接收端應用程式已從佇列接收訊息時，「訊息佇列」都會產生通知。</span><span class="sxs-lookup"><span data-stu-id="00cd1-160">Message Queuing can generate acknowledgments when a message has been received from a queue by a receiving application.</span></span> <span data-ttu-id="00cd1-161">該通知會傳送至傳送端應用程式所指定的佇列。</span><span class="sxs-lookup"><span data-stu-id="00cd1-161">The acknowledgments are sent to a queue specified by the sending application.</span></span> <span data-ttu-id="00cd1-162">至於大型訊息，您只針對其最後部分傳送此通知。</span><span class="sxs-lookup"><span data-stu-id="00cd1-162">In the case of large messages, you send this acknowledgment only for the last part of the large message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00cd1-163">請參閱</span><span class="sxs-lookup"><span data-stu-id="00cd1-163">See Also</span></span>  
 [<span data-ttu-id="00cd1-164">SDK 中的公用程式</span><span class="sxs-lookup"><span data-stu-id="00cd1-164">Utilities in the SDK</span></span>](../core/utilities-in-the-sdk.md)