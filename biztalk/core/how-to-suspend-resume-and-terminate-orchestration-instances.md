---
title: 如何擱置、 繼續和終止協調流程執行個體 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [orchestrations], resuming
- orchestrations, terminating
- managing [orchestrations], suspending
- orchestrations, resuming
- orchestrations, suspending
- managing [orchestrations], terminating
ms.assetid: 7b373dad-57d5-4696-9b29-a6c351d44fa8
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9528ac0e810a3d4e203733ab1cc5b041d3d61d31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256766"
---
# <a name="how-to-suspend-resume-and-terminate-orchestration-instances"></a><span data-ttu-id="03450-102">如何擱置、繼續和終止協調流程執行個體</span><span class="sxs-lookup"><span data-stu-id="03450-102">How to Suspend, Resume, and Terminate Orchestration Instances</span></span>
<span data-ttu-id="03450-103">本主題說明如何使用 BizTalk Server 管理主控台來擱置、繼續和終止協調流程的一或多個執行中的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="03450-103">This topic describes how to suspend, resume, and terminate one or more running service instances of an orchestration by using the BizTalk Server Administration console.</span></span> <span data-ttu-id="03450-104">服務執行個體是 BizTalk Server 正在處理或已經序列化至 MessageBox 做進一步處理或追蹤的協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="03450-104">A service instance is an instance of an orchestration that BizTalk Server is either processing or that has been serialized into the MessageBox for further processing or tracking.</span></span>  
  
 <span data-ttu-id="03450-105">以下說明這三項作業的作用：</span><span class="sxs-lookup"><span data-stu-id="03450-105">The following describes the effects of these three operations:</span></span>  
  
-   <span data-ttu-id="03450-106">**暫止。**</span><span class="sxs-lookup"><span data-stu-id="03450-106">**Suspend.**</span></span> <span data-ttu-id="03450-107">這會暫停服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="03450-107">This pauses the service instance.</span></span> <span data-ttu-id="03450-108">正在處理中訊息則會執行完畢。</span><span class="sxs-lookup"><span data-stu-id="03450-108">In-process messages run to completion.</span></span> <span data-ttu-id="03450-109">訊息仍然會路由傳送至服務執行個體，但不會經過處理。</span><span class="sxs-lookup"><span data-stu-id="03450-109">Messages are still routed to service instances, but are not processed.</span></span>  
  
-   <span data-ttu-id="03450-110">**繼續執行。**</span><span class="sxs-lookup"><span data-stu-id="03450-110">**Resume.**</span></span> <span data-ttu-id="03450-111">這會繼續處理已擱置的執行個體。</span><span class="sxs-lookup"><span data-stu-id="03450-111">This resumes processing of suspended instances.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03450-112">您不能從中斷點狀態繼續執行個體。</span><span class="sxs-lookup"><span data-stu-id="03450-112">You cannot resume an instance from a breakpoint state.</span></span> <span data-ttu-id="03450-113">繼續這種執行個體可能顯示「擱置」狀態，但執行個體實際上會失敗。</span><span class="sxs-lookup"><span data-stu-id="03450-113">Resuming such an instance may show a status of "Pending," but the instance will eventually fail.</span></span>  
  
-   <span data-ttu-id="03450-114">**終止。**</span><span class="sxs-lookup"><span data-stu-id="03450-114">**Terminate.**</span></span> <span data-ttu-id="03450-115">這會終止所有訊息處理。</span><span class="sxs-lookup"><span data-stu-id="03450-115">This terminates all message processing.</span></span> <span data-ttu-id="03450-116">服務執行個體會從 BizTalk Server 資料庫刪除。</span><span class="sxs-lookup"><span data-stu-id="03450-116">The service instance is deleted from the BizTalk Server databases.</span></span> <span data-ttu-id="03450-117">此服務執行個體正在處理的訊息也會被刪除，但其他未終止之服務執行個體所參考的任何訊息除外。</span><span class="sxs-lookup"><span data-stu-id="03450-117">Messages that the service instance is processing are also deleted, except for any messages that are also referenced by a service instance that is not being terminated.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="03450-118">必要條件</span><span class="sxs-lookup"><span data-stu-id="03450-118">Prerequisites</span></span>  
 <span data-ttu-id="03450-119">若要執行這個主題中的程序，您必須以「BizTalk Server 操作員」群組或「BizTalk Server 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="03450-119">To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Operators group or the BizTalk Server Administrators group.</span></span> <span data-ttu-id="03450-120">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="03450-120">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-view-start-stop-or-terminate-an-instance-of-an-orchestration"></a><span data-ttu-id="03450-121">若要檢視、啟動、停止或終止協調流程的執行個體</span><span class="sxs-lookup"><span data-stu-id="03450-121">To view start, stop, or terminate an instance of an orchestration</span></span>  
  
