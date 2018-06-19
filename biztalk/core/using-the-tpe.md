---
title: 使用 TPE |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tracking Profile Editor, about Tracking Profile Editor
- tracking profiles, prerequisites
ms.assetid: ebe9a5da-66ec-482d-8aac-892a829ca996
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0fa826ce68042336c2b6e4fb006ecb278a3f981
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288070"
---
# <a name="using-the-tpe"></a><span data-ttu-id="eb6fe-102">使用 TPE</span><span class="sxs-lookup"><span data-stu-id="eb6fe-102">Using the TPE</span></span>
<span data-ttu-id="eb6fe-103">您使用「追蹤設定檔編輯器」(TPE) 將協調流程和屬性對應至 BAM 活動定義。</span><span class="sxs-lookup"><span data-stu-id="eb6fe-103">You use the Tracking Profile Editor (TPE) to map orchestrations and properties to BAM activity definitions.</span></span>  
  
 <span data-ttu-id="eb6fe-104">TPE 的使用者可以在諸如里程碑和內容資料 (有時稱為「可見性期望清單」) 等 BAM 活動項目，與那些項目的 BizTalk 解決方案來源之間建立對應或追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="eb6fe-104">Users of the TPE create a map, or tracking profile, between items in a BAM activity such as milestones and contextual data (sometimes called the "visibility wish-list") and the BizTalk solution sources for those items.</span></span>  
  
 <span data-ttu-id="eb6fe-105">**建立追蹤設定檔**</span><span class="sxs-lookup"><span data-stu-id="eb6fe-105">**Creating a Tracking Profile**</span></span>  
  
 <span data-ttu-id="eb6fe-106">例如，包含稱為「收到的 PO」的里程碑的 BAM 活動。</span><span class="sxs-lookup"><span data-stu-id="eb6fe-106">For example, consider a BAM activity that includes a milestone called “PO Received.”</span></span> <span data-ttu-id="eb6fe-107">開發人員透過使用其他 BizTalk Server 開發工具建立程序，瞭解到實際的程序包括了初始化處理訂單流程的傳訊連接埠。</span><span class="sxs-lookup"><span data-stu-id="eb6fe-107">The developer knows, from having created processes in other BizTalk Server development tools, that the actual process includes a messaging port through which purchase orders flow to initiate processing.</span></span> <span data-ttu-id="eb6fe-108">發人員會判斷對解決方案中的連接埠而言，活動里程碑 (稱為「收到的 PO」) 是 BizTalk 傳訊屬性 (稱為 PortEndTime) 最正確的關聯。</span><span class="sxs-lookup"><span data-stu-id="eb6fe-108">The developer determines that the activity milestone, called “PO Received,” is most correctly associated with a BizTalk messaging property called “PortEndTime” for the port in the solution.</span></span> <span data-ttu-id="eb6fe-109">開發人員會藉由載入活動、選取事件來源，然後從事件來源將適當項目拖放至活動樹狀結構定義中的對應節點，讓此操作和任何其他對應可以完成追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="eb6fe-109">The developer makes this and any other mappings to complete the tracking profile by loading the activity, selecting event sources, and dragging the appropriate items from the event source and dropping them on the corresponding nodes in the activity tree definition.</span></span>  
  
 <span data-ttu-id="eb6fe-110">**建立設定檔的必要條件**</span><span class="sxs-lookup"><span data-stu-id="eb6fe-110">**Prerequisites for Creating a Profile**</span></span>  
  
 <span data-ttu-id="eb6fe-111">建立追蹤設定檔有兩個必要條件：</span><span class="sxs-lookup"><span data-stu-id="eb6fe-111">There are two prerequisites for creating a tracking profile:</span></span>  
  
1.  <span data-ttu-id="eb6fe-112">BAM 活動已經由商務分析師定義為整體觀察模型的一部分，並由系統管理員加以部署。</span><span class="sxs-lookup"><span data-stu-id="eb6fe-112">A BAM activity has been defined by the business analyst, as part of an overall observation model, and has been deployed by the system administrator.</span></span>  
  
