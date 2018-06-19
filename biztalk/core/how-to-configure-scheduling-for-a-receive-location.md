---
title: 如何設定排程的接收位置 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring, receive locations
- managing [receive locations], scheduling
- scheduling, receive locations
- managing [receive locations], configuring
ms.assetid: 2653e1c3-ddbd-4d3f-be64-2a5fcd7cf267
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea43814d6b7c23875bc222f6d6bd4aee5468b60f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248702"
---
# <a name="how-to-configure-scheduling-for-a-receive-location"></a><span data-ttu-id="af76b-102">如何設定接收位置的排程</span><span class="sxs-lookup"><span data-stu-id="af76b-102">How to Configure Scheduling for a Receive Location</span></span>
<span data-ttu-id="af76b-103">本主題描述如何使用 BizTalk Server 管理主控台來設定接收位置的排程屬性。</span><span class="sxs-lookup"><span data-stu-id="af76b-103">This topic describes how to use the BizTalk Server Administration console to configure scheduling properties for a receive location.</span></span> <span data-ttu-id="af76b-104">您可以指定想要接收位置開始和停止處理訊息的日期。</span><span class="sxs-lookup"><span data-stu-id="af76b-104">You can specify the dates when you want the receive location to start and stop processing messages.</span></span> <span data-ttu-id="af76b-105">您也可以指定您想要接收位置在一天當中處理訊息的特定時間。</span><span class="sxs-lookup"><span data-stu-id="af76b-105">You can also specify certain times of the day during which you want the receive location to process messages.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="af76b-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="af76b-106">Prerequisites</span></span>  
 <span data-ttu-id="af76b-107">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="af76b-107">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="af76b-108">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="af76b-108">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-configure-scheduling-for-a-receive-location"></a><span data-ttu-id="af76b-109">若要設定接收位置的排程</span><span class="sxs-lookup"><span data-stu-id="af76b-109">To configure scheduling for a receive location</span></span>  
  
1.  <span data-ttu-id="af76b-110">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="af76b-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="af76b-111">在主控台樹狀目錄中，展開您要為其設定接收位置排程的 BizTalk 群組與 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="af76b-111">In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure scheduling for a receive location.</span></span>  
  
3.  <span data-ttu-id="af76b-112">按一下**接收位置**，以滑鼠右鍵按一下接收位置，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="af76b-112">Click **Receive Locations**, right-click the receive location, and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="af76b-113">在左窗格中，按一下 **排程**下, 表中所述設定排程的屬性，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="af76b-113">In the left pane, click **Schedule**, configure scheduling properties as described in the following table, and then click **OK**.</span></span>  
  
    |<span data-ttu-id="af76b-114">使用</span><span class="sxs-lookup"><span data-stu-id="af76b-114">Use this</span></span>|<span data-ttu-id="af76b-115">動作</span><span class="sxs-lookup"><span data-stu-id="af76b-115">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="af76b-116">**開始日期**</span><span class="sxs-lookup"><span data-stu-id="af76b-116">**Start date**</span></span>|<span data-ttu-id="af76b-117">選取此核取方塊，然後從下拉式日曆選取接收位置開始處理訊息的日期。</span><span class="sxs-lookup"><span data-stu-id="af76b-117">Select this check box, and then from the pull-down calendar, select the date on which the receive location starts processing messages.</span></span> <span data-ttu-id="af76b-118">若要變更年份，請按一下以顯示的年份。</span><span class="sxs-lookup"><span data-stu-id="af76b-118">To change the year, click the displayed year.</span></span>|  
    |<span data-ttu-id="af76b-119">**停止日期**</span><span class="sxs-lookup"><span data-stu-id="af76b-119">**Stop date**</span></span>|<span data-ttu-id="af76b-120">選取此核取方塊，然後從下拉式日曆選取接收位置停止處理訊息的日期。</span><span class="sxs-lookup"><span data-stu-id="af76b-120">Select this check box, and then from the pull-down calendar, select the date on which the receive location stops processing messages.</span></span> <span data-ttu-id="af76b-121">此屬性是選擇項。</span><span class="sxs-lookup"><span data-stu-id="af76b-121">This property is optional.</span></span> <span data-ttu-id="af76b-122">若不指定停止日期，接收位置會一直處於作用中直至停用為止。</span><span class="sxs-lookup"><span data-stu-id="af76b-122">If you do not specify a stop date, the receive location remains active until it is disabled.</span></span>|  
    |<span data-ttu-id="af76b-123">**啟用服務窗口**</span><span class="sxs-lookup"><span data-stu-id="af76b-123">**Enable service window**</span></span>|<span data-ttu-id="af76b-124">選取此核取方塊，以只在指定的時間為一天，然後指定中的時間設定來接收訊息的接收位置**開始時間和停止時間**方塊。</span><span class="sxs-lookup"><span data-stu-id="af76b-124">Select this check box to configure the receive location to receive messages only at specified times of the day, then specify the times in the **Start time and Stop time** boxes.</span></span> <span data-ttu-id="af76b-125">若清除此核取方塊，接收位置便可隨時接收訊息。</span><span class="sxs-lookup"><span data-stu-id="af76b-125">If the check box is cleared, the receive location receives messages at any time.</span></span> <span data-ttu-id="af76b-126">預設值為 False (清除核取方塊)。</span><span class="sxs-lookup"><span data-stu-id="af76b-126">The default value is false (cleared).</span></span>|  
    |<span data-ttu-id="af76b-127">**開始時間**</span><span class="sxs-lookup"><span data-stu-id="af76b-127">**Start time**</span></span>|<span data-ttu-id="af76b-128">指定接收位置應開始接收訊息的時間。</span><span class="sxs-lookup"><span data-stu-id="af76b-128">Specify the time when the receive location should begin to receive messages.</span></span> <span data-ttu-id="af76b-129">這個方塊是只有**啟用服務窗口**選取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="af76b-129">This box is available only when the **Enable service window** check box is selected.</span></span>|  
    |<span data-ttu-id="af76b-130">**停止時間**</span><span class="sxs-lookup"><span data-stu-id="af76b-130">**Stop time**</span></span>|<span data-ttu-id="af76b-131">指定接收位置應停止接收訊息的時間。</span><span class="sxs-lookup"><span data-stu-id="af76b-131">Specify the time when the receive location should cease to receive messages.</span></span> <span data-ttu-id="af76b-132">這個方塊是只有**啟用服務窗口**選取核取方塊。</span><span class="sxs-lookup"><span data-stu-id="af76b-132">This box is available only when the **Enable service window** check box is selected.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="af76b-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af76b-133">See Also</span></span>  
 [<span data-ttu-id="af76b-134">管理接收位置</span><span class="sxs-lookup"><span data-stu-id="af76b-134">Managing Receive Locations</span></span>](../core/managing-receive-locations.md)