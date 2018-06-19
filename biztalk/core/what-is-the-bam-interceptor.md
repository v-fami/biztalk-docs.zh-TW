---
title: 何謂 BAM 攔截器？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAM Interceptor object
- BAM, collecting data
- BAM, Interceptor object
- data, collecting [BAM]
ms.assetid: e0213c4e-e2f4-4bb0-bd27-e5810f7e39d9
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9400e80a2f8e8acfdeb12e3d6e61a046151d1e7e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289798"
---
# <a name="what-is-the-bam-interceptor"></a><span data-ttu-id="bc91d-103">何謂 BAM 攔截器？</span><span class="sxs-lookup"><span data-stu-id="bc91d-103">What Is the BAM Interceptor?</span></span>
## <a name="overview"></a><span data-ttu-id="bc91d-104">概觀</span><span class="sxs-lookup"><span data-stu-id="bc91d-104">Overview</span></span> 

<span data-ttu-id="bc91d-105">BAM 攔截器是可讓您檢測應用程式以擷取感興趣的資料的物件。</span><span class="sxs-lookup"><span data-stu-id="bc91d-105">The BAM Interceptor is an object that lets you instrument your application to capture data of interest.</span></span> <span data-ttu-id="bc91d-106">下圖顯示 BAM 攔截器的角色以及與其他 BAM 元件的互動：</span><span class="sxs-lookup"><span data-stu-id="bc91d-106">The following diagram shows the role of the BAM interceptor and its interaction with the other BAM components:</span></span>  
  
 ![](../core/media/bam-config-api.gif "bam_config_api")  
<span data-ttu-id="bc91d-107">BAM 攔截器</span><span class="sxs-lookup"><span data-stu-id="bc91d-107">BAM Interceptor</span></span>  
  
 <span data-ttu-id="bc91d-108">在可能有感興趣資料的每個應用程式步驟中，您呼叫攔截器 OnStep、提供步驟的識別碼，以及提供您在應用程式中使用的某些資料或任意物件。</span><span class="sxs-lookup"><span data-stu-id="bc91d-108">In each step of your application where you could have data of interest, you call Interceptor OnStep, provide an identifier for the step, and provide some data or arbitrary object that you are using in your application.</span></span>  
  
 <span data-ttu-id="bc91d-109">您必須實作回呼函式，如此，當回呼發生時，回呼程序便會取得目前的步驟識別碼和資料物件。</span><span class="sxs-lookup"><span data-stu-id="bc91d-109">You must implement a callback function so when the callback occurs, your callback procedure gets the current step ID and your data object.</span></span> <span data-ttu-id="bc91d-110">基本上 BAM 攔截器只是將資料物件傳播至回呼。</span><span class="sxs-lookup"><span data-stu-id="bc91d-110">Essentially, the BAM interceptor is simply propagating the data object to the callback.</span></span> <span data-ttu-id="bc91d-111">擷取資料的實際邏輯存在於應用程式中。</span><span class="sxs-lookup"><span data-stu-id="bc91d-111">The actual logic of extracting data resides in your application.</span></span> <span data-ttu-id="bc91d-112">例如，如果資料使用 XML 訊息的形式，則回呼將使用 XPath。</span><span class="sxs-lookup"><span data-stu-id="bc91d-112">For example, if your data takes the form of XML messages, then the callback will use XPaths.</span></span> <span data-ttu-id="bc91d-113">如需有關 Xpath 的詳細資訊，請參閱[訊息指派中使用的 Xpath](../core/using-xpaths-in-message-assignments.md)。</span><span class="sxs-lookup"><span data-stu-id="bc91d-113">For more information about XPaths, see [Using XPaths in Message Assignment](../core/using-xpaths-in-message-assignments.md).</span></span>  
  
 <span data-ttu-id="bc91d-114">BAM 攔截器會根據以程式設計方式建立的組態，決定要在每個步驟要求哪些資料。</span><span class="sxs-lookup"><span data-stu-id="bc91d-114">The BAM interceptor decides which data to request at each step, based on the configuration that you can create programmatically.</span></span> <span data-ttu-id="bc91d-115">然後，BAM 攔截器會使用取得的資料呼叫所需的 DirectEventStream 或 BufferedEventStream，以便持續執行並將每次的時間當做引數傳遞給 OnStep。</span><span class="sxs-lookup"><span data-stu-id="bc91d-115">The BAM Interceptor then uses the obtained data to call either DirectEventStream or BufferedEventStream that you need to keep around and pass each time as an argument to OnStep.</span></span>  
  
 <span data-ttu-id="bc91d-116">呼叫每個步驟的攔截器並不是需要大量資源的作業。</span><span class="sxs-lookup"><span data-stu-id="bc91d-116">Calling the interceptor for each step is not a resource-intensive operation.</span></span> <span data-ttu-id="bc91d-117">如果您發出呼叫且此步驟沒有註冊任何資料，攔截器就會立即返回。</span><span class="sxs-lookup"><span data-stu-id="bc91d-117">If you call and you register nothing for this step, the interceptor returns immediately.</span></span> <span data-ttu-id="bc91d-118">這表示沒有磁碟作業、沒有交易，甚至沒有記憶體配置，因此，幾乎不會對效能造成影響。</span><span class="sxs-lookup"><span data-stu-id="bc91d-118">This means that there are no disk operations, no transactions, not even memory allocations, and thus almost no performance impact.</span></span> <span data-ttu-id="bc91d-119">同時，您有機會擷取 BAM 的任何資料 (如果需要的話)。</span><span class="sxs-lookup"><span data-stu-id="bc91d-119">At the same time, you have the opportunity to extract any data for BAM if necessary.</span></span> <span data-ttu-id="bc91d-120">受到的效能影響牽涉到資料擷取和資料的可用性的步驟將取決於您的實作`IBAMDataExtractor Interface`。</span><span class="sxs-lookup"><span data-stu-id="bc91d-120">The performance impact on the steps involving data extraction and the availability of the data will depend on your implementation of the `IBAMDataExtractor Interface`.</span></span>  
  
 <span data-ttu-id="bc91d-121">下列程式碼範例示範如何在組態和執行階段期間使用攔截器。</span><span class="sxs-lookup"><span data-stu-id="bc91d-121">The following code examples demonstrate the use of the interceptor during configuration and run time.</span></span>  
  
