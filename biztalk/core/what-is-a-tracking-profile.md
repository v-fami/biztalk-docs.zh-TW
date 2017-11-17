---
title: "何謂追蹤設定檔？ | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracking profiles, about tracking profiles
- tracking profiles, Tracking Profile Editor
- Tracking Profile Editor, tracking profiles
- tracking profiles
ms.assetid: b579bdc4-7c69-4fa0-bbc1-f98170c13d4f
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da032fb6063d81cedca9f21899c5e2bbe6eca947
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-a-tracking-profile"></a><span data-ttu-id="7ebed-103">何謂追蹤設定檔？</span><span class="sxs-lookup"><span data-stu-id="7ebed-103">What Is a Tracking Profile?</span></span>
<span data-ttu-id="7ebed-104">設定檔是定義商務程序的一組特性。</span><span class="sxs-lookup"><span data-stu-id="7ebed-104">A profile is a set of characteristics that define a business process.</span></span> <span data-ttu-id="7ebed-105">追蹤設定檔包含從活動到協調流程和連接埠這些特性的對應。</span><span class="sxs-lookup"><span data-stu-id="7ebed-105">A tracking profile contains the mapping of these characteristics from an activity to orchestrations and ports.</span></span> <span data-ttu-id="7ebed-106">追蹤設定檔的副檔名為 .btt。</span><span class="sxs-lookup"><span data-stu-id="7ebed-106">A tracking profile is a file with a .btt file name extension.</span></span>  
  
## <a name="using-tracking-profiles-in-the-tpe"></a><span data-ttu-id="7ebed-107">在 TPE 中使用追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="7ebed-107">Using tracking profiles in the TPE</span></span>  
 <span data-ttu-id="7ebed-108">TPE 的使用者可以在 BAM 活動項目與那些項目的 BizTalk Server 解決方案來源之間建立對應，也就是所謂的追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="7ebed-108">Users of the TPE create a map, or tracking profile, between items in a BAM activity and the BizTalk Server solution sources for those items.</span></span> <span data-ttu-id="7ebed-109">BAM 活動是由構成「可見性期望清單」的里程碑與內容資料所組成，並且定義追蹤設定檔所依循之商務中的工作單位。</span><span class="sxs-lookup"><span data-stu-id="7ebed-109">BAM activities consist of the milestones and contextual data that make up the "visibility wish-list" and define a unit of work in the business that the tracking profile follows.</span></span> <span data-ttu-id="7ebed-110">如需活動的詳細資訊，請參閱[使用事件資料流實作 BAM 活動](../core/implementing-bam-activities-with-event-streams.md)。</span><span class="sxs-lookup"><span data-stu-id="7ebed-110">For more information about activities, see [Implementing BAM Activities with Event Streams](../core/implementing-bam-activities-with-event-streams.md).</span></span>  
  
 <span data-ttu-id="7ebed-111">使用 TPE 建立追蹤設定檔時，您會用到下列物件：</span><span class="sxs-lookup"><span data-stu-id="7ebed-111">When you create a tracking profile using the TPE, you are working with the following objects:</span></span>  
  
-   <span data-ttu-id="7ebed-112">BAM 活動</span><span class="sxs-lookup"><span data-stu-id="7ebed-112">BAM activities</span></span>  
  
-   <span data-ttu-id="7ebed-113">已部署組件中的 BizTalk 協調流程</span><span class="sxs-lookup"><span data-stu-id="7ebed-113">BizTalk orchestrations in deployed assemblies</span></span>  
  
-   <span data-ttu-id="7ebed-114">接收埠與傳送埠</span><span class="sxs-lookup"><span data-stu-id="7ebed-114">Receive and send ports</span></span>  
  
-   <span data-ttu-id="7ebed-115">已部署組件中的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="7ebed-115">Message schemas in deployed assemblies</span></span>  
  
-   <span data-ttu-id="7ebed-116">內容屬性</span><span class="sxs-lookup"><span data-stu-id="7ebed-116">Context properties</span></span>  
  
-   <span data-ttu-id="7ebed-117">BAM 主要匯入資料庫</span><span class="sxs-lookup"><span data-stu-id="7ebed-117">BAM Primary Import database</span></span>  
  
-   <span data-ttu-id="7ebed-118">BizTalk 管理資料庫</span><span class="sxs-lookup"><span data-stu-id="7ebed-118">BizTalk Management database</span></span>  
  
