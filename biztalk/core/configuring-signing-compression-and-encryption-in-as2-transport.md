---
title: 設定簽署、 壓縮和加密 AS2 傳輸 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bc3537a7-c065-4a33-a375-29e7902b5ffa
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88309f17e335708b6e73109972c6c02d75ee483c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233974"
---
# <a name="configuring-signing-compression-and-encryption-in-as2-transport"></a><span data-ttu-id="e3b76-102">設定 AS2 傳輸中的簽章、壓縮和加密</span><span class="sxs-lookup"><span data-stu-id="e3b76-102">Configuring Signing, Compression, and Encryption in AS2 Transport</span></span>
<span data-ttu-id="e3b76-103">您可以從「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台」設定數位簽章、簽章驗證、加密和解密。</span><span class="sxs-lookup"><span data-stu-id="e3b76-103">You can configure digital signatures, signature verification, encryption, and decryption from within the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span> <span data-ttu-id="e3b76-104">此設定需要您為 AS2 管線和 BizTalk 合作對象設定適當的屬性。</span><span class="sxs-lookup"><span data-stu-id="e3b76-104">This configuration requires that you set the appropriate properties for the AS2 pipelines and BizTalk parties.</span></span>  
  
## <a name="using-as2-pipelines"></a><span data-ttu-id="e3b76-105">使用 AS2 管線</span><span class="sxs-lookup"><span data-stu-id="e3b76-105">Using AS2 Pipelines</span></span>  
 <span data-ttu-id="e3b76-106">為了保護輸入 AS2 訊息，請在您的接收位置中使用 AS2 接收管線 (AS2EdiReceive 或 AS2Receive)。</span><span class="sxs-lookup"><span data-stu-id="e3b76-106">To help secure an inbound AS2 message, use an AS2 receive pipeline (AS2EdiReceive or AS2Receive) in your receive location.</span></span> <span data-ttu-id="e3b76-107">「AS2 解碼器」會針對 AS2 訊息解密、解壓縮和/或執行簽章驗證。</span><span class="sxs-lookup"><span data-stu-id="e3b76-107">The AS2 Decoder decrypts, decompresses, and/or performs signature verification on AS2 messages.</span></span> <span data-ttu-id="e3b76-108">如需有關如何這麼的詳細資訊，請參閱的 < AS2 解碼器 > 一節[AS2 接收元件](../core/as2-receive-components.md)。</span><span class="sxs-lookup"><span data-stu-id="e3b76-108">For more information on how it does so, see the "AS2 Decoder" section of [AS2 Receive Components](../core/as2-receive-components.md).</span></span>  
  
 <span data-ttu-id="e3b76-109">為了保護輸出 AS2 訊息，請在您的傳送埠中使用 AS2 傳送管線 (AS2EdiSend 或 AS2Send)。</span><span class="sxs-lookup"><span data-stu-id="e3b76-109">To help secure an outbound AS2 message, use an AS2 send pipeline (AS2EdiSend or AS2Send) in your send port.</span></span> <span data-ttu-id="e3b76-110">「AS2 編碼器」會針對輸出 AS2 訊息執行簽署、壓縮和加密。</span><span class="sxs-lookup"><span data-stu-id="e3b76-110">The AS2 Encoder signs, compresses, and encrypts outbound AS2 messages.</span></span> <span data-ttu-id="e3b76-111">如需有關如何這麼的詳細資訊，請參閱的 < AS2 編碼器 > 一節[AS2 傳送元件](../core/as2-send-components.md)。</span><span class="sxs-lookup"><span data-stu-id="e3b76-111">For more information on how it does so, see the "AS2 Encoder" section of [AS2 Send Components](../core/as2-send-components.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e3b76-112">一旦訊息已簽署，簽章 BLOB 便不得變更，</span><span class="sxs-lookup"><span data-stu-id="e3b76-112">Once a message has been signed, the signature blob must not be changed.</span></span> <span data-ttu-id="e3b76-113">否則簽章會損毀。</span><span class="sxs-lookup"><span data-stu-id="e3b76-113">If changed, the signature would be corrupted.</span></span> <span data-ttu-id="e3b76-114">界限標頭 (或界限標頭外的任何內容) 可以變更，但在界限標頭內的任何內容都不可以變更。</span><span class="sxs-lookup"><span data-stu-id="e3b76-114">The boundary header, or anything outside the boundary headers, can be changed, but anything within the boundary headers must not be changed.</span></span>  
  
## <a name="setting-as2-agreement-properties"></a><span data-ttu-id="e3b76-115">設定 AS2 協議屬性</span><span class="sxs-lookup"><span data-stu-id="e3b76-115">Setting AS2 Agreement Properties</span></span>  
 <span data-ttu-id="e3b76-116">您可以設定 AS2 協議屬性來設定簽章和加密處理，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e3b76-116">You configure signature and encryption processing by setting AS2 agreement properties as follows:</span></span>  
  
-   <span data-ttu-id="e3b76-117">簽署、 壓縮，和 （或) 加密輸出訊息，請檢查**訊息應該簽署**，**訊息應該壓縮**，和**訊息應該加密**屬性上的**驗證**（適用於外寄的 AS2 訊息） 中之單向協議索引標籤頁面**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e3b76-117">To sign, compress, and/or encrypt an outbound message, check the **Message should be signed**, **Message should be compressed**, and **Message should be encrypted** properties on the **Validation** page of the one-way agreement tab (for the outgoing AS2 message) in the **Agreement Properties** dialog box.</span></span>  
  
