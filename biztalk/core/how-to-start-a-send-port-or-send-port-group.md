---
title: 如何啟動傳送埠或傳送埠群組 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- starting, send port groups
- starting, send ports
- managing [send port groups], starting
- managing [send ports], starting
- send port groups, starting
- send ports, starting
ms.assetid: f17c0b7c-cad7-4c5e-a08c-3ebf838faa54
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 558a9b8444a38607f18757ff09196e44a3ae0b71
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255598"
---
# <a name="how-to-start-a-send-port-or-send-port-group"></a><span data-ttu-id="62c4c-102">如何啟動傳送埠或傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="62c4c-102">How to Start a Send Port or Send Port Group</span></span>
<span data-ttu-id="62c4c-103">本主題描述如何使用 BizTalk Server 管理主控台來啟動傳送埠或傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="62c4c-103">This topic describes how to use the BizTalk Server Administration console to start a send port or send port group.</span></span> <span data-ttu-id="62c4c-104">傳送埠或傳送埠群組必須被啟動，才能處理訊息。</span><span class="sxs-lookup"><span data-stu-id="62c4c-104">You must start a send port or send port group before it can process messages.</span></span> <span data-ttu-id="62c4c-105">如果您啟動已取消登錄的傳送埠或傳送埠群組，BizTalk 便會在啟動傳送埠或傳送埠群組之前將其登錄。</span><span class="sxs-lookup"><span data-stu-id="62c4c-105">If you start an unenlisted send port or send port group, BizTalk enlists the send port or send port group before starting it.</span></span> <span data-ttu-id="62c4c-106">傳送埠群組必須包含至少一個處於已登錄狀態的傳送埠，才能加以啟動。</span><span class="sxs-lookup"><span data-stu-id="62c4c-106">A send port group must contain at least one send port in an enlisted state before you can start the send port group.</span></span> <span data-ttu-id="62c4c-107">啟動和停止傳送埠群組不會影響它所包含的任何傳送埠的狀態。</span><span class="sxs-lookup"><span data-stu-id="62c4c-107">Starting and stopping a send port group does not affect the state of any send ports that it contains.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="62c4c-108">依照預設，啟動 BizTalk 應用程式時將會啟動它所包含的所有成品。</span><span class="sxs-lookup"><span data-stu-id="62c4c-108">By default, starting a BizTalk application starts all of the artifacts that it contains.</span></span> <span data-ttu-id="62c4c-109">如需詳細資訊，請參閱[如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="62c4c-109">For more information, see [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="62c4c-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="62c4c-110">Prerequisites</span></span>  
 <span data-ttu-id="62c4c-111">若要執行這個主題中的程序，您必須以「BizTalk Server 操作員」群組或「BizTalk Server 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="62c4c-111">To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Operators group or the BizTalk Server Administrators group.</span></span> <span data-ttu-id="62c4c-112">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="62c4c-112">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-start-a-send-port-or-send-port-group"></a><span data-ttu-id="62c4c-113">啟動傳送埠或傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="62c4c-113">To start a send port or send port group</span></span>  
  
1.  <span data-ttu-id="62c4c-114">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="62c4c-114">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="62c4c-115">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**、 依序展開 BizTalk 群組、 展開**應用程式**，然後展開包含傳送埠或傳送埠群組，您想要的應用程式啟動。</span><span class="sxs-lookup"><span data-stu-id="62c4c-115">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the send port or send port group that you want to start.</span></span>  
  
3.  <span data-ttu-id="62c4c-116">按一下**傳送埠**或**傳送埠群組**，傳送埠或傳送埠群組，以滑鼠右鍵按一下，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="62c4c-116">Click **Send Ports** or **Send Port Groups**, right-click the send port or send port group, and then click **Start**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62c4c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62c4c-117">See Also</span></span>  
 [<span data-ttu-id="62c4c-118">管理傳送埠與傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="62c4c-118">Managing Send Ports and Send Port Groups</span></span>](../core/managing-send-ports-and-send-port-groups.md)