2.  <span data-ttu-id="eb6fe-113">BizTalk 解決方案 (包括協調流程、結構描述、對應和管線) 已經成功部署在目標環境中。</span><span class="sxs-lookup"><span data-stu-id="eb6fe-113">A BizTalk solution (including orchestrations, schemas, map, and pipelines) has been successfully deployed in the target environment.</span></span>  
  
 <span data-ttu-id="eb6fe-114">由於在安裝之後 TPE 不會填入任何資料以從資料庫進行擷取，因此必須具備這些必要條件。</span><span class="sxs-lookup"><span data-stu-id="eb6fe-114">These prerequisites are necessary since after installation the TPE is not populated with any data to retrieve from the databases.</span></span>  
  
 <span data-ttu-id="eb6fe-115">**針對自訂的 BAM 方案建立設定檔**</span><span class="sxs-lookup"><span data-stu-id="eb6fe-115">**Creating a Profile for Customized BAM Solutions**</span></span>  
  
 <span data-ttu-id="eb6fe-116">追蹤設定檔僅與具有攔截器的執行階段相關。</span><span class="sxs-lookup"><span data-stu-id="eb6fe-116">Tracking profiles are only relevant to run-times that have an interceptor.</span></span> <span data-ttu-id="eb6fe-117">由使用 BAM API 的自訂程式碼所組成的 BAM 方案並沒有相關的 BAM 執行階段攔截器，傳送資料至 BAM 的作業只能以兩種方式完成：</span><span class="sxs-lookup"><span data-stu-id="eb6fe-117">For BAM solutions that consist of custom code using the BAM APIs, there is no associated BAM run-time interceptor, and sending data to BAM can be done in only one of two ways:</span></span>  
  
-   <span data-ttu-id="eb6fe-118">透過 BAM API 直接完成。</span><span class="sxs-lookup"><span data-stu-id="eb6fe-118">Directly through the BAM APIs.</span></span> <span data-ttu-id="eb6fe-119">開發人員可以使用 API 來明確地將事件資料傳送至 BAM 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="eb6fe-119">Using the APIs developers can explicitly send event data to the BAM infrastructure.</span></span> <span data-ttu-id="eb6fe-120">如需有關如何使用 BAM Api 的詳細資訊，請參閱[使用事件資料流實作 BAM 活動](../core/implementing-bam-activities-with-event-streams.md)。</span><span class="sxs-lookup"><span data-stu-id="eb6fe-120">For more information about using the BAM APIs, see [Implementing BAM Activities with Event Streams](../core/implementing-bam-activities-with-event-streams.md).</span></span>  
  
-   <span data-ttu-id="eb6fe-121">透過 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 屬性間接完成。</span><span class="sxs-lookup"><span data-stu-id="eb6fe-121">Indirectly, through [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] properties.</span></span> <span data-ttu-id="eb6fe-122">如果遇到自訂程式碼是在某個執行階段內容內部執行，而該執行階段並無相關的攔截技術 (例如自訂管線)，或是叫用自訂組件的運算式/動作圖形，則您可依上述使用 BAM API，或使用傳統的資料升級技術。</span><span class="sxs-lookup"><span data-stu-id="eb6fe-122">In the case where the custom code is executing inside some run-time context that does have an associated interception technology, such as a custom pipeline - or expression/action shapes in invoking a custom assembly, You can use the BAM APIs as noted above or use traditional data promotion techniques.</span></span> <span data-ttu-id="eb6fe-123">將屬性升級後，就可以透過 TPE 存取這些屬性，然後可以使用正確的內容屬性，在 TPE 中建立該事件資料與 BAM 活動項目的關聯。</span><span class="sxs-lookup"><span data-stu-id="eb6fe-123">By promoting the properties you make them accessible to the TPE and the association of that event data to a BAM activity item can then be made in the TPE using the correct context property.</span></span> <span data-ttu-id="eb6fe-124">如需有關如何升級屬性的詳細資訊，請參閱[升級屬性](../core/promoting-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="eb6fe-124">For more information about promoting properties, see [Promoting Properties](../core/promoting-properties.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eb6fe-125">本節內容</span><span class="sxs-lookup"><span data-stu-id="eb6fe-125">In This Section</span></span>  
  
-   [<span data-ttu-id="eb6fe-126">建立追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="eb6fe-126">Creating Tracking Profiles</span></span>](../core/creating-tracking-profiles.md)  
  
-   [<span data-ttu-id="eb6fe-127">如何移除被遺棄的追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="eb6fe-127">How to Remove Orphaned Tracking Profiles</span></span>](../core/how-to-remove-orphaned-tracking-profiles.md)  
  
-   [<span data-ttu-id="eb6fe-128">使用多個接續</span><span class="sxs-lookup"><span data-stu-id="eb6fe-128">Using Multiple Continuations</span></span>](../core/using-multiple-continuations.md)