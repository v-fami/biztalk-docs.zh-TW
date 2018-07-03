---
title: 如何刪除傳送埠群組 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- send port groups, deleting
- managing [send port groups], deleting
- deleting, send port groups
ms.assetid: 90c01e58-d35c-4cb2-ac6d-92199199fb42
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4bf0e1a75799671ecd2e52515481c3d3be32ee67
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013687"
---
# <a name="how-to-delete-a-send-port-group"></a><span data-ttu-id="7d370-102">如何刪除傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="7d370-102">How to Delete a Send Port Group</span></span>
<span data-ttu-id="7d370-103">本主題描述如何使用 BizTalk Server 管理主控台，從 BizTalk 應用程式中刪除傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="7d370-103">This topic describes how use the BizTalk Server Administration console to delete a send port group from a BizTalk application.</span></span> <span data-ttu-id="7d370-104">這樣做也會從群組的 BizTalk 管理資料庫中刪除傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="7d370-104">When you do this, the send port group is also deleted from the BizTalk Management database for the group.</span></span> <span data-ttu-id="7d370-105">刪除傳送埠群組並不會刪除其包含的任何傳送埠。</span><span class="sxs-lookup"><span data-stu-id="7d370-105">Deleting a send port group does not delete any send ports that it contains.</span></span>  
  
 <span data-ttu-id="7d370-106">如果符合下列條件，您就可以只刪除傳送埠群組：</span><span class="sxs-lookup"><span data-stu-id="7d370-106">You can delete a send port group only if it meets the following conditions:</span></span>  
  
-   <span data-ttu-id="7d370-107">沒有協調流程繫結至此傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="7d370-107">An orchestration is not bound to the send port group.</span></span> <span data-ttu-id="7d370-108">如果發生這種情況，您可以依照下列中的指示移除繫結[如何解除繫結協調流程](../core/how-to-unbind-an-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="7d370-108">If this is the case, you can remove the binding by following the instructions in [How to Unbind an Orchestration](../core/how-to-unbind-an-orchestration.md).</span></span>  
  
-   <span data-ttu-id="7d370-109">已停止並取消登錄此傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="7d370-109">The send port group is both stopped and unenlisted.</span></span> <span data-ttu-id="7d370-110">如需停止及取消登錄傳送埠的指示，請參閱 <<c0> [ 如何取消登錄傳送埠或傳送埠群組](../core/how-to-unenlist-a-send-port-or-send-port-group.md)並[如何停止傳送埠或傳送埠群組](../core/how-to-stop-a-send-port-or-send-port-group.md)。</span><span class="sxs-lookup"><span data-stu-id="7d370-110">For instructions on stopping and unenlisting a send port, see [How to Unenlist a Send Port or Send Port Group](../core/how-to-unenlist-a-send-port-or-send-port-group.md) and [How to Stop a Send Port or Send Port Group](../core/how-to-stop-a-send-port-or-send-port-group.md).</span></span>  
  
-   <span data-ttu-id="7d370-111">沒有合作對象參考此傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="7d370-111">The send port group is not referenced by a party.</span></span> <span data-ttu-id="7d370-112">如需移除合作對象傳送埠群組的參考的指示，請參閱[如何檢視或編輯合作對象](http://msdn.microsoft.com/library/42e6f3a0-8f7d-4f6c-ab05-a1fab7bf46ca)。</span><span class="sxs-lookup"><span data-stu-id="7d370-112">For instructions on removing a reference to a send port group from a party, see [How to View or Edit a Party](http://msdn.microsoft.com/library/42e6f3a0-8f7d-4f6c-ab05-a1fab7bf46ca).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7d370-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="7d370-113">Prerequisites</span></span>  
 <span data-ttu-id="7d370-114">若要執行本主題中的程序，您必須為 BizTalk Server 系統管理員群組的成員登入。</span><span class="sxs-lookup"><span data-stu-id="7d370-114">To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="7d370-115">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="7d370-115">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-delete-a-send-port-group"></a><span data-ttu-id="7d370-116">刪除傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="7d370-116">To delete a send port group</span></span>  
  
1. <span data-ttu-id="7d370-117">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="7d370-117">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="7d370-118">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 BizTalk 群組、 展開**應用程式**，然後展開包含您想要刪除的傳送埠群組的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7d370-118">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, expand **Applications**, and then expand the application containing the send port group that you want to delete.</span></span>  
  
3. <span data-ttu-id="7d370-119">按一下 **傳送埠群組**，以滑鼠右鍵按一下傳送埠群組，然後按一下 **刪除**。</span><span class="sxs-lookup"><span data-stu-id="7d370-119">Click **Send Port Groups**, right-click the send port group, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d370-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d370-120">See Also</span></span>  
 [<span data-ttu-id="7d370-121">建立和設定傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="7d370-121">Creating and Configuring Send Port Groups</span></span>](../core/creating-and-configuring-send-port-groups.md)