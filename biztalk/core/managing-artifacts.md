---
title: "管理成品 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [applications], artifacts
- managing [artifacts]
- artifacts, managing
- managing [artifacts], about managing artificats
ms.assetid: aa7c5e60-7c16-4bcf-b913-b1bdfc5c7543
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ccca48682f009a24f538015b055c45dd79a9587
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="managing-artifacts"></a><span data-ttu-id="e7997-102">管理成品</span><span class="sxs-lookup"><span data-stu-id="e7997-102">Managing Artifacts</span></span>
<span data-ttu-id="e7997-103">本節說明如何管理成品，包括如何在 BizTalk 應用程式中新增和移除成品，以及如何設定其屬性。</span><span class="sxs-lookup"><span data-stu-id="e7997-103">This section describes how to manage artifacts, including how to add and remove them from a BizTalk application and how to configure their properties.</span></span>  
  
 <span data-ttu-id="e7997-104">成品是 BizTalk 應用程式中包含的項目，應用程式必須有這些項目才能執行。</span><span class="sxs-lookup"><span data-stu-id="e7997-104">Artifacts are the items contained in a BizTalk application that are required for it to run.</span></span> <span data-ttu-id="e7997-105">如需如何使用成品的 BizTalk 應用程式中的背景資訊，請參閱[什麼是 BizTalk 應用程式？](../core/what-is-a-biztalk-application.md)</span><span class="sxs-lookup"><span data-stu-id="e7997-105">For background information about how artifacts are used in a BizTalk application, see [What Is a BizTalk Application?](../core/what-is-a-biztalk-application.md)</span></span> <span data-ttu-id="e7997-106">如需成品的背景資訊，請參閱[執行階段架構](../core/runtime-architecture.md)。</span><span class="sxs-lookup"><span data-stu-id="e7997-106">For background information about artifacts, see [Runtime Architecture](../core/runtime-architecture.md).</span></span> <span data-ttu-id="e7997-107">如需管理成品，當您建立和修改 BizTalk 應用程式資訊，請參閱[建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="e7997-107">For information about how you manipulate artifacts when you create and modify a BizTalk application, see [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md).</span></span>  

## <a name="tracking-artifacts"></a><span data-ttu-id="e7997-108">追蹤成品</span><span class="sxs-lookup"><span data-stu-id="e7997-108">Tracking artifacts</span></span>
<span data-ttu-id="e7997-109">管理您所建立之成品的大一部分追蹤。</span><span class="sxs-lookup"><span data-stu-id="e7997-109">A big part of managing the artifacts you create is tracking.</span></span> <span data-ttu-id="e7997-110">您可以設定各種追蹤選項，在執行階段的協調流程、 傳送埠、 接收埠，以及使用 BizTalk Server 管理主控台的管線。</span><span class="sxs-lookup"><span data-stu-id="e7997-110">You can configure various tracking options during run time for orchestrations, send ports, receive ports, and pipelines using the BizTalk Server Administration console.</span></span> <span data-ttu-id="e7997-111">您可以隨時變更任何項目的追蹤選項，而不需要中斷商務程序。</span><span class="sxs-lookup"><span data-stu-id="e7997-111">You can change the tracking options for an item at any time, without interrupting the business process.</span></span>

<span data-ttu-id="e7997-112">追蹤組態設定可讓您追蹤下列資料類型：</span><span class="sxs-lookup"><span data-stu-id="e7997-112">The tracking configuration settings allow you to track the following types of data:</span></span>

- <span data-ttu-id="e7997-113">輸入和 (或) 輸出事件資料。</span><span class="sxs-lookup"><span data-stu-id="e7997-113">Inbound and/or outbound event data.</span></span> <span data-ttu-id="e7997-114">例如，訊息識別碼、成品的啟動與停止時間。</span><span class="sxs-lookup"><span data-stu-id="e7997-114">For example, message ID, start and stop times for the artifact.</span></span>

- <span data-ttu-id="e7997-115">輸入和 (或) 輸出訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="e7997-115">Inbound and/or outbound message properties.</span></span> <span data-ttu-id="e7997-116">例如，成品所處理的每個訊息的一般和升級屬性。</span><span class="sxs-lookup"><span data-stu-id="e7997-116">For example, general and promoted properties for each message that the artifact processes.</span></span>

- <span data-ttu-id="e7997-117">輸入和 (或) 輸出訊息內文和部分。</span><span class="sxs-lookup"><span data-stu-id="e7997-117">Inbound and/or outbound message bodies and parts.</span></span> <span data-ttu-id="e7997-118">例如，成品所處理的每個訊息的內文和部分。</span><span class="sxs-lookup"><span data-stu-id="e7997-118">For example, body and parts for each message that the artifact processes.</span></span>

- <span data-ttu-id="e7997-119">協調流程。</span><span class="sxs-lookup"><span data-stu-id="e7997-119">Orchestrations.</span></span> <span data-ttu-id="e7997-120">協調流程圖形的執行資料。</span><span class="sxs-lookup"><span data-stu-id="e7997-120">Execution data for orchestration shapes.</span></span>

<span data-ttu-id="e7997-121">[檢視追蹤訊息及執行個體資料](../core/viewing-tracked-message-and-instance-data.md)提供資訊很有用。</span><span class="sxs-lookup"><span data-stu-id="e7997-121">[Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md) provides some good info.</span></span> 


> [!TIP]
> <span data-ttu-id="e7997-122">如果您設定管線的追蹤選項，然後追蹤選項會全域設定的每個管線所使用的連接埠。</span><span class="sxs-lookup"><span data-stu-id="e7997-122">If you set tracking options on a pipeline, then the tracking options are set globally for every port that uses the pipeline.</span></span> <span data-ttu-id="e7997-123">這會導致更多超過您可能想要而且可能會影響系統效能正在追蹤的資料。</span><span class="sxs-lookup"><span data-stu-id="e7997-123">This results in far more data being tracked than you may intend, and may impact system performance.</span></span> <span data-ttu-id="e7997-124">在開發期間，這可能是正常現象。</span><span class="sxs-lookup"><span data-stu-id="e7997-124">During development, this may be normal.</span></span> <span data-ttu-id="e7997-125">在生產案例中，我們建議您啟用任何追蹤選項，傳送埠和接收埠，而不是管線。</span><span class="sxs-lookup"><span data-stu-id="e7997-125">In production scenarios, we recommend you enable any tracking options on the send ports and receive ports, instead of the pipelines.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="e7997-126">本節內容</span><span class="sxs-lookup"><span data-stu-id="e7997-126">In this section</span></span>  
  
-   [<span data-ttu-id="e7997-127">管理協調流程</span><span class="sxs-lookup"><span data-stu-id="e7997-127">Managing Orchestrations</span></span>](../core/managing-orchestrations.md)  
  
-   [<span data-ttu-id="e7997-128">管理角色連結</span><span class="sxs-lookup"><span data-stu-id="e7997-128">Managing Role Links</span></span>](../core/managing-role-links.md)  
  
-   [<span data-ttu-id="e7997-129">管理傳送埠與傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="e7997-129">Managing Send Ports and Send Port Groups</span></span>](../core/managing-send-ports-and-send-port-groups.md)  
  
-   [<span data-ttu-id="e7997-130">管理接收埠</span><span class="sxs-lookup"><span data-stu-id="e7997-130">Managing Receive Ports</span></span>](../core/managing-receive-ports.md)  
  
-   [<span data-ttu-id="e7997-131">管理接收位置</span><span class="sxs-lookup"><span data-stu-id="e7997-131">Managing Receive Locations</span></span>](../core/managing-receive-locations.md)  
  
-   [<span data-ttu-id="e7997-132">管理原則</span><span class="sxs-lookup"><span data-stu-id="e7997-132">Managing Policies</span></span>](../core/managing-policies.md)  
  
-   [<span data-ttu-id="e7997-133">管理結構描述</span><span class="sxs-lookup"><span data-stu-id="e7997-133">Managing Schemas</span></span>](../core/managing-schemas.md)  
  
-   [<span data-ttu-id="e7997-134">管理對應</span><span class="sxs-lookup"><span data-stu-id="e7997-134">Managing Maps</span></span>](../core/managing-maps.md)  
  
-   [<span data-ttu-id="e7997-135">管理管線</span><span class="sxs-lookup"><span data-stu-id="e7997-135">Managing Pipelines</span></span>](../core/managing-pipelines.md)  
  
-   [<span data-ttu-id="e7997-136">管理資源</span><span class="sxs-lookup"><span data-stu-id="e7997-136">Managing Resources</span></span>](../core/managing-resources.md)