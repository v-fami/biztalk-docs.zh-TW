---
title: 產生外寄 AS2 訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 288c8101-9a96-4f98-ae18-df43c7cdb3a0
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90a0b1e37e96086de7d8901b61afa8dea859a388
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246542"
---
# <a name="generating-an-outgoing-as2-message"></a><span data-ttu-id="133cb-102">產生外寄 AS2 訊息</span><span class="sxs-lookup"><span data-stu-id="133cb-102">Generating an Outgoing AS2 Message</span></span>
<span data-ttu-id="133cb-103">AS2EDISend 和 AS2Send 傳送管線會產生外寄訊息，如下所述。</span><span class="sxs-lookup"><span data-stu-id="133cb-103">The AS2EDISend and AS2Send send pipelines generate an outbound message as follows.</span></span> <span data-ttu-id="133cb-104">每個管線會使用的單向協議索引標籤中的屬性**協議屬性**來產生外寄 AS2 訊息的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="133cb-104">Each pipeline uses the properties in the one-way agreement tab of the **Agreement Properties** dialog box to generate the outgoing AS2 message.</span></span>  
  
## <a name="agreement-destination-and-messageid-determination"></a><span data-ttu-id="133cb-105">協議、 目的地和 MessageID 判斷</span><span class="sxs-lookup"><span data-stu-id="133cb-105">Agreement, Destination, and MessageID Determination</span></span>  
 <span data-ttu-id="133cb-106">AS2 傳送管線會判斷傳送 AS2 訊息時要使用的協議和目的地，如下所述：</span><span class="sxs-lookup"><span data-stu-id="133cb-106">The AS2 send pipelines determine the agreement and destination to be used in sending an AS2 message as follows:</span></span>  
  
