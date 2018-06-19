---
title: 最佳做法來管理 Certificates1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- best practices, certificates
- certificates, security
- security, certificates
- certificates, best practices
- best practices, security
- security, best practices
ms.assetid: cd182df4-0fcd-409c-9221-89f92e069f07
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e72d87530e5d080bd98ed55c2d29ca9554430375
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232086"
---
# <a name="best-practices-for-managing-certificates"></a><span data-ttu-id="83891-102">管理憑證的最佳作法</span><span class="sxs-lookup"><span data-stu-id="83891-102">Best Practices for Managing Certificates</span></span>
<span data-ttu-id="83891-103">本節提供在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境中管理憑證的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="83891-103">This section provides best practices for managing certificates in your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span>  
  
-   <span data-ttu-id="83891-104">**執行環境的威脅模型分析**</span><span class="sxs-lookup"><span data-stu-id="83891-104">**Do a Threat Model Analysis of your environment**</span></span>  
  
     <span data-ttu-id="83891-105">執行您環境的「威脅模型分析」(TMA) 以判斷簽章或加密憑證是否有助於減輕安全性威脅。</span><span class="sxs-lookup"><span data-stu-id="83891-105">Do a Threat Model Analysis (TMA) of your environment to determine whether signing or encryption certificates will help you mitigate security threats.</span></span>  
  
-   <span data-ttu-id="83891-106">**與夥伴建立公開金鑰憑證的計劃**</span><span class="sxs-lookup"><span data-stu-id="83891-106">**Create a plan for public key certificates with partners**</span></span>  
  
     <span data-ttu-id="83891-107">與夥伴建立用來傳送和接收公開金鑰憑證的計劃。</span><span class="sxs-lookup"><span data-stu-id="83891-107">Create a plan for sending and receiving public key certificates with partners.</span></span> <span data-ttu-id="83891-108">如果您沒有使用簽章憑證進行合作對象解析，則可以將公用憑證附加到訊息；在此情況下，您的系統並不需要預先準備憑證的複本。</span><span class="sxs-lookup"><span data-stu-id="83891-108">If you are not using signing certificates for party resolution, the public certificate can be attached to the message, in which case you do not need a copy of the certificate in your system beforehand.</span></span>  
  
-   <span data-ttu-id="83891-109">**設定的間隔下載憑證撤銷清單**</span><span class="sxs-lookup"><span data-stu-id="83891-109">**Download the certificate revocation list at set intervals**</span></span>  
  
     <span data-ttu-id="83891-110">下載憑證授權單位 (CA) 憑證撤銷的清單 (CRL) 設定的間隔。</span><span class="sxs-lookup"><span data-stu-id="83891-110">Download the certificate revocation list (CRL) from your certification authority (CA) at set intervals.</span></span> <span data-ttu-id="83891-111">我們建議一週下載一次。</span><span class="sxs-lookup"><span data-stu-id="83891-111">We recommend doing this once a week.</span></span> <span data-ttu-id="83891-112">如果 BizTalk 伺服器所加入的網域有 CA 存在，便會自動下載 CRL。</span><span class="sxs-lookup"><span data-stu-id="83891-112">The CRLs are downloaded automatically if there is a CA for the domain in which the BizTalk servers are joined.</span></span>  
  
-   <span data-ttu-id="83891-113">**與協力廠商的指導方針建立提交公開金鑰**</span><span class="sxs-lookup"><span data-stu-id="83891-113">**Establish guidelines with partners for submitting public keys**</span></span>  
  
     <span data-ttu-id="83891-114">在與夥伴的「服務等級協議」(SLA) 內容中，建立提交公開金鑰的指導方針，在他們的憑證即將到期時，以及在他們撤銷憑證時通知您。</span><span class="sxs-lookup"><span data-stu-id="83891-114">As part of your Service Level Agreement (SLA) with your partner, establish guidelines for submitting public keys, notifying you when their certificates are about to expire, and notifying you when they revoke a certificate.</span></span>  
  
