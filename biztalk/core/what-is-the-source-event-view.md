---
title: "何謂事件來源檢視？ | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking Profile Editor, Source Event view
- Source Event view [Tracking Profile Editor]
- message schemas, Tracking Profile Editor
- orchestrations, Tracking Profile Editor
- Tracking Profile Editor, message schemas
- Tracking Profile Editor, orchestrations
ms.assetid: 72e74780-8590-484b-899d-cdc3d2a908be
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2437d2effe2fa03078e7f92fdb06f378c9e7cac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-source-event-view"></a><span data-ttu-id="e5da7-103">何謂事件來源檢視？</span><span class="sxs-lookup"><span data-stu-id="e5da7-103">What Is the Source Event View?</span></span>
<span data-ttu-id="e5da7-104">[事件來源檢視] 是追蹤設定檔編輯器 (TPE) 表示從您對應到活動定義之組件或內容屬性中，所選取之協調流程或訊息結構描述的地方。</span><span class="sxs-lookup"><span data-stu-id="e5da7-104">The Event Source View is where the Tracking Profile Editor (TPE) presents the orchestrations or message schemas selected from the assemblies or the context properties which you map to the activity definition.</span></span>  
  
 <span data-ttu-id="e5da7-105">[事件來源檢視] 出現在使用者介面的右窗格中。</span><span class="sxs-lookup"><span data-stu-id="e5da7-105">The Source Event View is presented in the right pane of user interface.</span></span> <span data-ttu-id="e5da7-106">窗格的內容會視您選取的資料來源而有不同。</span><span class="sxs-lookup"><span data-stu-id="e5da7-106">The contents of the pane vary based on the data source you selected.</span></span>  
  
## <a name="event-source-options"></a><span data-ttu-id="e5da7-107">事件來源選項</span><span class="sxs-lookup"><span data-stu-id="e5da7-107">Event source options</span></span>  
 <span data-ttu-id="e5da7-108">您有四個選項的事件來源： 協調流程排程、 傳訊內容、 內容屬性和傳訊屬性。</span><span class="sxs-lookup"><span data-stu-id="e5da7-108">You have four options for event sources: orchestration schedules, messaging payloads, context properties, and messaging properties.</span></span>  
  
 <span data-ttu-id="e5da7-109">協調流程和傳訊內容會要求您選取所要對應資料項目的組件。</span><span class="sxs-lookup"><span data-stu-id="e5da7-109">Orchestrations and messaging payloads require that you select an assembly from which to map your data items.</span></span> <span data-ttu-id="e5da7-110">然後，您就可以從該組件中選取特定的協調流程，或所需的訊息內容結構描述。</span><span class="sxs-lookup"><span data-stu-id="e5da7-110">You then select the specific orchestrations or message payload schemas of interest from the assembly.</span></span> <span data-ttu-id="e5da7-111">如需協調流程排程，系統會提供您該組件中之協調流程的清單。</span><span class="sxs-lookup"><span data-stu-id="e5da7-111">For orchestration schedules you are given a list of the orchestrations in the assembly.</span></span> <span data-ttu-id="e5da7-112">傳訊內容可讓您從傳訊內容結構描述清單中進行選取，而內容屬性則會顯示該組件和系統結構描述中可公開使用的結構描述清單。</span><span class="sxs-lookup"><span data-stu-id="e5da7-112">Messaging payloads allow you to select from a list of messaging payload schemas, and context properties present a list of schemas in the assembly and in system schemas that are publicly available.</span></span>  
  
 <span data-ttu-id="e5da7-113">當您選取內容屬性時，會先提供內容屬性名稱的清單。</span><span class="sxs-lookup"><span data-stu-id="e5da7-113">When you select context properties, you are first given a list of context property names.</span></span> <span data-ttu-id="e5da7-114">當您選取某個內容屬性時，該內容屬性的相關結構描述會顯示在右窗格中。</span><span class="sxs-lookup"><span data-stu-id="e5da7-114">When you select the context property, the related schema of the context property is shown in the right pane.</span></span> <span data-ttu-id="e5da7-115">接著您就可以將內容屬性拖放到活動節點上，將該屬性對應到您的活動。</span><span class="sxs-lookup"><span data-stu-id="e5da7-115">You can then map the context property to your activity by dragging and dropping the property onto an activity node.</span></span>  
  
 <span data-ttu-id="e5da7-116">當您選取傳訊屬性時，系統會提供您已知傳訊屬性的清單，然後您就可以將這些屬性對應到活動。</span><span class="sxs-lookup"><span data-stu-id="e5da7-116">When you select messaging properties you are given a list of the known messaging properties that you can then map to the activity.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e5da7-117">本節內容</span><span class="sxs-lookup"><span data-stu-id="e5da7-117">In This Section</span></span>  
  
-   [<span data-ttu-id="e5da7-118">協調流程排程檢視</span><span class="sxs-lookup"><span data-stu-id="e5da7-118">Orchestration Schedule View</span></span>](../core/orchestration-schedule-view.md)  
  
-   [<span data-ttu-id="e5da7-119">傳訊內容檢視</span><span class="sxs-lookup"><span data-stu-id="e5da7-119">Messaging Payload View</span></span>](../core/messaging-payload-view.md)  
  
-   [<span data-ttu-id="e5da7-120">內容屬性檢視</span><span class="sxs-lookup"><span data-stu-id="e5da7-120">Context Property View</span></span>](../core/context-property-view.md)  
  
-   [<span data-ttu-id="e5da7-121">傳訊屬性檢視</span><span class="sxs-lookup"><span data-stu-id="e5da7-121">Messaging Property View</span></span>](../core/messaging-property-view.md)