---
title: 設定簽章憑證 (AS2) |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8539e210-1656-4fff-b026-36b81689061f
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32a52962976c2db62de902906f53f5c270e2c7c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233262"
---
# <a name="configuring-signature-certificates-as2"></a><span data-ttu-id="b96b9-102">設定簽章憑證 (AS2)</span><span class="sxs-lookup"><span data-stu-id="b96b9-102">Configuring Signature Certificates (AS2)</span></span>
<span data-ttu-id="b96b9-103">在此頁面的設定中，您可以指定當外送訊息和 MDN 解析為此協議時，要用於簽署這些外送訊息和 MDN 的憑證。</span><span class="sxs-lookup"><span data-stu-id="b96b9-103">As part of the settings on this page, you can specify the certificates to be used for signing all outgoing messages and MDN that resolve to this agreement.</span></span> <span data-ttu-id="b96b9-104">此頁面上的設定會覆寫 BizTalk 群組屬性中提供的憑證設定。</span><span class="sxs-lookup"><span data-stu-id="b96b9-104">The settings on this page override the certificate settings provided as part of the BizTalk Group properties.</span></span> <span data-ttu-id="b96b9-105">如需有關如何使用憑證的詳細資訊，請參閱[Configuring certificates for AS2 憑證](../core/configuring-certificates-for-as2.md)。</span><span class="sxs-lookup"><span data-stu-id="b96b9-105">For more information on how certificates are used, see [Configuring Certificates for AS2](../core/configuring-certificates-for-as2.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b96b9-106">任何屬性已停用此頁面上即使您清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。</span><span class="sxs-lookup"><span data-stu-id="b96b9-106">No properties are disabled on this page even if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b96b9-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="b96b9-107">Prerequisites</span></span>  
 <span data-ttu-id="b96b9-108">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="b96b9-108">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-agreement-level-signature-certificate"></a><span data-ttu-id="b96b9-109">若要設定協議層級的簽章憑證</span><span class="sxs-lookup"><span data-stu-id="b96b9-109">To configure agreement-level signature certificate</span></span>  
  
1.  <span data-ttu-id="b96b9-110">建立 AS2 協議中所述[設定一般設定 (AS2)](../core/configuring-general-settings-as2.md)。</span><span class="sxs-lookup"><span data-stu-id="b96b9-110">Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md).</span></span> <span data-ttu-id="b96b9-111">若要更新現有的 AS2 協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="b96b9-111">To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="b96b9-112">在單向協議索引標籤上，按一下 **簽章憑證**。</span><span class="sxs-lookup"><span data-stu-id="b96b9-112">On a one-way agreement tab, click **Signature Certificates**.</span></span>  
  
3.  <span data-ttu-id="b96b9-113">選取**覆寫群組簽章憑證**使用此頁面中的憑證簽署外寄 AS2 訊息和 MDN 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="b96b9-113">Select the **Override group signing certificate** check box to use the certificate provided in this page for signing outgoing AS2 messages and MDN.</span></span>  
  
4.  <span data-ttu-id="b96b9-114">按一下**瀏覽**顯示**選取憑證**對話方塊中，選取要套用此合作對象所傳輸訊息的簽章憑證的位置。</span><span class="sxs-lookup"><span data-stu-id="b96b9-114">Click **Browse** to display the **Select Certificate** dialog box, where you select the signature certificate to apply to messages transmitted by this party.</span></span>  
  
5.  <span data-ttu-id="b96b9-115">**一般名稱**文字方塊會顯示所選憑證的描述。</span><span class="sxs-lookup"><span data-stu-id="b96b9-115">The **Common Name** text box displays a description of the selected certificate.</span></span>  
  
6.  <span data-ttu-id="b96b9-116">**指紋**文字方塊會顯示憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="b96b9-116">The **Thumbprint** text box displays the thumbprint of certificate.</span></span> <span data-ttu-id="b96b9-117">憑證指紋的格式為 HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH，其中 H 是十六進位數字 (0 到 9 的數字或是 A 到 F 的字母)。</span><span class="sxs-lookup"><span data-stu-id="b96b9-117">The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit (a number from 0 through 9 or a letter from A through F).</span></span>  
  
7.  <span data-ttu-id="b96b9-118">按一下**移除憑證**若要移除選取的憑證。</span><span class="sxs-lookup"><span data-stu-id="b96b9-118">Click **Remove Certificate** to remove the selected certificate.</span></span>  
  
8.  <span data-ttu-id="b96b9-119">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b96b9-119">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b96b9-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b96b9-120">See Also</span></span>  
 [<span data-ttu-id="b96b9-121">設定 AS2 協議屬性</span><span class="sxs-lookup"><span data-stu-id="b96b9-121">Configuring AS2 Agreement Properties</span></span>](../core/configuring-as2-agreement-properties.md)