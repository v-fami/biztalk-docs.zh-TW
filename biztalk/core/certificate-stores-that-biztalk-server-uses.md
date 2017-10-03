---
title: "BizTalk Server 使用的憑證存放區 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- public key certificates
- certificate stores, warnings
- private key certificates
- certificates, private key
- Other People stores [certificates]
- certificate stores, Personal store
- Personal store [certificates]
- certificate stores, Windows stores
- certificates, public key
- certificates, certificate stores
- certificate stores
ms.assetid: 29b65913-be3b-45d9-9865-02e52e4370f4
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b142ff5b9c9007a86b09acd25f53f8c88796988c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="certificate-stores-that-biztalk-server-uses"></a><span data-ttu-id="161ec-102">BizTalk Server 使用的憑證存放區</span><span class="sxs-lookup"><span data-stu-id="161ec-102">Certificate Stores that BizTalk Server Uses</span></span>
<span data-ttu-id="161ec-103">BizTalk Server 使用兩種憑證存放區：公開金鑰的「其他人」憑證存放區，以及私密金鑰的每個主控件執行個體服務帳戶的「個人」憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="161ec-103">BizTalk Server uses two types of certificate stores, the Other People certificate store for public keys, and the Personal certificate store for each host instance service account for the private key.</span></span>  
  
 <span data-ttu-id="161ec-104">**其他人 」 憑證存放區中。**</span><span class="sxs-lookup"><span data-stu-id="161ec-104">**Other People certificate store.**</span></span> <span data-ttu-id="161ec-105">正如其名所指，公開金鑰憑證即是公開可供任何人存取的憑證，但是此人必須有權存取儲存該憑證的電腦。</span><span class="sxs-lookup"><span data-stu-id="161ec-105">Public key certificates, as their name implies, are public and accessible by anyone with access to the computer on which they are stored.</span></span> <span data-ttu-id="161ec-106">BizTalk Server 使用公開金鑰憑證來加密要送至特定合作對象的訊息，並驗證來自特定合作對象的內送訊息的數位簽章。</span><span class="sxs-lookup"><span data-stu-id="161ec-106">BizTalk Server uses public key certificates to encrypt messages to specific parties and to verify the digital signatures for incoming messages from specific parties.</span></span> <span data-ttu-id="161ec-107">Windows 提供「其他人」憑證存放區來儲存電腦上使用的公開金鑰憑證。</span><span class="sxs-lookup"><span data-stu-id="161ec-107">Windows provides the Other People certificate store to store the public key certificates used on the computer.</span></span> <span data-ttu-id="161ec-108">所有的使用者都可以讀取及使用這個存放區內的憑證，而 Windows 系統管理員具有維護此存放區的權限。</span><span class="sxs-lookup"><span data-stu-id="161ec-108">All users can read and use the certificates in this store, and Windows administrators have permissions to maintain this store.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="161ec-109">您必須將公開金鑰憑證儲存在本機電腦的「本機電腦\其他人」憑證存放區，而這台電腦中會有 BizTalk 主控件執行個體，可用來驗證簽章或加密傳送至遠端夥伴的訊息。</span><span class="sxs-lookup"><span data-stu-id="161ec-109">You must save the public key certificates on the Local Machine\Other People certificate store of the local computer where there is a BizTalk Host instance that is used to verify the signature or encrypt messages sent to a remote partner.</span></span>  
  
 <span data-ttu-id="161ec-110">下圖顯示 BizTalk Server 針對公開金鑰憑證所使用的「其他人」憑證存放區：</span><span class="sxs-lookup"><span data-stu-id="161ec-110">The following figure shows the Other People certificate store that BizTalk Server uses for public key certificates:</span></span>  
  
 <span data-ttu-id="161ec-111">![其他人 」 憑證存放區](../core/media/bpi-sp-msgsec-otherpeoplecertstore.gif "BPI_SP_MSGSEC_OTHERPEOPLECERTSTORE")</span><span class="sxs-lookup"><span data-stu-id="161ec-111">![Other People's Certificates Store](../core/media/bpi-sp-msgsec-otherpeoplecertstore.gif "BPI_SP_MSGSEC_OTHERPEOPLECERTSTORE")</span></span>  
  
 <span data-ttu-id="161ec-112">**個人憑證存放區。**</span><span class="sxs-lookup"><span data-stu-id="161ec-112">**Personal certificate store.**</span></span> <span data-ttu-id="161ec-113">BizTalk Server 使用私密金鑰憑證來解密內送訊息及簽署輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="161ec-113">BizTalk Server uses private key certificates to decrypt incoming messages and sign outbound messages.</span></span> <span data-ttu-id="161ec-114">在電腦上用來進行互動式登入的每個 Windows 帳戶都會有作業系統所儲存僅供該帳戶存取的個人憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="161ec-114">Every Windows account enabled to log on interactively on a computer has a personal certificate store by the operating system, which only that account can access.</span></span> <span data-ttu-id="161ec-115">BizTalk Server 使用各主控件執行個體服務帳戶的個人憑證存放區來存取每個服務帳戶有權存取的私密金鑰憑證。</span><span class="sxs-lookup"><span data-stu-id="161ec-115">BizTalk Server uses the personal certificate stores for each of the host instances service accounts to access the private key certificates to which each service account has access.</span></span> <span data-ttu-id="161ec-116">只有憑證存放區的擁有者才可以存取及維護各自的個人憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="161ec-116">Only owners of the certificate store can access and maintain their personal certificate stores.</span></span> <span data-ttu-id="161ec-117">也就是說，您必須以各主控件服務帳戶登入每一台裝載 S/MIME 解碼管線的電腦，然後使用 [憑證] 嵌入式管理單元，將解密憑證匯入至個人憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="161ec-117">In other words, you must log in into each computer that will host S/MIME decode pipelines as each host service account, and import the decryption certificate to the personal certificate store using the Certificates snap-in.</span></span>  
  
 <span data-ttu-id="161ec-118">下圖顯示 BizTalk Server 針對私密金鑰憑證所使用的「個人」憑證存放區：</span><span class="sxs-lookup"><span data-stu-id="161ec-118">The following figure shows the Personal certificate store that BizTalk Server uses for private key certificates:</span></span>  
  
 <span data-ttu-id="161ec-119">![目前的使用者憑證存放區](../core/media/bpi-sp-msgsec-mystore.gif "BPI_SP_MSGSEC_MYSTORE")</span><span class="sxs-lookup"><span data-stu-id="161ec-119">![Current User's Certificates Store](../core/media/bpi-sp-msgsec-mystore.gif "BPI_SP_MSGSEC_MYSTORE")</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="161ec-120">私密金鑰憑證必須已經儲存在每一台電腦上各個主控件執行個體服務帳戶的「目前使用者\個人」憑證存放區，而這些電腦中存在的 BizTalk (執行中的主控件執行個體) 需要可用來解密或簽署輸出訊息的憑證。</span><span class="sxs-lookup"><span data-stu-id="161ec-120">The private key certificates must be stored in the Current User\Personal certificate store for each host instance service account on each computer that has a BizTalk a running host instance that requires the certificate for decryption or for signing outbound messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="161ec-121">在新增用來簽署輸出訊息的私密金鑰憑證到服務帳戶的個人憑證存放區之後，您也必須在 BizTalk 管理主控台中指定這個簽章憑證。</span><span class="sxs-lookup"><span data-stu-id="161ec-121">After you have added the certificate with the private key to the personal certificate store of the service accounts that will sign outbound messages, you must also specify this signing certificate in the BizTalk Administration console.</span></span> <span data-ttu-id="161ec-122">如需詳細資訊，請參閱[傳送簽署的訊息設定 BizTalk Server 如何](../core/how-to-configure-biztalk-server-for-sending-signed-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="161ec-122">For more information, see [How to Configure BizTalk Server for Sending Signed Messages](../core/how-to-configure-biztalk-server-for-sending-signed-messages.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="161ec-123">當用於程式設計作業 (如憑證匯入及匯出的指令碼處理) 時，個人憑證存放區也稱為 MY 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="161ec-123">The personal certificate store is also called the MY certificate store when it is used for programmatic operations, such as scripting the importing and exporting of certificates.</span></span>  
  
 <span data-ttu-id="161ec-124">下表說明必須在每個 Windows 憑證存放區中安裝的憑證。</span><span class="sxs-lookup"><span data-stu-id="161ec-124">The following table describes the certificates that you must install in each Windows certificate store.</span></span>  
  
### <a name="table-1-certificates-for-each-windows-certificate-store"></a><span data-ttu-id="161ec-125">表 1：每個 Windows 憑證存放區的憑證</span><span class="sxs-lookup"><span data-stu-id="161ec-125">Table 1 Certificates for each Windows certificate store</span></span>  
  
|<span data-ttu-id="161ec-126">**憑證用途**</span><span class="sxs-lookup"><span data-stu-id="161ec-126">**Certificate purpose**</span></span>|<span data-ttu-id="161ec-127">**憑證類型**</span><span class="sxs-lookup"><span data-stu-id="161ec-127">**Certificate type**</span></span>|<span data-ttu-id="161ec-128">**憑證存放區**</span><span class="sxs-lookup"><span data-stu-id="161ec-128">**Certificate store**</span></span>|  
|-----------------------------|--------------------------|---------------------------|  
|<span data-ttu-id="161ec-129">簽署</span><span class="sxs-lookup"><span data-stu-id="161ec-129">Signing</span></span>|<span data-ttu-id="161ec-130">自有私密金鑰</span><span class="sxs-lookup"><span data-stu-id="161ec-130">Own private key</span></span>|<span data-ttu-id="161ec-131">每個服務帳戶具有傳送管線，其設定來簽署訊息的 MIME/SMIME 編碼器管線元件的主控件執行個體的個人存放區 (**加入簽章憑證至訊息**屬性設定為`True`)。</span><span class="sxs-lookup"><span data-stu-id="161ec-131">Personal store for each service account of a host instance that has a send pipeline with a MIME/SMIME Encoder pipeline component configured to sign messages (**Add Signing Cert To Message** property set to `True`).</span></span> <span data-ttu-id="161ec-132">如需詳細資訊，請參閱[如何設定 BizTalk Server 傳送簽署的訊息](../core/how-to-configure-biztalk-server-for-sending-signed-messages.md)</span><span class="sxs-lookup"><span data-stu-id="161ec-132">For more information, see [How to Configure BizTalk Server for Sending Signed Messages](../core/how-to-configure-biztalk-server-for-sending-signed-messages.md)</span></span>|  
|<span data-ttu-id="161ec-133">驗證簽章</span><span class="sxs-lookup"><span data-stu-id="161ec-133">Verifying signature</span></span>|<span data-ttu-id="161ec-134">夥伴的公開金鑰</span><span class="sxs-lookup"><span data-stu-id="161ec-134">Partner's public key</span></span>|<span data-ttu-id="161ec-135">具有主控件執行個體的各台電腦上的「其他人」存放區；這個執行個體具有包含 MIME/SMIME 解碼器管線元件的接收管線。</span><span class="sxs-lookup"><span data-stu-id="161ec-135">Other People store on each computer that has a host instance that has a receive pipeline with a MIME/SMIME Decoder pipeline component.</span></span> <span data-ttu-id="161ec-136">如需詳細資訊，請參閱[如何設定接收簽署訊息的 BizTalk 伺服器](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="161ec-136">For more information, see [How to Configure BizTalk Server for Receiving Signed Messages](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md).</span></span>|  
|<span data-ttu-id="161ec-137">解密</span><span class="sxs-lookup"><span data-stu-id="161ec-137">Decrypting</span></span>|<span data-ttu-id="161ec-138">自有私密金鑰</span><span class="sxs-lookup"><span data-stu-id="161ec-138">Own private key</span></span>|<span data-ttu-id="161ec-139">主控件執行個體的各個服務帳戶的個人存放區；這個執行個體具有包含 MIME/SMIME 解碼器管線元件的接收管線。</span><span class="sxs-lookup"><span data-stu-id="161ec-139">Personal store for each service account of a host instance that has a receive pipeline with a MIME/SMIME Decoder pipeline component.</span></span> <span data-ttu-id="161ec-140">如需詳細資訊，請參閱[如何設定 BizTalk Server 接收加密訊息](../core/how-to-configure-biztalk-server-for-receiving-encrypted-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="161ec-140">For more information, see [How to Configure BizTalk Server for Receiving Encrypted Messages](../core/how-to-configure-biztalk-server-for-receiving-encrypted-messages.md).</span></span>|  
|<span data-ttu-id="161ec-141">加密</span><span class="sxs-lookup"><span data-stu-id="161ec-141">Encrypting</span></span>|<span data-ttu-id="161ec-142">夥伴的公開金鑰</span><span class="sxs-lookup"><span data-stu-id="161ec-142">Partner's public key</span></span>|<span data-ttu-id="161ec-143">其他人 」 存放區已具有傳送管線，其設定為用於加密訊息的 MIME/SMIME 編碼器管線元件的主控件執行個體的每部電腦上 (**啟用加密**屬性設定為`True)`。</span><span class="sxs-lookup"><span data-stu-id="161ec-143">Other People store on each computer that has a host instance that has a send pipeline with a MIME/SMIME Encoder pipeline component configured to encrypt messages (**Enable encryption** property set to `True)`.</span></span> <span data-ttu-id="161ec-144">如需詳細資訊，請參閱[如何設定 BizTalk Server 傳送加密訊息](../core/how-to-configure-biztalk-server-for-sending-encrypted-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="161ec-144">For more information, see [How to Configure BizTalk Server for Sending Encrypted Messages](../core/how-to-configure-biztalk-server-for-sending-encrypted-messages.md).</span></span>|  
|<span data-ttu-id="161ec-145">合作對象解析</span><span class="sxs-lookup"><span data-stu-id="161ec-145">Party resolution</span></span>|<span data-ttu-id="161ec-146">夥伴的公開金鑰</span><span class="sxs-lookup"><span data-stu-id="161ec-146">Partner's public key</span></span>|<span data-ttu-id="161ec-147">在管理電腦上的「其他人」存放區，您將會從此存放區中設定合作對象解析。</span><span class="sxs-lookup"><span data-stu-id="161ec-147">Other People store on the administration computer from which you are configuring party resolution.</span></span> <span data-ttu-id="161ec-148">如需詳細資訊，請參閱[使用憑證進行合作對象解析](../core/using-certificates-for-party-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="161ec-148">For more information, see [Using Certificates for Party Resolution](../core/using-certificates-for-party-resolution.md).</span></span>|  
  
 <span data-ttu-id="161ec-149">下圖顯示您在接收訊息專用的 BizTalk Server 上的每個憑證存放區中，將會需要哪些憑證。</span><span class="sxs-lookup"><span data-stu-id="161ec-149">The following figure shows what certificates you will need in each certificate store on a BizTalk Server dedicated to receiving messages.</span></span>  
  
 <span data-ttu-id="161ec-150">![接收安全訊息所需的憑證](../core/media/bpi-sp-msgsec-certmgmt-certstores-receive.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Receive")</span><span class="sxs-lookup"><span data-stu-id="161ec-150">![Certificates required to receive secure messages](../core/media/bpi-sp-msgsec-certmgmt-certstores-receive.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Receive")</span></span>  
  
 <span data-ttu-id="161ec-151">下圖顯示您在傳送訊息專用的 BizTalk Server 上的每個憑證存放區中，將會需要哪些憑證。</span><span class="sxs-lookup"><span data-stu-id="161ec-151">The following figure shows what certificates you will need in each certificate store on a BizTalk Server dedicated to sending messages.</span></span>  
  
 <span data-ttu-id="161ec-152">![傳送安全訊息所需的憑證](../core/media/bpi-sp-msgsec-certmgmt-certstores-send.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Send")</span><span class="sxs-lookup"><span data-stu-id="161ec-152">![Certificates required to send secure messages](../core/media/bpi-sp-msgsec-certmgmt-certstores-send.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Send")</span></span>  
  
 <span data-ttu-id="161ec-153">如需有關 Microsoft 管理主控台 (MMC) 之憑證存放區和 [憑證] 嵌入式管理單元的詳細資訊，請在「Windows 說明」中搜尋＜憑證主控台＞。</span><span class="sxs-lookup"><span data-stu-id="161ec-153">For more information about the Certificate stores and the Certificate snap-in for the Microsoft Management Console (MMC), search for "Certificate console" on the Windows Help.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="161ec-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="161ec-154">See Also</span></span>  
 <span data-ttu-id="161ec-155">[BizTalk Server 用於簽章訊息的憑證](../core/certificates-that-biztalk-server-uses-for-signed-messages.md) </span><span class="sxs-lookup"><span data-stu-id="161ec-155">[Certificates that BizTalk Server Uses for Signed Messages](../core/certificates-that-biztalk-server-uses-for-signed-messages.md) </span></span>  
 <span data-ttu-id="161ec-156">[BizTalk Server 會使用加密訊息的憑證](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md) </span><span class="sxs-lookup"><span data-stu-id="161ec-156">[Certificates that BizTalk Server Uses for Encrypted Messages](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md) </span></span>  
 <span data-ttu-id="161ec-157">[加密和簽章憑證](../core/encryption-and-signing-certificates.md) </span><span class="sxs-lookup"><span data-stu-id="161ec-157">[Encryption and Signing Certificates](../core/encryption-and-signing-certificates.md) </span></span>  
 [<span data-ttu-id="161ec-158">實作訊息安全性</span><span class="sxs-lookup"><span data-stu-id="161ec-158">Implementing Message Security</span></span>](../core/implementing-message-security.md)