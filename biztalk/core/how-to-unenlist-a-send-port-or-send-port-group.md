---
title: "如何取消登錄傳送埠或傳送埠群組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unenlisting, send port groups
- send port groups, unenlisting
- managing [send ports], unenlisting
- managing [send port groups], unenlisting
- unenlisting, send ports
- send ports, unenlisting
ms.assetid: 3185adad-2efa-4abd-a532-77ae6c7b4c1d
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac2599ae3d06a75506de244a4f996a9e77cef6ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-unenlist-a-send-port-or-send-port-group"></a><span data-ttu-id="70849-102">如何取消登錄傳送埠或傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="70849-102">How to Unenlist a Send Port or Send Port Group</span></span>
<span data-ttu-id="70849-103">本主題描述如何使用 BizTalk Server 管理主控台來取消登錄傳送埠或傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="70849-103">This topic describes how to use the BizTalk Server Administration console to unenlist a send port or send port group.</span></span> <span data-ttu-id="70849-104">取消登錄傳送埠或傳送埠群組會刪除與傳送埠或傳送埠群組相關的所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="70849-104">Unenlisting a send port or send port group eliminates all subscriptions associated with that send port or send port group.</span></span> <span data-ttu-id="70849-105">您可以同時取消登錄正在執行和已停止的傳送埠或傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="70849-105">You can unenlist both running and stopped send ports or send port groups.</span></span> <span data-ttu-id="70849-106">取消登錄傳送埠或傳送埠群組會自動停止它。</span><span class="sxs-lookup"><span data-stu-id="70849-106">Unenlisting a send port or send port group automatically stops it.</span></span>  
  
 <span data-ttu-id="70849-107">例如，您可能想要取消登錄傳送埠或傳送埠群組以編輯其繫結，或想要從 BizTalk Server 環境移除傳送埠或傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="70849-107">For example, you may want to unenlist a send port or send port group to edit its bindings, or if you want to remove the send port or send port group from the BizTalk Server environment.</span></span>  
  
 <span data-ttu-id="70849-108">對於已經登錄或正在執行的傳送埠群組，您無法取消登錄其中最近一次登錄的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="70849-108">You cannot unenlist the last enlisted send port within a send port group that is enlisted or running.</span></span> <span data-ttu-id="70849-109">取消登錄傳送埠群組不會變更其中包含的任何傳送埠的狀態。</span><span class="sxs-lookup"><span data-stu-id="70849-109">Unenlisting a send port group does not change the state of any send ports that it contains.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="70849-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="70849-110">Prerequisites</span></span>  
 <span data-ttu-id="70849-111">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="70849-111">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="70849-112">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="70849-112">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-unenlist-a-send-port-or-send-port-group"></a><span data-ttu-id="70849-113">取消登錄傳送埠或傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="70849-113">To unenlist a send port or send port group</span></span>  
  
1.  <span data-ttu-id="70849-114">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="70849-114">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="70849-115">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**、 依序展開 BizTalk 群組、 展開**應用程式**，然後展開包含傳送埠或傳送埠群組，您想要的應用程式取消登錄。</span><span class="sxs-lookup"><span data-stu-id="70849-115">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the send port or send port group that you want to unenlist.</span></span>  
  
3.  <span data-ttu-id="70849-116">按一下**傳送埠**或**傳送埠群組**，傳送埠或傳送埠群組，以滑鼠右鍵按一下，然後按一下**取消登錄**。</span><span class="sxs-lookup"><span data-stu-id="70849-116">Click **Send Ports** or **Send Port Groups**, right-click the send port or send port group, and then click **Unenlist**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70849-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70849-117">See Also</span></span>  
 [<span data-ttu-id="70849-118">管理傳送埠與傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="70849-118">Managing Send Ports and Send Port Groups</span></span>](../core/managing-send-ports-and-send-port-groups.md)