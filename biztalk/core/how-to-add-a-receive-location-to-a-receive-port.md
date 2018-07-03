---
title: 如何新增接收位置，以接收連接埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive locations, adding to receive ports
- managing [receive ports], adding receive locations
- receive ports, adding receive locations
- adding, receive locations
ms.assetid: a71d50dc-629e-4b7f-aa59-6d2274d4cac3
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c657c96c7714f04d18a2bd8d6d2d7ef90ad9cbd1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998999"
---
# <a name="how-to-add-a-receive-location-to-a-receive-port"></a><span data-ttu-id="54c7d-102">如何將接收位置新增至接收埠</span><span class="sxs-lookup"><span data-stu-id="54c7d-102">How to Add a Receive Location to a Receive Port</span></span>
<span data-ttu-id="54c7d-103">本主題描述如何使用 BizTalk Server 管理主控台，將接收位置新增至接收埠。</span><span class="sxs-lookup"><span data-stu-id="54c7d-103">This topic describes how to use the BizTalk Server Administration console to add a new receive location to a receive port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54c7d-104">您可以繫結接收埠到協調流程時設定應用程式，如中所述[如何設定應用程式](../core/how-to-configure-an-application.md)或當您繫結協調流程中所述[如何設定繫結協調流程](../core/how-to-configure-bindings-for-an-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="54c7d-104">You can bind a receive port to an orchestration when you configure an application, as described in [How to Configure an Application](../core/how-to-configure-an-application.md) or when you bind an orchestration, as described in [How to Configure Bindings for an Orchestration](../core/how-to-configure-bindings-for-an-orchestration.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="54c7d-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="54c7d-105">Prerequisites</span></span>  
 <span data-ttu-id="54c7d-106">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="54c7d-106">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="54c7d-107">如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="54c7d-107">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-add-a-receive-location-to-a-receive-port"></a><span data-ttu-id="54c7d-108">將接收位置新增至接收埠</span><span class="sxs-lookup"><span data-stu-id="54c7d-108">To add a receive location to a receive port</span></span>  
  
1. <span data-ttu-id="54c7d-109">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="54c7d-109">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="54c7d-110">在主控台樹狀結構中，展開您要為其將接收位置新增至接收埠的 BizTalk 群組和 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="54c7d-110">In the console tree, expand the BizTalk group and the BizTalk application for which you want to add a receive location to a receive port.</span></span>  
  
3. <span data-ttu-id="54c7d-111">按一下 **接收連接埠**，以滑鼠右鍵按一下您想要新增接收位置，指向 接收埠**新增**，然後按一下**接收位置**。</span><span class="sxs-lookup"><span data-stu-id="54c7d-111">Click **Receive Ports**, right-click the receive port to which you want to add a receive location, point to **New**, and then click **Receive Location**.</span></span>  
  
4. <span data-ttu-id="54c7d-112">在 **名稱**，輸入新的接收位置的名稱。</span><span class="sxs-lookup"><span data-stu-id="54c7d-112">In **Name**, type a name for the new receive location.</span></span>  
  
5. <span data-ttu-id="54c7d-113">依照下列中的指示設定接收位置屬性[如何建立接收位置](../core/how-to-create-a-receive-location.md)，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="54c7d-113">Configure properties for the receive location by following the instructions in [How to Create a Receive Location](../core/how-to-create-a-receive-location.md), and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54c7d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54c7d-114">See Also</span></span>  
 [<span data-ttu-id="54c7d-115">管理接收埠</span><span class="sxs-lookup"><span data-stu-id="54c7d-115">Managing Receive Ports</span></span>](../core/managing-receive-ports.md)