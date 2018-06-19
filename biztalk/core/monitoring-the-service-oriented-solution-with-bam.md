---
title: 監控服務導向解決方案使用 BAM |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- monitoring, service solutions
- service solution tutorial, monitoring
- OrchestrationEventStream object
ms.assetid: 9b251580-9371-490e-9218-0ce3f6b00fa6
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc1aeaec2513ebe3c6d7fe62ef542b6f044bca56
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264110"
---
# <a name="monitoring-the-service-oriented-solution-with-bam"></a><span data-ttu-id="bfa67-102">監控服務導向 BAM 解決方案</span><span class="sxs-lookup"><span data-stu-id="bfa67-102">Monitoring the Service Oriented Solution with BAM</span></span>
<span data-ttu-id="bfa67-103">解決方案會監視所有版本中的活動**CustomerService**協調流程使用商務活動監控 (BAM) API。</span><span class="sxs-lookup"><span data-stu-id="bfa67-103">The solution monitors activity in all versions of the **CustomerService** orchestration using the Business Activity Monitoring (BAM) API.</span></span> <span data-ttu-id="bfa67-104">更具體來說，它會使用新**OrchestrationEventStream**物件。</span><span class="sxs-lookup"><span data-stu-id="bfa67-104">More specifically, it uses the new **OrchestrationEventStream** object.</span></span>  
  
