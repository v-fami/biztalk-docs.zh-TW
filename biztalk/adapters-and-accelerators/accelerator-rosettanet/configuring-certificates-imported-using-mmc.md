---
title: "設定使用 MMC 匯入憑證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- decryption certificates
- certificates, decryption certificates
- certificates, signing certificates
- importing certificates
- signing certificates
- certificates, importing
ms.assetid: 64dbfbcf-6026-4c68-a93a-f483ec52deac
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f60811a8b6875c8cbcf4a8037501855a08fe0be6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-certificates-imported-using-mmc"></a><span data-ttu-id="01919-102">設定使用 MMC 匯入的憑證</span><span class="sxs-lookup"><span data-stu-id="01919-102">Configuring Certificates Imported Using MMC</span></span>
<span data-ttu-id="01919-103">使用 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC) 中的「憑證」嵌入式管理單元匯入憑證後，必須設定憑證的使用方式。</span><span class="sxs-lookup"><span data-stu-id="01919-103">After you have imported certificates using the Certificates snap-in for the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC), you must configure their use.</span></span> <span data-ttu-id="01919-104">這包括設定 BizTalk 群組、BizTalk 主控件與外掛式主控件服務帳戶、「交易夥伴介面程序」(PIP)、交易夥伴協議與交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="01919-104">This requires configuring the BizTalk Group, the BizTalk Host and Isolated Host service accounts, Partner Interface Processes (PIPs), trading partner agreements, and partners.</span></span> <span data-ttu-id="01919-105">您必須執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="01919-105">You must perform the following steps:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01919-106">若您使用 CertWizard 公用程式匯入與設定憑證，則不需要手動執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="01919-106">If you use the CertWizard utility to import and configure a certificate, you do not have to perform these manual steps.</span></span>  
  
-   <span data-ttu-id="01919-107">設定主要組織的簽章憑證使用方式。</span><span class="sxs-lookup"><span data-stu-id="01919-107">Configure the use of a signing certificate for the home organization.</span></span> <span data-ttu-id="01919-108">這意謂著您使用私密金鑰，識別外寄訊息中的主要組織。</span><span class="sxs-lookup"><span data-stu-id="01919-108">This means that you use a private key to identify the home organization in outgoing messages.</span></span> <span data-ttu-id="01919-109">若要如此，請設定 BizTalk 群組的簽章憑證。</span><span class="sxs-lookup"><span data-stu-id="01919-109">To do this, you configure the signing certificate for the BizTalk Group.</span></span>  
  
-   <span data-ttu-id="01919-110">為主要組織設定解密憑證的使用方式。</span><span class="sxs-lookup"><span data-stu-id="01919-110">Configure the use of a decryption certificate for the home organization.</span></span> <span data-ttu-id="01919-111">請意謂著您使用交易夥伴公開金鑰對應的私密金鑰，解密內送訊息。</span><span class="sxs-lookup"><span data-stu-id="01919-111">This means that you use a private key, which corresponds to the partner's public key, to decrypt incoming messages.</span></span> <span data-ttu-id="01919-112">若要如此，請設定每個 BizTalk 主控件與 BizTalk 外掛式主控件服務帳戶的解密憑證。</span><span class="sxs-lookup"><span data-stu-id="01919-112">To do this, you configure the decryption certificate for each BizTalk Host and the BizTalk Isolated Host service accounts.</span></span> <span data-ttu-id="01919-113">您必須為主控件與外掛式主控件服務帳戶輸入相同的解密憑證，對於 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 您必須設為相同的帳戶。</span><span class="sxs-lookup"><span data-stu-id="01919-113">You must enter the same decryption certificate for both the host and isolated host service accounts, which for [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] you must set to the same account.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="01919-114">BizTalk 主控件與外掛式主控件必須具有相同的解密憑證，如此才能解密相同的加密內送訊息。</span><span class="sxs-lookup"><span data-stu-id="01919-114">The BizTalk Hosts and the Isolated Host must have the same decryption certificate so that they can both decrypt the same encrypted incoming messages.</span></span> <span data-ttu-id="01919-115">執行 HTTP 配接器的 BizTalk 外掛式主控件無法存取主控件憑證，因此必須具有憑證，才能接收訊息。</span><span class="sxs-lookup"><span data-stu-id="01919-115">The BizTalk Isolated Host that runs the HTTP adapter must have the certificate to receive the messages, because it does not have access to the Host certificate.</span></span> <span data-ttu-id="01919-116">BizTalk 主控件也必須具有憑證，才能在 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 接收訊息後處理訊息。</span><span class="sxs-lookup"><span data-stu-id="01919-116">The BizTalk Host also must have the certificate to process the messages after [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] has received them.</span></span>  
  
-   <span data-ttu-id="01919-117">為每個交易夥伴設定加密與簽章憑證。</span><span class="sxs-lookup"><span data-stu-id="01919-117">Configure encryption and signing certificates for each partner.</span></span> <span data-ttu-id="01919-118">若要這樣做，您必須輸入憑證**一般** 索引標籤**夥伴**屬性頁[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] ([!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]) 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="01919-118">To do this, you enter the certificates on the **General** tab of the **Partner** properties page in the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] ([!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]) Management Console.</span></span> <span data-ttu-id="01919-119">這包括加密至交易夥伴外寄訊息的公開公鑰加密憑證，以及在內送訊息中確認交易夥伴身份識別的公開金鑰簽章憑證。</span><span class="sxs-lookup"><span data-stu-id="01919-119">These include a public-key encryption certificate to encrypt outgoing messages to a partner, and a public-key signing certificate to verify the partner's identity on incoming messages.</span></span> <span data-ttu-id="01919-120">如需詳細資訊，請參閱[建立或編輯夥伴](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md)。</span><span class="sxs-lookup"><span data-stu-id="01919-120">For more information, see [Creating or Editing a Partner](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md).</span></span>  
  
