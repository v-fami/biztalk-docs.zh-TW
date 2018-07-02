---
title: BizTalk Server 所使用的憑證簽署的訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, signed messages
- messages, message flow [digital signatures]
- S/MIME messages
- signed messages
- digital signatures, message flow
- messages, certificates
ms.assetid: 0b521e11-73ef-424f-9e6a-4fb42dc263ff
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1cc45411d19bc23a2985dbd60fc68bc8de58594c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979847"
---
# <a name="certificates-that-biztalk-server-uses-for-signed-messages"></a><span data-ttu-id="dee67-102">BizTalk Server 用於簽章訊息的憑證</span><span class="sxs-lookup"><span data-stu-id="dee67-102">Certificates that BizTalk Server Uses for Signed Messages</span></span>
<span data-ttu-id="dee67-103">BizTalk Server 支援「安全多用途網際網路郵件延伸」(Secure Multipurpose Internet Mail Extensions，S/MIME) 輸入訊息的簽章輸出訊息及簽章驗證。</span><span class="sxs-lookup"><span data-stu-id="dee67-103">BizTalk Server supports signing outbound messages and signature verification for inbound Secure Multipurpose Internet Mail Extensions (S/MIME) messages.</span></span> <span data-ttu-id="dee67-104">BizTalk Server 使用 S/MIME 版本 2 和 3 來簽署輸出訊息及驗證輸入訊息的簽章。</span><span class="sxs-lookup"><span data-stu-id="dee67-104">BizTalk Server uses S/MIME versions 2 and 3 to sign outbound messages and to validate the signature of inbound messages.</span></span> <span data-ttu-id="dee67-105">同樣的，您可以設定 BizTalk Server 來簽署傳送給夥伴的訊息，然後將其加密。</span><span class="sxs-lookup"><span data-stu-id="dee67-105">Similarly, you can configure BizTalk Server to sign and then encrypt the messages it sends to its partners.</span></span>  
  
- <span data-ttu-id="dee67-106">BizTalk Server 支援用於驗證數位簽章的 SHA-1 和 MD5 簽章演算法。</span><span class="sxs-lookup"><span data-stu-id="dee67-106">BizTalk Server supports the SHA-1 and MD5 signing algorithms for verifying digital signatures.</span></span> <span data-ttu-id="dee67-107">BizTalk Server 使用 SHA-1 簽章演算法來簽署輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="dee67-107">BizTalk Server uses the SHA-1 signing algorithm to sign outbound messages.</span></span>  
  
- <span data-ttu-id="dee67-108">由 BizTalk Server 所支援用於簽章金鑰的金鑰交換系統是 Rivest-Shamir-Adleman (RSA) 演算法和「數位簽章標準」(Digital Signature Standard，DSS)。</span><span class="sxs-lookup"><span data-stu-id="dee67-108">The key exchange systems supported by BizTalk Server for signature keys are the Rivest-Shamir-Adleman (RSA) algorithms and the Digital Signature Standard (DSS).</span></span> <span data-ttu-id="dee67-109">BizTalk Server 不支援簽章金鑰的「先進加密標準」(Advanced Encryption Standard，AES) 交換系統。</span><span class="sxs-lookup"><span data-stu-id="dee67-109">BizTalk Server does not support the Advanced Encryption Standard (AES) exchange system for signature keys.</span></span>  
  
