---
title: "BizTalk Server 使用的憑證加密的訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, message flow [encrypted messages]
- encrypted messages
- messages, encryption
ms.assetid: 44b06488-4ecd-436d-af3d-b95e285ecb3e
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4eb1e9629b56fa667d68c246645d00416de221a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="certificates-that-biztalk-server-uses-for-encrypted-messages"></a><span data-ttu-id="f128c-102">BizTalk Server 會使用加密訊息的憑證</span><span class="sxs-lookup"><span data-stu-id="f128c-102">Certificates that BizTalk Server Uses for Encrypted Messages</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f128c-103"> 以「安全多用途網際網路郵件延伸」(Secure Multipurpose Internet Mail Extension，S/MIME) 為基礎，支援輸出訊息的公開金鑰加密以及輸入訊息的解密。</span><span class="sxs-lookup"><span data-stu-id="f128c-103"> supports public key encryption of outbound messages and decryption of inbound messages based on Secure Multipurpose Internet Mail Extensions (S/MIME).</span></span> <span data-ttu-id="f128c-104">BizTalk Server 在輸出訊息加密中使用 S/MIME 第 3 版，而在輸入訊息解密方面使用 S/MIME 第 2 和 3 版。</span><span class="sxs-lookup"><span data-stu-id="f128c-104">BizTalk Server uses S/MIME version 3 for encryption of outbound messages, and S/MIME versions 2 and 3 for decryption of inbound messages.</span></span>  
  
-   <span data-ttu-id="f128c-105">BizTalk Server 支援 RSA 和 Diffie Hellman 加密憑證。</span><span class="sxs-lookup"><span data-stu-id="f128c-105">BizTalk Server supports RSA and Diffie Hellman encryption certificates.</span></span>  
  
-   <span data-ttu-id="f128c-106">BizTalk Server 支援「資料加密標準」(Data Encryption Standard，DES)、3DES 和 RC2 加密演算法。</span><span class="sxs-lookup"><span data-stu-id="f128c-106">BizTalk Server supports Data Encryption Standard (DES), 3DES, and RC2 encryption algorithms.</span></span>  
  
 <span data-ttu-id="f128c-107">下圖顯示 BizTalk Server 接收加密訊息時的訊息流程。</span><span class="sxs-lookup"><span data-stu-id="f128c-107">The following figure shows the message flow when BizTalk Server receives an encrypted message.</span></span>  
  
 <span data-ttu-id="f128c-108">![當接收加密的訊息時，訊息流程](../core/media/bpi-sp-msgsec-inboundencryption.gif "BPI_SP_MSGSEC_InboundEncryption")</span><span class="sxs-lookup"><span data-stu-id="f128c-108">![Message flow when receiving an encrypted message](../core/media/bpi-sp-msgsec-inboundencryption.gif "BPI_SP_MSGSEC_InboundEncryption")</span></span>  
  
 <span data-ttu-id="f128c-109">BizTalk Server 接收加密訊息時的訊息流程如下：</span><span class="sxs-lookup"><span data-stu-id="f128c-109">The message flow when BizTalk Server receives an encrypted message is as follows:</span></span>  
  
1.  <span data-ttu-id="f128c-110">夥伴傳送訊息給 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="f128c-110">A partner sends a message to BizTalk Server.</span></span> <span data-ttu-id="f128c-111">夥伴使用 BizTalk Server 公開金鑰來加密訊息。</span><span class="sxs-lookup"><span data-stu-id="f128c-111">The partner encrypts the message with the BizTalk Server public key.</span></span>  
  
2.  <span data-ttu-id="f128c-112">適當的 BizTalk Server 接收處理常式會接收訊息。</span><span class="sxs-lookup"><span data-stu-id="f128c-112">The appropriate BizTalk Server receive handler receives the message.</span></span>  
  
