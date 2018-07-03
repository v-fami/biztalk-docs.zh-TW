---
title: 如何終止擱置的協調流程執行個體 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, terminating [HAT]
- messages, saving [HAT]
- HAT, saving messages
- HAT, terminating pipelines
- HAT, terminiating orchestrations
- orchestrations, terminating [HAT]
ms.assetid: b5d44cce-b05c-47f9-9015-5b10c2312bf1
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37de5e1153e9d361b76900ca206351e8b9549dc3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991967"
---
# <a name="how-to-terminate-suspended-orchestration-instances"></a><span data-ttu-id="cb9de-102">如何終止擱置的協調流程執行個體</span><span class="sxs-lookup"><span data-stu-id="cb9de-102">How to Terminate Suspended Orchestration Instances</span></span>
<span data-ttu-id="cb9de-103">您可以從 BizTalk Server 管理主控台中的 [查詢結果] 或 [預覽] 窗格，終止任何擱置的協調流程執行個體或連接埠。</span><span class="sxs-lookup"><span data-stu-id="cb9de-103">You can terminate any suspended orchestration instances or ports from the Query results or preview pane in the BizTalk Server Administration Console.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb9de-104">排序傳遞傳送埠的每一個執行個體都可能會有關聯的數個訊息。</span><span class="sxs-lookup"><span data-stu-id="cb9de-104">Each instance of an ordered delivery a send port may have several messages associated with it.</span></span> <span data-ttu-id="cb9de-105">為了防止意外終止或資料流失，請務必檢閱所有的這類關聯之後，再終止執行個體。</span><span class="sxs-lookup"><span data-stu-id="cb9de-105">To prevent accidental termination or data loss, be sure you have reviewed all such associations before terminating an instance.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cb9de-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="cb9de-106">Prerequisites</span></span>  
 <span data-ttu-id="cb9de-107">您必須以「BizTalk Server 操作員」群組的成員身分登入，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="cb9de-107">You must be logged on as a member of the BizTalk Server Operators group to perform this procedure.</span></span>  
  
### <a name="to-terminate-suspended-orchestration-instances"></a><span data-ttu-id="cb9de-108">終止擱置的協調流程執行個體</span><span class="sxs-lookup"><span data-stu-id="cb9de-108">To terminate suspended orchestration instances</span></span>  
  
1. <span data-ttu-id="cb9de-109">按一下 **開始**，按一下**程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="cb9de-109">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="cb9de-110">在主控台樹狀目錄中展開 [[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]]，然後按一下 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="cb9de-110">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then click the BizTalk group.</span></span>  
  
3. <span data-ttu-id="cb9de-111">在 詳細資料 窗格中，按一下**新的查詢** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cb9de-111">In the details pane, click the **New Query** tab.</span></span>  
  
4. <span data-ttu-id="cb9de-112">在 **查詢運算式**群組中**值**欄中，選取**已擱置服務執行個體**從下拉式清單方塊。</span><span class="sxs-lookup"><span data-stu-id="cb9de-112">In the **Query Expression** group, in the **Value** column, select **Suspended Service Instances** from the drop-down list box.</span></span>  
  
5. <span data-ttu-id="cb9de-113">執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="cb9de-113">Do one of the following:</span></span>  
  
   - <span data-ttu-id="cb9de-114">若要終止單一執行個體，**欄位名**星號旁邊的空白下拉式清單方塊中的資料行 (**\\**<em>)，選取 **服務名稱</em>* 篩選器，然後在\*\*值*\* 欄中，指定服務名稱。</span><span class="sxs-lookup"><span data-stu-id="cb9de-114">To terminate a single instance, in the **Field Name** column, in the empty drop-down list box next to the asterisk (**\\**<em>), select the \**Service Name</em>* filter and then in the **Value** column, specify the service name.</span></span>  
  
   - <span data-ttu-id="cb9de-115">若要終止大量執行個體，**欄位名**星號旁邊的空白下拉式清單方塊中的資料行 (**\\**<em>)，選取 **群組結果依據</em>* ，然後在\*\*值*\* 欄中，指定服務名稱。</span><span class="sxs-lookup"><span data-stu-id="cb9de-115">To terminate instances in bulk, in the **Field Name** column, in the empty drop-down list box next to the asterisk (**\\**<em>), select \**Group Results By</em>* and then in the **Value** column, specify the service name.</span></span>  
  
6. <span data-ttu-id="cb9de-116">按一下 **執行查詢**。</span><span class="sxs-lookup"><span data-stu-id="cb9de-116">Click **Run Query**.</span></span>  
  
7. <span data-ttu-id="cb9de-117">在查詢結果清單中，以滑鼠右鍵按一下您想要終止，然後按一下 執行個體群組的協調流程執行個體**終止執行個體**或是**終止執行個體**。</span><span class="sxs-lookup"><span data-stu-id="cb9de-117">In the query results list, right-click the orchestration instance or group of instances you want to terminate, and then click **Terminate Instance** or **Terminate Instances**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb9de-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb9de-118">See Also</span></span>  
 [<span data-ttu-id="cb9de-119">調查協調流程、連接埠和訊息失敗</span><span class="sxs-lookup"><span data-stu-id="cb9de-119">Investigating Orchestration, Port, and Message Failures</span></span>](../core/investigating-orchestration-port-and-message-failures.md)