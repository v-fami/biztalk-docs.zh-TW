---
title: 如何登錄傳送埠或傳送埠群組 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- enlisting, send port groups
- enlisting, send ports
- send port groups, enlisting
- send ports, enlisting
- managing [send ports], enlisting
- managing [send port groups], enlisting
ms.assetid: d4298b8e-7dc7-4382-af86-c4db0982b7e0
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 127673659878738a57045ea1b5bd9f1d1cf16d10
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37016193"
---
# <a name="how-to-enlist-a-send-port-or-send-port-group"></a><span data-ttu-id="01571-102">如何登錄傳送埠或傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="01571-102">How to Enlist a Send Port or Send Port Group</span></span>
<span data-ttu-id="01571-103">本主題描述如何使用 BizTalk Server 管理主控台來登錄傳送埠或傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="01571-103">This topic describes how to use the BizTalk Server Administration console to enlist a send port or send port group.</span></span> <span data-ttu-id="01571-104">登錄傳送埠或傳送埠群組會使傳送埠或傳送埠群組與 BizTalk 主控件產生關聯，並且為傳送埠或傳送埠群組建立訂閱。</span><span class="sxs-lookup"><span data-stu-id="01571-104">Enlisting a send port or send port group associates the send port or send port group with a BizTalk host and creates the subscriptions for the send port or send port group.</span></span> <span data-ttu-id="01571-105">如果傳送埠群組沒有包含傳送埠，登錄傳送埠群組並不會建立任何訂閱。</span><span class="sxs-lookup"><span data-stu-id="01571-105">If a send port group does not contain a send port, enlisting the send port group does not create any subscriptions.</span></span> <span data-ttu-id="01571-106">此外，登錄傳送埠群組也不會變更其包含的任何傳送埠的狀態。</span><span class="sxs-lookup"><span data-stu-id="01571-106">In addition, enlisting a send port group does not change the state of any send ports that it contains.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01571-107">啟動傳送埠或傳送埠群組也會自動將其登錄。</span><span class="sxs-lookup"><span data-stu-id="01571-107">Starting a send port or send port group also automatically enlists it.</span></span> <span data-ttu-id="01571-108">此外，啟動應用程式也會依預設登錄並啟動其所有的成品。</span><span class="sxs-lookup"><span data-stu-id="01571-108">In addition, by default starting an application enlists and starts all of its artifacts.</span></span> <span data-ttu-id="01571-109">如需詳細資訊，請參閱 <<c0> [ 如何啟動傳送埠或傳送埠群組](../core/how-to-start-a-send-port-or-send-port-group.md)。</span><span class="sxs-lookup"><span data-stu-id="01571-109">For more information, see [How to Start a Send Port or Send Port Group](../core/how-to-start-a-send-port-or-send-port-group.md).</span></span> <span data-ttu-id="01571-110">另請參閱[如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="01571-110">Also see [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="01571-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="01571-111">Prerequisites</span></span>  
 <span data-ttu-id="01571-112">若要執行本主題中的程序，您必須為 BizTalk Server 系統管理員群組的成員登入。</span><span class="sxs-lookup"><span data-stu-id="01571-112">To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="01571-113">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="01571-113">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-enlist-a-send-port-or-send-port-group"></a><span data-ttu-id="01571-114">登錄傳送埠或傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="01571-114">To enlist a send port or send port group</span></span>  
  
1. <span data-ttu-id="01571-115">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="01571-115">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="01571-116">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組，展開**應用程式**，然後展開包含您想要的傳送埠群組的傳送埠的應用程式登錄。</span><span class="sxs-lookup"><span data-stu-id="01571-116">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the send port or send port group that you want to enlist.</span></span>  
  
3. <span data-ttu-id="01571-117">按一下 **傳送埠**或是**傳送埠群組**，以滑鼠右鍵按一下傳送埠或傳送埠群組，然後按一下 **登錄**。</span><span class="sxs-lookup"><span data-stu-id="01571-117">Click **Send Ports** or **Send Port Groups**, right-click the send port or send port group, and then click **Enlist**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01571-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01571-118">See Also</span></span>  
 [<span data-ttu-id="01571-119">管理傳送埠和傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="01571-119">Managing Send Ports and Send Port Groups</span></span>](../core/managing-send-ports-and-send-port-groups.md)