3.  <span data-ttu-id="f128c-113">在接收管線執行期間，MIME/SMIME 解碼器管線元件會使用 BizTalk Server 私密金鑰來解密訊息。</span><span class="sxs-lookup"><span data-stu-id="f128c-113">During the receive pipeline execution, the MIME/SMIME Decoder pipeline component decrypts the message by using the BizTalk Server private key.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f128c-114">IIS 7.0 電腦上成功解密管線，請對 IIS 應用程式集區帳戶和相關聯的接收處理常式的主控件執行個體所使用的帳戶都相同，而且此帳戶的成員\<machineName> \IIS_WPG 群組。</span><span class="sxs-lookup"><span data-stu-id="f128c-114">For pipeline decryption to succeed on an IIS 7.0 computer, ensure that the account for the IIS application pool and the account used by the host instance associated with the receive handler are the same and that this account is a member of the \<machineName>\IIS_WPG group.</span></span> <span data-ttu-id="f128c-115">如需有關設定 IIS 處理序識別，如 IIS 7.0，請參閱的[解決 IIS 權限問題的指導方針](../core/guidelines-for-resolving-iis-permissions-problems.md)。</span><span class="sxs-lookup"><span data-stu-id="f128c-115">For more information on setting IIS process identity for IIS 7.0 see [Guidelines for Resolving IIS Permissions Problems](../core/guidelines-for-resolving-iis-permissions-problems.md).</span></span> <span data-ttu-id="f128c-116">這些處理序必須在相同的帳戶下執行，以確保可載入帳戶設定檔，而這樣會載入在管線中執行解密所需的登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="f128c-116">These processes must run under the same account to ensure that the account profile is loaded which in turns loads the registry keys required to perform decryption in the pipeline.</span></span> <span data-ttu-id="f128c-117">基於效能考量，IIS 7.0 時並未載入帳戶設定檔啟動關聯的 w3wp.exe 處理序，因此必須使用相同的帳戶設定 BizTalk 主控件執行個體，以便讓 BizTalk 載入帳戶設定檔和登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="f128c-117">For performance reasons, IIS 7.0 does not load the account profile when starting the associated w3wp.exe process so the BizTalk host instance must be configured with the same account so that BizTalk will load the account profile and registry keys.</span></span>  
  
4.  <span data-ttu-id="f128c-118">進行其他處理。</span><span class="sxs-lookup"><span data-stu-id="f128c-118">Additional processing occurs.</span></span>  
  
 <span data-ttu-id="f128c-119">下圖顯示 BizTalk Server 傳送加密訊息時的訊息流程。</span><span class="sxs-lookup"><span data-stu-id="f128c-119">The following figure shows the message flow when BizTalk Server sends an encrypted message.</span></span>  
  
 <span data-ttu-id="f128c-120">![傳送加密的訊息時，訊息流程](../core/media/bpi-sp-msgsec-outboundencryption.gif "BPI_SP_MSGSEC_OutboundEncryption")</span><span class="sxs-lookup"><span data-stu-id="f128c-120">![Message flow when sending an encrypted message](../core/media/bpi-sp-msgsec-outboundencryption.gif "BPI_SP_MSGSEC_OutboundEncryption")</span></span>  
  
 <span data-ttu-id="f128c-121">BizTalk Server 傳送加密訊息給夥伴的訊息流程如下：</span><span class="sxs-lookup"><span data-stu-id="f128c-121">The message flow when BizTalk Server sends an encrypted message to a partner is as follows:</span></span>  
  
1.  <span data-ttu-id="f128c-122">適當的 BizTalk Server 傳送處理常式將訊息傳送給夥伴。</span><span class="sxs-lookup"><span data-stu-id="f128c-122">The appropriate BizTalk Server send handler sends a message to the partner.</span></span>  
  
2.  <span data-ttu-id="f128c-123">在傳送管線執行期間，MIME/SMIME 編碼器管線元件會使用夥伴的公開金鑰來加密訊息。</span><span class="sxs-lookup"><span data-stu-id="f128c-123">During the send pipeline execution, the MIME/SMIME Encoder pipeline component encrypts the message by using the partner's public key.</span></span>  
  
3.  <span data-ttu-id="f128c-124">夥伴從 BizTalk Server 接收訊息。</span><span class="sxs-lookup"><span data-stu-id="f128c-124">The partner receives the message from BizTalk Server.</span></span> <span data-ttu-id="f128c-125">夥伴使用自己的私密金鑰來解密訊息。</span><span class="sxs-lookup"><span data-stu-id="f128c-125">The partner uses its private key to decrypt the message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f128c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f128c-126">See Also</span></span>  
 <span data-ttu-id="f128c-127">[BizTalk Server 用於簽章訊息的憑證](../core/certificates-that-biztalk-server-uses-for-signed-messages.md) </span><span class="sxs-lookup"><span data-stu-id="f128c-127">[Certificates that BizTalk Server Uses for Signed Messages](../core/certificates-that-biztalk-server-uses-for-signed-messages.md) </span></span>  
 <span data-ttu-id="f128c-128">[BizTalk Server 使用的憑證存放區](../core/certificate-stores-that-biztalk-server-uses.md) </span><span class="sxs-lookup"><span data-stu-id="f128c-128">[Certificate Stores that BizTalk Server Uses](../core/certificate-stores-that-biztalk-server-uses.md) </span></span>  
 <span data-ttu-id="f128c-129">[加密和簽章憑證](../core/encryption-and-signing-certificates.md) </span><span class="sxs-lookup"><span data-stu-id="f128c-129">[Encryption and Signing Certificates](../core/encryption-and-signing-certificates.md) </span></span>  
 [<span data-ttu-id="f128c-130">傳送和接收加密的訊息</span><span class="sxs-lookup"><span data-stu-id="f128c-130">Sending and Receiving Encrypted Messages</span></span>](../core/sending-and-receiving-encrypted-messages.md)