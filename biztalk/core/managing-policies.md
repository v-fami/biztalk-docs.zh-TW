---
title: "管理原則 |Microsoft 文件"
description: "匯入的快速連結發佈、 新增、 部署、 移除或 BizTalk Server 中匯出原則"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7b3bf92-8868-4c35-953f-61a7f2edff9c
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d49f0343c324900bf10c2efcce46cd57682ed04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="manage-policies"></a><span data-ttu-id="6002b-103">管理原則</span><span class="sxs-lookup"><span data-stu-id="6002b-103">Manage policies</span></span>

## <a name="overview"></a><span data-ttu-id="6002b-104">概觀</span><span class="sxs-lookup"><span data-stu-id="6002b-104">Overview</span></span>
<span data-ttu-id="6002b-105">本節中的主題提供使用 BizTalk Server 管理主控台或 BTSTask 命令列工具以管理原則的指示。</span><span class="sxs-lookup"><span data-stu-id="6002b-105">The topics in this section provide instructions on using the BizTalk Server Administration console or the BTSTask command-line tool to manage policies.</span></span> <span data-ttu-id="6002b-106">原則是商務規則的邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="6002b-106">A policy is a logical grouping of business rules.</span></span> <span data-ttu-id="6002b-107">如需原則的背景資訊，請參閱[原則](../core/policies.md)。</span><span class="sxs-lookup"><span data-stu-id="6002b-107">For background information on policies, see [Policies](../core/policies.md).</span></span>  
  
## <a name="import-publish-deploy-and-remove-policies"></a><span data-ttu-id="6002b-108">匯入、 發行、 部署和移除原則</span><span class="sxs-lookup"><span data-stu-id="6002b-108">Import, publish, deploy, and remove policies</span></span>
 <span data-ttu-id="6002b-109">方案開發人員可以建立和中所述，使用 「 商務規則編輯器 」 中，檢視原則[使用商務規則編輯器建立商務規則](../core/creating-business-rules-using-the-business-rule-composer.md)。</span><span class="sxs-lookup"><span data-stu-id="6002b-109">Solution developers can create and view policies by using the Business Rule Composer, as described in [Creating Business Rules Using the Business Rule Composer](../core/creating-business-rules-using-the-business-rule-composer.md).</span></span> <span data-ttu-id="6002b-110">之後開發人員和 IT 管理員就可以執行下列工作 (將在本節的主題中說明)，以部署和管理 BizTalk 群組和應用程式中的原則：</span><span class="sxs-lookup"><span data-stu-id="6002b-110">Developers and IT administrators can then perform the following tasks, which are described in the topics in this section, to deploy and manage policies in a BizTalk group and application:</span></span>  
  
-   <span data-ttu-id="6002b-111">**原則匯入到 BizTalk 群組。**</span><span class="sxs-lookup"><span data-stu-id="6002b-111">**Import the policy into a BizTalk group.**</span></span> <span data-ttu-id="6002b-112">當您這樣做時，原則新增至群組的規則引擎資料庫，並顯示在 BizTalk Server 管理主控台中\<所有成品 > 節點的 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="6002b-112">When you do this, the policy is added to the Rule Engine database for the group and displays in the BizTalk Server Administration console in the \<All Artifacts> node for the BizTalk group.</span></span> <span data-ttu-id="6002b-113">這並不會使原則針對任何特定應用程式而生效。</span><span class="sxs-lookup"><span data-stu-id="6002b-113">This does not put the policy into effect for any particular application.</span></span> <span data-ttu-id="6002b-114">您必須先發佈此原則，將它新增至 BizTalk 應用程式，然後加以部署，如本節其他主題中所述。</span><span class="sxs-lookup"><span data-stu-id="6002b-114">You must first publish the policy, add it to an application, and then deploy it, as described in other topics in this section.</span></span> <span data-ttu-id="6002b-115">規則引擎資料庫是包含 BizTalk 群組中所有原則的資料庫。</span><span class="sxs-lookup"><span data-stu-id="6002b-115">The Rule Engine database is a database that contains all of the policies in a BizTalk group.</span></span>  
  
-   <span data-ttu-id="6002b-116">**發佈原則。**</span><span class="sxs-lookup"><span data-stu-id="6002b-116">**Publish a policy.**</span></span> <span data-ttu-id="6002b-117">：如此就可以在 BizTalk 應用程式中使用該原則。</span><span class="sxs-lookup"><span data-stu-id="6002b-117">This makes it available to use in a BizTalk application.</span></span>  
  
