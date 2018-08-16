---
title: 如何設定 SSO 票證 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
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
ms.openlocfilehash: edec81ab1fa64ce7b4523771bb2c69b39c00bdfd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018756"
---
# <a name="how-to-configure-the-sso-tickets"></a><span data-ttu-id="0d937-102">如何設定 SSO 票證</span><span class="sxs-lookup"><span data-stu-id="0d937-102">How to Configure the SSO Tickets</span></span>
<span data-ttu-id="0d937-103">您可以使用 [MMC 嵌入式管理單元] 或命令列來控制整個「單一登入」系統的票證行為，包括是否允許票證以及系統是否必須驗證票證。</span><span class="sxs-lookup"><span data-stu-id="0d937-103">You can use the MMC Snap-In or the command line to control ticket behavior for the entire Single Sign-On system, including whether to allow tickets, and whether the system must validate the tickets.</span></span>  
  
 <span data-ttu-id="0d937-104">您可以使用 [Yes]、[No]、[On] 或 [Off] 來表示是否允許和/或驗證票證。</span><span class="sxs-lookup"><span data-stu-id="0d937-104">You can use Yes, No, On, or Off to indicate whether to allow and/or validate tickets.</span></span> <span data-ttu-id="0d937-105">這些字與大小寫無關，不論您的語言設定為何都必須使用。</span><span class="sxs-lookup"><span data-stu-id="0d937-105">These words are case independent, and must be used regardless of your language settings.</span></span>  
  
 <span data-ttu-id="0d937-106">若您在遠端電腦上安裝 SSO 管理功能，則可執行遠端 IssueTicket 作業。</span><span class="sxs-lookup"><span data-stu-id="0d937-106">If you have the SSO Administration feature installed on a remote computer, remote IssueTicket operation can be performed.</span></span> <span data-ttu-id="0d937-107">請注意，SSO 管理模組與執行階段模組 (ENTSSO 服務) 之間的所有流量都會加密。</span><span class="sxs-lookup"><span data-stu-id="0d937-107">Note that all traffic between the SSO Administration module and the Runtime module (ENTSSO service) is encrypted.</span></span>  
  
 <span data-ttu-id="0d937-108">只有在執行應用程式更新 (而不是在建立階段) 時，才可以使用命令列公用程式 ssomanage.exe 在「分支機構應用程式」層級指定票證逾時。</span><span class="sxs-lookup"><span data-stu-id="0d937-108">Using the command line utility, ssomanage.exe, you can specify the ticket timeout at the Affiliate Application level only when an update of the Application is performed,  not at creation time.</span></span>  
  
 <span data-ttu-id="0d937-109">只有 SSO 系統管理員可以在 SSO 系統層級與分支機構應用程式層級中設定票證。</span><span class="sxs-lookup"><span data-stu-id="0d937-109">Only an SSO Administrator can configure tickets at the SSO System level and at the Affiliate Application level.</span></span>  
  
 <span data-ttu-id="0d937-110">若票證在系統層級中停用，則也無法用於分支機構應用程式層級。</span><span class="sxs-lookup"><span data-stu-id="0d937-110">If ticketing is disabled at the system level, it cannot be used at the Affiliate Application level either.</span></span> <span data-ttu-id="0d937-111">可以在系統層級中啟用票證，然後在分支機構應用程式層級中將它停用。</span><span class="sxs-lookup"><span data-stu-id="0d937-111">It is possible to enable tickets at the system level and disable it at the Affiliate Application level.</span></span>  
  
 <span data-ttu-id="0d937-112">若在系統層級中啟用驗證，則分支機構應用程式層級也需要票證驗證。</span><span class="sxs-lookup"><span data-stu-id="0d937-112">If validation is enabled at the system level, validation of tickets are required at the Affiliate Application level as well.</span></span> <span data-ttu-id="0d937-113">可以在系統層級中停用驗證，然後在分支機構應用程式層級中將它啟用。</span><span class="sxs-lookup"><span data-stu-id="0d937-113">It is possible to disable validation at the system level and enable it at the Affiliate Application level.</span></span>  
  
 <span data-ttu-id="0d937-114">若在系統層級與分支機構應用程式層級都指定票證逾時，則在分支機構應用程式層級指定的值會用來決定票證到期時間。</span><span class="sxs-lookup"><span data-stu-id="0d937-114">If Ticket timeout is specified both at the System level and the Affiliate Application level, the one specified at the Affiliate Application level is used to determine the ticket expiry time.</span></span>  
  
 <span data-ttu-id="0d937-115">如需有關票證和票證驗證的詳細資訊，請參閱 < [SSO 票證](../core/sso-tickets.md)。</span><span class="sxs-lookup"><span data-stu-id="0d937-115">For more information about tickets and tickets validation, see [SSO Tickets](../core/sso-tickets.md).</span></span>  
  