1.  <span data-ttu-id="03450-122">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="03450-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="03450-123">選取要顯示 [群組中樞] 頁面的 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="03450-123">Select the BizTalk Group to display the Group Hub page.</span></span>  
  
3.  <span data-ttu-id="03450-124">在下**進行中的工作**，按一下 **執行服務執行個體**。</span><span class="sxs-lookup"><span data-stu-id="03450-124">Under **Work in Progress**, click **Running service instances**.</span></span>  
  
     <span data-ttu-id="03450-125">頁面下端區域中的查詢結果面板會顯示協調流程的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="03450-125">The query results panel in the lower section of the page displays all instances of the orchestration.</span></span>  
  
4.  <span data-ttu-id="03450-126">若要精簡查詢並檢視協調流程的不同執行個體，請按一下底下的方塊**值**如**搜尋**欄位中，選取執行個體類型，若要檢視，然後按一下**執行查詢**.</span><span class="sxs-lookup"><span data-stu-id="03450-126">To refine the query and view different instances for the orchestration, click the box under **Value** for the **Search For** field, select the instance type to view, and then click **Run Query**.</span></span> <span data-ttu-id="03450-127">如需有關建立查詢的詳細資訊，請參閱在＜另請參閱＞下搜尋到的相關主題。</span><span class="sxs-lookup"><span data-stu-id="03450-127">For more information about creating queries, see the topics on searching under See Also.</span></span>  
  
5.  <span data-ttu-id="03450-128">以滑鼠右鍵按一下執行個體，然後按一下**暫停**，**繼續**，或**Terminate**。</span><span class="sxs-lookup"><span data-stu-id="03450-128">Right-click the instance you want and click **Suspend**, **Resume**, or **Terminate**.</span></span> <span data-ttu-id="03450-129">此功能可讓您選取哪些執行個體將繼續。</span><span class="sxs-lookup"><span data-stu-id="03450-129">This functionality allows you to select which instances to resume.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="03450-130">若要在多個執行個體上執行作業，請按住 CTRL 鍵並按一下所要的執行個體。</span><span class="sxs-lookup"><span data-stu-id="03450-130">To perform the operation on multiple instances, hold down the CTRL key and click the instances you want.</span></span> <span data-ttu-id="03450-131">以滑鼠右鍵按一下執行個體，然後按一下 **暫停**，**繼續**，或**Terminate**。</span><span class="sxs-lookup"><span data-stu-id="03450-131">Then right-click an instance and click **Suspend**, **Resume**, or **Terminate**.</span></span>  
  
     <span data-ttu-id="03450-132">[服務執行個體狀態](../core/service-instance-states.md)提供暫止狀態的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="03450-132">[Service Instance States](../core/service-instance-states.md) provides more information on the suspended state.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03450-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03450-133">See Also</span></span>  
 <span data-ttu-id="03450-134">[管理協調流程](../core/managing-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="03450-134">[Managing Orchestrations](../core/managing-orchestrations.md) </span></span>  
 <span data-ttu-id="03450-135">[如何搜尋執行中服務執行個體](../core/how-to-search-for-running-service-instances.md) </span><span class="sxs-lookup"><span data-stu-id="03450-135">[How to Search for Running Service Instances](../core/how-to-search-for-running-service-instances.md) </span></span>  
 [<span data-ttu-id="03450-136">如何搜尋已擱置的服務執行個體</span><span class="sxs-lookup"><span data-stu-id="03450-136">How to Search for Suspended Service Instances</span></span>](../core/how-to-search-for-suspended-service-instances.md)