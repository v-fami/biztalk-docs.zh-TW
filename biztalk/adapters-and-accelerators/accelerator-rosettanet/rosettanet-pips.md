---
title: "RosettaNet Pip |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PIPs, clusters
- RosettaNet, PIPs
- PIPs, PIP specifications
- PIPs, segments
- PIPs, RosettaNet
- DTDs, DTD files
ms.assetid: 2f7e8db3-9ccb-403a-9fe7-58fbba3c4cb1
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1980f7c5e22259dc6c09d4f2d8dba31f3ac04d61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="rosettanet-pips"></a><span data-ttu-id="ae050-102">RosettaNet Pip</span><span class="sxs-lookup"><span data-stu-id="ae050-102">RosettaNet PIPs</span></span>
<span data-ttu-id="ae050-103">RosettaNet 組織建立並維護交易夥伴介面處理程序 (PIP) 以為所有 RosettaNet 訊息交換提供一般商務處理程序定義。</span><span class="sxs-lookup"><span data-stu-id="ae050-103">The RosettaNet organization creates and maintains Partner Interface Processes (PIPs) to provide common business-process definitions for all RosettaNet message exchanges.</span></span>  
  
 <span data-ttu-id="ae050-104">每個 PIP 規格都提供了文件類型定義 (DTD) 檔案以及訊息指導方針文件。</span><span class="sxs-lookup"><span data-stu-id="ae050-104">Each PIP specification provides a document type definition (DTD) file and a message guideline document.</span></span> <span data-ttu-id="ae050-105">DTD 檔案定義服務內容訊息結構。</span><span class="sxs-lookup"><span data-stu-id="ae050-105">The DTD file defines the service-content message structure.</span></span> <span data-ttu-id="ae050-106">訊息指導方針文件是可以閱讀的 HTML 檔案，其中指定元素階層條件約束。</span><span class="sxs-lookup"><span data-stu-id="ae050-106">The message-guideline document, which is a human-readable HTML file, specifies element-level constraints.</span></span> <span data-ttu-id="ae050-107">這兩者一起提供完整的商務程序定義。</span><span class="sxs-lookup"><span data-stu-id="ae050-107">Together, they provide a complete definition of the business process.</span></span>  
  
 <span data-ttu-id="ae050-108">如需有關 PIP 規格的詳細資訊，請參閱 RosettaNet 網站，網址[http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=33859)。</span><span class="sxs-lookup"><span data-stu-id="ae050-108">For more information about PIP specifications, see the RosettaNet Web site at [http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=33859).</span></span>  
  
## <a name="pip-contents"></a><span data-ttu-id="ae050-109">PIP 內容</span><span class="sxs-lookup"><span data-stu-id="ae050-109">PIP Contents</span></span>  
 <span data-ttu-id="ae050-110">PIP 規格執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ae050-110">A PIP specification does the following:</span></span>  
  
-   <span data-ttu-id="ae050-111">描述實作的公開程序模式</span><span class="sxs-lookup"><span data-stu-id="ae050-111">Describes which public process pattern it implements</span></span>  
  
-   <span data-ttu-id="ae050-112">描述設定公開程序的方法</span><span class="sxs-lookup"><span data-stu-id="ae050-112">Describes how to configure the public process</span></span>  
  
-   <span data-ttu-id="ae050-113">提供在 PIP 之內交換的文件參照。</span><span class="sxs-lookup"><span data-stu-id="ae050-113">Provides references to the documents to exchange within the PIP</span></span>  
  
 <span data-ttu-id="ae050-114">PIP 規格包含三個主要部分： 商務營運檢視 (BOV)、 功能服務檢視 (FSV) 以及實作架構檢視 (IFV)。</span><span class="sxs-lookup"><span data-stu-id="ae050-114">A PIP specification includes three major parts: a Business Operational View (BOV), Functional Service View (FSV), and an Implementation Framework View (IFV).</span></span> <span data-ttu-id="ae050-115">每個檢視都會指定元素階層條件約束：</span><span class="sxs-lookup"><span data-stu-id="ae050-115">Each of these views specifies element-level constraints:</span></span>  
  
