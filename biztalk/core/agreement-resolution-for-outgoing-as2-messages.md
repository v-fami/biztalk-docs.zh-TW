---
title: 外寄 AS2 訊息的協議解析 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 578d7565-534c-4c13-b473-975f347f3a9b
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce8329b2b80ca3b9bfd6b34379d936d6be1df3ef
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975855"
---
# <a name="agreement-resolution-for-outgoing-as2-messages"></a><span data-ttu-id="28688-102">外寄 AS2 訊息的協議解析</span><span class="sxs-lookup"><span data-stu-id="28688-102">Agreement Resolution for Outgoing AS2 Messages</span></span>
<span data-ttu-id="28688-103">當 AS2 傳送管線處理透過 HTTP/HTTPS 傳輸的外寄 EDIINT/AS2 編碼訊息時，它會判斷該訊息將解析的協議。</span><span class="sxs-lookup"><span data-stu-id="28688-103">When an AS2 send pipeline processes an outgoing EDIINT/AS2-encoded message over HTTP/HTTPS transport, it determines the agreement that the message will resolve to.</span></span> <span data-ttu-id="28688-104">它接著會使用這些協議屬性來處理外寄訊息。</span><span class="sxs-lookup"><span data-stu-id="28688-104">It will then use those agreement properties to process the outgoing message.</span></span> <span data-ttu-id="28688-105">傳送管線會使用下列準則來判斷協議 (依優先順序)：</span><span class="sxs-lookup"><span data-stu-id="28688-105">The send pipeline will use the following criteria to determine the agreement (in order of priority):</span></span>  
  
1. <span data-ttu-id="28688-106">傳送管線會嘗試將 AS2From 和 AS2To 的內容屬性與指定為協議屬性一部分之 AS2From 和 AS2To 的值進行比對。</span><span class="sxs-lookup"><span data-stu-id="28688-106">The send pipeline attempts to match the AS2From and AS2To context properties with the values of AS2From and AS2To specified as part of the agreement properties.</span></span>  
  
2. <span data-ttu-id="28688-107">如果上一個步驟失敗，傳送管線會嘗試比對輸出訊息的 AS2To 內容屬性，與 AS2To 屬性，做為其他的協議解析程式中設定的值**識別碼**協議索引標籤屬性。</span><span class="sxs-lookup"><span data-stu-id="28688-107">If the previous step fails, the send pipeline will attempt to match the AS2To context property of the outbound message with the value of AS2To property, which is set as additional agreement resolver in the **Identifiers** tab of agreement properties.</span></span>  
  
   > [!NOTE]
   >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="28688-108"> 不會將 AS2To 屬性寫入內容。</span><span class="sxs-lookup"><span data-stu-id="28688-108"> does not write the AS2To property to the context.</span></span> <span data-ttu-id="28688-109">如果您想對 AS2To 內容屬性執行協議解析，必須併入自訂協調流程或自訂管線元件才行。</span><span class="sxs-lookup"><span data-stu-id="28688-109">If you want to perform agreement resolution on the AS2To context property, you will have to incorporate a custom orchestration or a custom pipeline component to do so.</span></span> <span data-ttu-id="28688-110">如需詳細資訊，請參閱 <<c0> [ 撰寫 AS2 內容屬性，以執行輸出合作對象解析](../core/writing-as2-context-properties-for-outbound-party-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="28688-110">For more information, see [Writing AS2 Context Properties for Outbound Party Resolution](../core/writing-as2-context-properties-for-outbound-party-resolution.md).</span></span>  
   > 
   > [!NOTE]
   >  <span data-ttu-id="28688-111">當您使用動態傳送埠時，必須將 AS2To 屬性寫入至內容才能進行協議解析。</span><span class="sxs-lookup"><span data-stu-id="28688-111">When you are using a dynamic send port, the AS2To property must be written to the context for agreement resolution.</span></span>  
  
3. <span data-ttu-id="28688-112">如果上述步驟失敗，傳送管線會嘗試比對與協議關聯的傳送埠以及訂閱訊息的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="28688-112">If the previous step fails, the send pipeline will attempt to match the send port that is associated with an agreement with the send port that subscribed to the message.</span></span> <span data-ttu-id="28688-113">傳送埠是中的協議相關聯**傳送埠**頁面的單向 AS2 協議**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="28688-113">The send port is associated with the agreement in the **Send Ports** page of the one-way AS2 agreement of the **Agreement Properties** dialog box.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="28688-114">與 EDI 處理不同的是，當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法判斷協議時，沒有可用的後援 AS2 屬性。</span><span class="sxs-lookup"><span data-stu-id="28688-114">Unlike in EDI processing, there are no fallback AS2 properties that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can use if it cannot determine the agreement.</span></span> <span data-ttu-id="28688-115">不過，有預設的協議可用來傳送 MDN。</span><span class="sxs-lookup"><span data-stu-id="28688-115">There is, however, a default agreement used to send an MDN.</span></span> <span data-ttu-id="28688-116">此外，也不會使用傳送埠或 Http.UserHttpHeaders 內容屬性來解析 MDN 的協議。</span><span class="sxs-lookup"><span data-stu-id="28688-116">In addition, neither the send port nor the Http.UserHttpHeaders context property is used to resolve the agreement for an MDN.</span></span> <span data-ttu-id="28688-117">如需詳細資訊，請參閱的 「 協議解析 MDN > 一節[傳送外寄 MDN](../core/sending-an-outgoing-mdn.md)。</span><span class="sxs-lookup"><span data-stu-id="28688-117">For more information, see the "Agreement Resolution for an MDN" section of [Sending an Outgoing MDN](../core/sending-an-outgoing-mdn.md).</span></span>  
   > 
   > [!NOTE]
   >  <span data-ttu-id="28688-118">如果 AS2-To 協議屬性中**識別碼**頁面的單向 AS2 協議**協議屬性**預設為英文的合作對象名稱，而 AS2 中的值設定對話方塊-To 標頭AS2 訊息設定為非英文名稱，則會找不到相符項目。</span><span class="sxs-lookup"><span data-stu-id="28688-118">If the AS2-To agreement property in the **Identifiers** page of the one-way AS2 agreement of the **Agreement Properties** dialog box is set by default to an English party name, and the value in the AS2-To header of the AS2 message is set to a non-English name, then the match will not be found.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28688-119">透過 AS2 傳送 EDI 時，您必須針對 EDI 和 AS2 使用不同的協議。</span><span class="sxs-lookup"><span data-stu-id="28688-119">When sending EDI over AS2, you are required to use separate agreements for both EDI and AS2.</span></span>  
  
 <span data-ttu-id="28688-120">如需傳送程序的詳細資訊，請參閱 <<c0> [ 產生外寄 AS2 訊息](../core/generating-an-outgoing-as2-message.md)。</span><span class="sxs-lookup"><span data-stu-id="28688-120">For more details on the send process, see [Generating an Outgoing AS2 Message](../core/generating-an-outgoing-as2-message.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28688-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28688-121">See Also</span></span>  
 [<span data-ttu-id="28688-122">BizTalk Server 如何傳送 AS2 訊息</span><span class="sxs-lookup"><span data-stu-id="28688-122">How BizTalk Server Sends AS2 Messages</span></span>](../core/how-biztalk-server-sends-as2-messages.md)