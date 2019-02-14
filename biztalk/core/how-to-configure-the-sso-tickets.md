---
title: 設定 SSO 票證 |Microsoft Docs
description: 使用 SSO 管理或命令列來允許及驗證企業單一登入票證系統層級，以及在 BizTalk Server 中的分支機構應用程式。
ms.custom: ''
ms.date: 01/08/2019
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [SSO], configuring tickets
- SSO, tickets
- tickets [SSO], configuring
ms.assetid: 32f0384b-ac79-4cce-b3f5-f4f8a73a673a
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3abac3a0d527c6834105db8fd1c74fd934fd821d
ms.sourcegitcommit: 41947648c73d437a201b2190307e0270d61e037a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56087930"
---
# <a name="configure-the-sso-tickets-in-biztalk-server"></a><span data-ttu-id="e8725-103">在 BizTalk Server 中設定 SSO 票證</span><span class="sxs-lookup"><span data-stu-id="e8725-103">Configure the SSO Tickets in BizTalk Server</span></span>
<span data-ttu-id="e8725-104">針對整個單一登入系統，您可以使用企業單一登入 (SSO) 管理的 MMC 或命令列，以控制票證行為。</span><span class="sxs-lookup"><span data-stu-id="e8725-104">You can use Enterprise Single Sign-On (SSO) Administration MMC or the command line to control ticket behavior for the entire single sign-on system.</span></span> <span data-ttu-id="e8725-105">使用此工具，您就可以允許票證，並驗證 SSO 票證。</span><span class="sxs-lookup"><span data-stu-id="e8725-105">Using this tools, you can allow tickets and validate SSO tickets.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="e8725-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="e8725-106">Before you begin</span></span>