-   <span data-ttu-id="ae050-116">BOV 指定商務資料實體及商務程序流程的語意，</span><span class="sxs-lookup"><span data-stu-id="ae050-116">The BOV specifies the semantics of business data entities and the business process flow.</span></span> <span data-ttu-id="ae050-117">描述開始和結束狀態，以及交易夥伴角色。</span><span class="sxs-lookup"><span data-stu-id="ae050-117">It describes start and end states, and partner roles.</span></span> <span data-ttu-id="ae050-118">並描述角色之間的互動，以及安全性、稽核和程序控制的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ae050-118">It describes the interaction between roles, and details security, audit, and process controls.</span></span> <span data-ttu-id="ae050-119">它指定商務文件及商務資料實體。</span><span class="sxs-lookup"><span data-stu-id="ae050-119">It specifies the business documents and business data entities.</span></span>  
  
-   <span data-ttu-id="ae050-120">FSV 指定網路元件服務、代理程式以及互動，</span><span class="sxs-lookup"><span data-stu-id="ae050-120">The FSV specifies network component services, agents, and interactions.</span></span> <span data-ttu-id="ae050-121">提供執行 PIP 所需的網路元件設計，並描述可能的網路元件互動。</span><span class="sxs-lookup"><span data-stu-id="ae050-121">It provides the network component design required to run the PIPs, and describes possible network component interactions.</span></span>  
  
-   <span data-ttu-id="ae050-122">IFV 指定執行 PIP 所需的網路通訊協定訊息格式和通訊需求。</span><span class="sxs-lookup"><span data-stu-id="ae050-122">The IFV specifies the network-protocol message formats and communication requirements required to run the PIP.</span></span>  
  
## <a name="clusters-and-segments"></a><span data-ttu-id="ae050-123">叢集與區段</span><span class="sxs-lookup"><span data-stu-id="ae050-123">Clusters and Segments</span></span>  
 <span data-ttu-id="ae050-124">您可以依照高層級商務功能 (叢集) 和副功能 (區段) 區分 PIP。</span><span class="sxs-lookup"><span data-stu-id="ae050-124">You categorize PIPs by a high-level business function (cluster) and a subfunction (segment).</span></span> <span data-ttu-id="ae050-125">叢集和區段會將商務訊息組織成可辨識的類別。</span><span class="sxs-lookup"><span data-stu-id="ae050-125">Clusters and segments organize business messages into recognizable categories.</span></span> <span data-ttu-id="ae050-126">下表列出這些叢集和區段。</span><span class="sxs-lookup"><span data-stu-id="ae050-126">The following table lists these clusters and segments.</span></span>  
  
