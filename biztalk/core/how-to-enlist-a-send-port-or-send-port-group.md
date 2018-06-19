---
title: 如何登錄傳送埠或傳送埠群組 |Microsoft 文件
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
ms.openlocfilehash: bb42a4ceaa88ca3d04b5dfb6d6d3afc11847421a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254470"
---
# <a name="how-to-enlist-a-send-port-or-send-port-group"></a><span data-ttu-id="5994d-102">如何登錄傳送埠或傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="5994d-102">How to Enlist a Send Port or Send Port Group</span></span>
<span data-ttu-id="5994d-103">本主題描述如何使用 BizTalk Server 管理主控台來登錄傳送埠或傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="5994d-103">This topic describes how to use the BizTalk Server Administration console to enlist a send port or send port group.</span></span> <span data-ttu-id="5994d-104">登錄傳送埠或傳送埠群組會使傳送埠或傳送埠群組與 BizTalk 主控件產生關聯，並且為傳送埠或傳送埠群組建立訂閱。</span><span class="sxs-lookup"><span data-stu-id="5994d-104">Enlisting a send port or send port group associates the send port or send port group with a BizTalk host and creates the subscriptions for the send port or send port group.</span></span> <span data-ttu-id="5994d-105">如果傳送埠群組沒有包含傳送埠，登錄傳送埠群組並不會建立任何訂閱。</span><span class="sxs-lookup"><span data-stu-id="5994d-105">If a send port group does not contain a send port, enlisting the send port group does not create any subscriptions.</span></span> <span data-ttu-id="5994d-106">此外，登錄傳送埠群組也不會變更其包含的任何傳送埠的狀態。</span><span class="sxs-lookup"><span data-stu-id="5994d-106">In addition, enlisting a send port group does not change the state of any send ports that it contains.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5994d-107">啟動傳送埠或傳送埠群組也會自動將其登錄。</span><span class="sxs-lookup"><span data-stu-id="5994d-107">Starting a send port or send port group also automatically enlists it.</span></span> <span data-ttu-id="5994d-108">此外，啟動應用程式也會依預設登錄並啟動其所有的成品。</span><span class="sxs-lookup"><span data-stu-id="5994d-108">In addition, by default starting an application enlists and starts all of its artifacts.</span></span> <span data-ttu-id="5994d-109">如需詳細資訊，請參閱[如何啟動傳送埠或傳送埠群組](../core/how-to-start-a-send-port-or-send-port-group.md)。</span><span class="sxs-lookup"><span data-stu-id="5994d-109">For more information, see [How to Start a Send Port or Send Port Group](../core/how-to-start-a-send-port-or-send-port-group.md).</span></span> <span data-ttu-id="5994d-110">另請參閱[如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="5994d-110">Also see [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5994d-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="5994d-111">Prerequisites</span></span>  
 <span data-ttu-id="5994d-112">若要執行本主題中的程序，您必須為 BizTalk Server 系統管理員群組的成員登入。</span><span class="sxs-lookup"><span data-stu-id="5994d-112">To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="5994d-113">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="5994d-113">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-enlist-a-send-port-or-send-port-group"></a><span data-ttu-id="5994d-114">登錄傳送埠或傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="5994d-114">To enlist a send port or send port group</span></span>  
  
1.  <span data-ttu-id="5994d-115">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="5994d-115">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="5994d-116">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**、 依序展開 BizTalk 群組、 展開**應用程式**，然後展開包含傳送埠或傳送埠群組，您想要的應用程式登錄。</span><span class="sxs-lookup"><span data-stu-id="5994d-116">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the send port or send port group that you want to enlist.</span></span>  
  
3.  <span data-ttu-id="5994d-117">按一下**傳送埠**或**傳送埠群組**，傳送埠或傳送埠群組，以滑鼠右鍵按一下，然後按一下**登錄**。</span><span class="sxs-lookup"><span data-stu-id="5994d-117">Click **Send Ports** or **Send Port Groups**, right-click the send port or send port group, and then click **Enlist**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5994d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5994d-118">See Also</span></span>  
 [<span data-ttu-id="5994d-119">管理傳送埠與傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="5994d-119">Managing Send Ports and Send Port Groups</span></span>](../core/managing-send-ports-and-send-port-groups.md)