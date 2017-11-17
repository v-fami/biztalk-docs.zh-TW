---
title: "系統管理員 ExplorerOM （BizTalk Server 範例資料夾） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, administering
- administering, examples
ms.assetid: f6553138-9ab3-4368-84bf-9813e909e372
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b8b33db0460a5e44ecfcd732535022bb28940d3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="admin-explorerom-biztalk-server-samples-folder"></a><span data-ttu-id="0b85d-102">系統管理員 ExplorerOM （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="0b85d-102">Admin-ExplorerOM (BizTalk Server Samples Folder)</span></span>
<span data-ttu-id="0b85d-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在其軟體開發套件 (SDK) 的 Admin\ExplorerOM 資料夾中包含了範例。</span><span class="sxs-lookup"><span data-stu-id="0b85d-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes samples in the Admin\ExplorerOM folder in its software development kit (SDK).</span></span> <span data-ttu-id="0b85d-104">本節會詳細介紹每個 BizTalk 總管物件模型管理範例所示範的功能、用來建置和執行範例的指示，以及可預期結果。</span><span class="sxs-lookup"><span data-stu-id="0b85d-104">This section provides detailed information about the functionality demonstrated by each BizTalk Explorer object model administration sample, instructions for building and running the sample, and the results you can expect.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="0b85d-105">如果在部署後不需要部署指令碼，就應該將其移除。</span><span class="sxs-lookup"><span data-stu-id="0b85d-105">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="0b85d-106">必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。</span><span class="sxs-lookup"><span data-stu-id="0b85d-106">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b85d-107">Microsoft.BizTalk.ExplorerOM.dll 同時支援 32 位元和 64 位元程序。</span><span class="sxs-lookup"><span data-stu-id="0b85d-107">Microsoft.BizTalk.ExplorerOM.dll supports both 32 bit and 64 bit processes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0b85d-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="0b85d-108">In This Section</span></span>  
  
-   <span data-ttu-id="0b85d-109">[（BizTalk Server 範例） ApplicationManager](../core/applicationmanager-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="0b85d-109">[ApplicationManager (BizTalk Server Sample)](../core/applicationmanager-biztalk-server-sample.md).</span></span> <span data-ttu-id="0b85d-110">示範如何啟動或停止 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0b85d-110">Demonstrates how to start or stop a BizTalk application.</span></span>  
  
-   <span data-ttu-id="0b85d-111">[（BizTalk Server 範例） BrowsingArtifacts](../core/browsingartifacts-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="0b85d-111">[BrowsingArtifacts (BizTalk Server Sample)](../core/browsingartifacts-biztalk-server-sample.md).</span></span> <span data-ttu-id="0b85d-112">示範如何列舉 BizTalk 成品和屬性。</span><span class="sxs-lookup"><span data-stu-id="0b85d-112">Demonstrates how to enumerate BizTalk artifacts and attributes.</span></span>  
  
-   <span data-ttu-id="0b85d-113">[CBR （BizTalk Server 範例）](../core/cbr-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="0b85d-113">[CBR (BizTalk Server Sample)](../core/cbr-biztalk-server-sample.md).</span></span> <span data-ttu-id="0b85d-114">示範如何加入和設定新的內容為基礎的路由的 BizTalk 訊息的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="0b85d-114">Demonstrates adding and configuring new send ports for content based routing of BizTalk messages.</span></span>  
  
-   <span data-ttu-id="0b85d-115">[DeleteParty （BizTalk Server 範例）](../core/deleteparty-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="0b85d-115">[DeleteParty (BizTalk Server Sample)](../core/deleteparty-biztalk-server-sample.md).</span></span> <span data-ttu-id="0b85d-116">示範如何刪除指定的合作對象。</span><span class="sxs-lookup"><span data-stu-id="0b85d-116">Demonstrates how to delete a specified party.</span></span>  
  
-   <span data-ttu-id="0b85d-117">[OrchestrationBinding （BizTalk Server 範例）](../core/orchestrationbinding-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="0b85d-117">[OrchestrationBinding (BizTalk Server Sample)](../core/orchestrationbinding-biztalk-server-sample.md).</span></span> <span data-ttu-id="0b85d-118">示範如何設定及管理協調流程。</span><span class="sxs-lookup"><span data-stu-id="0b85d-118">Demonstrates configuring and managing orchestrations.</span></span>  
  
-   <span data-ttu-id="0b85d-119">[（BizTalk Server 範例） PartnerManagement](../core/partnermanagement-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="0b85d-119">[PartnerManagement (BizTalk Server Sample)](../core/partnermanagement-biztalk-server-sample.md).</span></span> <span data-ttu-id="0b85d-120">示範如何建立和刪除合作對象。</span><span class="sxs-lookup"><span data-stu-id="0b85d-120">Demonstrates creating and deleting parties.</span></span> <span data-ttu-id="0b85d-121">也會示範與角色登錄和取消登錄合作對象。</span><span class="sxs-lookup"><span data-stu-id="0b85d-121">Also demonstrates enlisting and un-enlisting parties with roles.</span></span>  
  
-   <span data-ttu-id="0b85d-122">[ReceiveLocations （BizTalk Server 範例）](../core/receivelocations-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="0b85d-122">[ReceiveLocations (BizTalk Server Sample)](../core/receivelocations-biztalk-server-sample.md).</span></span> <span data-ttu-id="0b85d-123">示範如何建立和管理接收埠的接收位置。</span><span class="sxs-lookup"><span data-stu-id="0b85d-123">Demonstrates how to create and manage receive locations for receive ports.</span></span>  
  
-   <span data-ttu-id="0b85d-124">[接收埠 （BizTalk Server 範例）](../core/receiveports-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="0b85d-124">[ReceivePorts (BizTalk Server Sample)](../core/receiveports-biztalk-server-sample.md).</span></span> <span data-ttu-id="0b85d-125">示範建立、 列舉和刪除接收埠。</span><span class="sxs-lookup"><span data-stu-id="0b85d-125">Demonstrates creating, enumerating and deleting receive ports.</span></span>  
  
-   <span data-ttu-id="0b85d-126">[傳送埠群組 （BizTalk Server 範例）](../core/sendportgroups-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="0b85d-126">[SendPortGroups (BizTalk Server Sample)](../core/sendportgroups-biztalk-server-sample.md).</span></span> <span data-ttu-id="0b85d-127">示範如何列舉和管理傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="0b85d-127">Demonstrates how to enumerate and manage send port groups.</span></span>  
  
-   <span data-ttu-id="0b85d-128">[SendPorts （BizTalk Server 範例）](../core/sendports-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="0b85d-128">[SendPorts (BizTalk Server Sample)](../core/sendports-biztalk-server-sample.md).</span></span> <span data-ttu-id="0b85d-129">示範如何列舉和管理傳送埠。</span><span class="sxs-lookup"><span data-stu-id="0b85d-129">Demonstrates how to enumerate and manage send ports.</span></span>  
  
-   <span data-ttu-id="0b85d-130">[UnenlistParties （BizTalk Server 範例）](../core/unenlistparties-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="0b85d-130">[UnenlistParties (BizTalk Server Sample)](../core/unenlistparties-biztalk-server-sample.md).</span></span> <span data-ttu-id="0b85d-131">示範如何取消登錄與已部署 BizTalk 組件關聯的所有合作對象。</span><span class="sxs-lookup"><span data-stu-id="0b85d-131">Demonstrates how to unenlist all of the parties associated with a deployed BizTalk assembly.</span></span>