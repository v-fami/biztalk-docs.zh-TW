---
title: "案例： 更新應用程式成品 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, artifacts
- updating, artifacts
- artifacts, examples
- updating, examples
- examples, updating
- artifacts, updating
ms.assetid: 76833df3-2330-48af-84d8-731028b192ff
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e95e6a66fb0e6bccc1fcc2fb4a7664538e50d3e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-updating-application-artifacts"></a><span data-ttu-id="e5aea-102">案例： 更新應用程式成品</span><span class="sxs-lookup"><span data-stu-id="e5aea-102">Scenario: Updating Application Artifacts</span></span>
<span data-ttu-id="e5aea-103">在應用程式部署至實際執行環境後，更新應用程式中的成品有兩種基本案例：</span><span class="sxs-lookup"><span data-stu-id="e5aea-103">There are two basic scenarios for updating the artifacts in an application that has been deployed into a production environment:</span></span>  
  
-   <span data-ttu-id="e5aea-104">當協調流程處理長時間執行的交易或正在等候請求-回應連接埠的回應時，以新版本更新協調流程。</span><span class="sxs-lookup"><span data-stu-id="e5aea-104">Updating an orchestration with a new version when the orchestration handles long-running transactions or is waiting for a response from a solicit-response port.</span></span>  
  
-   <span data-ttu-id="e5aea-105">不用考慮完成訊息處理時，例如以新版本更新結構描述或對應，這是較一般的更新案例。</span><span class="sxs-lookup"><span data-stu-id="e5aea-105">The more general update case, when you are not concerned with completing message processing, such as updating a schema or map with a new version.</span></span>  
  
 <span data-ttu-id="e5aea-106">在一般更新案例中，您可以用新版本更新成品，例如處理商務需求的變更。</span><span class="sxs-lookup"><span data-stu-id="e5aea-106">In the general update case, you may be updating an artifact with a new version, for example to address a change in business requirements.</span></span> <span data-ttu-id="e5aea-107">這個案例相當單純，您可以用更新版本來覆寫原始成品。</span><span class="sxs-lookup"><span data-stu-id="e5aea-107">This scenario is relatively straightforward, and you can overwrite the original artifact with the updated one.</span></span> <span data-ttu-id="e5aea-108">如需所需的步驟，請參閱[檢查清單： 更新 BizTalk 應用程式中的成品](../core/checklist-update-the-artifacts-in-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="e5aea-108">For a list of the steps involved, see [Checklist: Update the Artifacts in a BizTalk Application](../core/checklist-update-the-artifacts-in-a-biztalk-application.md).</span></span>  
  
 <span data-ttu-id="e5aea-109">另一個案例較為複雜。</span><span class="sxs-lookup"><span data-stu-id="e5aea-109">The second scenario is more complex.</span></span> <span data-ttu-id="e5aea-110">在這個案例中，您必須讓現有協調流程完成訊息的處理。</span><span class="sxs-lookup"><span data-stu-id="e5aea-110">In this case, you must allow the existing orchestration to finish processing the messages.</span></span> <span data-ttu-id="e5aea-111">同時，您必須防止現有協調流程處理任何新訊息。</span><span class="sxs-lookup"><span data-stu-id="e5aea-111">At the same time, you must prevent the existing orchestration from processing any new messages.</span></span> <span data-ttu-id="e5aea-112">相反地，您要協調流程更新版本來接管。</span><span class="sxs-lookup"><span data-stu-id="e5aea-112">Instead, you want the updated version of the orchestration to take over.</span></span> <span data-ttu-id="e5aea-113">若要完成這項作業，您要將包含更新協調流程的組件部署到與原始版本相同的 BizTalk 應用程式中，然後同時執行兩個協調流程</span><span class="sxs-lookup"><span data-stu-id="e5aea-113">To accomplish this, you deploy the assembly containing the updated orchestration into the same BizTalk application as the original version, and then run both orchestrations simultaneously.</span></span> <span data-ttu-id="e5aea-114">(新組件的版本號碼必須與包含原始協調流程的組件不同，否則將無法部署到相同的 BizTalk 群組)。然後再停止原始的協調流程，不使新訊息路由傳送給它，並啟動更新版本，使所有新訊息都傳送給它。</span><span class="sxs-lookup"><span data-stu-id="e5aea-114">(The new assembly must have a different version number than the assembly containing the original orchestration, or you will not be able to deploy it into the same BizTalk group.) You then stop the original orchestration, so that no new messages are routed to it, and start the updated version, so that all new messages are sent to it.</span></span> <span data-ttu-id="e5aea-115">在原始的版本完成所有其訊息的處理之後，即可將它解除部署。</span><span class="sxs-lookup"><span data-stu-id="e5aea-115">After the original version has finished processing all of its messages, you can then undeploy it.</span></span> <span data-ttu-id="e5aea-116">如需執行這些工作的指示，請參閱[如何升級協調流程](../core/how-to-upgrade-an-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="e5aea-116">For instructions on performing these tasks, see [How to Upgrade an Orchestration](../core/how-to-upgrade-an-orchestration.md).</span></span>  
  
 <span data-ttu-id="e5aea-117">下圖顯示典型的並存協調流程部署。</span><span class="sxs-lookup"><span data-stu-id="e5aea-117">The following diagram shows a typical side-by-side orchestration deployment.</span></span>  
  
 <span data-ttu-id="e5aea-118">![並存部署案例](../core/media/ebiz-depl-sidebyside-scenario.gif "ebiz_depl_sidebyside_scenario")</span><span class="sxs-lookup"><span data-stu-id="e5aea-118">![Side by Side Deployment Scenario](../core/media/ebiz-depl-sidebyside-scenario.gif "ebiz_depl_sidebyside_scenario")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5aea-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5aea-119">See Also</span></span>  
 <span data-ttu-id="e5aea-120">[應用程式部署和管理案例](../core/application-deployment-and-management-scenarios.md) </span><span class="sxs-lookup"><span data-stu-id="e5aea-120">[Application Deployment and Management Scenarios](../core/application-deployment-and-management-scenarios.md) </span></span>  
 [<span data-ttu-id="e5aea-121">更新應用程式的重要考量</span><span class="sxs-lookup"><span data-stu-id="e5aea-121">Important Considerations for Updating Applications</span></span>](../core/important-considerations-for-updating-applications.md)