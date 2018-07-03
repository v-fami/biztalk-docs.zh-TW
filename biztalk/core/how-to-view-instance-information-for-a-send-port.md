---
title: 如何檢視傳送埠的執行個體資訊 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- send ports, viewing
- managing [send ports], viewing
- viewing, send ports
ms.assetid: 37cf6561-5341-4a05-b531-33ab0334966e
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5dc1ae4401303845f92b95e6cdf7f4903c165b07
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975143"
---
# <a name="how-to-view-instance-information-for-a-send-port"></a><span data-ttu-id="9be75-102">如何檢視傳送埠的執行個體資訊</span><span class="sxs-lookup"><span data-stu-id="9be75-102">How to View Instance Information for a Send Port</span></span>
<span data-ttu-id="9be75-103">本主題描述如何使用 BizTalk Server 管理主控台來檢視傳送埠之執行中服務執行個體的清單。</span><span class="sxs-lookup"><span data-stu-id="9be75-103">This topic describes how to use the BizTalk Server Administration console to view a list of the running service instances of a send port.</span></span> <span data-ttu-id="9be75-104">服務執行個體是將訊息傳送到傳送埠時建立之傳送埠服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9be75-104">A service instance is an instance of the send port service that is created when a message is sent to the send port.</span></span> <span data-ttu-id="9be75-105">當您遵循這個主題中的程序時，執行個體資訊會顯示在傳送埠的 [群組概觀] 頁面中。</span><span class="sxs-lookup"><span data-stu-id="9be75-105">When you follow the procedure in this topic, instance information displays in the Group Overview page for the send port.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9be75-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="9be75-106">Prerequisites</span></span>  
 <span data-ttu-id="9be75-107">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組或「BizTalk Server 操作員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="9be75-107">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group or BizTalk Server Operators group.</span></span> <span data-ttu-id="9be75-108">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="9be75-108">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-view-instance-information-for-a-send-port"></a><span data-ttu-id="9be75-109">檢視傳送埠的執行個體資訊</span><span class="sxs-lookup"><span data-stu-id="9be75-109">To view instance information for a send port</span></span>  
  
1. <span data-ttu-id="9be75-110">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="9be75-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="9be75-111">在主控台樹狀目錄中，展開您要檢視其傳送埠服務執行個體資訊的 BizTalk 群組與 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9be75-111">In the console tree, expand the BizTalk group and the BizTalk application for which you want to view service instance information for a send port.</span></span>  
  
3. <span data-ttu-id="9be75-112">按一下 **傳送埠**，以滑鼠右鍵按一下傳送埠，指向**檢視**，然後按一下**執行個體資訊**。</span><span class="sxs-lookup"><span data-stu-id="9be75-112">Click **Send Ports**, right-click the send port, point to **View**, and then click **Instance Information**.</span></span>  
  
    <span data-ttu-id="9be75-113">在頁面下方的查詢結果面板中，會顯示傳送埠的所有執行中執行個體。</span><span class="sxs-lookup"><span data-stu-id="9be75-113">The query results panel in the lower section of the page displays all running instances of the send port.</span></span>  
  
4. <span data-ttu-id="9be75-114">若要精簡查詢並檢視傳送埠的不同服務執行個體資訊，請按一下底下的方塊**值**的 搜尋 欄位中，選取 執行個體類型，若要檢視，然後按一下**執行查詢**。</span><span class="sxs-lookup"><span data-stu-id="9be75-114">To refine the query and view different service instance information for the send port, click the box under **Value** for the Search For field, select the instance type to view, and then click **Run Query**.</span></span> <span data-ttu-id="9be75-115">如需有關建立查詢的詳細資訊，請參閱在＜另請參閱＞下搜尋到的相關主題。</span><span class="sxs-lookup"><span data-stu-id="9be75-115">For more information about creating queries, see the topics on searching under See Also.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9be75-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9be75-116">See Also</span></span>  
 <span data-ttu-id="9be75-117">[建立和設定傳送埠](../core/creating-and-configuring-send-ports.md) </span><span class="sxs-lookup"><span data-stu-id="9be75-117">[Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md) </span></span>  
 <span data-ttu-id="9be75-118">[如何搜尋執行中服務執行個體](../core/how-to-search-for-running-service-instances.md) </span><span class="sxs-lookup"><span data-stu-id="9be75-118">[How to Search for Running Service Instances](../core/how-to-search-for-running-service-instances.md) </span></span>  
 <span data-ttu-id="9be75-119">[如何搜尋已擱置的服務執行個體](../core/how-to-search-for-suspended-service-instances.md) </span><span class="sxs-lookup"><span data-stu-id="9be75-119">[How to Search for Suspended Service Instances](../core/how-to-search-for-suspended-service-instances.md) </span></span>  
 <span data-ttu-id="9be75-120">[如何搜尋訊息](../core/how-to-search-for-messages.md) </span><span class="sxs-lookup"><span data-stu-id="9be75-120">[How to Search for Messages](../core/how-to-search-for-messages.md) </span></span>  
 [<span data-ttu-id="9be75-121">如何搜尋訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="9be75-121">How to Search for Subscriptions</span></span>](../core/how-to-search-for-subscriptions.md)