-   <span data-ttu-id="e3b76-118">若要要求簽署的 MDN 以回應輸出訊息，請檢查**要求 MDN**和**要求簽署的 MDN**屬性**通知 (Mdn)** 頁面單向協議索引標籤**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e3b76-118">To request a signed MDN in response to an outbound message, check the **Request MDN** and **Request signed MDN** properties on the **Acknowledgements (MDNs)** page of the one-way agreement tab of the **Agreement Properties** dialog box.</span></span>  
  
-   <span data-ttu-id="e3b76-119">指定傳入的訊息簽署、 壓縮和/或加密，請檢查**對驗證與 MDN 使用協議設定，而非訊息標頭**屬性，**訊息應該簽署**屬性，**訊息應該壓縮**屬性，而**訊息應該加密**屬性**驗證**頁面的單向協議索引標籤 （適用於內送的 AS2 訊息） 的**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e3b76-119">To specify that an inbound message is signed, compressed, and/or encrypted, check the **Use agreement settings for validation and MDN instead of message header** property, the **Message should be signed** property, the **Message should be compressed** property, and the **Message should be encrypted** property on the **Validation** page of the one-way agreement tab (for the incoming AS2 message) in the **Agreement Properties** dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e3b76-120">當**對驗證與 MDN 使用協議設定，而非訊息標頭**屬性選取，所有內送訊息的標頭詳細資料會被忽略，處理該訊息會根據協議設定。</span><span class="sxs-lookup"><span data-stu-id="e3b76-120">When the **Use agreement settings for validation and MDN instead of message header** property is selected, all header details of the incoming message are ignored and the message is processed based on the agreement settings.</span></span>  
  
-   <span data-ttu-id="e3b76-121">若要選取的輸入的訊息屬性會覆寫時，指定簽署的 MDN 以回應傳入訊息，**對驗證與 MDN 使用協議設定，而非訊息標頭**屬性，檢查**要求簽署的 MDN**屬性**通知 (Mdn)** 頁面**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e3b76-121">To specify a signed MDN in response to an inbound message, when the inbound message properties are overridden by selecting the **Use agreement settings for validation and MDN instead of message header** property, check the **Request Signed MDN** property on **Acknowledgements (MDNs)** page of the **Agreement Properties** dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e3b76-122">當**對驗證與 MDN 使用協議設定，而非訊息標頭**屬性選取，所有內送訊息的標頭詳細資料會被忽略，處理該訊息會根據協議設定。</span><span class="sxs-lookup"><span data-stu-id="e3b76-122">When the **Use agreement settings for validation and MDN instead of message header** property is selected, all header details of the incoming message are ignored and the message is processed based on the agreement settings.</span></span>  
  
