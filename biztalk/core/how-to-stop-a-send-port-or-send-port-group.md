---
title: 如何停止傳送埠或傳送埠群組 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [send ports], stopping
- managing [send port groups], stopping
- stopping, send ports
- send port groups, stopping
- stopping, send port groups
- send ports, stopping
ms.assetid: a7a5eab3-34fe-4417-900a-c37ec16ec009
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efb98529c66659f3b78d4bc9eefb9ce119ff5104
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987319"
---
# <a name="how-to-stop-a-send-port-or-send-port-group"></a><span data-ttu-id="185b5-102">如何停止傳送埠或傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="185b5-102">How to Stop a Send Port or Send Port Group</span></span>
<span data-ttu-id="185b5-103">本主題描述如何使用 BizTalk Server 管理主控台來停止傳送埠或傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="185b5-103">This topic describes how to use the BizTalk Server Administration console to stop a send port or send port group.</span></span> <span data-ttu-id="185b5-104">傳送埠或傳送埠群組被停止時，就無法再處理訊息。</span><span class="sxs-lookup"><span data-stu-id="185b5-104">When you stop a send port or send port group, it no longer processes messages.</span></span> <span data-ttu-id="185b5-105">BizTalk Server 會擱置所有停止之傳送埠或傳送埠群組的啟動訊息。</span><span class="sxs-lookup"><span data-stu-id="185b5-105">BizTalk Server suspends all activation messages to a stopped send port or send port group.</span></span> <span data-ttu-id="185b5-106">停止傳送埠群組不會影響其中所含任何傳送埠的狀態。</span><span class="sxs-lookup"><span data-stu-id="185b5-106">Stopping a send port group does not affect the state of any send ports that it contains.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="185b5-107">依照預設，啟動 BizTalk 應用程式時將會啟動它所包含的所有成品。</span><span class="sxs-lookup"><span data-stu-id="185b5-107">By default, starting a BizTalk application starts all of the artifacts that it contains.</span></span> <span data-ttu-id="185b5-108">如需詳細資訊，請參閱 <<c0> [ 如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="185b5-108">For more information, see [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="185b5-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="185b5-109">Prerequisites</span></span>  
 <span data-ttu-id="185b5-110">若要執行這個主題中的程序，您必須使用「BizTalk Server 操作員」或「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="185b5-110">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Operators group or the BizTalk Server Administrators group.</span></span> <span data-ttu-id="185b5-111">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="185b5-111">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-stop-a-send-port-or-send-port-group"></a><span data-ttu-id="185b5-112">停止傳送埠或傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="185b5-112">To stop a send port or send port group</span></span>  
  
1. <span data-ttu-id="185b5-113">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="185b5-113">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="185b5-114">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組，展開**應用程式**，然後展開包含您想要的傳送埠群組的傳送埠的應用程式停止。</span><span class="sxs-lookup"><span data-stu-id="185b5-114">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the send port or send port group that you want to stop.</span></span>  
  
3. <span data-ttu-id="185b5-115">按一下 **傳送埠**或是**傳送埠群組**，以滑鼠右鍵按一下傳送埠或傳送埠，然後按一下**停止**。</span><span class="sxs-lookup"><span data-stu-id="185b5-115">Click **Send Ports** or **Send Port Groups**, right-click the send port or send port, and then click **Stop**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="185b5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="185b5-116">See Also</span></span>  
 [<span data-ttu-id="185b5-117">管理傳送埠和傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="185b5-117">Managing Send Ports and Send Port Groups</span></span>](../core/managing-send-ports-and-send-port-groups.md)