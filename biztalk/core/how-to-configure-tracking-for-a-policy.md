---
title: 如何設定原則的追蹤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- policies, tracking
- HAT, policies
- managing [policies], tracking
- tracking, policies
- managing [policies], configuring
- policies, configuring
- configuring [HAT tracking], policies
- tracking, configuring
ms.assetid: f126e541-c183-4544-8b9d-ca07d2af303e
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f92e8555c0d644411c165284dd734eb94e6569e9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980407"
---
# <a name="how-to-configure-tracking-for-a-policy"></a><span data-ttu-id="37e1f-102">如何設定原則的追蹤</span><span class="sxs-lookup"><span data-stu-id="37e1f-102">How to Configure Tracking for a Policy</span></span>
<span data-ttu-id="37e1f-103">本主題描述如何使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定原則的追蹤。</span><span class="sxs-lookup"><span data-stu-id="37e1f-103">This topic describes how to use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administration console to configure tracking for a policy.</span></span> <span data-ttu-id="37e1f-104">您可以在管理主控台 [群組中樞] 頁面的查詢檢視中選取選項，以檢視執行個體資料、條件結果、動作以及議程更新。</span><span class="sxs-lookup"><span data-stu-id="37e1f-104">You can select options to view instance data, results of conditions, actions, and agenda updates in the query views of the administration console Group Hub page.</span></span>  
  
 <span data-ttu-id="37e1f-105">如需有關建立和使用查詢的詳細資訊，請參閱 <<c0> [ 使用 BizTalk Server 管理主控台](../core/using-the-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="37e1f-105">For more information about creating and using queries, see [Using the BizTalk Server Administration Console](../core/using-the-biztalk-server-administration-console.md).</span></span> <span data-ttu-id="37e1f-106">如需詳細資訊追蹤功能的訊息和服務執行個體的相關[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 檢視追蹤的訊息和執行個體資料](../core/viewing-tracked-message-and-instance-data.md)。</span><span class="sxs-lookup"><span data-stu-id="37e1f-106">For more information about the message and service instance  tracking features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="37e1f-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="37e1f-107">Prerequisites</span></span>  
 <span data-ttu-id="37e1f-108">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="37e1f-108">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="37e1f-109">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="37e1f-109">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-configure-tracking-for-a-policy"></a><span data-ttu-id="37e1f-110">設定原則的追蹤</span><span class="sxs-lookup"><span data-stu-id="37e1f-110">To configure tracking for a policy</span></span>  
  
1. <span data-ttu-id="37e1f-111">按一下 **開始**，按一下**程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="37e1f-111">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="37e1f-112">在主控台樹狀結構中，展開您要為原則設定追蹤的 BizTalk 群組與 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="37e1f-112">In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure tracking for a policy.</span></span>  
  
3. <span data-ttu-id="37e1f-113">按一下 **原則**，以滑鼠右鍵按一下原則，按一下**屬性**，然後按一下**追蹤**。</span><span class="sxs-lookup"><span data-stu-id="37e1f-113">Click **Policies**, right-click the policy, click **Properties**, and then click **Tracking**.</span></span>  
  
4. <span data-ttu-id="37e1f-114">下表中所述，選取您要的追蹤選項，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="37e1f-114">Select the tracking options you want, as described in the following table, and then click **OK**.</span></span>  
  
   |<span data-ttu-id="37e1f-115">使用</span><span class="sxs-lookup"><span data-stu-id="37e1f-115">Use this</span></span>|<span data-ttu-id="37e1f-116">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="37e1f-116">To do this</span></span>|  
   |--------------|----------------|  
   |<span data-ttu-id="37e1f-117">**快速活動**</span><span class="sxs-lookup"><span data-stu-id="37e1f-117">**Fast activity**</span></span>|<span data-ttu-id="37e1f-118">選取此核取方塊，追蹤原則運作所在之處的執行個體資料。</span><span class="sxs-lookup"><span data-stu-id="37e1f-118">Select this check box to track the instance data on which the policy operates.</span></span>|  
   |<span data-ttu-id="37e1f-119">**條件評估**</span><span class="sxs-lookup"><span data-stu-id="37e1f-119">**Condition evaluation**</span></span>|<span data-ttu-id="37e1f-120">選取此核取方塊，追蹤所選取原則的條件結果值是 True 或 False。</span><span class="sxs-lookup"><span data-stu-id="37e1f-120">Select this check box to track the true/false results of conditions in the selected policy.</span></span>|  
   |<span data-ttu-id="37e1f-121">**規則引發**</span><span class="sxs-lookup"><span data-stu-id="37e1f-121">**Rule firings**</span></span>|<span data-ttu-id="37e1f-122">選取此核取方塊，追蹤原則所啟動的動作。</span><span class="sxs-lookup"><span data-stu-id="37e1f-122">Select this check box to track the actions started as a result of the policy.</span></span>|  
   |<span data-ttu-id="37e1f-123">**議程更新**</span><span class="sxs-lookup"><span data-stu-id="37e1f-123">**Agenda updates**</span></span>|<span data-ttu-id="37e1f-124">選取此核取方塊，追蹤議程的更新。</span><span class="sxs-lookup"><span data-stu-id="37e1f-124">Select this check box to track updates to the agenda.</span></span> <span data-ttu-id="37e1f-125">議程包含一份值為 "True" 且需要引發的動作清單。</span><span class="sxs-lookup"><span data-stu-id="37e1f-125">The agenda contains a list of actions that are "true" and need to fire.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="37e1f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37e1f-126">See Also</span></span>  
 [<span data-ttu-id="37e1f-127">管理原則</span><span class="sxs-lookup"><span data-stu-id="37e1f-127">Managing Policies</span></span>](../core/managing-policies.md)