### <a name="to-configure-the-enterprise-single-sign-on-tickets-using-the-mmc-snap-in-for-the-affiliate-application"></a><span data-ttu-id="0d937-116">使用 MMC 嵌入式管理單元為分支機構應用程式設定企業單一登入票證</span><span class="sxs-lookup"><span data-stu-id="0d937-116">To configure the Enterprise Single Sign-On tickets using the MMC Snap-In for the Affiliate Application</span></span>  
  
1.  <span data-ttu-id="0d937-117">在 **[開始]** 功能表上，依序按一下 **[所有程式]** 及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。</span><span class="sxs-lookup"><span data-stu-id="0d937-117">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="0d937-118">在 範圍 窗格的 ENTSSO MMC 嵌入式管理單元，依序展開**分支機構應用程式**節點。</span><span class="sxs-lookup"><span data-stu-id="0d937-118">In the scope pane of the ENTSSO MMC Snap-In, expand the **Affiliate Applications** node.</span></span>  
  
3.  <span data-ttu-id="0d937-119">以滑鼠右鍵按一下**分支機構應用程式**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="0d937-119">Right-click **Affiliate Application**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="0d937-120">按一下 [**選項**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0d937-120">Click the **Options** tab.</span></span>  
  
5.  <span data-ttu-id="0d937-121">選取 **允許票證**並依適當情況設定票證逾時。</span><span class="sxs-lookup"><span data-stu-id="0d937-121">Select **Allow Tickets** and configure the ticket timeout as appropriate.</span></span>  
  
### <a name="to-configure-the-enterprise-single-sign-on-system-level-tickets-using-the-command-line"></a><span data-ttu-id="0d937-122">使用命令列設定企業單一登入系統層級票證</span><span class="sxs-lookup"><span data-stu-id="0d937-122">To configure the Enterprise Single Sign-On system-level tickets using the command line</span></span>  
  
1. <span data-ttu-id="0d937-123">在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="0d937-123">On the **Start** menu, click **run**, and then type **cmd**.</span></span>  
  
2. <span data-ttu-id="0d937-124">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="0d937-124">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="0d937-125">預設的安裝目錄*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="0d937-125">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3. <span data-ttu-id="0d937-126">類型 * * ssomanage-tickets\<允許是/否\> *\<驗證是/否\>**<em>，其中 *\<允許是/否\></em>表示，系統是否允許票證以及*\<驗證是/否\>* 指出是否必須進行驗證後贖回票證。</span><span class="sxs-lookup"><span data-stu-id="0d937-126">Type **ssomanage –tickets \<allowed yes/no\> *\<validate yes/no\>**<em>, where *\<allowed yes/no\></em> indicates whether tickets will be allowed or not, and *\<validate yes/no\>* indicates whether tickets will need to be validated after they are redeemed.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="0d937-127">您可以使用 [yes]、[no]、[on] 或 [off] 來表示是否允許和/或驗證票證。</span><span class="sxs-lookup"><span data-stu-id="0d937-127">You can use yes, no, on, or off to indicate whether to allow and/or validate tickets.</span></span> <span data-ttu-id="0d937-128">這些字與大小寫無關，不論您的語言設定為何都必須使用。</span><span class="sxs-lookup"><span data-stu-id="0d937-128">These words are case independent, and must be used regardless of your language settings.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="0d937-129">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="0d937-129">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d937-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d937-130">See Also</span></span>  
 <span data-ttu-id="0d937-131">[了解 SSO](../core/understanding-sso.md) </span><span class="sxs-lookup"><span data-stu-id="0d937-131">[Understanding SSO](../core/understanding-sso.md) </span></span>  
 [<span data-ttu-id="0d937-132">使用 SSO</span><span class="sxs-lookup"><span data-stu-id="0d937-132">Using SSO</span></span>](../core/using-sso.md)