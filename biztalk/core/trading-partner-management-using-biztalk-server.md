---
title: 交易夥伴使用 BizTalk Server 的管理 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f31a5e49-ef19-41a3-9cf3-cf85d0685a59
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed1a3591314634c41cfd598aa074e497dd19ec03
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983719"
---
# <a name="trading-partner-management-using-biztalk-server"></a><span data-ttu-id="cdb37-102">使用 BizTalk Server 管理交易夥伴</span><span class="sxs-lookup"><span data-stu-id="cdb37-102">Trading Partner Management Using BizTalk Server</span></span>
## <a name="introduction-to-tpm"></a><span data-ttu-id="cdb37-103">TPM 的簡介</span><span class="sxs-lookup"><span data-stu-id="cdb37-103">Introduction to TPM</span></span>
<span data-ttu-id="cdb37-104">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 交易夥伴管理 (TPM) 對於如何管理與儲存夥伴和其業務的相關資訊，有著全新的基礎概念。</span><span class="sxs-lookup"><span data-stu-id="cdb37-104">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Trading Partner Management (TPM) rebuilds the fundamental concepts around how to manage and store information about partners and their business.</span></span> <span data-ttu-id="cdb37-105">增強的 TPM 方案會反映實際商場上的商務實體與關係，讓組織更容易管理與交易夥伴之間的業務合作關係。</span><span class="sxs-lookup"><span data-stu-id="cdb37-105">The enhanced TPM solution reflects the business entities and relationships in the field, thereby enabling organizations to better manage your business partnerships with trading partners.</span></span> <span data-ttu-id="cdb37-106">如需有關 TPM 方案如何塑造 BizTalk 環境中的之交易合作關係的詳細資訊，請參閱 <<c0> [ 交易夥伴管理解決方案的建置組塊](../core/building-blocks-of-a-trading-partner-management-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="cdb37-106">For more information on how the TPM solution models trading partnerships in a BizTalk environment, see [Building Blocks of a Trading Partner Management Solution](../core/building-blocks-of-a-trading-partner-management-solution.md).</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="cdb37-107"> 包含電子資料交換 (EDI) 資料交換與 AS2 資料傳輸的原生支援。</span><span class="sxs-lookup"><span data-stu-id="cdb37-107"> includes native support for Electronic Data Interchange (EDI) data exchange and AS2 data transport.</span></span> <span data-ttu-id="cdb37-108">這項支援讓企業能夠擴充以 EDI 為基礎的商務程序管理解決方案，並且充分利用自動化交換 EDI 交易所提供的產能改進優勢。</span><span class="sxs-lookup"><span data-stu-id="cdb37-108">This support enables businesses to extend their EDI-based business process management solutions, taking advantage of the productivity improvements that the automated exchange of EDI transactions provides.</span></span> <span data-ttu-id="cdb37-109">BizTalk Server 為企業提供使用 EDI 和 EDIINT/AS2 的方式，可以更安全、更可靠地將夥伴連接到重要供應鏈商務程序。</span><span class="sxs-lookup"><span data-stu-id="cdb37-109">BizTalk Server provides these businesses with the means to more securely and reliably connect partners to critical supply-chain business processes using EDI and EDIINT/AS2.</span></span>  
  
 <span data-ttu-id="cdb37-110">TPM 方案搭配 EDI 和 AS2 支援用於管理中的交易夥伴提供功能強大且可擴充的解決方案[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cdb37-110">The TPM solution coupled with the EDI and AS2 support provide a robust and scalable solution for managing trading partners in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="cdb37-111">本節中的主題 (和下方所列的其他主題) 對於 TPM 和如何使用 TPM 來管理交易夥伴，提供了高階概觀。</span><span class="sxs-lookup"><span data-stu-id="cdb37-111">The topics in this section, and other topics listed below, provide a high-level overview of TPM and how to use TPM to manage trading partners.</span></span> <span data-ttu-id="cdb37-112">這些主題也提供了關於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 如何執行 EDI 和 AS2 處理的說明。</span><span class="sxs-lookup"><span data-stu-id="cdb37-112">The topics also provide description of how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performs EDI and AS2 processing.</span></span>  
  
## <a name="in-this-section-and-more-good-info"></a><span data-ttu-id="cdb37-113">在本節與良好的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="cdb37-113">In this section and more good info</span></span>

<span data-ttu-id="cdb37-114">**了解，開始使用，和教學課程**</span><span class="sxs-lookup"><span data-stu-id="cdb37-114">**Learn, get started, and tutorials**</span></span>  

-   [<span data-ttu-id="cdb37-115">交易夥伴管理解決方案的建置區塊</span><span class="sxs-lookup"><span data-stu-id="cdb37-115">Building Blocks of a Trading Partner Management Solution</span></span>](../core/building-blocks-of-a-trading-partner-management-solution.md)  
  
-   [<span data-ttu-id="cdb37-116">BizTalk Server EDI 功能</span><span class="sxs-lookup"><span data-stu-id="cdb37-116">BizTalk Server EDI Functionality</span></span>](../core/biztalk-server-edi-functionality.md)  
  
-   [<span data-ttu-id="cdb37-117">BizTalk Server AS2 功能</span><span class="sxs-lookup"><span data-stu-id="cdb37-117">BizTalk Server AS2 Functionality</span></span>](../core/biztalk-server-as2-functionality.md)  

- [<span data-ttu-id="cdb37-118">EDI 和 AS2 解決方案架構</span><span class="sxs-lookup"><span data-stu-id="cdb37-118">EDI and AS2 solution architecture</span></span>](../core/edi-and-as2-solution-architecture.md)

-   [<span data-ttu-id="cdb37-119">環境最佳化的後續設定步驟</span><span class="sxs-lookup"><span data-stu-id="cdb37-119">Post-configuration steps to optimize your environment</span></span>](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md) 

- [<span data-ttu-id="cdb37-120">EDI、AS2 和 EDIFACT 的教學課程和逐步解說</span><span class="sxs-lookup"><span data-stu-id="cdb37-120">Tutorials and walkthroughs for EDI, AS2, and EDIFACT</span></span>](../core/tutorials-and-walkthroughs-for-edi-as2-and-edifact.md)


<span data-ttu-id="cdb37-121">**深入了解在建立 EDI 和 AS2 解決方案**</span><span class="sxs-lookup"><span data-stu-id="cdb37-121">**Deep-dive in creating EDI and AS2 solutions**</span></span>
- [<span data-ttu-id="cdb37-122">建立 EDI 和 AS2 成品</span><span class="sxs-lookup"><span data-stu-id="cdb37-122">Create EDI and AS2 artifacts</span></span>](../core/managing-edi-and-as2-solutions.md)

- [<span data-ttu-id="cdb37-123">開發和設定 BizTalk Server EDI 解決方案</span><span class="sxs-lookup"><span data-stu-id="cdb37-123">Developing and Configuring BizTalk Server EDI Solutions</span></span>](../core/developing-and-configuring-biztalk-server-edi-solutions.md)

- [<span data-ttu-id="cdb37-124">開發和設定 BizTalk Server AS2 解決方案</span><span class="sxs-lookup"><span data-stu-id="cdb37-124">Developing and Configuring BizTalk Server AS2 Solutions</span></span>](../core/developing-and-configuring-biztalk-server-as2-solutions.md)

-   [<span data-ttu-id="cdb37-125">EDI 和 AS2 SDK 的範例）</span><span class="sxs-lookup"><span data-stu-id="cdb37-125">EDI and AS2 SDK samples)</span></span>](../core/edi-and-as2-biztalk-server-samples-folder.md)  


 <span data-ttu-id="cdb37-126">**使用繫結檔案**</span><span class="sxs-lookup"><span data-stu-id="cdb37-126">**Using binding files**</span></span>  

- [<span data-ttu-id="cdb37-127">使用繫結檔案匯入或匯出為新的 BizTalk Server 2016</span><span class="sxs-lookup"><span data-stu-id="cdb37-127">Use binding files to import or export - NEW in BizTalk Server 2016</span></span>](../core/use-binding-files-to-import-or-export.md)  

-   [<span data-ttu-id="cdb37-128">如何匯出 EDI-AS2 解決方案的繫結</span><span class="sxs-lookup"><span data-stu-id="cdb37-128">How to Export Bindings for an EDI-AS2 Solution</span></span>](../core/how-to-export-bindings-for-an-edi-as2-solution.md)  
  
-   [<span data-ttu-id="cdb37-129">如何匯入 EDI-AS2 解決方案的繫結</span><span class="sxs-lookup"><span data-stu-id="cdb37-129">How to Import Bindings for an EDI-AS2 Solution</span></span>](../core/how-to-import-bindings-for-an-edi-as2-solution.md)  
  
-   [<span data-ttu-id="cdb37-130">自訂繫結檔案</span><span class="sxs-lookup"><span data-stu-id="cdb37-130">Customizing Binding Files</span></span>](../core/customizing-binding-files.md)  


<span data-ttu-id="cdb37-131">**監視和疑難排解**</span><span class="sxs-lookup"><span data-stu-id="cdb37-131">**Monitor and troubleshoot**</span></span>

- [<span data-ttu-id="cdb37-132">監控 EDI 和 AS2 解決方案</span><span class="sxs-lookup"><span data-stu-id="cdb37-132">Monitoring EDI and AS2 Solutions</span></span>](../core/monitoring-edi-and-as2-solutions.md)

- [<span data-ttu-id="cdb37-133">疑難排解 EDI 和 AS2 解決方案</span><span class="sxs-lookup"><span data-stu-id="cdb37-133">Troubleshooting EDI and AS2 Solutions</span></span>](../core/troubleshooting-edi-and-as2-solutions.md)
  
- <span data-ttu-id="cdb37-134">檢視 詳細資料 [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="cdb37-134">View UI details [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span> 
  
- [<span data-ttu-id="cdb37-135">EDI 和 AS2 事件與錯誤</span><span class="sxs-lookup"><span data-stu-id="cdb37-135">EDI and AS2 Events and Errors</span></span>](../core/edi-and-as2-events-and-errors.md)
 


  