- <span data-ttu-id="dee67-110">BizTalk Server 支援的簽章憑證為 x.509 第 3 版。</span><span class="sxs-lookup"><span data-stu-id="dee67-110">The signing certificate supported by BizTalk Server is x.509 version 3.</span></span>  
  
  <span data-ttu-id="dee67-111">下圖顯示當 BizTalk Server 接收數位簽章訊息，並選擇使用簽章將夥伴識別解析為 BizTalk Server 環境中的合作對象時的訊息流程。</span><span class="sxs-lookup"><span data-stu-id="dee67-111">The following figure shows the message flow when BizTalk Server receives a digitally signed message and optionally uses the signature to resolve the partner identity to a party in the BizTalk Server environment.</span></span>  
  
  <span data-ttu-id="dee67-112">![傳送已簽署的訊息時，訊息流程](../core/media/6fd1674d-5a21-4272-83ca-608d7b400de7.gif "6fd1674d-5a21-4272-83ca-608d7b400de7")</span><span class="sxs-lookup"><span data-stu-id="dee67-112">![Message flow when sending a signed message](../core/media/6fd1674d-5a21-4272-83ca-608d7b400de7.gif "6fd1674d-5a21-4272-83ca-608d7b400de7")</span></span>  
  
  <span data-ttu-id="dee67-113">BizTalk Server 接收數位簽章訊息的訊息流程如下：</span><span class="sxs-lookup"><span data-stu-id="dee67-113">The message flow when BizTalk Server receives a digitally signed message is as follows:</span></span>  
  
1. <span data-ttu-id="dee67-114">夥伴傳送訊息給 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="dee67-114">A partner sends a message to BizTalk Server.</span></span> <span data-ttu-id="dee67-115">夥伴以其私密金鑰憑證簽署訊息。</span><span class="sxs-lookup"><span data-stu-id="dee67-115">The partner signs the message with its private key certificate.</span></span>  
  
2. <span data-ttu-id="dee67-116">適當的 BizTalk Server 接收處理常式會接收訊息。</span><span class="sxs-lookup"><span data-stu-id="dee67-116">The appropriate BizTalk Server receive handler receives the message.</span></span>  
  
3. <span data-ttu-id="dee67-117">在接收管線執行期間，MIME/SMIME 解碼器管線元件會使用夥伴的公開金鑰來驗證數位簽章。</span><span class="sxs-lookup"><span data-stu-id="dee67-117">During the execution of the receive pipeline, the MIME/SMIME Decoder pipeline component verifies the digital signature by using the partner's public key.</span></span>  
  
4. <span data-ttu-id="dee67-118">如果已設定合作對象解析元件，便會在接收管線合作對象解析元件的執行期間，使用夥伴的公開金鑰憑證來識別 BizTalk Server 系統中的合作對象。</span><span class="sxs-lookup"><span data-stu-id="dee67-118">If party resolution component is configured, the partner's public key certificate is used to identify the party in the BizTalk Server system during the execution of the receive pipeline party resolution component.</span></span>  
  
5. <span data-ttu-id="dee67-119">進行其他處理。</span><span class="sxs-lookup"><span data-stu-id="dee67-119">Additional processing occurs.</span></span>  
  
   <span data-ttu-id="dee67-120">下圖顯示 BizTalk Server 傳送數位簽章訊息的訊息流程。</span><span class="sxs-lookup"><span data-stu-id="dee67-120">The following figure shows the message flow when BizTalk Server sends a digitally signed message.</span></span>  
  
   <span data-ttu-id="dee67-121">![](../core/media/bts-bpi-sp-msgsec-outboundsigning-r2c.gif "bts_BPI_SP_MSGSEC_OutboundSigning_R2c")</span><span class="sxs-lookup"><span data-stu-id="dee67-121">![](../core/media/bts-bpi-sp-msgsec-outboundsigning-r2c.gif "bts_BPI_SP_MSGSEC_OutboundSigning_R2c")</span></span>  
  
   <span data-ttu-id="dee67-122">BizTalk Server 將數位簽章訊息傳送給夥伴的訊息流程如下：</span><span class="sxs-lookup"><span data-stu-id="dee67-122">The message flow when BizTalk Server sends a digitally signed message to a partner is as follows:</span></span>  
  
6. <span data-ttu-id="dee67-123">適當的 BizTalk Server 傳送處理常式將訊息傳送給夥伴。</span><span class="sxs-lookup"><span data-stu-id="dee67-123">The appropriate BizTalk Server send handler sends a message to the partner.</span></span>  
  
7. <span data-ttu-id="dee67-124">在傳送管線執行期間，MIME/SMIME 編碼器管線元件會使用 BizTalk Server 私密金鑰來簽署訊息。</span><span class="sxs-lookup"><span data-stu-id="dee67-124">During the execution of the send pipeline, the MIME/SMIME Encoder pipeline component signs the message by using the BizTalk Server private key.</span></span>  
  