-   <span data-ttu-id="01919-121">設定主要組織與交易夥伴之間的加密原則。</span><span class="sxs-lookup"><span data-stu-id="01919-121">Configure the encryption policy between a home organization and a trading partner.</span></span> <span data-ttu-id="01919-122">若要這樣做，您必須設定交易夥伴協議上**通訊協定** 索引標籤**協議屬性**頁面[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="01919-122">To do this, you configure the trading partner agreement on the **Protocol** tab of the **Agreement Properties** page in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console.</span></span> <span data-ttu-id="01919-123">如需詳細資訊，請參閱[建立或編輯協議](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)。</span><span class="sxs-lookup"><span data-stu-id="01919-123">For more information, see [Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).</span></span>  
  
### <a name="to-configure-the-signing-certificate-for-a-biztalk-group-or-the-decryption-certificate-for-a-biztalk-host"></a><span data-ttu-id="01919-124">設定 BizTalk 群組的簽章憑證或 BizTalk 主控件的解密憑證</span><span class="sxs-lookup"><span data-stu-id="01919-124">To configure the signing certificate for a BizTalk Group or the decryption certificate for a BizTalk Host</span></span>  
  
1.  <span data-ttu-id="01919-125">按一下**啟動**，按一下**執行**，型別**runas /user:\<裝載服務 > mmc**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="01919-125">Click **Start**, click **Run**, type **runas /user:\<host service> mmc**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="01919-126">如\<*裝載服務*>，輸入您在安裝時，主控件服務關聯的服務名稱[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="01919-126">For \<*host service*>, type the name of the service that you associated with the host service when you installed [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)].</span></span>  
  
2.  <span data-ttu-id="01919-127">輸入的密碼\<*裝載服務*>，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="01919-127">Type the password for \<*host service*>, and then press ENTER.</span></span>  
  
3.  <span data-ttu-id="01919-128">按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下 [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **管理主控台**。</span><span class="sxs-lookup"><span data-stu-id="01919-128">Click **Start**, point to **All Programs**, point to [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.</span></span>  
  
4.  <span data-ttu-id="01919-129">展開**憑證-目前使用者**，依序展開**個人**，然後按一下**憑證**。</span><span class="sxs-lookup"><span data-stu-id="01919-129">Expand **Certificates - Current User**, expand **Personal**, and then click **Certificates**.</span></span>  
  
5.  <span data-ttu-id="01919-130">在右側窗格中，按兩下私用憑證。</span><span class="sxs-lookup"><span data-stu-id="01919-130">In the right pane, double-click a private certificate.</span></span>  
  
6.  <span data-ttu-id="01919-131">在 憑證 視窗上**詳細資料**索引標籤上，按一下 **指紋**，然後顯示在視窗中選取十六進位的識別碼。</span><span class="sxs-lookup"><span data-stu-id="01919-131">In the Certificate window, on the **Details** tab, click **Thumbprint**, and then select the hexadecimal identification number in the display window.</span></span> <span data-ttu-id="01919-132">按下 CTRL+C 以複製識別碼。</span><span class="sxs-lookup"><span data-stu-id="01919-132">Press CTRL+C to copy it.</span></span>  
  
7.  <span data-ttu-id="01919-133">按一下**啟動**，指向 **所有程式**，指向  **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下 **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="01919-133">Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
8.  <span data-ttu-id="01919-134">若要設定 BizTalk 群組的簽章憑證，以滑鼠右鍵按一下**Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **（本機）**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="01919-134">To configure the signing certificate for a BizTalk Group, right-click **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]**(Local)**, and then click **Properties**.</span></span> <span data-ttu-id="01919-135">按一下右邊的文字方塊**指紋**，按 CTRL + V 將憑證指紋數貼到文字方塊中，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="01919-135">Click in the text box to the right of **Thumbprint**, press CTRL+V to paste the thumbprint number into the text box, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="01919-136">若要為 BizTalk 主控件設定解密憑證，請展開**Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **（本機）**，依序展開**主機**，以滑鼠右鍵按一下您想要的主機設定，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="01919-136">To configure the decryption certificate for a BizTalk Host, expand **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **(Local)**, expand **Hosts**, right-click the host that you want to configure, and then click **Properties**.</span></span>  
  
10. <span data-ttu-id="01919-137">在**憑證**索引標籤上，按一下文字方塊右邊的**指紋**，按 CTRL + V 將憑證指紋數貼到文字方塊中，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="01919-137">On the **Certificate** tab, click in the text box to the right of **Thumbprint**, press CTRL+V to paste the thumbprint number into the text box, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="01919-138">您必須設定 BizTalk 主控件 (BizTalkServerApplication) 與 BizTalk 外掛式主控件 (BizTalkServerIsolatedHost) 的解密憑證。</span><span class="sxs-lookup"><span data-stu-id="01919-138">You must configure the decrypting certificates on both the BizTalk Host (BizTalkServerApplication) and the BizTalk Isolated Host (BizTalkServerIsolatedHost).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01919-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01919-139">See Also</span></span>  
 [<span data-ttu-id="01919-140">管理憑證</span><span class="sxs-lookup"><span data-stu-id="01919-140">Managing Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/managing-certificates1.md)