---
title: "加密和簽章憑證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, security
- security, certificates
- security, messages
- certificates, encryption
- encryption certificates, messages
- messages, encryption
- messages, certificates
- security, encryption
ms.assetid: 3c3f9de5-4156-4133-8d5e-c30b142b6d61
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 633484a6c5599b9323bfd7798f621b27a501ce6b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="encryption-and-signing-certificates"></a><span data-ttu-id="6eb08-102">加密和簽章憑證</span><span class="sxs-lookup"><span data-stu-id="6eb08-102">Encryption and Signing Certificates</span></span>
<span data-ttu-id="6eb08-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 非常依賴憑證提供的安全性。</span><span class="sxs-lookup"><span data-stu-id="6eb08-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] relies heavily on the security provided by certificates.</span></span> <span data-ttu-id="6eb08-104">將憑證用於加密和數位簽章，BizTalk Server 就可以傳送並接收可信任的資料，同時也可以協助確保其處理的資料安全無虞。</span><span class="sxs-lookup"><span data-stu-id="6eb08-104">By using certificates for encryption and digital signatures, BizTalk Server can send and receive data that can be trusted, and can help ensure that the data it processes is secure.</span></span> <span data-ttu-id="6eb08-105">在加密和數位簽章這兩方面，都需要用到公開金鑰憑證和私密金鑰憑證。</span><span class="sxs-lookup"><span data-stu-id="6eb08-105">For both encryption and digital signatures, there is a public key certificate and a private key certificate.</span></span> <span data-ttu-id="6eb08-106">就加密而言，訊息傳送者會使用接收器的公開金鑰憑證來加密訊息，而訊息接收器 (BizTalk Server) 則使用自己的私密金鑰來解密訊息。</span><span class="sxs-lookup"><span data-stu-id="6eb08-106">For encryption, the sender of the message uses the receiver's public key certificate to encrypt the message, while the receiver of the message (BizTalk Server) uses its private key to decrypt the message.</span></span> <span data-ttu-id="6eb08-107">就數位簽章而言，訊息傳送者會使用私密金鑰憑證來簽署訊息，而訊息接收器 (BizTalk Server) 則使用傳送者的公開金鑰憑證來驗證簽章。</span><span class="sxs-lookup"><span data-stu-id="6eb08-107">For digital signatures, the sender of the message uses a private key certificate to sign the message, and the receiver of the message (BizTalk Server) uses the public key certificate of the sender to verify the signature.</span></span>  
  
 <span data-ttu-id="6eb08-108">BizTalk Server 使用公開金鑰憑證來驗證輸入訊息的數位簽章並加密輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="6eb08-108">BizTalk Server uses public key certificates to verify the digital signatures of inbound messages and for encrypting outbound messages.</span></span> <span data-ttu-id="6eb08-109">BizTalk Server 使用私密金鑰憑證以解密輸入訊息並簽署輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="6eb08-109">BizTalk Server uses private key certificates for decrypting inbound messages and signing outbound messages.</span></span>  
  
 <span data-ttu-id="6eb08-110">在 BizTalk 總管 和 BizTalk 管理主控台中，您可以設定 BizTalk Server 使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="6eb08-110">You configure the certificates BizTalk Server uses in BizTalk Explorer and in the BizTalk Administration Console.</span></span>  
  
 <span data-ttu-id="6eb08-111">如需有關數位簽章的詳細資訊，請參閱 Microsoft TechNet 網站，網址[http://go.microsoft.com/fwlink/?LinkId=60508](http://go.microsoft.com/fwlink/?LinkId=60508)。</span><span class="sxs-lookup"><span data-stu-id="6eb08-111">For more information about digital certificates, see the Microsoft TechNet Web site at [http://go.microsoft.com/fwlink/?LinkId=60508](http://go.microsoft.com/fwlink/?LinkId=60508).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6eb08-112">處理「安全多用途網際網路郵件延伸」(Secure Multipurpose Internet Mail Extension，S/MIME) 訊息時，您可以選擇讓 BizTalk Server 引擎檢查「憑證撤銷清單」(CRL) 來確保憑證沒有過期，並確定下至「根憑證授權單位」(CA) 都受到信任。</span><span class="sxs-lookup"><span data-stu-id="6eb08-112">While processing Secure Multipurpose Internet Mail Extensions (S/MIME) messages, you can choose to have the BizTalk Server engine check the Certificate Revocation List (CRL) to ensure that a certificate has not expired and that it is trusted down to a Root Certificate Authority (CA).</span></span> <span data-ttu-id="6eb08-113">這個驗證會在管線處理訊息時，於 MIME/SMIME 解碼器元件中進行。</span><span class="sxs-lookup"><span data-stu-id="6eb08-113">This verification occurs while the pipeline processes the message, in the MIME/SMIME decoder component.</span></span> <span data-ttu-id="6eb08-114">如需有關如何設定**檢查撤銷清單**屬性，請參閱[如何設定 MIME SMIME 解碼器管線元件](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="6eb08-114">For more information about how to set **Check Revocation List** property, see [How to Configure the MIME-SMIME Decoder Pipeline Component](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6eb08-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="6eb08-115">In This Section</span></span>  
  
-   [<span data-ttu-id="6eb08-116">BizTalk Server 使用的憑證存放區</span><span class="sxs-lookup"><span data-stu-id="6eb08-116">Certificate Stores that BizTalk Server Uses</span></span>](../core/certificate-stores-that-biztalk-server-uses.md)  
  
-   [<span data-ttu-id="6eb08-117">BizTalk Server 用於簽章訊息的憑證</span><span class="sxs-lookup"><span data-stu-id="6eb08-117">Certificates that BizTalk Server Uses for Signed Messages</span></span>](../core/certificates-that-biztalk-server-uses-for-signed-messages.md)  
  
-   [<span data-ttu-id="6eb08-118">BizTalk Server 會使用加密訊息的憑證</span><span class="sxs-lookup"><span data-stu-id="6eb08-118">Certificates that BizTalk Server Uses for Encrypted Messages</span></span>](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md)