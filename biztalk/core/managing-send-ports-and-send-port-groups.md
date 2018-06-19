---
title: 管理傳送埠與傳送埠群組 |Microsoft 文件
description: 若要建立，連結設定、 登錄、 取消登錄和啟動和停止 BizTalk Server 中的傳送埠
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db45f9f9-b32a-4b9c-a3bf-8c271d0f0cf9
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 928160ed5b67602c8fc8d9d646459bf2425d7a01
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262702"
---
# <a name="manage-send-ports-and-send-port-groups"></a><span data-ttu-id="b1340-103">管理傳送埠與傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="b1340-103">Manage Send Ports and Send Port Groups</span></span>

## <a name="overview"></a><span data-ttu-id="b1340-104">概觀</span><span class="sxs-lookup"><span data-stu-id="b1340-104">Overview</span></span>
<span data-ttu-id="b1340-105">本節提供使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台，在 BizTalk 應用程式中建立、設定和管理傳送埠與傳送埠群組的相關指示。</span><span class="sxs-lookup"><span data-stu-id="b1340-105">This section provides instructions on using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to create, configure, and manage send ports and send port groups in a BizTalk application.</span></span> <span data-ttu-id="b1340-106">傳送埠會指定傳送訊息所至以及選擇性接收回應的位置。</span><span class="sxs-lookup"><span data-stu-id="b1340-106">A send port specifies the location to which messages are sent and optionally responses are received.</span></span> <span data-ttu-id="b1340-107">任何時候將訊息傳送至傳送埠，建立傳送埠服務的新執行個體，稱為*服務執行個體*。</span><span class="sxs-lookup"><span data-stu-id="b1340-107">Any time a message is sent to a send port, a new instance of the send port service is created, which is called a *service instance*.</span></span>  
  
 <span data-ttu-id="b1340-108">傳送埠群組是傳送埠的邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="b1340-108">A send port group is a logical grouping of send ports.</span></span> <span data-ttu-id="b1340-109">將訊息傳送至傳送埠群組時，該訊息會路由至所有相關的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="b1340-109">When a message is sent to a send port group, it is routed to all of the associated send ports.</span></span>  <span data-ttu-id="b1340-110">如需傳送埠與傳送埠群組的背景資訊，請參閱[傳送埠與傳送埠群組](../core/send-ports-and-send-port-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="b1340-110">For background information about send ports and send port groups, see [Send Ports and Send Port Groups](../core/send-ports-and-send-port-groups.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1340-111">您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。</span><span class="sxs-lookup"><span data-stu-id="b1340-111">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="b1340-112">如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="b1340-112">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
> [!NOTE]
>  <span data-ttu-id="b1340-113">開發 BizTalk 應用程式時，開發人員可以使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中的 BizTalk 設計工具 (例如協調流程設計師)，來建立和設定傳送埠與傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="b1340-113">While developing a BizTalk application, the developer can use BizTalk design tools in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], such as Orchestration Designer, to create and configure send ports and send port groups.</span></span> <span data-ttu-id="b1340-114">如需詳細資訊，請參閱[協調流程中使用連接埠](../core/using-ports-in-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="b1340-114">For more information, see [Using Ports in Orchestrations](../core/using-ports-in-orchestrations.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b1340-115">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="b1340-115">Next steps</span></span>
  
-   [<span data-ttu-id="b1340-116">建立和設定傳送埠</span><span class="sxs-lookup"><span data-stu-id="b1340-116">Creating and Configuring Send Ports</span></span>](../core/creating-and-configuring-send-ports.md)  
  
-   [<span data-ttu-id="b1340-117">建立和設定傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="b1340-117">Creating and Configuring Send Port Groups</span></span>](../core/creating-and-configuring-send-port-groups.md)  
  
-   [<span data-ttu-id="b1340-118">登錄傳送埠或傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="b1340-118">Enlist a Send Port or Send Port Group</span></span>](../core/how-to-enlist-a-send-port-or-send-port-group.md)  
  
-   [<span data-ttu-id="b1340-119">取消登錄傳送埠或傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="b1340-119">Unenlist a Send Port or Send Port Group</span></span>](../core/how-to-unenlist-a-send-port-or-send-port-group.md)  
  
-   [<span data-ttu-id="b1340-120">啟動傳送埠或傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="b1340-120">Start a Send Port or Send Port Group</span></span>](../core/how-to-start-a-send-port-or-send-port-group.md)  
  
-   [<span data-ttu-id="b1340-121">停止傳送埠或傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="b1340-121">Stop a Send Port or Send Port Group</span></span>](../core/how-to-stop-a-send-port-or-send-port-group.md)