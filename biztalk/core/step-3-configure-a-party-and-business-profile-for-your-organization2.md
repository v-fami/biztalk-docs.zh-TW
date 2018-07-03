---
title: 步驟 3： 設定合作對象與商務設定檔為您 Organization2 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 024d1ec7-237a-43cb-8159-90f9c71a670e
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 809c8bd4080a7d2ddf14d9c84e98c050e198e6cd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000359"
---
# <a name="step-3-configure-a-party-and-business-profile-for-your-organization"></a><span data-ttu-id="15b02-102">步驟 3： 為您的組織設定合作對象與商務設定檔</span><span class="sxs-lookup"><span data-stu-id="15b02-102">Step 3: Configure a Party and Business Profile for Your Organization</span></span>
<span data-ttu-id="15b02-103">![步驟 11-3](../core/media/tut-step3-of-11.gif "Tut_Step3_of_11")</span><span class="sxs-lookup"><span data-stu-id="15b02-103">![Step 3 of 11](../core/media/tut-step3-of-11.gif "Tut_Step3_of_11")</span></span>  
  
 <span data-ttu-id="15b02-104">在此步驟中，您要為組織設定合作對象與商務設定檔，以便接收來自交易夥伴的 864 訊息，並傳回 997 通知訊息與非同步 MDN。</span><span class="sxs-lookup"><span data-stu-id="15b02-104">In this step, you configure a party and a business profile for your organization to receive an 864 message from your trading partner and return a 997 acknowledgment message and an asynchronous MDN.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="15b02-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="15b02-105">Prerequisites</span></span>  
 <span data-ttu-id="15b02-106">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="15b02-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-configure-a-party-and-business-profile-for-your-organization"></a><span data-ttu-id="15b02-107">若要設定組織的合作對象與商務設定檔</span><span class="sxs-lookup"><span data-stu-id="15b02-107">To configure a party and business profile for your organization</span></span>  
  
1. <span data-ttu-id="15b02-108">開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下**開始**、 指向**所有程式**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下 [ **BizTalk Server 管理]**.</span><span class="sxs-lookup"><span data-stu-id="15b02-108">Open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console by clicking **Start**, pointing to **All Programs**, pointing to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then clicking **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="15b02-109">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，然後展開**BizTalk 群組**。</span><span class="sxs-lookup"><span data-stu-id="15b02-109">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then expand **BizTalk Group**.</span></span> <span data-ttu-id="15b02-110">以滑鼠右鍵按一下**合作對象**，指向**新增**，然後按一下**合作對象**。</span><span class="sxs-lookup"><span data-stu-id="15b02-110">Right-click **Parties**, point to **New**, and then click **Party**.</span></span>  
  
3. <span data-ttu-id="15b02-111">在 **合作對象屬性**對話方塊方塊中，輸入**Contoso**中**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="15b02-111">In the **Party Properties** dialog box, enter **Contoso** in the **Name** field.</span></span>  
  
4. <span data-ttu-id="15b02-112">選取 **本機 BizTalk 可處理支援此合作對象傳送訊息的合作對象所接收的訊息**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="15b02-112">Select the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box.</span></span> <span data-ttu-id="15b02-113">選取核取方塊，即可指定合作對象 (在此情況下， **Contoso**) 也裝載 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="15b02-113">By selecting the check box you specify that the party (in this case, **Contoso**) also hosts BizTalk Server.</span></span>  
  
5. <span data-ttu-id="15b02-114">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="15b02-114">Click **OK**.</span></span>  
  
6. <span data-ttu-id="15b02-115">以滑鼠右鍵按一下合作對象名稱、 指向**的新**，然後按一下**商務設定檔**。</span><span class="sxs-lookup"><span data-stu-id="15b02-115">Right-click the party name, point to **New**, and then click **Business Profile**.</span></span>  
  
7. <span data-ttu-id="15b02-116">在 **設定檔屬性**對話方塊的 **一般**頁面上，輸入`Contoso_Profile`中**名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="15b02-116">In the **Profile Properties** dialog box, on the **General** page, enter `Contoso_Profile` in the **Name** text box.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="15b02-117">當您建立合作對象時，會同時建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="15b02-117">When you create a party, a profile is also created.</span></span> <span data-ttu-id="15b02-118">您可以重新命名再使用該設定檔，而不需建立新設定檔。</span><span class="sxs-lookup"><span data-stu-id="15b02-118">You can rename and use that profile instead of creating a new one.</span></span> <span data-ttu-id="15b02-119">若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="15b02-119">To rename a profile, right-click the profile and select **Properties**.</span></span> <span data-ttu-id="15b02-120">在 **一般**頁面上，指定設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="15b02-120">In the **General** page, specify a name for the profile.</span></span>  
  
8. <span data-ttu-id="15b02-121">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="15b02-121">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="15b02-122">後續步驟</span><span class="sxs-lookup"><span data-stu-id="15b02-122">Next Steps</span></span>  
 <span data-ttu-id="15b02-123">您的夥伴組織設定合作對象與商務設定檔 (**Fabrikam**) 中所述[步驟 4： 為您的交易夥伴設定合作對象和商務設定檔](../core/step-4-configure-a-party-and-business-profile-for-your-trading-partner2.md)。</span><span class="sxs-lookup"><span data-stu-id="15b02-123">You configure a party and business profile for your partner organization (**Fabrikam**), as described in [Step 4: Configure a Party and Business Profile for Your Trading Partner](../core/step-4-configure-a-party-and-business-profile-for-your-trading-partner2.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15b02-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15b02-124">See Also</span></span>  
 [<span data-ttu-id="15b02-125">設定 EDI 屬性</span><span class="sxs-lookup"><span data-stu-id="15b02-125">Configuring EDI Properties</span></span>](../core/configuring-edi-properties.md)