-   <span data-ttu-id="6002b-118">**將原則加入至 BizTalk 應用程式。**</span><span class="sxs-lookup"><span data-stu-id="6002b-118">**Add a policy to a BizTalk application.**</span></span> <span data-ttu-id="6002b-119">：如此可讓應用程式使用該原則，但不會使原則生效。</span><span class="sxs-lookup"><span data-stu-id="6002b-119">This allows the application to use the policy, but does not put the policy into effect.</span></span> <span data-ttu-id="6002b-120">原則會在部署時生效。</span><span class="sxs-lookup"><span data-stu-id="6002b-120">The policy takes effect when it is deployed.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="6002b-121">如果原則是由兩個或多個應用程式所共用，您應該建立個別的應用程式來容納此原則，然後建立參考，從使用此原則的應用程式參考到包含此原則的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6002b-121">If a policy is shared across two or more applications, you should create a separate application to contain the policy and then create references from the applications that use the policy to the application containing the policy.</span></span> <span data-ttu-id="6002b-122">這是因為如果您停止了包含原則的應用程式，該原則就會自動解除部署，而且任何使用此原則的應用程式都將無法再使用它。</span><span class="sxs-lookup"><span data-stu-id="6002b-122">This is because if you stop an application that contains a policy, the policy is automatically undeployed and no longer functions for any of the applications that use it.</span></span>  
  
-   <span data-ttu-id="6002b-123">**部署原則。**</span><span class="sxs-lookup"><span data-stu-id="6002b-123">**Deploy a policy.**</span></span> <span data-ttu-id="6002b-124">：這麼做會使原則開始作業</span><span class="sxs-lookup"><span data-stu-id="6002b-124">Doing this puts it into operation.</span></span> <span data-ttu-id="6002b-125">(類似於啟動協調流程)。您可以用手動方式部署及解除部署原則。</span><span class="sxs-lookup"><span data-stu-id="6002b-125">(This is similar to starting an orchestration.) You can deploy and undeploy a policy manually.</span></span> <span data-ttu-id="6002b-126">此外，當應用程式啟動時，其原則會自動部署，而應用程式停止時，其原則會自動解除部署。</span><span class="sxs-lookup"><span data-stu-id="6002b-126">In addition, when an application is started, its policies are automatically deployed, and when an application is stopped, its policies are automatically undeployed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6002b-127">原則一旦部署之後，就無法修改。</span><span class="sxs-lookup"><span data-stu-id="6002b-127">Once a policy is deployed, it can no longer be modified.</span></span> <span data-ttu-id="6002b-128">如果想要修改已部署的原則，必須將其解除部署，或者使用商務規則編輯器重新加以建立，並為其提供新的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="6002b-128">If you want to modify a deployed policy, you must either undeploy it, or recreate it by using the Business Rule Composer and give it a new version number.</span></span>  
  
-   <span data-ttu-id="6002b-129">**從 BizTalk 應用程式和 BizTalk 群組中移除原則。**</span><span class="sxs-lookup"><span data-stu-id="6002b-129">**Remove a policy from a BizTalk application and the BizTalk group.**</span></span> <span data-ttu-id="6002b-130">：如此會解除部署原則，並從應用程式以及群組的規則引擎資料庫將其移除。</span><span class="sxs-lookup"><span data-stu-id="6002b-130">This undeploys the policy and removes it from the application as well as the Rule Engine database for the group.</span></span>  
  
-   <span data-ttu-id="6002b-131">**將原則匯出。**</span><span class="sxs-lookup"><span data-stu-id="6002b-131">**Export the policy.**</span></span> <span data-ttu-id="6002b-132">：您可以接著將原則匯入到不同的 BizTalk 群組以在該群組中使用。</span><span class="sxs-lookup"><span data-stu-id="6002b-132">You can then import it into a different BizTalk group to use there.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6002b-133">您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。</span><span class="sxs-lookup"><span data-stu-id="6002b-133">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="6002b-134">如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="6002b-134">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="6002b-135">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="6002b-135">Next steps</span></span>
  
-   [<span data-ttu-id="6002b-136">匯入原則</span><span class="sxs-lookup"><span data-stu-id="6002b-136">Import a Policy</span></span>](../core/how-to-import-a-policy.md)  
  
-   [<span data-ttu-id="6002b-137">發佈原則</span><span class="sxs-lookup"><span data-stu-id="6002b-137">Publish a Policy</span></span>](../core/how-to-publish-a-policy.md)  
  
-   [<span data-ttu-id="6002b-138">新增原則至應用程式</span><span class="sxs-lookup"><span data-stu-id="6002b-138">Add a Policy to an Application</span></span>](../core/how-to-add-a-policy-to-an-application.md)  
  
-   [<span data-ttu-id="6002b-139">部署或解除部署原則</span><span class="sxs-lookup"><span data-stu-id="6002b-139">Deploy or Undeploy a Policy</span></span>](../core/how-to-deploy-or-undeploy-a-policy.md)  
  
-   [<span data-ttu-id="6002b-140">設定原則的追蹤</span><span class="sxs-lookup"><span data-stu-id="6002b-140">Configure Tracking for a Policy</span></span>](../core/how-to-configure-tracking-for-a-policy.md)  
  
-   [<span data-ttu-id="6002b-141">從應用程式和 BizTalk 群組移除原則</span><span class="sxs-lookup"><span data-stu-id="6002b-141">Remove a Policy from an Application and the BizTalk Group</span></span>](../core/how-to-remove-a-policy-from-an-application-and-the-biztalk-group.md)  
  
-   [<span data-ttu-id="6002b-142">匯出原則</span><span class="sxs-lookup"><span data-stu-id="6002b-142">Export a Policy</span></span>](../core/how-to-export-a-policy.md)