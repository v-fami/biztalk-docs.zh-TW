---
title: "如何從傳送埠群組移除傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send port groups, deleting send ports
- managing [send port groups], deleting send ports
- managing [send ports], deleting send ports
- deleting, send ports
- send ports, deleting from send port groups
ms.assetid: a2289bfe-5bc9-4bc7-949c-5152ffb5bc62
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d109064a1286bcd622479a4075ef2d23dc8d320c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-send-port-from-a-send-port-group"></a><span data-ttu-id="f6c58-102">如何從傳送埠群組移除傳送埠</span><span class="sxs-lookup"><span data-stu-id="f6c58-102">How to Remove a Send Port from a Send Port Group</span></span>
<span data-ttu-id="f6c58-103">本主題描述如何使用 BizTalk Server 管理主控台，從傳送埠群組中移除傳送埠。</span><span class="sxs-lookup"><span data-stu-id="f6c58-103">This topic describes how to use the BizTalk Server Administration console to remove a send port from a send port group.</span></span> <span data-ttu-id="f6c58-104">這樣做並不會從應用程式或 BizTalk 管理資料庫中刪除傳送埠。</span><span class="sxs-lookup"><span data-stu-id="f6c58-104">When you do this, the send port is not deleted from the application or the BizTalk Management database.</span></span>  
  
 <span data-ttu-id="f6c58-105">傳送埠必須處於停止或取消登錄的狀態，才可以被移除。</span><span class="sxs-lookup"><span data-stu-id="f6c58-105">Before you can remove a send port, it must be in a stopped or unenlisted state.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6c58-106">若要路由訊息，傳送埠群組必須包含至少一個傳送埠。</span><span class="sxs-lookup"><span data-stu-id="f6c58-106">To route messages, a send port group must contain at least one send port.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f6c58-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="f6c58-107">Prerequisites</span></span>  
 <span data-ttu-id="f6c58-108">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="f6c58-108">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="f6c58-109">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="f6c58-109">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-remove-a-send-port-from-a-send-port-group"></a><span data-ttu-id="f6c58-110">從傳送埠群組移除傳送埠</span><span class="sxs-lookup"><span data-stu-id="f6c58-110">To remove a send port from a send port group</span></span>  
  
1.  <span data-ttu-id="f6c58-111">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="f6c58-111">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="f6c58-112">在主控台樹狀結構中，展開您要在其中將傳送埠自傳送埠群組移除的 BizTalk 群組和 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f6c58-112">In the console tree, expand the BizTalk group and the BizTalk application in which you want to remove a send port from a send port group.</span></span>  
  
3.  <span data-ttu-id="f6c58-113">按一下**傳送埠群組**，以滑鼠右鍵按一下傳送埠群組，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="f6c58-113">Click **Send Port Groups**, right-click the send port group, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="f6c58-114">在下**名稱**，按一下要移除，然後按一下 傳送埠**移除**。</span><span class="sxs-lookup"><span data-stu-id="f6c58-114">Under **Name**, click the send port to remove, and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6c58-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6c58-115">See Also</span></span>  
 <span data-ttu-id="f6c58-116">[建立和設定傳送埠群組](../core/creating-and-configuring-send-port-groups.md) </span><span class="sxs-lookup"><span data-stu-id="f6c58-116">[Creating and Configuring Send Port Groups](../core/creating-and-configuring-send-port-groups.md) </span></span>  
 [<span data-ttu-id="f6c58-117">建立和設定傳送埠</span><span class="sxs-lookup"><span data-stu-id="f6c58-117">Creating and Configuring Send Ports</span></span>](../core/creating-and-configuring-send-ports.md)