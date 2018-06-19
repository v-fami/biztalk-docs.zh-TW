---
title: 步驟 4： 設定合作對象與商務設定檔為您的交易夥伴 2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ce07a1a6-4d5d-44ea-b1cb-04d7ae85747f
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f775a720c6dcc42a3edd22154843a4a9118cc90e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278118"
---
# <a name="step-4-configure-a-party-and-business-profile-for-your-trading-partner"></a><span data-ttu-id="24d42-102">步驟 4： 為交易夥伴設定合作對象與商務設定檔</span><span class="sxs-lookup"><span data-stu-id="24d42-102">Step 4: Configure a Party and Business Profile for Your Trading Partner</span></span>
<span data-ttu-id="24d42-103">![步驟 11-4](../core/media/tut-step4-of-11.gif "Tut_Step4_of_11")</span><span class="sxs-lookup"><span data-stu-id="24d42-103">![Step 4 of 11](../core/media/tut-step4-of-11.gif "Tut_Step4_of_11")</span></span>  
  
 <span data-ttu-id="24d42-104">在此步驟中，您會設定合作對象與商務設定檔，以便讓交易夥伴 Fabrikam 傳送 864 訊息至您的組織，並收到傳回的 997 通知訊息與非同步 MDN。</span><span class="sxs-lookup"><span data-stu-id="24d42-104">In this step, you configure a party and business profile for your trading partner Fabrikam to send an 864 message to your organization and receive a 997 acknowledgment message and an asynchronous MDN in return.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="24d42-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="24d42-105">Prerequisites</span></span>  
 <span data-ttu-id="24d42-106">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="24d42-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-configure-a-party-and-business-profile-for-your-trading-partner"></a><span data-ttu-id="24d42-107">若要為交易夥伴設定合作對象與商務設定檔</span><span class="sxs-lookup"><span data-stu-id="24d42-107">To configure a party and business profile for your trading partner</span></span>  
  
1.  <span data-ttu-id="24d42-108">開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台按一下**啟動**、 指向**所有程式**、 指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**.</span><span class="sxs-lookup"><span data-stu-id="24d42-108">Open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console by clicking **Start**, pointing to **All Programs**, pointing to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then clicking **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="24d42-109">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開  [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，然後展開**BizTalk 群組**。</span><span class="sxs-lookup"><span data-stu-id="24d42-109">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then expand **BizTalk Group**.</span></span> <span data-ttu-id="24d42-110">以滑鼠右鍵按一下**合作對象**，指向 **新增**，然後按一下 **合作對象**。</span><span class="sxs-lookup"><span data-stu-id="24d42-110">Right-click **Parties**, point to **New**, and then click **Party**.</span></span>  
  
3.  <span data-ttu-id="24d42-111">在**合作對象屬性**對話方塊方塊中，輸入**Fabrikam**中**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="24d42-111">In the **Party Properties** dialog box, enter **Fabrikam** in the **Name** field.</span></span>  
  
4.  <span data-ttu-id="24d42-112">清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="24d42-112">Clear the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box.</span></span> <span data-ttu-id="24d42-113">清除核取方塊，即可指定合作對象 (在此情況下， **Fabrikam**) 未裝載 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="24d42-113">By clearing the check box you specify that the party (in this case, **Fabrikam**) does not host BizTalk Server.</span></span>  
  
5.  <span data-ttu-id="24d42-114">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="24d42-114">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="24d42-115">以滑鼠右鍵按一下合作對象名稱，指向**新增**，然後按一下 **商務設定檔**。</span><span class="sxs-lookup"><span data-stu-id="24d42-115">Right-click the party name, point to **New**, and then click **Business Profile**.</span></span>  
  
7.  <span data-ttu-id="24d42-116">在**設定檔屬性**對話方塊**一般**頁面上，輸入`Fabrikam_Profile`中**名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="24d42-116">In the **Profile Properties** dialog box, on the **General** page, enter `Fabrikam_Profile` in the **Name** text box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="24d42-117">當您建立合作對象時，會同時建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="24d42-117">When you create a party, a profile is also created.</span></span> <span data-ttu-id="24d42-118">您可以重新命名再使用該設定檔，而不需建立新設定檔。</span><span class="sxs-lookup"><span data-stu-id="24d42-118">You can rename and use that profile instead of creating a new one.</span></span> <span data-ttu-id="24d42-119">若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="24d42-119">To rename a profile, right-click the profile and select **Properties**.</span></span> <span data-ttu-id="24d42-120">在**一般**頁面上，指定設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="24d42-120">In the **General** page, specify a name for the profile.</span></span>  
  
8.  <span data-ttu-id="24d42-121">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="24d42-121">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="24d42-122">後續步驟</span><span class="sxs-lookup"><span data-stu-id="24d42-122">Next Steps</span></span>  
 <span data-ttu-id="24d42-123">您設定 BTS ISAPI 篩選器和 Fabrikam 和 Contoso 網頁中[步驟 5： 設定交易夥伴網頁](../core/step-5-configure-the-trading-partner-web-pages.md)。</span><span class="sxs-lookup"><span data-stu-id="24d42-123">You configure the BTS ISAPI filter and the Fabrikam and Contoso Web pages in [Step 5: Configure the Trading Partner Web Pages](../core/step-5-configure-the-trading-partner-web-pages.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24d42-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24d42-124">See Also</span></span>  
 [<span data-ttu-id="24d42-125">設定 EDI 屬性</span><span class="sxs-lookup"><span data-stu-id="24d42-125">Configuring EDI Properties</span></span>](../core/configuring-edi-properties.md)