-   <span data-ttu-id="83891-115">**驗證簽章憑證**</span><span class="sxs-lookup"><span data-stu-id="83891-115">**Verify signing certificates**</span></span>  
  
     <span data-ttu-id="83891-116">您務必要根據憑證撤銷清單驗證簽章憑證。</span><span class="sxs-lookup"><span data-stu-id="83891-116">Make sure you verify the signing certificates against the certificate revocation list.</span></span> <span data-ttu-id="83891-117">如需如何驗證簽章憑證的詳細資訊，請參閱[如何設定 MIME SMIME 解碼器管線元件](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="83891-117">For more information about how to verify the signing certificates, see [How to Configure the MIME-SMIME Decoder Pipeline Component](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md).</span></span>  
  
-   <span data-ttu-id="83891-118">**避免阻斷服務攻擊的數位簽章**</span><span class="sxs-lookup"><span data-stu-id="83891-118">**Avoid denial of service attacks for digital signatures**</span></span>  
  
     <span data-ttu-id="83891-119">決定您要在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法驗證數位簽章時處理訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="83891-119">Determine what you want to do with messages when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot validate the digital signature.</span></span> <span data-ttu-id="83891-120">設定**驗證**接收埠上的屬性，將有助於避免阻斷服務攻擊。</span><span class="sxs-lookup"><span data-stu-id="83891-120">Setting the **Authentication** property on the receive port will help prevent denial of service attacks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="83891-121">**驗證-捨棄訊息**和**驗證-保留訊息**接收埠上的旗標需要正確地設定合作對象解析管線元件和合作對象為在 BizTalk Server 中定義。</span><span class="sxs-lookup"><span data-stu-id="83891-121">The **Authentication - Drop messages** and **Authentication - Keep messages** flags on the receive port require that the Party Resolution pipeline component be configured correctly, and that the parties are defined in BizTalk Server.</span></span> <span data-ttu-id="83891-122">如需有關如何設定合作對象解析管線元件的詳細資訊，請參閱[合作對象解析管線元件](../core/party-resolution-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="83891-122">For more information about configuring the Party Resolution pipeline component, see [Party Resolution Pipeline Component](../core/party-resolution-pipeline-component.md).</span></span>  
  
-   <span data-ttu-id="83891-123">**建立個別的加密和未加密的訊息接收位置**</span><span class="sxs-lookup"><span data-stu-id="83891-123">**Create separate receive locations for encrypted and unencrypted messages**</span></span>  
  
     <span data-ttu-id="83891-124">如果您打算從某些夥伴接收 MIME 加密訊息，並從其他夥伴接收未加密的訊息，請在不同的主控件中，為加密和未加密的訊息分別建立接收位置。</span><span class="sxs-lookup"><span data-stu-id="83891-124">If you plan to receive MIME-encrypted messages from some partners and unencrypted messages from other partners, create separate receive locations in different hosts for encrypted and unencrypted messages.</span></span> <span data-ttu-id="83891-125">當您希望只有 MIME 加密訊息時，設定**允許非 MIME 訊息**解碼 MIME/SMIME 管線元件中的選項**否**。</span><span class="sxs-lookup"><span data-stu-id="83891-125">When you expect only MIME-encrypted messages, configure the **Allow Non MIME Message** option in the Decode MIME/SMIME pipeline component to **No**.</span></span>  
  
-   <span data-ttu-id="83891-126">**與夥伴管理憑證**</span><span class="sxs-lookup"><span data-stu-id="83891-126">**Manage certificates with partners**</span></span>  
  
     <span data-ttu-id="83891-127">將憑證管理納入夥伴管理實務的環節。</span><span class="sxs-lookup"><span data-stu-id="83891-127">Make certificate management part of your partner management practices.</span></span> <span data-ttu-id="83891-128">在從 BizTalk Server 環境中新增或移除合作對象時，建議您新增或移除與該夥伴相關聯的憑證。</span><span class="sxs-lookup"><span data-stu-id="83891-128">When you add or remove a party from the BizTalk Server environment, we recommend that you add or remove the certificates associated with that partner.</span></span>  
  
-   <span data-ttu-id="83891-129">**移除主控件執行個體前移除憑證**</span><span class="sxs-lookup"><span data-stu-id="83891-129">**Remove certificates before removing a host instance**</span></span>  
  
     <span data-ttu-id="83891-130">從 BizTalk Server 移除主控件執行個體前，請先移除主控件執行個體執行時所用帳戶的個人存放區中的憑證。</span><span class="sxs-lookup"><span data-stu-id="83891-130">Before removing a host instance from a BizTalk server, remove the certificates in the personal store of the account under which the host instance is running.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83891-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83891-131">See Also</span></span>  
 <span data-ttu-id="83891-132">[管理 BizTalk Server 安全性](../core/managing-biztalk-server-security.md) </span><span class="sxs-lookup"><span data-stu-id="83891-132">[Managing BizTalk Server Security](../core/managing-biztalk-server-security.md) </span></span>  
 [<span data-ttu-id="83891-133">管理 Windows 群組和使用者帳戶的最佳作法</span><span class="sxs-lookup"><span data-stu-id="83891-133">Best Practices for Managing Windows Groups and User Accounts</span></span>](../core/best-practices-for-managing-windows-groups-and-user-accounts.md)