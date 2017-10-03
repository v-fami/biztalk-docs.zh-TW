---
title: "BizTalk Server 如何具現化配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ebe7585-5939-4142-9281-990b4849e28d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b32e6e40bf39c09e747391bba51a54143fc67e57
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-biztalk-server-instantiates-an-adapter"></a><span data-ttu-id="bd09b-102">BizTalk Server 如何具現化配接器</span><span class="sxs-lookup"><span data-stu-id="bd09b-102">How BizTalk Server Instantiates an Adapter</span></span>
<span data-ttu-id="bd09b-103">當 BizTalk 服務啟動時，便會具現化所有的接收配接器 (只要這些配接器具有一個或多個已設定的使用中接收位置)。</span><span class="sxs-lookup"><span data-stu-id="bd09b-103">When the BizTalk service starts, all receive adapters are instantiated, as long as they have one or more configured and active receive locations.</span></span> <span data-ttu-id="bd09b-104">根據預設，在「傳訊引擎」從佇列移除使用某個傳送配接器所傳送的第一個訊息前，不會具現化該傳送配接器</span><span class="sxs-lookup"><span data-stu-id="bd09b-104">By default a send adapter is not instantiated until the Messaging Engine removes from the queue the first message to be sent by using that send adapter.</span></span> <span data-ttu-id="bd09b-105">（這有時候稱為 「 延遲建立 」。）不過，如果您需要具現化傳送配接器服務啟動時，您可以使用**InitTransmitterOnServiceStart**配接器功能。</span><span class="sxs-lookup"><span data-stu-id="bd09b-105">(This is sometimes called "lazy creation.") However, if you need to instantiate a send adapter on service startup, you can use the **InitTransmitterOnServiceStart** adapter capability.</span></span> <span data-ttu-id="bd09b-106">這樣便會指引「傳訊引擎」在服務啟動時建立傳送配接器，而非使用預設的延遲建立。</span><span class="sxs-lookup"><span data-stu-id="bd09b-106">This directs the Messaging Engine to create the send adapter on service startup rather than using the default lazy creation.</span></span> <span data-ttu-id="bd09b-107">當沒有在端點上設定配接器時，預設的延遲建立方法有助於減少系統資源的使用量。</span><span class="sxs-lookup"><span data-stu-id="bd09b-107">The default lazy creation approach helps to reduce the amount of system resources used when adapters are not configured on endpoints.</span></span>  
  
 <span data-ttu-id="bd09b-108">當您建立自訂配接器時，建議您使用 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="bd09b-108">When you create a custom adapter, we recommend that you use managed code.</span></span> <span data-ttu-id="bd09b-109">然而，也有可能使用原生的 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="bd09b-109">However, it is possible to use native COM components.</span></span> <span data-ttu-id="bd09b-110">COM 元件的配接器中執行個體化時正常方式使用**CoCreateInstance**。</span><span class="sxs-lookup"><span data-stu-id="bd09b-110">For COM components the adapter is instantiated in the normal manner using **CoCreateInstance**.</span></span>  
  
 <span data-ttu-id="bd09b-111">Managed 程式碼，您必須指定.NET**類型**組態檔案中的組件路徑為選擇性。</span><span class="sxs-lookup"><span data-stu-id="bd09b-111">For managed code, you need to specify the .NET **type** in the configuration file; the assembly path is optional.</span></span>  
  
 <span data-ttu-id="bd09b-112">下列是可能的部署選項：</span><span class="sxs-lookup"><span data-stu-id="bd09b-112">The following deployment options are possible:</span></span>  
  