-   <span data-ttu-id="e3b76-123">若要指定簽署的 MDN 以回應傳入訊息，不會覆寫輸入的訊息屬性 (**對驗證與 MDN 使用協議設定，而非訊息標頭**清除)，但訊息標頭不指定簽章檢查**簽署要求的 MDN，如果配置通知選項標頭不存在，或簽署回條通訊協定標頭設定為選擇性**屬性**接收者 MDN 設定**頁面**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e3b76-123">To specify a signed MDN in response to an inbound message, when the inbound message properties are not overridden (the **Use agreement settings for validation and MDN instead of message header** is cleared), but the message headers do not specify signing, check the **Sign requested MDN if Disposition-Notification-Option header is not present or if Signed-Receipt-Protocol header is set to optional** property on the **Receiver MDN Settings** page of the **Agreement Properties** dialog box.</span></span>  
  
-   <span data-ttu-id="e3b76-124">若要指定與外寄 AS2 訊息的 BizTalk 群組屬性中指定不同的簽署憑證，請選取**覆寫群組簽章憑證**中**簽章憑證**單向協議索引標籤的頁面**協議屬性**對話方塊方塊中，並指定簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="e3b76-124">To specify a different signing certificate than the one specified in the BizTalk Group properties for outgoing AS2 messages, select **Override Group Signature Certificate** in the **Signature Certificate** page of the one-way agreement tab of the **Agreement Properties** dialog box, and specify a signing certificate.</span></span> <span data-ttu-id="e3b76-125">如果設定此屬性，將會使用所提供的憑證簽署任何解析為協議的 AS2 訊息**簽章憑證**頁面上，並不是由憑證提供做為 BizTalk 群組屬性的一部分。</span><span class="sxs-lookup"><span data-stu-id="e3b76-125">If this property is set, whichever AS2 message that resolves to the agreement will be signed using the certificate provided in the **Signature Certificate** page and not by the certificate provided as part of the BizTalk Group properties.</span></span>  
  
 <span data-ttu-id="e3b76-126">如需有關設定合作對象屬性的詳細資訊，請參閱[設定 AS2 屬性](../core/configuring-as2-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e3b76-126">For more information about setting up party properties, see [Configuring AS2 Properties](../core/configuring-as2-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3b76-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3b76-127">See Also</span></span>  
 <span data-ttu-id="e3b76-128">[AS2 安全性](../core/as2-security.md) </span><span class="sxs-lookup"><span data-stu-id="e3b76-128">[AS2 Security](../core/as2-security.md) </span></span>  
 <span data-ttu-id="e3b76-129">[設定 AS2 的憑證](../core/configuring-certificates-for-as2.md) </span><span class="sxs-lookup"><span data-stu-id="e3b76-129">[Configuring Certificates for AS2](../core/configuring-certificates-for-as2.md) </span></span>  
 <span data-ttu-id="e3b76-130">[AS2 訊息](../core/as2-messages.md) </span><span class="sxs-lookup"><span data-stu-id="e3b76-130">[AS2 Messages](../core/as2-messages.md) </span></span>  
 <span data-ttu-id="e3b76-131">[AS2 接收元件](../core/as2-receive-components.md) </span><span class="sxs-lookup"><span data-stu-id="e3b76-131">[AS2 Receive Components](../core/as2-receive-components.md) </span></span>  
 <span data-ttu-id="e3b76-132">[AS2 傳送元件](../core/as2-send-components.md) </span><span class="sxs-lookup"><span data-stu-id="e3b76-132">[AS2 Send Components](../core/as2-send-components.md) </span></span>  
 [<span data-ttu-id="e3b76-133">設定 AS2 屬性</span><span class="sxs-lookup"><span data-stu-id="e3b76-133">Configuring AS2 Properties</span></span>](../core/configuring-as2-properties.md)