-   <span data-ttu-id="133cb-107">為了判斷處理外寄訊息時使用的協議，AS2 編碼器會嘗試比對訊息中的 AS2-To 屬性與合作對象商務設定檔的 AS2Identity，或是比對訂閱訊息的傳送埠與協議的相關聯傳送埠。</span><span class="sxs-lookup"><span data-stu-id="133cb-107">To determine the agreement to use in processing an outgoing message, the AS2 encoder attempts to match the AS2-To properties in the message and the AS2Identity for a party’s business profile, or the send port subscribing to the message with a send port associated with the agreement.</span></span> <span data-ttu-id="133cb-108">如需這個程序的詳細資訊，請參閱[外寄 AS2 訊息的協議解析](../core/agreement-resolution-for-outgoing-as2-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="133cb-108">For more information on this process, see [Agreement Resolution for Outgoing AS2 Messages](../core/agreement-resolution-for-outgoing-as2-messages.md).</span></span>  
  
-   <span data-ttu-id="133cb-109">為判斷訊息的目的地，動態傳送埠中的傳送管線會使用 OutboundTransportLocation 屬性，該屬性必須由後端應用程式撰寫或升級至內容，動態傳送埠才能運作。</span><span class="sxs-lookup"><span data-stu-id="133cb-109">To determine the destination of the message, the send pipeline in a dynamic send port uses the OutboundTransportLocation property, which must be written or promoted to the context by a backend application for the dynamic send port to work.</span></span> <span data-ttu-id="133cb-110">靜態傳送管線中的傳送管線將根據 AS2 協議屬性中的 AS2-From 屬性，以及商務設定檔屬性的識別判斷目的地。</span><span class="sxs-lookup"><span data-stu-id="133cb-110">The send pipeline in a static send pipeline will determine the destination from the AS2-From property in the AS2 agreement properties and the identities of the business profile properties.</span></span>  
  
-   <span data-ttu-id="133cb-111">AS2 編碼器必須設定外寄 AS2 訊息的 MessageId 標頭。</span><span class="sxs-lookup"><span data-stu-id="133cb-111">The AS2 Encoder needs to set the MessageId header of an outgoing AS2 message.</span></span> <span data-ttu-id="133cb-112">傳送管線會根據 `EdiIntAS.MessageId` 內容屬性或 `HTTP.UserHttpHeaders` 內容屬性判斷 MessageId。</span><span class="sxs-lookup"><span data-stu-id="133cb-112">The send pipeline determines the MessageId from either the `EdiIntAS.MessageId` context property or the `HTTP.UserHttpHeaders` context property.</span></span> <span data-ttu-id="133cb-113">如果同時設定了這兩個內容屬性，則編碼器會使用 `HTTP.UserHttpHeaders` 內容屬性的值。</span><span class="sxs-lookup"><span data-stu-id="133cb-113">If both of those context properties are set, the encoder uses the value from the `HTTP.UserHttpHeaders` context property.</span></span> <span data-ttu-id="133cb-114">如果兩個屬性都未設定，則傳送管線會自動產生 MessageID 的值。</span><span class="sxs-lookup"><span data-stu-id="133cb-114">If neither of them is set, the send pipeline autogenerates a value for MessageID.</span></span>  
  
## <a name="outgoing-message-processing"></a><span data-ttu-id="133cb-115">外寄訊息處理</span><span class="sxs-lookup"><span data-stu-id="133cb-115">Outgoing Message Processing</span></span>  
 <span data-ttu-id="133cb-116">AS2 傳送管線處理外寄 AS2 訊息時採取的步驟如下所示：</span><span class="sxs-lookup"><span data-stu-id="133cb-116">The steps that the AS2 send pipelines use in processing an outgoing AS2 message are as follows:</span></span>  
  
-   <span data-ttu-id="133cb-117">如果已在協議屬性中啟用 AS2 訊息的不可否認性，就以原生格式複製訊息並將複本儲存在不可否認性資料庫中。</span><span class="sxs-lookup"><span data-stu-id="133cb-117">Makes a copy of the message in native format, and stores the copy in the non-repudiation database, if non-repudiation of AS2 messages is enabled in agreement properties.</span></span>  
  
-   <span data-ttu-id="133cb-118">AS2 編碼器會在 `HTTP.UserHttpHeaders` 內容屬性中建置 HTTP (和 AS2) 標頭。</span><span class="sxs-lookup"><span data-stu-id="133cb-118">The AS2 Encoder builds the HTTP (and AS2) headers into the `HTTP.UserHttpHeaders` context property.</span></span> <span data-ttu-id="133cb-119">如需這個程序的詳細資訊，請參閱[傳送端處理透過 AS2 外寄 EDI 訊息](../core/send-side-processing-of-an-outgoing-edi-message-over-as2.md)。</span><span class="sxs-lookup"><span data-stu-id="133cb-119">For more information on this process, see [Send-Side Processing of an Outgoing EDI Message over AS2](../core/send-side-processing-of-an-outgoing-edi-message-over-as2.md).</span></span>  
  
-   <span data-ttu-id="133cb-120">將 `HTTP.UserHttpHeaders` 寫入內容。</span><span class="sxs-lookup"><span data-stu-id="133cb-120">Writes `HTTP.UserHttpHeaders` to the context.</span></span>  
  
-   <span data-ttu-id="133cb-121">壓縮外寄訊息 (如已啟用)。</span><span class="sxs-lookup"><span data-stu-id="133cb-121">Compresses the outgoing message, if enabled.</span></span>  
  
-   <span data-ttu-id="133cb-122">執行 MIME 處理，包括加密訊息 (如果啟用 在**訊息應該加密**協議屬性) 以及套用數位簽章 (如果啟用 在**訊息應該簽署的**協議屬性)。</span><span class="sxs-lookup"><span data-stu-id="133cb-122">Performs MIME processing, including encrypting the message (if enabled in the **Message should be encrypted** agreement property) and applying a digital signature (if enabled in the **Message should be signed** agreement properties).</span></span> <span data-ttu-id="133cb-123">AS2Send 管線會根據協議設定，使用 SHA1 或 MD5 來套用簽章。</span><span class="sxs-lookup"><span data-stu-id="133cb-123">The AS2Send pipeline uses either SHA1 or MD5 to apply the signature, based upon agreement settings.</span></span>  
  
-   <span data-ttu-id="133cb-124">如果已在協議屬性中啟用傳輸檔案名稱，便建立包含指定值的 Content-Disposition MIME 標頭。</span><span class="sxs-lookup"><span data-stu-id="133cb-124">Creates a Content-Disposition MIME header containing the specified value, if transmit file name is enabled in agreement properties.</span></span>  
  
-   <span data-ttu-id="133cb-125">加密訊息的複本 （電傳格式），並將複本儲存在不可否認性資料庫中，如果在啟用**為輸出的編碼 AS2 訊息啟用 NRR**協議屬性中。</span><span class="sxs-lookup"><span data-stu-id="133cb-125">Makes a copy of the encrypted message (in wire format), and stores the copy in the non-repudiation database, if enabled in the **NRR enabled for outbound encoded AS2 messages** in the agreement property.</span></span>  
  
-   <span data-ttu-id="133cb-126">如果必須使用 MDN，則計算 MIC 值並將它儲存到資料存放區。</span><span class="sxs-lookup"><span data-stu-id="133cb-126">If an MDN is required, computes the MIC value and stores it in the data store.</span></span>  
  
-   <span data-ttu-id="133cb-127">將訊息傳遞至 HTTP 配接器，該配接器會從 UserHTTPHeaders 內容屬性將標頭寫入至外寄 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="133cb-127">Delivers the message to the HTTP adapter, which writes the headers from the UserHTTPHeaders context property into the outgoing AS2 message.</span></span>  
  
-   <span data-ttu-id="133cb-128">如果需要可靠的傳訊，就會重新傳送訊息，直到接收 MDN 為止。</span><span class="sxs-lookup"><span data-stu-id="133cb-128">If reliable messaging is required, resends the message until an MDN is received.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="133cb-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="133cb-129">See Also</span></span>  
 <span data-ttu-id="133cb-130">[BizTalk Server 傳送 AS2 訊息的方式](../core/how-biztalk-server-sends-as2-messages.md) </span><span class="sxs-lookup"><span data-stu-id="133cb-130">[How BizTalk Server Sends AS2 Messages](../core/how-biztalk-server-sends-as2-messages.md) </span></span>  
 [<span data-ttu-id="133cb-131">AS2 傳送元件</span><span class="sxs-lookup"><span data-stu-id="133cb-131">AS2 Send Components</span></span>](../core/as2-send-components.md)