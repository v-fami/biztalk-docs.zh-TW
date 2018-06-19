---
title: EventStream 類別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a3e7a6b3-69cc-4312-9074-acccd1175d37
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89eafdced54927007bcc8dfc02e4834641e2ae2f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22245822"
---
# <a name="eventstream-classes"></a><span data-ttu-id="a66f8-102">EventStream 類別</span><span class="sxs-lookup"><span data-stu-id="a66f8-102">EventStream Classes</span></span>
<span data-ttu-id="a66f8-103">BAM 的 EventStream API 位於 Microsoft.BizTalk.BAM.EventObservation 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="a66f8-103">The EventStream APIs for BAM reside in the Microsoft.BizTalk.BAM.EventObservation namespace.</span></span> <span data-ttu-id="a66f8-104">若要針對這些 API 撰寫程式碼，您必須在開發電腦上安裝下列 DLL：</span><span class="sxs-lookup"><span data-stu-id="a66f8-104">To code against the APIs, you must install the following DLLs on your development computer:</span></span>  
  
-   <span data-ttu-id="a66f8-105">Microsoft.BizTalk.BAM.EventObservation.dll</span><span class="sxs-lookup"><span data-stu-id="a66f8-105">Microsoft.BizTalk.BAM.EventObservation.dll</span></span>  
  
-   <span data-ttu-id="a66f8-106">Microsoft.biztalk.bam.xlangs.dll 新增： 這個 DLL 時需要撰寫程式碼的協調流程事件資料流。</span><span class="sxs-lookup"><span data-stu-id="a66f8-106">Microsoft.Biztalk.BAM.Xlangs.dll: This DLL is required when coding for Orchestration event streams.</span></span>  
  
-   <span data-ttu-id="a66f8-107">Microsoft.BizTalk.Pipeline.dll： 使用訊息事件資料流的編碼管線內容時需要這個 DLL。</span><span class="sxs-lookup"><span data-stu-id="a66f8-107">Microsoft.BizTalk.Pipeline.dll: This DLL required when using coding pipeline contexts for Messaging event streams.</span></span>  
  
 <span data-ttu-id="a66f8-108">將此 DLL 加入到專案參考中，並利用下列 using 陳述式在您的程式碼中包含命名空間：</span><span class="sxs-lookup"><span data-stu-id="a66f8-108">Add the DLL to your project reference and include the namespace in your code with the following using statement:</span></span>  
  
```  
using Microsoft.BizTalk.Bam.EventObservation;  
```  
  
 <span data-ttu-id="a66f8-109">**類別**</span><span class="sxs-lookup"><span data-stu-id="a66f8-109">**Classes**</span></span>  
  
|<span data-ttu-id="a66f8-110">名稱</span><span class="sxs-lookup"><span data-stu-id="a66f8-110">Name</span></span>|<span data-ttu-id="a66f8-111">Description</span><span class="sxs-lookup"><span data-stu-id="a66f8-111">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="a66f8-112">DirectEventStream (DES)</span><span class="sxs-lookup"><span data-stu-id="a66f8-112">DirectEventStream (DES)</span></span>|<span data-ttu-id="a66f8-113">同步、無延遲</span><span class="sxs-lookup"><span data-stu-id="a66f8-113">Synchronous, no latency</span></span>|  
|<span data-ttu-id="a66f8-114">BufferedEventStream (BES)</span><span class="sxs-lookup"><span data-stu-id="a66f8-114">BufferedEventStream (BES)</span></span>|<span data-ttu-id="a66f8-115">非同步、高輸送量、一些延遲</span><span class="sxs-lookup"><span data-stu-id="a66f8-115">Asynchronous, high throughput, some latency</span></span>|  
|<span data-ttu-id="a66f8-116">OrchestrationEventStream (OES)</span><span class="sxs-lookup"><span data-stu-id="a66f8-116">OrchestrationEventStream (OES)</span></span>|<span data-ttu-id="a66f8-117">非同步、參與 BizTalk 協調流程交易</span><span class="sxs-lookup"><span data-stu-id="a66f8-117">Asynchronous, participates in BizTalk orchestration transactions</span></span>|  
|<span data-ttu-id="a66f8-118">IPipelineContext 介面</span><span class="sxs-lookup"><span data-stu-id="a66f8-118">IPipelineContext Interface</span></span>|<span data-ttu-id="a66f8-119">非同步、參與 BizTalk Server 管線交易。</span><span class="sxs-lookup"><span data-stu-id="a66f8-119">Asynchronous, participates in BizTalk Server pipeline transactions.</span></span> <span data-ttu-id="a66f8-120">用來建立訊息事件資料流 (MES)。</span><span class="sxs-lookup"><span data-stu-id="a66f8-120">Used to create Messaging Event Streams (MES).</span></span>|  
  
 <span data-ttu-id="a66f8-121">您應該根據下列因素來選擇 API：</span><span class="sxs-lookup"><span data-stu-id="a66f8-121">You should choose an API based on the following factors:</span></span>  
  