## <a name="configuration-time"></a><span data-ttu-id="bc91d-122">組態階段</span><span class="sxs-lookup"><span data-stu-id="bc91d-122">Configuration time</span></span>  
 <span data-ttu-id="bc91d-123">下列程式碼示範如何設定攔截器停止在應用程式的步驟 recvPO，並且要求「客戶名稱」和「客戶 SSN」：</span><span class="sxs-lookup"><span data-stu-id="bc91d-123">The following code shows how you configure the Interceptor to stop at step recvPO of the application, and ask for Customer Name and Customer SSN:</span></span>  
  
```  
ActivityInterceptorConfiguration cfg= new ActivityInterceptorConfiguration ("PurchaseOrder");  
...  
cfg.RegisterDataExtraction("CustomerName",recvPO,XpathName);  
cfg.RegisterDataExtraction("CustomerSSN",recvPO,XpathSSN);  
...  
BAMInterceptor interceptor=new BAMInterceptor();  
cfg.UpdateInterceptor(interceptor);  
...  
// The interceptor instance is ready.  
```  
  
 <span data-ttu-id="bc91d-124">建立攔截器執行個體之後，您就可以儲存攔截器執行個體，以便稍後在執行階段使用。</span><span class="sxs-lookup"><span data-stu-id="bc91d-124">After you create an interceptor instance, you can store it for later use at runtime.</span></span>  
  
 <span data-ttu-id="bc91d-125">您可以保留預先建立的不同攔截器，那些攔截器代表 BAM 資料和里程碑的不同喜好設定。</span><span class="sxs-lookup"><span data-stu-id="bc91d-125">You may keep different pre-created interceptors representing different preferences for the data and milestones for BAM.</span></span> <span data-ttu-id="bc91d-126">為了得到最佳效能，請使用 BinaryFormatter 類別序列化攔截器執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc91d-126">For best performance, serialize the Interceptor instances using the BinaryFormatter class.</span></span>  
  