8. <span data-ttu-id="dee67-125">夥伴從 BizTalk Server 接收訊息。</span><span class="sxs-lookup"><span data-stu-id="dee67-125">The partner receives the message from BizTalk Server.</span></span> <span data-ttu-id="dee67-126">夥伴使用 BizTalk Server 公開金鑰來驗證數位簽章。</span><span class="sxs-lookup"><span data-stu-id="dee67-126">The partner uses the BizTalk Server public key to verify the digital signature.</span></span>  
  
   <span data-ttu-id="dee67-127">BizTalk Server 會驗證憑證的憑證授權單位 (CA) 信任鏈及憑證的有效期限，以確認內送簽章訊息的關聯憑證之有效性。</span><span class="sxs-lookup"><span data-stu-id="dee67-127">BizTalk Server verifies the validity of the certificates associated with the incoming signed messages by validating the certification authority (CA) trust chain for the certificate and by verifying that the certificate has not expired.</span></span> <span data-ttu-id="dee67-128">執行 CA 信任鏈的驗證程序時，需要遍歷憑證上的信任鏈結，直到到達根憑證授權單位為止。</span><span class="sxs-lookup"><span data-stu-id="dee67-128">The process of validating the CA trust chain involves traversing the chain of trust on certificates until a root certification authority is reached.</span></span> <span data-ttu-id="dee67-129">這麼做會驗證用來簽章訊息的憑證確實來自同一個合作對象。</span><span class="sxs-lookup"><span data-stu-id="dee67-129">This validates that the certificate used to sign a message is indeed from the identified party.</span></span> <span data-ttu-id="dee67-130">此驗證工作會在執行階段針對每一個簽章的訊息執行。</span><span class="sxs-lookup"><span data-stu-id="dee67-130">This validation occurs at runtime for each and every signed message.</span></span>  
  
   <span data-ttu-id="dee67-131">此外，BizTalk Server 可以確認憑證授權單位未撤銷用來簽章或加密訊息的憑證。</span><span class="sxs-lookup"><span data-stu-id="dee67-131">In addition, BizTalk Server can verify that the certification authority has not revoked the certificate used to sign or encrypt the message.</span></span> <span data-ttu-id="dee67-132">若要這麼做，您必須下載憑證授權單位的憑證撤銷清單 (CRL)，然後使用 Windows 檔案總管進行安裝。</span><span class="sxs-lookup"><span data-stu-id="dee67-132">To do this, you must download the certificate revocation list (CRL) from the certification authority and install it using Windows Explorer.</span></span> <span data-ttu-id="dee67-133">如需如何驗證憑證的詳細資訊，請參閱[如何設定 MIME SMIME 解碼器管線元件](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="dee67-133">For more information about how to validate a certificate, see [How to Configure the MIME-SMIME Decoder Pipeline Component](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dee67-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dee67-134">See Also</span></span>  
 <span data-ttu-id="dee67-135">[BizTalk Server 用於加密訊息的憑證](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md) </span><span class="sxs-lookup"><span data-stu-id="dee67-135">[Certificates that BizTalk Server Uses for Encrypted Messages](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md) </span></span>  
 <span data-ttu-id="dee67-136">[BizTalk Server 使用的憑證存放區](../core/certificate-stores-that-biztalk-server-uses.md) </span><span class="sxs-lookup"><span data-stu-id="dee67-136">[Certificate Stores that BizTalk Server Uses](../core/certificate-stores-that-biztalk-server-uses.md) </span></span>  
 <span data-ttu-id="dee67-137">[加密和簽署憑證](../core/encryption-and-signing-certificates.md) </span><span class="sxs-lookup"><span data-stu-id="dee67-137">[Encryption and Signing Certificates](../core/encryption-and-signing-certificates.md) </span></span>  
 [<span data-ttu-id="dee67-138">傳送和接收簽署的訊息</span><span class="sxs-lookup"><span data-stu-id="dee67-138">Sending and Receiving Signed Messages</span></span>](../core/sending-and-receiving-signed-messages.md)