|<span data-ttu-id="bd09b-113">.NET 類型</span><span class="sxs-lookup"><span data-stu-id="bd09b-113">.NET type</span></span>|<span data-ttu-id="bd09b-114">組件路徑</span><span class="sxs-lookup"><span data-stu-id="bd09b-114">Assembly path</span></span>|<span data-ttu-id="bd09b-115">組件部署方法</span><span class="sxs-lookup"><span data-stu-id="bd09b-115">Assembly deployment method</span></span>|  
|---------------|-------------------|--------------------------------|  
|<span data-ttu-id="bd09b-116">已指定</span><span class="sxs-lookup"><span data-stu-id="bd09b-116">Specified</span></span>|<span data-ttu-id="bd09b-117">未指定</span><span class="sxs-lookup"><span data-stu-id="bd09b-117">Not specified</span></span>|<span data-ttu-id="bd09b-118">使用與組件相同的名稱，將組件 XCopy 到產品目錄，或是產品目錄中的子目錄</span><span class="sxs-lookup"><span data-stu-id="bd09b-118">XCopy assembly to product directory or subdirectory in product directory with the same name as the assembly</span></span>|  
|<span data-ttu-id="bd09b-119">已指定</span><span class="sxs-lookup"><span data-stu-id="bd09b-119">Specified</span></span>|<span data-ttu-id="bd09b-120">未指定</span><span class="sxs-lookup"><span data-stu-id="bd09b-120">Not specified</span></span>|<span data-ttu-id="bd09b-121">全域組件快取 (GAC) 組件</span><span class="sxs-lookup"><span data-stu-id="bd09b-121">Global assembly cache (GAC) assembly</span></span>|  
|<span data-ttu-id="bd09b-122">已指定</span><span class="sxs-lookup"><span data-stu-id="bd09b-122">Specified</span></span>|<span data-ttu-id="bd09b-123">已指定</span><span class="sxs-lookup"><span data-stu-id="bd09b-123">Specified</span></span>|<span data-ttu-id="bd09b-124">將組件複製至指定的目錄</span><span class="sxs-lookup"><span data-stu-id="bd09b-124">XCopy assembly to specified directory</span></span>|  
  
 <span data-ttu-id="bd09b-125">**疑難排解秘訣：**當您建立配接器使用 managed 程式碼，如果在建立失敗時，則使用 fuslogvw.exe 工具來判斷是否有無法解析的組件的參考。</span><span class="sxs-lookup"><span data-stu-id="bd09b-125">**Troubleshooting Tip:** When you create an adapter using managed code, if the creation fails, use the fuslogvw.exe tool to determine if there are references to assemblies that cannot be resolved.</span></span> <span data-ttu-id="bd09b-126">這是常見的錯誤。</span><span class="sxs-lookup"><span data-stu-id="bd09b-126">This is a common mistake.</span></span>  
  
 <span data-ttu-id="bd09b-127">下圖顯示根據指定的組態而建立配接器的邏輯：</span><span class="sxs-lookup"><span data-stu-id="bd09b-127">The following figure shows the logic for creating adapters, depending on the configuration specified:</span></span>  
  
 ![](../core/media/initializingtheadapter.gif "InitializingTheAdapter")  
  
 <span data-ttu-id="bd09b-128">下表提供如何設定接收配接器的範例，以及設定執行階段組件的方式。</span><span class="sxs-lookup"><span data-stu-id="bd09b-128">The following table gives an example of how a receive adapter may be configured, and the ways the run-time assembly may be configured.</span></span>  
  
|<span data-ttu-id="bd09b-129">組件部署方法</span><span class="sxs-lookup"><span data-stu-id="bd09b-129">Assembly deployment method</span></span>|<span data-ttu-id="bd09b-130">InboundTypeName</span><span class="sxs-lookup"><span data-stu-id="bd09b-130">InboundTypeName</span></span>|<span data-ttu-id="bd09b-131">InboundAssemblyPath</span><span class="sxs-lookup"><span data-stu-id="bd09b-131">InboundAssemblyPath</span></span>|  
|--------------------------------|---------------------|-------------------------|  
|<span data-ttu-id="bd09b-132">指定組件位置</span><span class="sxs-lookup"><span data-stu-id="bd09b-132">Specify assembly location</span></span>|<span data-ttu-id="bd09b-133">Microsoft.Samples.MyReceiveAdapter</span><span class="sxs-lookup"><span data-stu-id="bd09b-133">Microsoft.Samples.MyReceiveAdapter</span></span>|<span data-ttu-id="bd09b-134">C:\MyAdapter\MyAdapter.dll</span><span class="sxs-lookup"><span data-stu-id="bd09b-134">C:\MyAdapter\MyAdapter.dll</span></span>|  
|<span data-ttu-id="bd09b-135">指定 .NET 類型 (包括公開金鑰、版本及文化特性資訊)</span><span class="sxs-lookup"><span data-stu-id="bd09b-135">Specify .NET type (include public key, version, and culture information)</span></span>|<span data-ttu-id="bd09b-136">Microsoft.Samples.MyReceiveAdapter，MyReceiveAdapter，版本 = 1.0.2510.24622，Culture = neutral，PublicKeyToken = 077cf886a2d1c020</span><span class="sxs-lookup"><span data-stu-id="bd09b-136">Microsoft.Samples.MyReceiveAdapter, MyReceiveAdapter, Version=1.0.2510.24622, Culture=neutral, PublicKeyToken=077cf886a2d1c020</span></span>|<span data-ttu-id="bd09b-137">不適用</span><span class="sxs-lookup"><span data-stu-id="bd09b-137">N/A</span></span>|  
|<span data-ttu-id="bd09b-138">GAC 組件</span><span class="sxs-lookup"><span data-stu-id="bd09b-138">GAC assembly</span></span>|<span data-ttu-id="bd09b-139">Microsoft.Samples.MyReceiveAdapter，MyReceiveAdapter，版本 = 1.0.2510.24622，Culture = neutral，PublicKeyToken = 077cf886a2d1c020</span><span class="sxs-lookup"><span data-stu-id="bd09b-139">Microsoft.Samples.MyReceiveAdapter, MyReceiveAdapter, Version=1.0.2510.24622, Culture=neutral, PublicKeyToken=077cf886a2d1c020</span></span>|<span data-ttu-id="bd09b-140">不適用</span><span class="sxs-lookup"><span data-stu-id="bd09b-140">N/A</span></span>|