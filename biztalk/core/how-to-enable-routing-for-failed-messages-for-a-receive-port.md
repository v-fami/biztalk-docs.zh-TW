---
title: 如何啟用的路由失敗訊息的接收埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive ports, routing
- managing [receive ports], errors
- managing [receive ports], failed messages
- enabling, routing
- messages, failed messages
- routing, messages
- managing [receive ports], routing
- messages, routing
- receive ports, errors
- routing, receive ports
- routing, failed messages
- errors, receive ports
ms.assetid: 22366664-545d-4981-9bde-4df48b115002
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 59020dc67fa2d5b070ffc95b31648d382a66437b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254086"
---
# <a name="how-to-enable-routing-for-failed-messages-for-a-receive-port"></a><span data-ttu-id="61f10-102">如何啟用接收埠之失敗訊息的路由</span><span class="sxs-lookup"><span data-stu-id="61f10-102">How to Enable Routing for Failed Messages for a Receive Port</span></span>
<span data-ttu-id="61f10-103">本主題描述如何使用 BizTalk Server 管理主控台來啟用接收埠處理之訊息的路由。</span><span class="sxs-lookup"><span data-stu-id="61f10-103">This topic describes how to use the BizTalk Server Administration console to enable routing for the messages processed by a receive port.</span></span> <span data-ttu-id="61f10-104">當您啟用這個選項時，BizTalk Server 會嘗試將處理失敗的訊息路由至訂閱應用程式 (例如另一個接收埠或協調流程排程)。</span><span class="sxs-lookup"><span data-stu-id="61f10-104">When you enable this option, BizTalk Server will attempt to route any message that fails processing to a subscribing application (such as another receive port or orchestration schedule).</span></span> <span data-ttu-id="61f10-105">未啟用這個選項時 (預設值)，BizTalk Server 會擱置失敗的訊息，並產生負值通知 (NACK)。</span><span class="sxs-lookup"><span data-stu-id="61f10-105">When this option is not enabled (the default), BizTalk Server suspends failed messages and generates a negative acknowledgment (NACK).</span></span> <span data-ttu-id="61f10-106">如需管理失敗的訊息的背景資訊，請參閱[使用失敗訊息路由](../core/using-failed-message-routing.md)。</span><span class="sxs-lookup"><span data-stu-id="61f10-106">For background information about managing failed messages, see [Using Failed Message Routing](../core/using-failed-message-routing.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="61f10-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="61f10-107">Prerequisites</span></span>  
 <span data-ttu-id="61f10-108">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="61f10-108">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="61f10-109">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="61f10-109">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-enable-routing-for-failed-messages-for-a-receive-port"></a><span data-ttu-id="61f10-110">啟用接收埠之失敗訊息的路由</span><span class="sxs-lookup"><span data-stu-id="61f10-110">To enable routing for failed messages for a receive port</span></span>  
  
1.  <span data-ttu-id="61f10-111">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="61f10-111">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="61f10-112">在主控台樹狀目錄中，展開您要為接收埠設定失敗訊息路由的 BizTalk 群組與 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="61f10-112">In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure failed message routing for a receive port.</span></span>  
  
3.  <span data-ttu-id="61f10-113">按一下**接收埠**，接收埠，以滑鼠右鍵按一下，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="61f10-113">Click **Receive Ports**, right-click the receive port, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="61f10-114">選取**啟用的路由失敗訊息**核取方塊，然後**確定**。</span><span class="sxs-lookup"><span data-stu-id="61f10-114">Select the **Enable routing for failed messages** check box, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61f10-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61f10-115">See Also</span></span>  
 [<span data-ttu-id="61f10-116">管理接收埠</span><span class="sxs-lookup"><span data-stu-id="61f10-116">Managing Receive Ports</span></span>](../core/managing-receive-ports.md)