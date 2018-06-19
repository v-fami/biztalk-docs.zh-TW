---
title: 如何檢視協調流程的執行個體資訊 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, viewing
- managing [orchestrations], viewing
ms.assetid: 860ac2b2-c556-4e1f-8b7f-18ab8be52db4
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84129d48fba15dadfc97722ead85b1535a8fa597
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256526"
---
# <a name="how-to-view-instance-information-for-an-orchestration"></a><span data-ttu-id="d420b-102">如何檢視協調流程的執行個體資訊</span><span class="sxs-lookup"><span data-stu-id="d420b-102">How to View Instance Information for an Orchestration</span></span>
<span data-ttu-id="d420b-103">本主題描述如何使用 BizTalk Server 管理主控台來檢視協調流程的執行個體資訊。</span><span class="sxs-lookup"><span data-stu-id="d420b-103">This topic describes how to view instance information for an orchestration by using the BizTalk Server Administration console.</span></span> <span data-ttu-id="d420b-104">服務執行個體是 BizTalk Server 正在處理或已經序列化至 MessageBox 做進一步處理或追蹤的協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="d420b-104">A service instance is an instance of an orchestration that BizTalk Server is either processing or has serialized into the MessageBox for further processing or tracking.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d420b-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="d420b-105">Prerequisites</span></span>  
 <span data-ttu-id="d420b-106">若要執行本主題中的程序，您必須為 BizTalk Server 系統管理員群組的成員登入。</span><span class="sxs-lookup"><span data-stu-id="d420b-106">To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="d420b-107">如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="d420b-107">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-view-instance-information-for-an-orchestration"></a><span data-ttu-id="d420b-108">檢視協調流程的執行個體資訊</span><span class="sxs-lookup"><span data-stu-id="d420b-108">To view instance information for an orchestration</span></span>  
  
1.  <span data-ttu-id="d420b-109">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="d420b-109">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="d420b-110">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 依序展開 BizTalk 群組、 展開**應用程式**，然後展開包含您要檢視執行個體資訊的協調流程的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d420b-110">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration for which you want to view instance information.</span></span>  
  
3.  <span data-ttu-id="d420b-111">按一下**協調流程**，選取您要檢視執行個體資訊的協調流程按一下**檢視**，，然後選取 **執行個體資訊**。</span><span class="sxs-lookup"><span data-stu-id="d420b-111">Click **Orchestrations**, select the orchestration for which you want to view instance information, click **View**, and then select **Instance Information**.</span></span>  
  
     <span data-ttu-id="d420b-112">頁面下端區域中的查詢結果面板會顯示協調流程的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="d420b-112">The query results panel in the lower section of the page displays all instances of the orchestration.</span></span>  
  
     <span data-ttu-id="d420b-113">若要精簡查詢和檢視不同的執行個體資訊的協調流程，請按一下底下的方塊**值**的 搜尋 欄位中，選取 執行個體類型，若要檢視，然後按一下**執行查詢**。</span><span class="sxs-lookup"><span data-stu-id="d420b-113">To refine the query and view different instance information for the orchestration, click the box under **Value** for the Search For field, select the instance type to view, and then click **Run Query**.</span></span> <span data-ttu-id="d420b-114">如需有關建立查詢的詳細資訊，請參閱在＜另請參閱＞下搜尋到的相關主題。</span><span class="sxs-lookup"><span data-stu-id="d420b-114">For more information about creating queries, see the topics on searching under See Also.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d420b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d420b-115">See Also</span></span>  
 <span data-ttu-id="d420b-116">[管理協調流程](../core/managing-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="d420b-116">[Managing Orchestrations](../core/managing-orchestrations.md) </span></span>  
 <span data-ttu-id="d420b-117">[如何搜尋執行中服務執行個體](../core/how-to-search-for-running-service-instances.md) </span><span class="sxs-lookup"><span data-stu-id="d420b-117">[How to Search for Running Service Instances](../core/how-to-search-for-running-service-instances.md) </span></span>  
 <span data-ttu-id="d420b-118">[如何搜尋已擱置的服務執行個體](../core/how-to-search-for-suspended-service-instances.md) </span><span class="sxs-lookup"><span data-stu-id="d420b-118">[How to Search for Suspended Service Instances](../core/how-to-search-for-suspended-service-instances.md) </span></span>  
 <span data-ttu-id="d420b-119">[如何搜尋訊息](../core/how-to-search-for-messages.md) </span><span class="sxs-lookup"><span data-stu-id="d420b-119">[How to Search for Messages](../core/how-to-search-for-messages.md) </span></span>  
 [<span data-ttu-id="d420b-120">如何搜尋訂閱</span><span class="sxs-lookup"><span data-stu-id="d420b-120">How to Search for Subscriptions</span></span>](../core/how-to-search-for-subscriptions.md)