## <a name="run-time"></a><span data-ttu-id="bc91d-127">執行階段</span><span class="sxs-lookup"><span data-stu-id="bc91d-127">Run time</span></span>  
 <span data-ttu-id="bc91d-128">使用下列程式碼，以便在實際執行環境中的執行階段使用攔截器：</span><span class="sxs-lookup"><span data-stu-id="bc91d-128">Use this code to use the interceptor at runtime in a production environment:</span></span>  
  
```  
// Deserialize the Interceptor that was prepared before  
...  
es=new DirectEventStream(...)  
...  
Interceptor.OnStep(recvPO, data1, es, callback)  
...  
Interceptor.OnStep(approvePO, data2, es, callback)  
...  
```  
  
 <span data-ttu-id="bc91d-129">其中：</span><span class="sxs-lookup"><span data-stu-id="bc91d-129">Where:</span></span>  
  
-   <span data-ttu-id="bc91d-130">*recvPO*和*approvePO*是任意的物件，您用來識別您的應用程式中的步驟。</span><span class="sxs-lookup"><span data-stu-id="bc91d-130">*recvPO* and *approvePO* are arbitrary objects you use to identify the steps in your application.</span></span>  
  
-   <span data-ttu-id="bc91d-131">*data1*和*data2*是任意的物件，您已在該點，並可能包含感興趣的資料 – 例如訂單的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="bc91d-131">*data1* and *data2* are arbitrary objects that you have at that point and may contain interesting data – for example the XML document of the purchase order.</span></span>  
  
-   <span data-ttu-id="bc91d-132">*es*是 DirectEventStream 或 BufferedEvent 資料流，視效能需求而定。</span><span class="sxs-lookup"><span data-stu-id="bc91d-132">*es* is either DirectEventStream or BufferedEvent stream depending on your performance requirements.</span></span>  
  
-   <span data-ttu-id="bc91d-133">*回呼*是實作`IBAMDataExtractor Interface`。</span><span class="sxs-lookup"><span data-stu-id="bc91d-133">*callback* is your implementation of the `IBAMDataExtractor Interface`.</span></span>  
  
 <span data-ttu-id="bc91d-134">Sdk > 範例[BAM API （BizTalk Server 範例）](../core/bam-api-biztalk-server-sample.md)，示範如何使用攔截器，其中包含這兩種組態工具和範例執行階段應用程式。</span><span class="sxs-lookup"><span data-stu-id="bc91d-134">The SDK sample, [BAM API (BizTalk Server Sample)](../core/bam-api-biztalk-server-sample.md), demonstrates using the Interceptor, which contains both a configuration tool and example runtime application.</span></span>  
  
 <span data-ttu-id="bc91d-135">BizTalk 協調流程引擎會配合攔截，以允許在執行階段使用追蹤設定檔編輯器變更為 BAM 收集的資料。</span><span class="sxs-lookup"><span data-stu-id="bc91d-135">The BizTalk Orchestration Engine accommodates interception, which allows changing what data is collected for BAM at runtime using the Tracking Profile Editor.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bc91d-136">本節內容</span><span class="sxs-lookup"><span data-stu-id="bc91d-136">In This Section</span></span>  
  
-   [<span data-ttu-id="bc91d-137">如何判斷和設定活動事件寫入者角色</span><span class="sxs-lookup"><span data-stu-id="bc91d-137">How to Determine and Set Event Writer Roles for Activities</span></span>](../core/how-to-determine-and-set-event-writer-roles-for-activities.md)  
  
## <a name="see-also"></a><span data-ttu-id="bc91d-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc91d-138">See Also</span></span>  
 [<span data-ttu-id="bc91d-139">BAM API （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="bc91d-139">BAM API (BizTalk Server Sample)</span></span>](../core/bam-api-biztalk-server-sample.md)