-   <span data-ttu-id="7ebed-119">BizTalk 追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="7ebed-119">BizTalk Tracking database</span></span>  
  
 <span data-ttu-id="7ebed-120">將訊息結構描述、協調流程圖形與內容屬性中的項目拖放到商務里程碑 (事件) 和資料項目資料夾，藉此定義協調流程中的資料擷取。</span><span class="sxs-lookup"><span data-stu-id="7ebed-120">You define the data extraction from an orchestration by dropping items from message schemas, orchestration shapes, and context properties into business milestone (event) and data item folders.</span></span>  
  
 <span data-ttu-id="7ebed-121">舉例來說，假設 BAM 活動包含名為「收到的 PO」的里程碑，並且含有讓訂單連入以初始化處理作業的傳訊連接埠。</span><span class="sxs-lookup"><span data-stu-id="7ebed-121">For example, consider a BAM activity that includes a milestone called PO Received and has a Messaging port through which purchase orders flow to initiate processing.</span></span> <span data-ttu-id="7ebed-122">開發人員可以將 `PO Received` 里程碑與方案中連接埠的 BizTalk 傳訊屬性 `PortEndTime` 產生關聯。</span><span class="sxs-lookup"><span data-stu-id="7ebed-122">Developers can associate the `PO Received` milestone with a BizTalk Messaging property called `PortEndTime` for the port in their solution.</span></span> <span data-ttu-id="7ebed-123">語意上，這代表只要接收埠結束動作，並填入 `PortEndTime` 屬性，就會成功接收到 PO。</span><span class="sxs-lookup"><span data-stu-id="7ebed-123">Semantically, this indicates that the PO is successfully received once the receive port concludes its action and populates the `PortEndTime` property.</span></span> <span data-ttu-id="7ebed-124">開發人員會讓此關聯與任何其他對應能夠完成追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="7ebed-124">The developer makes this and any other mappings to complete the tracking profile.</span></span> <span data-ttu-id="7ebed-125">此活動中含有 BizTalk Server 來源的所有項目都會建立對應，但如果資料或事件的來源是來自 BizTalk Server 執行階段環境以外的處理序，則會保留未對應的狀態，以便由 API 呼叫直接填入。</span><span class="sxs-lookup"><span data-stu-id="7ebed-125">All items in the activity are mapped if they have a BizTalk Server source, or are left unmapped to be populated by API calls directly if the source of the data or event is from a process outside of BizTalk Server’s run-time environment.</span></span>  
  
 <span data-ttu-id="7ebed-126">雖然 TPE 中的每個窗格或檢視都有獨特功能，但所有檢視與資料夾的瀏覽功能都很類似，方便您尋找和處理資訊。</span><span class="sxs-lookup"><span data-stu-id="7ebed-126">Although each pane or view in the TPE has a unique function, all the views and folders have similar navigational features to help you find and manipulate information.</span></span>  
  
## <a name="who-uses-tracking-profiles-and-the-tpe"></a><span data-ttu-id="7ebed-127">誰會用到追蹤設定檔與 TPE？</span><span class="sxs-lookup"><span data-stu-id="7ebed-127">Who uses tracking profiles and the TPE?</span></span>  
 <span data-ttu-id="7ebed-128">需要進行企業整合開發的使用者可以使用追蹤設定檔與 TPE，將 BizTalk Server 事件來源對應到 BAM 目標活動。</span><span class="sxs-lookup"><span data-stu-id="7ebed-128">Users involved with enterprise integration development use tracking profiles and the TPE to map BizTalk Server event sources to BAM target activities.</span></span> <span data-ttu-id="7ebed-129">產生的 .btt 檔案會交付給 IT 實作進行部署。</span><span class="sxs-lookup"><span data-stu-id="7ebed-129">The resulting .btt file is handed off to IT Implementation for deployment.</span></span>  
  
 <span data-ttu-id="7ebed-130">一般而言，IT 實作使用者會使用命令列工具 (BTTDeploy) 套用追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="7ebed-130">IT Implementation users will typically apply tracking profiles using command-line tools (BTTDeploy).</span></span> <span data-ttu-id="7ebed-131">IT 使用者也可以使用 TPE 直接套用追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="7ebed-131">The IT user can also use the TPE directly to apply the tracking profile.</span></span>  
  
 <span data-ttu-id="7ebed-132">IT 作業部門的使用者可能要負責定期對追蹤設定檔進行更新 (包括任何必要的資料庫作業，例如備份與還原)，尤其是商務需求有所變更時，更是非做不可。</span><span class="sxs-lookup"><span data-stu-id="7ebed-132">Users in IT Operations may be responsible for periodic updates to tracking profiles on a scheduled basis (including any database operations required, such as backup and restore), especially as a result of changes in business requirements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ebed-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ebed-133">See Also</span></span>  
 [<span data-ttu-id="7ebed-134">追蹤設定檔編輯器</span><span class="sxs-lookup"><span data-stu-id="7ebed-134">Tracking Profile Editor</span></span>](../core/tracking-profile-editor.md)