|<span data-ttu-id="ae050-127">Clusters</span><span class="sxs-lookup"><span data-stu-id="ae050-127">Clusters</span></span>|<span data-ttu-id="ae050-128">區段</span><span class="sxs-lookup"><span data-stu-id="ae050-128">Segments</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="ae050-129">0: RosettaNet 支援</span><span class="sxs-lookup"><span data-stu-id="ae050-129">0: RosettaNet Support</span></span>|<span data-ttu-id="ae050-130">0A： 系統管理</span><span class="sxs-lookup"><span data-stu-id="ae050-130">0A: Administrative</span></span><br /><br /> <span data-ttu-id="ae050-131">0 C： 測試</span><span class="sxs-lookup"><span data-stu-id="ae050-131">0C: Testing</span></span>|  
|<span data-ttu-id="ae050-132">1： 交易夥伴產品 & 服務重新檢視</span><span class="sxs-lookup"><span data-stu-id="ae050-132">1: Partner Product & Service Review</span></span>|<span data-ttu-id="ae050-133">1A： 夥伴檢閱</span><span class="sxs-lookup"><span data-stu-id="ae050-133">1A: Partner Review</span></span><br /><br /> <span data-ttu-id="ae050-134">1B： 產品 & 服務重新檢視</span><span class="sxs-lookup"><span data-stu-id="ae050-134">1B: Product & Service Review</span></span>|  
|<span data-ttu-id="ae050-135">2： 產品資訊</span><span class="sxs-lookup"><span data-stu-id="ae050-135">2: Product Information</span></span>|<span data-ttu-id="ae050-136">2A： 散佈準備</span><span class="sxs-lookup"><span data-stu-id="ae050-136">2A: Preparation for Distribution</span></span><br /><br /> <span data-ttu-id="ae050-137">2B： 產品變更通知</span><span class="sxs-lookup"><span data-stu-id="ae050-137">2B: Product Change Notification</span></span><br /><br /> <span data-ttu-id="ae050-138">2c： 產品設計資訊</span><span class="sxs-lookup"><span data-stu-id="ae050-138">2C: Product Design Information</span></span><br /><br /> <span data-ttu-id="ae050-139">2D： 共同作業設計以及工程</span><span class="sxs-lookup"><span data-stu-id="ae050-139">2D: Collaborative Design & Engineering</span></span>|  
|<span data-ttu-id="ae050-140">3： 訂單管理</span><span class="sxs-lookup"><span data-stu-id="ae050-140">3: Order Management</span></span>|<span data-ttu-id="ae050-141">3A： 加上引號 （& s) 排序項目</span><span class="sxs-lookup"><span data-stu-id="ae050-141">3A: Quote & Order Entry</span></span><br /><br /> <span data-ttu-id="ae050-142">3B： 運輸及散布</span><span class="sxs-lookup"><span data-stu-id="ae050-142">3B: Transportation & Distribution</span></span><br /><br /> <span data-ttu-id="ae050-143">3c： 傳回與 Finance</span><span class="sxs-lookup"><span data-stu-id="ae050-143">3C: Returns & Finance</span></span><br /><br /> <span data-ttu-id="ae050-144">3D： 產品組態</span><span class="sxs-lookup"><span data-stu-id="ae050-144">3D: Product Configuration</span></span>|  
|<span data-ttu-id="ae050-145">4： 庫存管理</span><span class="sxs-lookup"><span data-stu-id="ae050-145">4: Inventory Management</span></span>|<span data-ttu-id="ae050-146">4A： 共同作業趨勢預測</span><span class="sxs-lookup"><span data-stu-id="ae050-146">4A: Collaborative Forecasting</span></span><br /><br /> <span data-ttu-id="ae050-147">4B： 存貨配置</span><span class="sxs-lookup"><span data-stu-id="ae050-147">4B: Inventory Allocation</span></span><br /><br /> <span data-ttu-id="ae050-148">4c： 清查報告</span><span class="sxs-lookup"><span data-stu-id="ae050-148">4C: Inventory Reporting</span></span><br /><br /> <span data-ttu-id="ae050-149">4 D： 存貨補充</span><span class="sxs-lookup"><span data-stu-id="ae050-149">4D: Inventory Replenishment</span></span><br /><br /> <span data-ttu-id="ae050-150">4E： 銷售報告</span><span class="sxs-lookup"><span data-stu-id="ae050-150">4E: Sales Reporting</span></span><br /><br /> <span data-ttu-id="ae050-151">4F： 價格保護</span><span class="sxs-lookup"><span data-stu-id="ae050-151">4F: Price Protection</span></span>|  
|<span data-ttu-id="ae050-152">5： 行銷資訊管理</span><span class="sxs-lookup"><span data-stu-id="ae050-152">5: Marketing Information Management</span></span>|<span data-ttu-id="ae050-153">5A： 領先機會管理</span><span class="sxs-lookup"><span data-stu-id="ae050-153">5A: Lead Opportunity Management</span></span><br /><br /> <span data-ttu-id="ae050-154">5B： 行銷陣營管理</span><span class="sxs-lookup"><span data-stu-id="ae050-154">5B: Marketing Campaign Management</span></span>|  
|<span data-ttu-id="ae050-155">6： 服務及支援中心</span><span class="sxs-lookup"><span data-stu-id="ae050-155">6: Service and Support</span></span>|<span data-ttu-id="ae050-156">6A： 提供以及管理員保證、 服務套件、 以及合約服務</span><span class="sxs-lookup"><span data-stu-id="ae050-156">6A: Provide and Administer Warranties, Service Packages, and Contract Services</span></span><br /><br /> <span data-ttu-id="ae050-157">6B： 提供以及管理員資產管理 （與 6A 合併）</span><span class="sxs-lookup"><span data-stu-id="ae050-157">6B: Provide and Administer Asset Management (Merged with 6A)</span></span><br /><br /> <span data-ttu-id="ae050-158">6c： 技術支援及服務管理</span><span class="sxs-lookup"><span data-stu-id="ae050-158">6C: Technical Support and Service Management</span></span>|  
|<span data-ttu-id="ae050-159">7： 製造</span><span class="sxs-lookup"><span data-stu-id="ae050-159">7: Manufacturing</span></span>|<span data-ttu-id="ae050-160">7A： 設計傳輸</span><span class="sxs-lookup"><span data-stu-id="ae050-160">7A: Design Transfer</span></span><br /><br /> <span data-ttu-id="ae050-161">7B： 管理製造 WO & WIP</span><span class="sxs-lookup"><span data-stu-id="ae050-161">7B: Manage Manufacturing WO & WIP</span></span><br /><br /> <span data-ttu-id="ae050-162">7 的 C： 散佈製造資訊</span><span class="sxs-lookup"><span data-stu-id="ae050-162">7C: Distribute Manufacturing Information</span></span>|  
  
 <span data-ttu-id="ae050-163">每個區段都包含數個特定的訊息 PIP。</span><span class="sxs-lookup"><span data-stu-id="ae050-163">Each segment includes a number of specific message PIPs.</span></span> <span data-ttu-id="ae050-164">例如，3A4 PIP 屬於「訂單管理」叢集 (叢集 3) 和「報價及訂單輸入」區段 (叢集 3 的區段 A)。</span><span class="sxs-lookup"><span data-stu-id="ae050-164">For example, the 3A4 PIP is a part of the Order Management cluster (Cluster 3) and the Quote and Order Entry segment (Segment A of Cluster 3).</span></span> <span data-ttu-id="ae050-165">這個區段包含其他相關的訊息 PIP，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ae050-165">This segment includes other related message PIPs, as follows:</span></span>  
  
 <span data-ttu-id="ae050-166">叢集 3： 訂單管理</span><span class="sxs-lookup"><span data-stu-id="ae050-166">Cluster 3: Order Management</span></span>  
  