-   <span data-ttu-id="a66f8-122">如果您擔心延遲，請選擇 DES，此時會使用與 BAM 主要匯入資料庫同步的方式來保存資料。</span><span class="sxs-lookup"><span data-stu-id="a66f8-122">If your concern is latency, choose DES, where data is persisted synchronously to the BAM Primary Import database.</span></span> <span data-ttu-id="a66f8-123">除 DES 外的所有其他 EventStream 類別都是非同步類別，因而會有一些延遲 。</span><span class="sxs-lookup"><span data-stu-id="a66f8-123">Except for DES, all other EventStream classes are asynchronous and have some latency.</span></span> <span data-ttu-id="a66f8-124">資料會先保存在 MessageBox 中，接著再由 TDDS 進行處理，將資料移到 BAMPrimaryImport 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="a66f8-124">The data is first persisted to MessageBox and subsequently processed by TDDS which moves data into the BAMPrimaryImport database.</span></span>  
  
-   <span data-ttu-id="a66f8-125">如果您擔心事件插入的效能和輸送量，請選擇非同步 API。</span><span class="sxs-lookup"><span data-stu-id="a66f8-125">If your concern is performance and throughput of event insertion, choose an asynchronous API.</span></span>  
  
-   <span data-ttu-id="a66f8-126">如果您撰寫的應用程式在未安裝 BizTalk Server 的電腦上執行，請使用 DES 和 BES</span><span class="sxs-lookup"><span data-stu-id="a66f8-126">If you are writing an application that runs on a computer that does not have BizTalk Server installed, use DES and BES.</span></span> <span data-ttu-id="a66f8-127">(換句話說，這些 API 可用於非 BizTalk 應用程式)。</span><span class="sxs-lookup"><span data-stu-id="a66f8-127">(In other words, these APIs can be used in non-BizTalk applications.)</span></span>  
  
-   <span data-ttu-id="a66f8-128">如果您的應用程式要在已安裝 BizTalk Server 的電腦上執行，請使用 MES 和 OES</span><span class="sxs-lookup"><span data-stu-id="a66f8-128">If your application runs on a computer on which BizTalk Server is installed, use MES and OES.</span></span> <span data-ttu-id="a66f8-129">(這些 API 只能從 BizTalk 應用程式使用)。</span><span class="sxs-lookup"><span data-stu-id="a66f8-129">(These APIs are available only from BizTalk applications.)</span></span>  
  
    -   <span data-ttu-id="a66f8-130">如果您希望 BAM 事件持續性會與管線交易同步，您應該使用訊息事件資料流。</span><span class="sxs-lookup"><span data-stu-id="a66f8-130">If you want BAM event persistence to be in sync with pipeline transaction, you should use a Messaging Event Stream.</span></span>  
  
    -   <span data-ttu-id="a66f8-131">OES 相當於 MES，但它適用於 BizTalk 協調流程。</span><span class="sxs-lookup"><span data-stu-id="a66f8-131">OES is the equivalent of MES but for BizTalk orchestrations.</span></span>  
  
 <span data-ttu-id="a66f8-132">您可能會在一些情況下想要混合 EventStream 類型。</span><span class="sxs-lookup"><span data-stu-id="a66f8-132">There are scenarios in which you may want to mix EventStream types.</span></span> <span data-ttu-id="a66f8-133">例如在管線處理中，您可能會想要擷取 BAM 中的特定資料，而不論管線是否回復其交易。</span><span class="sxs-lookup"><span data-stu-id="a66f8-133">For example, in a pipeline processing, you may want to capture the particular data in BAM regardless of whether the pipeline is rolling back its transaction.</span></span> <span data-ttu-id="a66f8-134">特別是，您可能會想要擷取在管線處理期間有多少訊息失敗及多少重試次數的相關資料。</span><span class="sxs-lookup"><span data-stu-id="a66f8-134">In particular, you may want capture data about how many messages failed or how many retries there were during pipeline processing.</span></span> <span data-ttu-id="a66f8-135">若要在這種情況下擷取資料，您應該使用 BES。</span><span class="sxs-lookup"><span data-stu-id="a66f8-135">To capture the data in this situation you should use BES.</span></span>  
  
 <span data-ttu-id="a66f8-136">所有的非同步 EventStream (BES、MES 和 OES) 都會先將資料保存在 BizTalk MessageBox 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="a66f8-136">All the asynchronous EventStreams (BES, MES, and OES) persist data first in the BizTalk MessageBox database.</span></span> <span data-ttu-id="a66f8-137">然後再由 Tracking Data Decode Service (TDDS) 定期處理資料，並將資料保存到 BAM 主要匯入資料庫中。</span><span class="sxs-lookup"><span data-stu-id="a66f8-137">Periodically the data is processed and persisted to the BAM Primary Import database by the Tracking Data Decode Service (TDDS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a66f8-138">為了確保 EventStream 呼叫不會從 BizTalk 應用程式產生瓶頸，建議您最好使用非同步 API。</span><span class="sxs-lookup"><span data-stu-id="a66f8-138">To ensure that EventStream calls do not create a bottleneck from a BizTalk application, we recommend that you use asynchronous APIs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a66f8-139">本節內容</span><span class="sxs-lookup"><span data-stu-id="a66f8-139">In This Section</span></span>  
  
-   [<span data-ttu-id="a66f8-140">OrchestrationEventStream</span><span class="sxs-lookup"><span data-stu-id="a66f8-140">OrchestrationEventStream</span></span>](../core/orchestrationeventstream.md)  
  
-   [<span data-ttu-id="a66f8-141">訊息事件資料流</span><span class="sxs-lookup"><span data-stu-id="a66f8-141">Messaging Event Streams</span></span>](../core/messaging-event-streams.md)