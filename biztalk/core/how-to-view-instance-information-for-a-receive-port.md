---
title: 若要檢視的執行個體資訊的方式接收連接埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [receive ports], viewing
- receive ports, viewing
- viewing, receive ports
ms.assetid: dad038bc-1202-489b-b144-a93bf1f53c0c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ece5525e18eda82d480adec407f92f9f632453e2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970247"
---
# <a name="how-to-view-instance-information-for-a-receive-port"></a><span data-ttu-id="7adba-102">如何檢視接收埠的執行個體資訊</span><span class="sxs-lookup"><span data-stu-id="7adba-102">How to View Instance Information for a Receive Port</span></span>
<span data-ttu-id="7adba-103">本主題描述如何使用 BizTalk Server 管理主控台來檢視接收埠的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="7adba-103">This topic describes how to use the BizTalk Server Administration console to view the service instances for a receive port.</span></span> <span data-ttu-id="7adba-104">每當接收埠接收訊息時，都會建立服務執行個體以處理訊息。</span><span class="sxs-lookup"><span data-stu-id="7adba-104">Each time the receive port receives a message, a service instance is created to process the message.</span></span> <span data-ttu-id="7adba-105">依照這個主題中的程序執行時，執行個體資訊會顯示在接收埠的 [群組概觀] 頁面中。</span><span class="sxs-lookup"><span data-stu-id="7adba-105">When you follow the procedure in this topic, instance information displays in the Group Overview page for the receive port.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7adba-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="7adba-106">Prerequisites</span></span>  
 <span data-ttu-id="7adba-107">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="7adba-107">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="7adba-108">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="7adba-108">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-view-instance-information-for-a-receive-port"></a><span data-ttu-id="7adba-109">檢視接收埠的執行個體資訊</span><span class="sxs-lookup"><span data-stu-id="7adba-109">To view instance information for a receive port</span></span>  
  
1. <span data-ttu-id="7adba-110">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="7adba-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="7adba-111">在主控台樹狀結構中，展開您要檢視其接收埠執行個體資訊的 BizTalk 群組與 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7adba-111">In the console tree, expand the BizTalk group and the BizTalk application for which you want to view instance information for a receive port.</span></span>  
  
3. <span data-ttu-id="7adba-112">按一下 **接收連接埠**，選取接收埠，按一下**檢視**，然後按一下**執行個體資訊**。</span><span class="sxs-lookup"><span data-stu-id="7adba-112">Click **Receive Ports**, select the receive port, click **View**, and then click **Instance Information**.</span></span>  
  
    <span data-ttu-id="7adba-113">頁面下端區段中的查詢結果面板會顯示接收埠的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="7adba-113">The query results panel in the lower section of the page displays all instances of the receive port.</span></span>  
  
4. <span data-ttu-id="7adba-114">若要精簡查詢並檢視接收埠的其他執行個體資訊，請按一下底下的方塊**值**for**搜尋**欄位中，選取執行個體類型，若要檢視，然後按一下**執行查詢**。</span><span class="sxs-lookup"><span data-stu-id="7adba-114">To refine the query and view different instance information for the receive port, click the box under **Value** for the **Search For** field, select the instance type to view, and then click **Run Query**.</span></span> <span data-ttu-id="7adba-115">如需有關建立查詢的詳細資訊，請參閱在＜另請參閱＞下搜尋到的相關主題。</span><span class="sxs-lookup"><span data-stu-id="7adba-115">For more information about creating queries, see the topics on searching under See Also.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7adba-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7adba-116">See Also</span></span>  
 <span data-ttu-id="7adba-117">[管理接收埠](../core/managing-receive-ports.md) </span><span class="sxs-lookup"><span data-stu-id="7adba-117">[Managing Receive Ports](../core/managing-receive-ports.md) </span></span>  
 <span data-ttu-id="7adba-118">[如何搜尋執行中服務執行個體](../core/how-to-search-for-running-service-instances.md) </span><span class="sxs-lookup"><span data-stu-id="7adba-118">[How to Search for Running Service Instances](../core/how-to-search-for-running-service-instances.md) </span></span>  
 <span data-ttu-id="7adba-119">[如何搜尋已擱置的服務執行個體](../core/how-to-search-for-suspended-service-instances.md) </span><span class="sxs-lookup"><span data-stu-id="7adba-119">[How to Search for Suspended Service Instances](../core/how-to-search-for-suspended-service-instances.md) </span></span>  
 <span data-ttu-id="7adba-120">[如何搜尋訊息](../core/how-to-search-for-messages.md) </span><span class="sxs-lookup"><span data-stu-id="7adba-120">[How to Search for Messages](../core/how-to-search-for-messages.md) </span></span>  
 [<span data-ttu-id="7adba-121">如何搜尋訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="7adba-121">How to Search for Subscriptions</span></span>](../core/how-to-search-for-subscriptions.md)