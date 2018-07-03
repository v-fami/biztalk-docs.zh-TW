---
title: 如何設定協調流程的追蹤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, tracking
- orchestrations, HAT
- managing [orchestrations], tracking
- configuring [HAT tracking], orchestrations
- tracking, orchestrations
- HAT, orchestrations
ms.assetid: 8f5ed525-11f8-4bef-95c4-cfe9c971b663
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c64d7521bf6d65458f66bb0ef06d08421edf1b4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013191"
---
# <a name="how-to-configure-tracking-for-an-orchestration"></a><span data-ttu-id="c7572-102">如何設定協調流程的追蹤</span><span class="sxs-lookup"><span data-stu-id="c7572-102">How to Configure Tracking for an Orchestration</span></span>
<span data-ttu-id="c7572-103">本主題描述如何使用 BizTalk Server 管理主控台，以設定協調流程的追蹤。</span><span class="sxs-lookup"><span data-stu-id="c7572-103">This topic describes how to use the BizTalk Server Administration console to configure tracking for an orchestration.</span></span>  
  
 <span data-ttu-id="c7572-104">如需有關建立和使用查詢的詳細資訊，請參閱 <<c0> [ 使用 BizTalk Server 管理主控台](../core/using-the-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="c7572-104">For more information about creating and using queries, see [Using the BizTalk Server Administration Console](../core/using-the-biztalk-server-administration-console.md).</span></span> <span data-ttu-id="c7572-105">如需追蹤功能的詳細資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 檢視追蹤的訊息和執行個體資料](../core/viewing-tracked-message-and-instance-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c7572-105">For more information about the tracking features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c7572-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="c7572-106">Prerequisites</span></span>  
 <span data-ttu-id="c7572-107">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="c7572-107">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="c7572-108">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="c7572-108">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-configure-tracking-for-an-orchestration"></a><span data-ttu-id="c7572-109">設定協調流程的追蹤</span><span class="sxs-lookup"><span data-stu-id="c7572-109">To configure tracking for an orchestration</span></span>  
  
1. <span data-ttu-id="c7572-110">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="c7572-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="c7572-111">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 BizTalk 群組、 展開**應用程式**，然後展開包含您要設定追蹤之協調的流程的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c7572-111">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration for which you want to configure tracking.</span></span>  
  
3. <span data-ttu-id="c7572-112">按一下 **協調流程**，以滑鼠右鍵按一下您要設定追蹤，然後按一下協調的流程**屬性**。</span><span class="sxs-lookup"><span data-stu-id="c7572-112">Click **Orchestrations**, right-click the orchestration for which you want to configure tracking, and then click **Properties**.</span></span>  
  
4. <span data-ttu-id="c7572-113">按一下 **追蹤**索引標籤上，選取您要的追蹤選項下, 表中所述，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c7572-113">Click the **Tracking** tab, select the tracking options you want, as described in the following table, and then click **OK**.</span></span>  
  
   |<span data-ttu-id="c7572-114">選項</span><span class="sxs-lookup"><span data-stu-id="c7572-114">Option</span></span>|<span data-ttu-id="c7572-115">描述</span><span class="sxs-lookup"><span data-stu-id="c7572-115">Description</span></span>|  
   |------------|-----------------|  
   |<span data-ttu-id="c7572-116">**追蹤事件-協調流程開始和結束**</span><span class="sxs-lookup"><span data-stu-id="c7572-116">**Track Events - Orchestration start and end**</span></span>|<span data-ttu-id="c7572-117">選取此核取方塊，在處理整個商務程序之前及之後追蹤協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="c7572-117">Select this check box to track the orchestration instance before and after processing of the entire business process.</span></span> <span data-ttu-id="c7572-118">協調流程追蹤可讓您查看的執行個體中追蹤查詢結果檢視。</span><span class="sxs-lookup"><span data-stu-id="c7572-118">Orchestration tracking enables you to see the instances in the tracking query result views.</span></span>|  
   |<span data-ttu-id="c7572-119">**追蹤事件-訊息傳送與接收**</span><span class="sxs-lookup"><span data-stu-id="c7572-119">**Track Events - Message send and receive**</span></span>|<span data-ttu-id="c7572-120">選取此核取方塊以追蹤訊息傳送與接收事件。</span><span class="sxs-lookup"><span data-stu-id="c7572-120">Select this check box to track message send and receive events.</span></span> <span data-ttu-id="c7572-121">此核取方塊才會提供您所選取**協調流程開始和結束**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c7572-121">This check box is available only if you select the **Orchestration start and end** check box.</span></span>|  
   |<span data-ttu-id="c7572-122">**追蹤事件-流程化開始與結束**</span><span class="sxs-lookup"><span data-stu-id="c7572-122">**Track Events - Shape start and end**</span></span>|<span data-ttu-id="c7572-123">當您需要在「協調流程偵錯工具」中偵錯協調流程執行個體時，請選取此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c7572-123">Select this check box when you need to debug orchestration instances in the Orchestration Debugger.</span></span> <span data-ttu-id="c7572-124">當您選取此核取方塊，會填入此「協調流程偵錯工具」中的事件清單。</span><span class="sxs-lookup"><span data-stu-id="c7572-124">When this check box is selected, the event list in the Orchestration Debugger is populated.</span></span> <span data-ttu-id="c7572-125">此核取方塊才會提供您所選取**協調流程開始和結束**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c7572-125">This check box is available only if you select the **Orchestration start and end** check box.</span></span>|  
   |<span data-ttu-id="c7572-126">**追蹤訊息內文-協調流程處理之前**</span><span class="sxs-lookup"><span data-stu-id="c7572-126">**Track Message Bodies - Before orchestration processing**</span></span>|<span data-ttu-id="c7572-127">選取此核取方塊以在協調流程執行個體處理之前儲存和追蹤實際訊息內容。</span><span class="sxs-lookup"><span data-stu-id="c7572-127">Select this check box to save and track the actual message content prior to processing by the orchestration instance.</span></span> <span data-ttu-id="c7572-128">此核取方塊才會提供您所選取**訊息傳送與接收**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c7572-128">This check box is available only if you select the **Message send and receive** check box.</span></span>|  
   |<span data-ttu-id="c7572-129">**追蹤訊息內文-協調流程處理之後**</span><span class="sxs-lookup"><span data-stu-id="c7572-129">**Track Message Bodies - After orchestration processing**</span></span>|<span data-ttu-id="c7572-130">選取此核取方塊以在協調流程執行個體處理之後儲存和追蹤實際訊息內容。</span><span class="sxs-lookup"><span data-stu-id="c7572-130">Select this check box to save and track the actual message content after processing by the orchestration instance.</span></span> <span data-ttu-id="c7572-131">此核取方塊才會提供您所選取**訊息傳送與接收**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c7572-131">This check box is available only if you select the **Message send and receive** check box.</span></span>|  
   |<span data-ttu-id="c7572-132">**追蹤訊息屬性-連入訊息**</span><span class="sxs-lookup"><span data-stu-id="c7572-132">**Track Message Properties - Incoming messages**</span></span>|<span data-ttu-id="c7572-133">選取此核取方塊，可追蹤輸入訊息的升級屬性。</span><span class="sxs-lookup"><span data-stu-id="c7572-133">Select this check box to track the promoted properties of an inbound message.</span></span>|  
   |<span data-ttu-id="c7572-134">**追蹤訊息屬性-外寄訊息**</span><span class="sxs-lookup"><span data-stu-id="c7572-134">**Track Message Properties - Outgoing messages**</span></span>|<span data-ttu-id="c7572-135">選取此核取方塊以追蹤輸出訊息的升級的屬性。</span><span class="sxs-lookup"><span data-stu-id="c7572-135">Select this check box to track the promoted properties of an outbound message.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c7572-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7572-136">See Also</span></span>  
 [<span data-ttu-id="c7572-137">管理協調流程</span><span class="sxs-lookup"><span data-stu-id="c7572-137">Managing Orchestrations</span></span>](../core/managing-orchestrations.md)