- <span data-ttu-id="e8725-107">如果遠端電腦上安裝 SSO 管理，您可以執行遠端[IssueTicket](https://docs.microsoft.com/biztalk/core/technical-reference/issoticket-issueticket-method)作業。</span><span class="sxs-lookup"><span data-stu-id="e8725-107">If SSO Administration is installed on a remote computer, you can run a remote [IssueTicket](https://docs.microsoft.com/biztalk/core/technical-reference/issoticket-issueticket-method) operation.</span></span> <span data-ttu-id="e8725-108">SSO 管理模組和執行階段模組 （ENTSSO 服務） 之間的所有流量都會都加密。</span><span class="sxs-lookup"><span data-stu-id="e8725-108">All traffic between the SSO Administration module and the Runtime module (ENTSSO service) is encrypted.</span></span>  
  
- <span data-ttu-id="e8725-109">使用 ssomanage.exe 命令列公用程式，您可以輸入分支機構應用程式層級的票證逾時。</span><span class="sxs-lookup"><span data-stu-id="e8725-109">Using the ssomanage.exe command line utility, you can enter the ticket timeout at the Affiliate Application level.</span></span> <span data-ttu-id="e8725-110">只有在進行應用程式的更新時，會建立應用程式時，不時，您可以這麼做。</span><span class="sxs-lookup"><span data-stu-id="e8725-110">You can do this only when an update of the application is made, not when the application is created.</span></span>
  
- <span data-ttu-id="e8725-111">在 SSO 系統層級與分支機構應用程式層級，只有 SSO 系統管理員群組的使用者，才可以設定票證。</span><span class="sxs-lookup"><span data-stu-id="e8725-111">Only users in the SSO Administrator group can configure tickets at the SSO system-level and at the Affiliate Application level.</span></span>  
  
- <span data-ttu-id="e8725-112">如果在系統層級停用票證，它不能在分支機構應用程式層級。</span><span class="sxs-lookup"><span data-stu-id="e8725-112">If ticketing is disabled at the system-level, it can't be used at the Affiliate Application level.</span></span> <span data-ttu-id="e8725-113">您可在系統層級中啟用票證和分支機構應用程式層級停用它們。</span><span class="sxs-lookup"><span data-stu-id="e8725-113">It's possible to enable tickets at the system level, and disable them at the Affiliate Application level.</span></span>  
  
- <span data-ttu-id="e8725-114">如果驗證已啟用在系統層級，則必須驗證票證，分支機構應用程式層級。</span><span class="sxs-lookup"><span data-stu-id="e8725-114">If validation is enabled at the system-level, tickets must be validated at the Affiliate Application level.</span></span> <span data-ttu-id="e8725-115">可以停用在系統層級的驗證，並啟用分支機構應用程式層級。</span><span class="sxs-lookup"><span data-stu-id="e8725-115">It's possible to disable validation at the system-level, and enable it at the Affiliate Application level.</span></span>  
  
- <span data-ttu-id="e8725-116">如果您輸入票證逾時的系統層級和分支機構應用程式層級，輸入分支機構應用程式層級會決定票證到期時間。</span><span class="sxs-lookup"><span data-stu-id="e8725-116">If ticket timeout is entered at the system-level and the Affiliate Application level, the one entered at the Affiliate Application level determines the ticket expiration time.</span></span>  
  
<span data-ttu-id="e8725-117">如需有關票證和票證驗證的詳細資訊，請參閱 < [SSO 票證](../core/sso-tickets.md)。</span><span class="sxs-lookup"><span data-stu-id="e8725-117">For more information about tickets and tickets validation, see [SSO Tickets](../core/sso-tickets.md).</span></span>  
  
## <a name="allow-affiliate-application-tickets-using-sso-administration"></a><span data-ttu-id="e8725-118">允許使用 SSO 管理分支機構應用程式票證</span><span class="sxs-lookup"><span data-stu-id="e8725-118">Allow Affiliate Application tickets using SSO Administration</span></span>  
  
1.  <span data-ttu-id="e8725-119">從**開始**功能表上，選取**所有程式** > **Microsoft 企業單一登入** > **SSO 管理**.</span><span class="sxs-lookup"><span data-stu-id="e8725-119">From the **Start** menu, select **All Programs** > **Microsoft Enterprise Single Sign-On** > **SSO Administration**.</span></span>
  
2.  <span data-ttu-id="e8725-120">在 範圍 窗格的 ENTSSO MMC 嵌入式管理單元，依序展開**分支機構應用程式**節點。</span><span class="sxs-lookup"><span data-stu-id="e8725-120">In the scope pane of the ENTSSO MMC Snap-In, expand the **Affiliate Applications** node.</span></span>  
  
3.  <span data-ttu-id="e8725-121">以滑鼠右鍵按一下**分支機構應用程式** > **屬性**。</span><span class="sxs-lookup"><span data-stu-id="e8725-121">Right-click **Affiliate Application** > **Properties**.</span></span>  
  
4.  <span data-ttu-id="e8725-122">選擇**選項** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e8725-122">Choose the **Options** tab.</span></span>  
  
5.  <span data-ttu-id="e8725-123">選取 **允許票證**並輸入您想要的票證逾時。</span><span class="sxs-lookup"><span data-stu-id="e8725-123">Select **Allow Tickets** and enter the ticket timeout you want.</span></span>  
  
## <a name="allow-and-validate-sso-system-level-tickets-using-the-command-line"></a><span data-ttu-id="e8725-124">允許和驗證使用命令列的 SSO 系統層級票證</span><span class="sxs-lookup"><span data-stu-id="e8725-124">Allow and validate SSO system-level tickets using the command line</span></span>  
  
1. <span data-ttu-id="e8725-125">開啟命令提示字元 ([開始] 功能表 > 型別**命令提示字元**> 選取**命令提示字元**)。</span><span class="sxs-lookup"><span data-stu-id="e8725-125">Open a command prompt (Start menu > type **command prompt** > select **Command Prompt**).</span></span>

    > [!TIP]
    >  <span data-ttu-id="e8725-126">在系統上可支援使用者帳戶控制 (UAC)，您可能需要系統管理權限開啟命令提示字元 (以滑鼠右鍵按一下**命令提示字元** > **系統管理員身分執行**)。</span><span class="sxs-lookup"><span data-stu-id="e8725-126">On a system that supports User Account Control (UAC), you may need to open the command prompt with Administrative privileges (right-click **Command Prompt** > **Run as administrator**).</span></span>
  
2. <span data-ttu-id="e8725-127">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="e8725-127">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="e8725-128">預設安裝目錄是`\Program Files\Common Files\Enterprise Single Sign-On`。</span><span class="sxs-lookup"><span data-stu-id="e8725-128">The default installation directory is `\Program Files\Common Files\Enterprise Single Sign-On`.</span></span> <span data-ttu-id="e8725-129">例如，輸入：</span><span class="sxs-lookup"><span data-stu-id="e8725-129">For example, enter:</span></span> 

    `cd C:\Program Files\Common Files\Enterprise Single Sign-On`
  
3. <span data-ttu-id="e8725-130">型別`ssomanage -tickets <allowed yes/no> <validate yes/no>`，其中 *\<允許是/否\>* 指出，是否允許票證以及 *\<驗證是/否\>* 指出是否需要它們正在兌換之後驗證票證。</span><span class="sxs-lookup"><span data-stu-id="e8725-130">Type `ssomanage -tickets <allowed yes/no> <validate yes/no>`, where *\<allowed yes/no\>* indicates whether tickets are allowed or not, and *\<validate yes/no\>* indicates whether tickets need to be validated after they're redeemed.</span></span>  
  
    <span data-ttu-id="e8725-131">您可以使用`yes`， `no`， `on`，或`off`允許和/或驗證票證。</span><span class="sxs-lookup"><span data-stu-id="e8725-131">You can use `yes`, `no`, `on`, or `off` to allow and/or validate tickets.</span></span> <span data-ttu-id="e8725-132">這些字與大小寫無關，不論您的語言設定為何都必須使用。</span><span class="sxs-lookup"><span data-stu-id="e8725-132">These words are case independent, and must be used regardless of your language settings.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e8725-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8725-133">See Also</span></span>

<span data-ttu-id="e8725-134">[了解 SSO](../core/understanding-sso.md) </span><span class="sxs-lookup"><span data-stu-id="e8725-134">[Understanding SSO](../core/understanding-sso.md) </span></span>  
[<span data-ttu-id="e8725-135">使用 SSO</span><span class="sxs-lookup"><span data-stu-id="e8725-135">Using SSO</span></span>](../core/using-sso.md)
