---
title: 如何停用接收位置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [receive locations], disabling
- receive locations, disabling
- disabling, receive locations
ms.assetid: 079a5c2c-3aec-49b3-afac-f3202404bca1
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96c0fd5d9007ccb6cdcfbb9fad89b81bae70d70d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018169"
---
# <a name="how-to-disable-a-receive-location"></a><span data-ttu-id="c1e0b-102">如何停用接收位置</span><span class="sxs-lookup"><span data-stu-id="c1e0b-102">How to Disable a Receive Location</span></span>
<span data-ttu-id="c1e0b-103">本主題描述如何使用 BizTalk Server 管理主控台來停用接收位置。</span><span class="sxs-lookup"><span data-stu-id="c1e0b-103">This topic describes how to use the BizTalk Server Administration console to disable a receive location.</span></span> <span data-ttu-id="c1e0b-104">停用接收位置時，它就會停止接收訊息。</span><span class="sxs-lookup"><span data-stu-id="c1e0b-104">When you disable a receive location, it stops receiving messages.</span></span> <span data-ttu-id="c1e0b-105">如有需要，在停用接受位置之後，您還是可以再啟用它，它就會再次接收訊息。</span><span class="sxs-lookup"><span data-stu-id="c1e0b-105">If you want, after disabling a receive location, you can enable it again, so that it will again receive messages.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c1e0b-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="c1e0b-106">Prerequisites</span></span>  
 <span data-ttu-id="c1e0b-107">若要執行這個主題中的程序，您必須使用「BizTalk Server 操作員」或「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="c1e0b-107">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Operators group or the BizTalk Server Administrators group.</span></span> <span data-ttu-id="c1e0b-108">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="c1e0b-108">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-disable-a-receive-location"></a><span data-ttu-id="c1e0b-109">停用接收位置</span><span class="sxs-lookup"><span data-stu-id="c1e0b-109">To disable a receive location</span></span>  
  
1. <span data-ttu-id="c1e0b-110">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="c1e0b-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="c1e0b-111">在主控台樹狀結構中，展開您要停用其接收位置的 BizTalk 群組和 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c1e0b-111">In the console tree, expand the BizTalk group and the BizTalk application for which you want to disable a receive location.</span></span>  
  
3. <span data-ttu-id="c1e0b-112">按一下 **接收位置**，以滑鼠右鍵按一下接收位置，然後按一下 **停用**。</span><span class="sxs-lookup"><span data-stu-id="c1e0b-112">Click **Receive Locations**, right-click the receive location, and then click **Disable**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1e0b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1e0b-113">See Also</span></span>  
 <span data-ttu-id="c1e0b-114">[管理接收位置](../core/managing-receive-locations.md) </span><span class="sxs-lookup"><span data-stu-id="c1e0b-114">[Managing Receive Locations](../core/managing-receive-locations.md) </span></span>  
 [<span data-ttu-id="c1e0b-115">如何啟用接收位置</span><span class="sxs-lookup"><span data-stu-id="c1e0b-115">How to Enable a Receive Location</span></span>](../core/how-to-enable-a-receive-location.md)