-   <span data-ttu-id="ae050-167">區段 a: Quote 及排列項目</span><span class="sxs-lookup"><span data-stu-id="ae050-167">Segment A: Quote and Order Entry</span></span>  
  
    -   <span data-ttu-id="ae050-168">PIP 3A1： 要求報價</span><span class="sxs-lookup"><span data-stu-id="ae050-168">PIP 3A1: Request Quote</span></span>  
  
    -   <span data-ttu-id="ae050-169">PIP 3A2： 要求價格與可用性</span><span class="sxs-lookup"><span data-stu-id="ae050-169">PIP 3A2: Request Price and Availability</span></span>  
  
    -   <span data-ttu-id="ae050-170">PIP 3A3： 要求購物車轉移</span><span class="sxs-lookup"><span data-stu-id="ae050-170">PIP 3A3: Request Shopping Cart Transfer</span></span>  
  
    -   <span data-ttu-id="ae050-171">PIP 3A4： 管理訂單</span><span class="sxs-lookup"><span data-stu-id="ae050-171">PIP 3A4: Manage Purchase Order</span></span>  
  
    -   <span data-ttu-id="ae050-172">PIP 3A5： 查詢訂單狀態</span><span class="sxs-lookup"><span data-stu-id="ae050-172">PIP 3A5: Query Order Status</span></span>  
  
    -   <span data-ttu-id="ae050-173">PIP 3A6： 散佈訂單狀態</span><span class="sxs-lookup"><span data-stu-id="ae050-173">PIP 3A6: Distribute Order Status</span></span>  
  
    -   <span data-ttu-id="ae050-174">…</span><span class="sxs-lookup"><span data-stu-id="ae050-174">…</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae050-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae050-175">See Also</span></span>  
 <span data-ttu-id="ae050-176">[RosettaNet 與 CIDX 訊息標準](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-and-cidx-messaging-standards.md) </span><span class="sxs-lookup"><span data-stu-id="ae050-176">[RosettaNet and CIDX Messaging Standards](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-and-cidx-messaging-standards.md) </span></span>  
 [<span data-ttu-id="ae050-177">RNIF 標準</span><span class="sxs-lookup"><span data-stu-id="ae050-177">RNIF Standard</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/rnif-standard.md)