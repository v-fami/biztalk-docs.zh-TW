---
title: "SDK 範例 |Microsoft 文件"
description: "配接器、 應用程式部署、 BAM、 商務規則、 協調流程、 管線和 BizTalk Server 中提供更多的 SDK 範例"
ms.custom: 
ms.date: 10/17/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53bca653-e604-4452-8805-72632d3397c2
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5780e90260f591696e494411deff97a4cdc246f3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="samples-in-the-sdk"></a><span data-ttu-id="c5542-103">SDK 中的範例</span><span class="sxs-lookup"><span data-stu-id="c5542-103">Samples in the SDK</span></span>

## <a name="folder-paths"></a><span data-ttu-id="c5542-104">資料夾路徑</span><span class="sxs-lookup"><span data-stu-id="c5542-104">Folder paths</span></span>
<span data-ttu-id="c5542-105">本章節描述 30 個以上的範例包含在 Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]軟體開發套件 (SDK)。</span><span class="sxs-lookup"><span data-stu-id="c5542-105">This section describes more than 30 samples included in the Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Software Development Kit (SDK).</span></span> <span data-ttu-id="c5542-106">本節提供有關每個範例，包括建置範例、 如何執行此程式碼，和預期的結果指示的詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="c5542-106">The section provides detailed information about each sample, including instructions for building the sample, how to run it, and what results to expect.</span></span>  
  
 <span data-ttu-id="c5542-107">這些範例說明文件會使用路徑縮寫\<*範例路徑*\>來代表您的安裝中的範例的路徑。</span><span class="sxs-lookup"><span data-stu-id="c5542-107">The samples documentation uses the path abbreviation \<*Samples Path*\> to denote the path to the samples in your installation.</span></span> <span data-ttu-id="c5542-108">預設路徑可能隨著安裝期間所做的選擇而不同。</span><span class="sxs-lookup"><span data-stu-id="c5542-108">The default for the path can vary based on decisions made during installation.</span></span> <span data-ttu-id="c5542-109">下表提供一般安裝案例的預設路徑。</span><span class="sxs-lookup"><span data-stu-id="c5542-109">The following table provides the default path for common installation scenarios.</span></span>  
  
|<span data-ttu-id="c5542-110">Description</span><span class="sxs-lookup"><span data-stu-id="c5542-110">Description</span></span>|<span data-ttu-id="c5542-111">路徑</span><span class="sxs-lookup"><span data-stu-id="c5542-111">Path</span></span>|  
|-----------------|----------|  
|<span data-ttu-id="c5542-112">安裝在 32 位元平台上</span><span class="sxs-lookup"><span data-stu-id="c5542-112">Installation on 32-bit platform</span></span>|[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="c5542-113">\SDK\Samples</span><span class="sxs-lookup"><span data-stu-id="c5542-113">\SDK\Samples</span></span>|  
|<span data-ttu-id="c5542-114">在 64 位元平台上安裝。</span><span class="sxs-lookup"><span data-stu-id="c5542-114">Installation on a 64-bit platform.</span></span>|[!INCLUDE[btsBizTalkServerPathx64](../includes/btsbiztalkserverpathx64-md.md)]<span data-ttu-id="c5542-115">\SDK\Samples</span><span class="sxs-lookup"><span data-stu-id="c5542-115">\SDK\Samples</span></span>|  
  
> [!IMPORTANT]
>  <span data-ttu-id="c5542-116">為了簡化起見，這個 SDK 中的範例以及本說明文件會假設您使用 BizTalk Server 的單一電腦開發人員安裝。</span><span class="sxs-lookup"><span data-stu-id="c5542-116">For the sake of simplicity, the samples in this SDK, and this documentation, assume that you are using a single computer developer installation of BizTalk Server.</span></span> <span data-ttu-id="c5542-117">如果您不會執行完整安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，某些範例可能無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="c5542-117">If you do not perform a complete installation of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], some samples may not work properly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5542-118">所有的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]SDK 項目提供英文版和僅支援英文語言安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c5542-118">All of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SDK items are provided in English and are supported only for English-language installations of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="available-samples"></a><span data-ttu-id="c5542-119">可用的範例</span><span class="sxs-lookup"><span data-stu-id="c5542-119">Available samples</span></span> 
  
-   [<span data-ttu-id="c5542-120">配接器範例 - 開發</span><span class="sxs-lookup"><span data-stu-id="c5542-120">Adapter Samples - Development</span></span>](../core/adapter-samples-development.md)  
  
-   [<span data-ttu-id="c5542-121">配接器範例 - 用法</span><span class="sxs-lookup"><span data-stu-id="c5542-121">Adapter Samples - Usage</span></span>](../core/adapter-samples-usage.md)  
  
-   [<span data-ttu-id="c5542-122">Admin (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="c5542-122">Admin (BizTalk Server Samples Folder)</span></span>](../core/admin-biztalk-server-samples-folder.md)  
  
-   [<span data-ttu-id="c5542-123">應用程式部署 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="c5542-123">Application Deployment (BizTalk Server Samples Folder)</span></span>](../core/application-deployment-biztalk-server-samples-folder.md)  
  
-   [<span data-ttu-id="c5542-124">商務活動監控 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="c5542-124">Business Activity Monitoring (BizTalk Server Samples Folder)</span></span>](../core/business-activity-monitoring-biztalk-server-samples-folder.md)  
  
-   [<span data-ttu-id="c5542-125">商務規則 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="c5542-125">Business Rules (BizTalk Server Samples Folder)</span></span>](../core/business-rules-biztalk-server-samples-folder.md)  
  
-   [<span data-ttu-id="c5542-126">EDI 和 AS2 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="c5542-126">EDI and AS2 (BizTalk Server Samples Folder)</span></span>](../core/edi-and-as2-biztalk-server-samples-folder.md)  
  
-   [<span data-ttu-id="c5542-127">傳訊 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="c5542-127">Messaging (BizTalk Server Samples Folder)</span></span>](../core/messaging-biztalk-server-samples-folder.md)  
  
-   [<span data-ttu-id="c5542-128">協調流程 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="c5542-128">Orchestrations (BizTalk Server Samples Folder)</span></span>](../core/orchestrations-biztalk-server-samples-folder.md)  
  
-   [<span data-ttu-id="c5542-129">管線 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="c5542-129">Pipelines (BizTalk Server Samples Folder)</span></span>](../core/pipelines-biztalk-server-samples-folder.md)  
  
-   [<span data-ttu-id="c5542-130">SSO (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="c5542-130">SSO (BizTalk Server Samples Folder)</span></span>](../core/sso-biztalk-server-samples-folder.md)  
  
-   [<span data-ttu-id="c5542-131">XML 工具 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="c5542-131">XML Tools (BizTalk Server Samples Folder)</span></span>](../core/xml-tools-biztalk-server-samples-folder.md)