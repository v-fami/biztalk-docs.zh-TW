---
title: 設定一般合作對象屬性 (AS2) |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9a4dbd0-8849-403a-af82-58ee0b10f85a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62d947baa1a3f9ea867f1b3a85a8b60129d31ee3
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26007048"
---
# <a name="configuring-general-party-properties-as2"></a><span data-ttu-id="8fd05-102">設定一般合作對象屬性 (AS2)</span><span class="sxs-lookup"><span data-stu-id="8fd05-102">Configuring General Party Properties (AS2)</span></span>
<span data-ttu-id="8fd05-103">合作對象或交易夥伴代表商務關係中的參與組織。</span><span class="sxs-lookup"><span data-stu-id="8fd05-103">A party or trading partner represents a participating organization in a business relationship.</span></span> <span data-ttu-id="8fd05-104">合作對象屬性包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="8fd05-104">Party properties contain the following information:</span></span>  
  
-   <span data-ttu-id="8fd05-105">一般資訊，例如合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="8fd05-105">General information such as party name</span></span>  
  
-   <span data-ttu-id="8fd05-106">與合作對象相關聯的傳送埠</span><span class="sxs-lookup"><span data-stu-id="8fd05-106">Send ports associated with the party</span></span>  
  
-   <span data-ttu-id="8fd05-107">與合作對象相關聯的憑證</span><span class="sxs-lookup"><span data-stu-id="8fd05-107">Certificates associated with the party</span></span>  
  
 <span data-ttu-id="8fd05-108">如需合作對象或交易夥伴的詳細資訊，請參閱[交易夥伴](../core/trading-partners-and-business-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="8fd05-108">For more information about parties or trading partners, see [Trading Partners](../core/trading-partners-and-business-profiles.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8fd05-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="8fd05-109">Prerequisites</span></span>  
 <span data-ttu-id="8fd05-110">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="8fd05-110">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-party-properties"></a><span data-ttu-id="8fd05-111">若要設定合作對象屬性</span><span class="sxs-lookup"><span data-stu-id="8fd05-111">To configure party properties</span></span>  
  
1.  <span data-ttu-id="8fd05-112">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**，指向 **新增**，然後按一下 **合作對象**。</span><span class="sxs-lookup"><span data-stu-id="8fd05-112">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click **Parties**, point to **New**, and then click **Party**.</span></span>  
  
2.  <span data-ttu-id="8fd05-113">在**一般**頁面**合作對象屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="8fd05-113">On the **General** page of the **Party Properties** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="8fd05-114">使用</span><span class="sxs-lookup"><span data-stu-id="8fd05-114">Use this</span></span>|<span data-ttu-id="8fd05-115">動作</span><span class="sxs-lookup"><span data-stu-id="8fd05-115">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="8fd05-116">**名稱**</span><span class="sxs-lookup"><span data-stu-id="8fd05-116">**Name**</span></span>|<span data-ttu-id="8fd05-117">輸入合作對象名稱。</span><span class="sxs-lookup"><span data-stu-id="8fd05-117">Enter a party name.</span></span>|  
    |<span data-ttu-id="8fd05-118">**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**</span><span class="sxs-lookup"><span data-stu-id="8fd05-118">**Local BizTalk processes messages received by the party or supports sending messages from this party**</span></span>|<span data-ttu-id="8fd05-119">選取此核取方塊，以指定合作對象代表同時裝載了 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的同一個交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="8fd05-119">Select this checkbox to specify that the party represents the same trading partner that also hosts [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="8fd05-120">**重要事項：** 對於兩個合作對象 TPM 解決方案會使用管線的方塊外，隨附於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您必須選取此核取方塊，至少一個合作對象。</span><span class="sxs-lookup"><span data-stu-id="8fd05-120">**Important:**  For a two-party TPM solution that uses out-of-the-box pipelines shipped with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you must select this check box for at least one party.</span></span> <span data-ttu-id="8fd05-121">**注意：** 某些屬性如果您清除此核取方塊，將會停用時建立此合作對象的協議。</span><span class="sxs-lookup"><span data-stu-id="8fd05-121">**Note:**  If you clear this check box, some properties will be disabled while creating the agreements for this party.</span></span>|  
    |<span data-ttu-id="8fd05-122">**其他屬性 – 名稱/值**</span><span class="sxs-lookup"><span data-stu-id="8fd05-122">**Additional Properties – Name / Value**</span></span>|<span data-ttu-id="8fd05-123">請輸入名稱-值組來儲存合作對象的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="8fd05-123">Enter a name-value pair to store any information about the party.</span></span> <span data-ttu-id="8fd05-124">您可以視需要新增任意數目的名稱-值組。</span><span class="sxs-lookup"><span data-stu-id="8fd05-124">You can add as many name-value pairs as you want.</span></span> <span data-ttu-id="8fd05-125">**注意：** 名稱 / 值組不會由 BizTalk Server 進行任何處理; 此資料僅供資訊。</span><span class="sxs-lookup"><span data-stu-id="8fd05-125">**Note:**  The name-value pairs are not used by the BizTalk Server for any processing; this data is for information purposes only.</span></span>|  
    |<span data-ttu-id="8fd05-126">**Delete**</span><span class="sxs-lookup"><span data-stu-id="8fd05-126">**Delete**</span></span>|<span data-ttu-id="8fd05-127">按一下選取的名稱-值組，加以刪除。</span><span class="sxs-lookup"><span data-stu-id="8fd05-127">Click to delete the selected name-value pair.</span></span>|  
  
3.  <span data-ttu-id="8fd05-128">在**傳送埠**頁面**合作對象屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="8fd05-128">On the **Send Ports** page of the **Party Properties** dialog box, do the following:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8fd05-129">在 BizTalk Server 傳送埠關聯是在協議層級。</span><span class="sxs-lookup"><span data-stu-id="8fd05-129">In BizTalk Server, the send port association is done at the agreement level.</span></span> <span data-ttu-id="8fd05-130">**傳送埠**可用為合作對象屬性的一部分是純粹是為了回溯相容性 頁面。</span><span class="sxs-lookup"><span data-stu-id="8fd05-130">The **Send Ports** page available as part of the party properties is purely for backward compatibility.</span></span> <span data-ttu-id="8fd05-131">當您將傳送埠與協議相關聯後，傳送埠設定也會傳播到合作對象設定，而您就可以在此頁面看到該傳送埠關聯。</span><span class="sxs-lookup"><span data-stu-id="8fd05-131">Whenever you associate a send port with an agreement, the send port setting is also propagated to the party setting and you can see the send port association in this page as well.</span></span> <span data-ttu-id="8fd05-132">但是，並非反之亦然。</span><span class="sxs-lookup"><span data-stu-id="8fd05-132">However, the reverse is not true.</span></span> <span data-ttu-id="8fd05-133">在您將傳送埠與合作夥伴相關聯後，該傳送埠無法自動出現在協議設定中。</span><span class="sxs-lookup"><span data-stu-id="8fd05-133">You cannot associate a send port with a party and then have that send port be automatically available as part of the agreement settings.</span></span> <span data-ttu-id="8fd05-134">如需如何將傳送埠與協議相關聯的詳細資訊，請參閱此處。</span><span class="sxs-lookup"><span data-stu-id="8fd05-134">For more information on how to associate send ports with agreement, see here.</span></span>  
  
    |<span data-ttu-id="8fd05-135">使用</span><span class="sxs-lookup"><span data-stu-id="8fd05-135">Use this</span></span>|<span data-ttu-id="8fd05-136">動作</span><span class="sxs-lookup"><span data-stu-id="8fd05-136">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="8fd05-137">**傳送埠-名稱**</span><span class="sxs-lookup"><span data-stu-id="8fd05-137">**Send ports - Name**</span></span>|<span data-ttu-id="8fd05-138">從下拉式清單選取要繫結至此合作對象的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="8fd05-138">From the drop-down list, select a send port to bind to this party.</span></span>|  
    |<span data-ttu-id="8fd05-139">**傳送埠-URI**</span><span class="sxs-lookup"><span data-stu-id="8fd05-139">**Send ports - URI**</span></span>|<span data-ttu-id="8fd05-140">顯示傳送埠位址。</span><span class="sxs-lookup"><span data-stu-id="8fd05-140">Displays the send port address.</span></span>|  
    |<span data-ttu-id="8fd05-141">**移除**</span><span class="sxs-lookup"><span data-stu-id="8fd05-141">**Remove**</span></span>|<span data-ttu-id="8fd05-142">按一下以從合作對象移除選取的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="8fd05-142">Click to remove the selected send port from the party.</span></span>|  
    |<span data-ttu-id="8fd05-143">**屬性**</span><span class="sxs-lookup"><span data-stu-id="8fd05-143">**Properties**</span></span>|<span data-ttu-id="8fd05-144">按一下即可顯示**傳送埠屬性**選取的傳送埠 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8fd05-144">Click to display the **Send Port Properties** dialog box for the selected send port.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="8fd05-145">BizTalk Server 可以透過比對訂閱訊息的傳送埠以及與合作對象關聯的傳送埠，判斷訊息傳送目標的合作對象。</span><span class="sxs-lookup"><span data-stu-id="8fd05-145">BizTalk Server can determine the party to send the message to by matching the send port that subscribes to the message with the send port associated with a party.</span></span> <span data-ttu-id="8fd05-146">它也可以使用內容屬性來執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="8fd05-146">It can also do so using context properties.</span></span> <span data-ttu-id="8fd05-147">如需詳細資訊，請參閱[外寄 AS2 訊息的協議解析](../core/agreement-resolution-for-outgoing-as2-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="8fd05-147">For more information, see [Agreement Resolution for Outgoing AS2 Messages](../core/agreement-resolution-for-outgoing-as2-messages.md).</span></span>  
  
4.  <span data-ttu-id="8fd05-148">在**憑證**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="8fd05-148">On the **Certificate** page, do the following:</span></span>  
  
    |<span data-ttu-id="8fd05-149">使用</span><span class="sxs-lookup"><span data-stu-id="8fd05-149">Use this</span></span>|<span data-ttu-id="8fd05-150">動作</span><span class="sxs-lookup"><span data-stu-id="8fd05-150">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="8fd05-151">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="8fd05-151">**Browse**</span></span>|<span data-ttu-id="8fd05-152">按一下即可顯示**選取憑證**對話方塊，其中的本機電腦 」 或 「 其他人憑證存放區設定要套用至訊息傳送至合作對象選取簽章憑證。</span><span class="sxs-lookup"><span data-stu-id="8fd05-152">Click to display the **Select Certificate** dialog box, where you select the signature certificate from the Local Machine or Other People certificate store to apply to messages transmitted to the party.</span></span>|  
    |<span data-ttu-id="8fd05-153">**一般名稱**</span><span class="sxs-lookup"><span data-stu-id="8fd05-153">**Common Name**</span></span>|<span data-ttu-id="8fd05-154">顯示選取憑證的描述。</span><span class="sxs-lookup"><span data-stu-id="8fd05-154">Displays a description of the selected certificate.</span></span>|  
    |<span data-ttu-id="8fd05-155">**憑證指紋**</span><span class="sxs-lookup"><span data-stu-id="8fd05-155">**Thumbprint**</span></span>|<span data-ttu-id="8fd05-156">顯示私密金鑰憑證的指紋，此私密金鑰憑證是用於合作對象解析與簽章驗證。</span><span class="sxs-lookup"><span data-stu-id="8fd05-156">Displays the thumbprint of the private key certificate that is used for party resolution and signature verification.</span></span> <span data-ttu-id="8fd05-157">憑證指紋的格式為 HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH，其中 H 是十六進位數字 (0 到 9 的數字或是 A 到 F 的字母)。</span><span class="sxs-lookup"><span data-stu-id="8fd05-157">The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit (a number from 0 through 9 or a letter from A through F).</span></span>|  
    |<span data-ttu-id="8fd05-158">**移除憑證**</span><span class="sxs-lookup"><span data-stu-id="8fd05-158">**Remove certificate**</span></span>|<span data-ttu-id="8fd05-159">按一下以移除顯示的憑證。</span><span class="sxs-lookup"><span data-stu-id="8fd05-159">Click to remove the displayed certificate.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="8fd05-160">您為合作對象指定的憑證，會用以對來自該合作對象的 AS2 訊息或 MDN 進行簽章驗證。</span><span class="sxs-lookup"><span data-stu-id="8fd05-160">The certificate you specify for a party is used to verify signature of an AS2 message or MDN from the party.</span></span> <span data-ttu-id="8fd05-161">驗證某個合作對象的簽章時所使用的憑證，必須不同於驗證其他合作對象的簽章時所使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="8fd05-161">The certificate used to verify a signature for a party must be unique from the certificates used to verify signatures for other parties.</span></span> <span data-ttu-id="8fd05-162">如需搭配 AS2 訊息使用的憑證的詳細資訊，請參閱[AS2 安全性](../core/as2-security.md)。</span><span class="sxs-lookup"><span data-stu-id="8fd05-162">For more information on certificates used with AS2 messages, see [AS2 Security](../core/as2-security.md).</span></span> <span data-ttu-id="8fd05-163">您可能必須安裝及定義輸出簽署、輸入簽章驗證、輸出加密與輸入解密的憑證。</span><span class="sxs-lookup"><span data-stu-id="8fd05-163">You may need to install and define certificates for outbound signing, inbound signature verification, outbound encryption, and inbound decryption.</span></span>  
  
5.  <span data-ttu-id="8fd05-164">按一下**套用**接受這些屬性，或按一下**確定**來完成組態設定。</span><span class="sxs-lookup"><span data-stu-id="8fd05-164">Click **Apply** to accept the properties, or click **OK** to complete the configuration setting.</span></span> <span data-ttu-id="8fd05-165">任何一項動作都會驗證設定。</span><span class="sxs-lookup"><span data-stu-id="8fd05-165">Either action will validate the settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fd05-166">請參閱</span><span class="sxs-lookup"><span data-stu-id="8fd05-166">See Also</span></span>  
 [<span data-ttu-id="8fd05-167">設定 AS2 屬性</span><span class="sxs-lookup"><span data-stu-id="8fd05-167">Configuring AS2 Properties</span></span>](../core/configuring-as2-properties.md)