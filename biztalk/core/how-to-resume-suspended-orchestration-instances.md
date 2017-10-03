---
title: "如何繼續擱置的協調流程執行個體 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- instances, resuming [HAT]
- HAT, resuming orchestrations
- HAT, resuming pipelines
- orchestrations, resuming
- resuming, pipelines
- resuming, orchestrations
- HAT, debug mode
ms.assetid: da133183-68d9-48d1-9601-8f6d4d5b8898
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6696547ce3e918dc8d84b7cfcb4f24e31c8b70a0
ms.sourcegitcommit: 5355a25d120d094778fb8f68ea14cab55c68d292
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2017
---
# <a name="how-to-resume-suspended-orchestration-instances"></a><span data-ttu-id="e67ba-102">如何繼續擱置的協調流程執行個體</span><span class="sxs-lookup"><span data-stu-id="e67ba-102">How to Resume Suspended Orchestration Instances</span></span>
<span data-ttu-id="e67ba-103">如果您有列示為「已擱置，可繼續」的擱置協調流程執行個體，則可以嘗試從 [查詢結果] 或 [預覽] 窗格中繼續該協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="e67ba-103">If you have suspended orchestration instances that are listed as "suspended resumable," you can attempt to resume the orchestration instance from the query results or preview pane.</span></span> <span data-ttu-id="e67ba-104">只有同時解決導致協調流程執行個體擱置的基本問題之後，您才能夠順利繼續協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="e67ba-104">Resuming the orchestration instance will only succeed if the underlying problem that caused the orchestration instance to become suspended has also been fixed.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e67ba-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="e67ba-105">Prerequisites</span></span>  
 <span data-ttu-id="e67ba-106">您必須以「BizTalk Server 操作員」群組的成員身分登入，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="e67ba-106">You must be logged on as a member of the BizTalk Server Operators group to perform this procedure.</span></span>  
  
### <a name="to-resume-suspended-orchestration-instances"></a><span data-ttu-id="e67ba-107">繼續擱置的協調流程執行個體</span><span class="sxs-lookup"><span data-stu-id="e67ba-107">To resume suspended orchestration instances</span></span>  
  
1.  <span data-ttu-id="e67ba-108">按一下**啟動**，按一下 **程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="e67ba-108">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="e67ba-109">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，然後按一下 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="e67ba-109">In the console tree, expand **BizTalk Server Administration**, and then click the BizTalk group.</span></span>  
  
3.  <span data-ttu-id="e67ba-110">在 詳細資料 窗格中，按一下**新查詢** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e67ba-110">In the details pane, click the **New Query** tab.</span></span>  
  
4.  <span data-ttu-id="e67ba-111">在**查詢運算式**群組中**值**欄中，選取**已擱置服務執行個體**從下拉式清單方塊。</span><span class="sxs-lookup"><span data-stu-id="e67ba-111">In the **Query Expression** group, in the **Value** column, select **Suspended Service Instances** from the drop-down list box.</span></span>  
  
5.  <span data-ttu-id="e67ba-112">執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="e67ba-112">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="e67ba-113">若要繼續單一執行個體，在**欄位名稱**星號旁邊的空白下拉式清單方塊中的資料行 (**\***)，請選取**服務名稱**篩選和接著在**值**資料行中，指定服務名稱。</span><span class="sxs-lookup"><span data-stu-id="e67ba-113">To resume a single instance, in the **Field Name** column, in the empty drop-down list box next to the asterisk (**\***), select the **Service Name** filter and then in the **Value** column, specify the service name.</span></span>  
  
    -   <span data-ttu-id="e67ba-114">若要繼續大量執行個體，在**欄位名稱**星號旁邊的空白下拉式清單方塊中的資料行 (**\***)，請選取**群組結果依據**，然後在**值**資料行中，指定服務名稱。</span><span class="sxs-lookup"><span data-stu-id="e67ba-114">To resume instances in bulk, in the **Field Name** column, in the empty drop-down list box next to the asterisk (**\***), select **Group Results By** and then in the **Value** column, specify the service name.</span></span>  
  
6.  <span data-ttu-id="e67ba-115">按一下**執行查詢**。</span><span class="sxs-lookup"><span data-stu-id="e67ba-115">Click **Run Query**.</span></span>  
  
7.  <span data-ttu-id="e67ba-116">在查詢結果清單中，以滑鼠右鍵按一下您要繼續，然後按一下 協調流程執行個體**繼續的執行個體**或**繼續的執行個體**。</span><span class="sxs-lookup"><span data-stu-id="e67ba-116">In the query results list, right-click the orchestration instance you want to resume, and then click **Resume Instance** or **Resume Instances**.</span></span> <span data-ttu-id="e67ba-117">這可讓您選取的執行個體將繼續。</span><span class="sxs-lookup"><span data-stu-id="e67ba-117">This allows you to select which instances to resume.</span></span>  
  
     <span data-ttu-id="e67ba-118">[服務執行個體狀態](../core/service-instance-states.md)提供的詳細資訊在暫停狀態。</span><span class="sxs-lookup"><span data-stu-id="e67ba-118">[Service Instance States](../core/service-instance-states.md) provides more information on the on the suspended state.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e67ba-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e67ba-119">See Also</span></span>  
 [<span data-ttu-id="e67ba-120">調查協調流程、 連接埠和訊息失敗</span><span class="sxs-lookup"><span data-stu-id="e67ba-120">Investigating Orchestration, Port, and Message Failures</span></span>](../core/investigating-orchestration-port-and-message-failures.md)
