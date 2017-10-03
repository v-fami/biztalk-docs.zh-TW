---
title: "SDK 中的範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, SDK
- SDK examples
- examples
ms.assetid: 53bca653-e604-4452-8805-72632d3397c2
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f42429ed2aa9b6a074a62e472ca804caad676f84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="samples-in-the-sdk"></a><span data-ttu-id="c8df2-102">SDK 中的範例</span><span class="sxs-lookup"><span data-stu-id="c8df2-102">Samples in the SDK</span></span>
## <a name="folder-paths"></a><span data-ttu-id="c8df2-103">資料夾路徑</span><span class="sxs-lookup"><span data-stu-id="c8df2-103">Folder paths</span></span>
<span data-ttu-id="c8df2-104">本章節描述 30 個以上的範例包含在 Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]軟體開發套件 (SDK)。</span><span class="sxs-lookup"><span data-stu-id="c8df2-104">This section describes more than 30 samples included in the Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Software Development Kit (SDK).</span></span> <span data-ttu-id="c8df2-105">本節提供有關每個範例，包括建置範例、 如何執行此程式碼，和預期的結果指示的詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="c8df2-105">The section provides detailed information about each sample, including instructions for building the sample, how to run it, and what results to expect.</span></span>  
  
 <span data-ttu-id="c8df2-106">這些範例說明文件會使用路徑縮寫\<*範例路徑*> 來代表您的安裝中的範例的路徑。</span><span class="sxs-lookup"><span data-stu-id="c8df2-106">The samples documentation uses the path abbreviation \<*Samples Path*> to denote the path to the samples in your installation.</span></span> <span data-ttu-id="c8df2-107">預設路徑可能隨著安裝期間所做的選擇而不同。</span><span class="sxs-lookup"><span data-stu-id="c8df2-107">The default for the path can vary based on decisions made during installation.</span></span> <span data-ttu-id="c8df2-108">下表提供一般安裝案例的預設路徑。</span><span class="sxs-lookup"><span data-stu-id="c8df2-108">The following table provides the default path for common installation scenarios.</span></span>  
  
|<span data-ttu-id="c8df2-109">Description</span><span class="sxs-lookup"><span data-stu-id="c8df2-109">Description</span></span>|<span data-ttu-id="c8df2-110">路徑</span><span class="sxs-lookup"><span data-stu-id="c8df2-110">Path</span></span>|  
|-----------------|----------|  
|<span data-ttu-id="c8df2-111">安裝在 32 位元平台上</span><span class="sxs-lookup"><span data-stu-id="c8df2-111">Installation on 32-bit platform</span></span>|[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="c8df2-112">\SDK\Samples</span><span class="sxs-lookup"><span data-stu-id="c8df2-112">\SDK\Samples</span></span>|  
|<span data-ttu-id="c8df2-113">在 64 位元平台上安裝。</span><span class="sxs-lookup"><span data-stu-id="c8df2-113">Installation on a 64-bit platform.</span></span>|[!INCLUDE[btsBizTalkServerPathx64](../includes/btsbiztalkserverpathx64-md.md)]<span data-ttu-id="c8df2-114">\SDK\Samples</span><span class="sxs-lookup"><span data-stu-id="c8df2-114">\SDK\Samples</span></span>|  
  
> [!IMPORTANT]
>  <span data-ttu-id="c8df2-115">為了簡化起見，這個 SDK 中的範例以及本說明文件會假設您使用 BizTalk Server 的單一電腦開發人員安裝。</span><span class="sxs-lookup"><span data-stu-id="c8df2-115">For the sake of simplicity, the samples in this SDK, and this documentation, assume that you are using a single computer developer installation of BizTalk Server.</span></span> <span data-ttu-id="c8df2-116">如果您不會執行完整安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，某些範例可能無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="c8df2-116">If you do not perform a complete installation of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], some samples may not work properly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8df2-117">所有的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]SDK 項目提供英文版和僅支援英文語言安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c8df2-117">All of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SDK items are provided in English and are supported only for English-language installations of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="available-samples"></a><span data-ttu-id="c8df2-118">可用的範例</span><span class="sxs-lookup"><span data-stu-id="c8df2-118">Available samples</span></span> 
  
-   [<span data-ttu-id="c8df2-119">取得其他範例</span><span class="sxs-lookup"><span data-stu-id="c8df2-119">Get More Samples</span></span>](../core/get-more-samples.md)  
  
-   [<span data-ttu-id="c8df2-120">配接器範例-開發</span><span class="sxs-lookup"><span data-stu-id="c8df2-120">Adapter Samples - Development</span></span>](../core/adapter-samples-development.md)  
  
-   [<span data-ttu-id="c8df2-121">配接器範例-使用方式</span><span class="sxs-lookup"><span data-stu-id="c8df2-121">Adapter Samples - Usage</span></span>](../core/adapter-samples-usage.md)  
  
-   [<span data-ttu-id="c8df2-122">系統管理員 （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="c8df2-122">Admin (BizTalk Server Samples Folder)</span></span>](../core/admin-biztalk-server-samples-folder.md)  
  
-   [<span data-ttu-id="c8df2-123">應用程式部署 （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="c8df2-123">Application Deployment (BizTalk Server Samples Folder)</span></span>](../core/application-deployment-biztalk-server-samples-folder.md)  
  
-   [<span data-ttu-id="c8df2-124">商務活動監控 （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="c8df2-124">Business Activity Monitoring (BizTalk Server Samples Folder)</span></span>](../core/business-activity-monitoring-biztalk-server-samples-folder.md)  
  
-   [<span data-ttu-id="c8df2-125">商務規則 （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="c8df2-125">Business Rules (BizTalk Server Samples Folder)</span></span>](../core/business-rules-biztalk-server-samples-folder.md)  
  
-   [<span data-ttu-id="c8df2-126">EDI 和 AS2 （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="c8df2-126">EDI and AS2 (BizTalk Server Samples Folder)</span></span>](../core/edi-and-as2-biztalk-server-samples-folder.md)  
  
-   [<span data-ttu-id="c8df2-127">傳訊 （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="c8df2-127">Messaging (BizTalk Server Samples Folder)</span></span>](../core/messaging-biztalk-server-samples-folder.md)  
  
-   [<span data-ttu-id="c8df2-128">協調流程 （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="c8df2-128">Orchestrations (BizTalk Server Samples Folder)</span></span>](../core/orchestrations-biztalk-server-samples-folder.md)  
  
-   [<span data-ttu-id="c8df2-129">管線 （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="c8df2-129">Pipelines (BizTalk Server Samples Folder)</span></span>](../core/pipelines-biztalk-server-samples-folder.md)  
  
-   [<span data-ttu-id="c8df2-130">SSO （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="c8df2-130">SSO (BizTalk Server Samples Folder)</span></span>](../core/sso-biztalk-server-samples-folder.md)  
  
-   [<span data-ttu-id="c8df2-131">XML 工具 （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="c8df2-131">XML Tools (BizTalk Server Samples Folder)</span></span>](../core/xml-tools-biztalk-server-samples-folder.md)