## <a name="what-is-the-orchestrationeventstream-object"></a><span data-ttu-id="bfa67-105">何謂 OrchestrationEventStream 物件？</span><span class="sxs-lookup"><span data-stu-id="bfa67-105">What is the OrchestrationEventStream Object?</span></span>  
 <span data-ttu-id="bfa67-106">新**OrchestrationEventStream**物件可讓追蹤及監控從協調流程。</span><span class="sxs-lookup"><span data-stu-id="bfa67-106">The new **OrchestrationEventStream** object enables tracking and monitoring from orchestrations.</span></span> <span data-ttu-id="bfa67-107">擷取的資訊在交易上會與協調流程狀態一致。</span><span class="sxs-lookup"><span data-stu-id="bfa67-107">The information captured is transactionally consistent with the orchestration state.</span></span> <span data-ttu-id="bfa67-108">例如，若協調流程主控件執行個體在協調流程執行中期重新開始，則協調流程執行個體會從執行個體的最後持續點重新開始。</span><span class="sxs-lookup"><span data-stu-id="bfa67-108">For example, if the orchestration host instance restarts in the middle of executing the orchestration, the orchestration instance restarts from the last persistence point of the instance.</span></span> <span data-ttu-id="bfa67-109">**OrchestrationEventStream**類別可確保擷取的資料在交易上一致的協調流程執行個體的上次保存點。</span><span class="sxs-lookup"><span data-stu-id="bfa67-109">The **OrchestrationEventStream** class ensures that the captured data is transactionally consistent with the orchestration instance's last persistence point.</span></span> <span data-ttu-id="bfa67-110">所有的**OrchestrationEventStream**方法是靜態的因此您的協調流程不需要建立它的執行個體。</span><span class="sxs-lookup"><span data-stu-id="bfa67-110">All of the **OrchestrationEventStream** methods are static so that your orchestration does not need to create an instance of it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bfa67-111">若要使用**OrchestrationEventStream**物件，您需要將參考加入至**Microsoft.BizTalk.Bam.XLANGs**和**Microsoft.BizTalk.Bam.EventObservation**組件。</span><span class="sxs-lookup"><span data-stu-id="bfa67-111">To use the **OrchestrationEventStream** object, you need to add references to the **Microsoft.BizTalk.Bam.XLANGs** and **Microsoft.BizTalk.Bam.EventObservation** assemblies.</span></span> <span data-ttu-id="bfa67-112">雖然**OrchestrationEventStream**物件是處於**Microsoft.BizTalk.Bam.EventObservation**命名空間，它位於**Microsoft.BizTalk.Bam.XLANGs**組件。</span><span class="sxs-lookup"><span data-stu-id="bfa67-112">Although the **OrchestrationEventStream** object is in the **Microsoft.BizTalk.Bam.EventObservation** namespace, it resides in the **Microsoft.BizTalk.Bam.XLANGs** assembly.</span></span>  
  
 <span data-ttu-id="bfa67-113">雖然追蹤設定檔編輯器 (TPE) 是使用 BAM 的偏好方式，但是 TPE 無法擷取協調流程變數值，也無法處理自訂物件。</span><span class="sxs-lookup"><span data-stu-id="bfa67-113">Although the Tracking Profile Editor (TPE) is the preferred way of using BAM, TPE cannot capture the orchestration variable values, nor can it handle custom objects.</span></span> <span data-ttu-id="bfa67-114">解決方案可使用 BAM API 來克服這些限制。</span><span class="sxs-lookup"><span data-stu-id="bfa67-114">The solution uses the BAM API to overcome these limitations.</span></span>  
  
 <span data-ttu-id="bfa67-115">如需 BAM 的一般資訊，請參閱[使用商務活動監控](../core/using-business-activity-monitoring.md)。</span><span class="sxs-lookup"><span data-stu-id="bfa67-115">For general information about BAM, see [Using Business Activity Monitoring](../core/using-business-activity-monitoring.md).</span></span> <span data-ttu-id="bfa67-116">如需追蹤設定檔編輯器 (TPE) 的相關資訊，請參閱[追蹤設定檔編輯器](../core/tracking-profile-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="bfa67-116">For information about the Tracking Profile Editor (TPE), see [Tracking Profile Editor](../core/tracking-profile-editor.md).</span></span>  
  
## <a name="wrapping-the-orchestrationeventstream-object"></a><span data-ttu-id="bfa67-117">包裝 OrchestrationEventStream 物件</span><span class="sxs-lookup"><span data-stu-id="bfa67-117">Wrapping the OrchestrationEventStream Object</span></span>  
 <span data-ttu-id="bfa67-118">服務導向解決方案會包裝**OrchestrationEventStream**類別**ServiceLevelTracking**類別。</span><span class="sxs-lookup"><span data-stu-id="bfa67-118">The service oriented solution wraps the **OrchestrationEventStream** class with the **ServiceLevelTracking** class.</span></span> <span data-ttu-id="bfa67-119">**ServiceLevelTracking**類別提供應用程式特定的里程碑方法，並隱藏一些詳細資料的使用**OrchestrationEventStream**。</span><span class="sxs-lookup"><span data-stu-id="bfa67-119">The **ServiceLevelTracking** class provides application-specific milestone methods and hides some of the details of using **OrchestrationEventStream**.</span></span>  
  
 <span data-ttu-id="bfa67-120">在**OrchestrationEventStream**的所有方法**ServiceLevelTracking**都是靜態的。</span><span class="sxs-lookup"><span data-stu-id="bfa67-120">As in **OrchestrationEventStream**, all the methods of **ServiceLevelTracking** are static.</span></span> <span data-ttu-id="bfa67-121">所以，協調流程或自訂元件不需要建立它的執行個體。</span><span class="sxs-lookup"><span data-stu-id="bfa67-121">Thus, the orchestration or custom component does not need to create an instance of it.</span></span> <span data-ttu-id="bfa67-122">開始追蹤活動的方法， **TrackingBeginRequest**，傳回唯一的活動執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="bfa67-122">The method that begins tracking an activity, **TrackingBeginRequest**, returns a unique activity instance ID.</span></span> <span data-ttu-id="bfa67-123">所有後續的追蹤事件必須與此活動的執行個體 ID 相關聯才能正確擷取服務層級資料，因為它是執行個體的唯一**CustomerService**協調流程。</span><span class="sxs-lookup"><span data-stu-id="bfa67-123">All subsequent tracking events must be associated with this activity instance ID in order to capture the service level data correctly, because it is unique to the instance of the **CustomerService** orchestration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfa67-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfa67-124">See Also</span></span>  
 <span data-ttu-id="bfa67-125">[開發服務導向解決方案](../core/developing-a-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="bfa67-125">[Developing a Service Oriented Solution](../core/developing-a-service-oriented-solution.md) </span></span>  
 [<span data-ttu-id="bfa67-126">實作會反白顯示的服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="bfa67-126">Implementation Highlights of the Service Oriented Solution</span></span>](../core/implementation-highlights-of-the-service-oriented-solution.md)